# Webpack 開発環境

## Table of contents

* [TypeScript + PostCSS](#typescript--postcss--pug)

## Webpack Configurations

### TypeScript + PostCSS + Pug

#### Packages

```
$ yarn add -D \
webpack webpack-merge webpack-dev-server path html-webpack-plugin mini-css-extract-plugin ts-loader pug-loader style-loader css-loader postcss-loader pug typescript sugarss postcss tslint stylelint \
tslint-loader friendly-errors-webpack-plugin \
optimize-css-assets-webpack-plugin uglifyjs-webpack-plugin
```

※ あくまでWebpackのビルドに必要なパッケージのみです

#### npm-scripts

```json
{
  "start": "NODE_ENV=development webpack-dev-server --config webpack.dev",
  "prod": "NODE_ENV=production webpack --config webpack.prod"
}
```

#### Files

|File Name|Overview|
|:--:|:---|
|`webpack.base.js`|環境によって変わらないベースの設定|
|`webpack.dev.js`|開発向けの設定|
|`webpack.prod.js`|本番向けの設定

##### webpack.base.js

```js
const glob = require('glob-promise');
const HtmlWebpackPlugin = require('html-webpack-plugin');
const MiniCssExtractPlugin = require('mini-css-extract-plugin');
const path = require('path');

const dist = path.resolve(__dirname, 'dist');
const isProd = process.env.NODE_ENV === 'production';

module.exports = {
  mode: process.env.NODE_ENV,

  entry: {
    app: [
      './src/scripts/entry.ts'
    ]
  },

  output: {
    path: dist,
    publicPath: './',
    filename: 'scripts/[name].js',
    sourceMapFilename: '[name].map'
  },

  module: {
    rules: [
      {
        test: /\.tsx?$/,
        exclude: /node_modules/,
        use: 'ts-loader'
      },
      {
        test: /\.pug$/,
        use: 'pug-loader'
      },
      {
        test: /\.sss$/,
        use: [
          isProd ? MiniCssExtractPlugin.loader : 'style-loader',
          {
            loader: 'css-loader',
            options: {
              importLoaders: 1,
              modules: false,
              sourceMap: true,
              url: false
            }
          },
          'postcss-loader'
        ]
      }
    ]
  },

  resolve: {
    extensions: ['.ts', '.tsx', '.js']
  }
};
```

##### webpack.dev.js

```js
const FriendlyErrorsWebpackPlugin = require('friendly-errors-webpack-plugin');
const path = require('path');
const merge = require('webpack-merge');

const baseConfig = require('./webpack.base');
const dist = path.resolve(__dirname, 'dist');
const port = process.env.PORT || 4300;

module.exports = merge(baseConfig, {
  devtool: 'inline-source-map',

  devServer: {
    clientLogLevel: 'warning',
    contentBase: dist,
    hot: false,
    inline: true,
    overlay: true,
    port,
    publicPath: '/',
    quiet: true,
    watchContentBase: true
  },

  module: {
    rules: [
      {
        enforce: 'pre',
        exclude: /node_modules/,
        loader: 'tslint-loader',
        test: /\.tsx?$/,
        options: {
          fix: true
        }
      }
    ]
  },

  plugins: [
    new FriendlyErrorsWebpackPlugin({
      compilationSuccessInfo: {
        notes: [`🎉 Build Success 👉 http://localhost:${port}`]
      }
    })
  ]
});
```

##### webpack.prod.js

```js
const MiniCssExtractPlugin = require('mini-css-extract-plugin');
const OptimizeCSSAssetsPlugin = require("optimize-css-assets-webpack-plugin");
const UglifyJsPlugin = require("uglifyjs-webpack-plugin");
const merge = require('webpack-merge');

const baseConfig = require('./webpack.base');

module.exports = merge(baseConfig, {
  optimization: {
    minimizer: [
      new UglifyJsPlugin({
        sourceMap: true
      }),
      new OptimizeCSSAssetsPlugin({})
    ]
  },

  plugins: [
    new MiniCssExtractPlugin({
      filename: 'styles/[name].css'
    }),
  ]
});
```

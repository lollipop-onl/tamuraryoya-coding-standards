# PostCSS 標準設定

## Required packages

```
$ yarn add -D postcss sugarss path autoprefixer postcss-calc postcss-hexrgba postcss-import postcss-nested postcss-reoprter postcss-simple-vars
```

## `postcss.config.js`

> with SugarSS

```js
const path = require('path');
const cssVariables = {};

module.exports = (context) => ({
  map: context.options.map,
  parser: context.file.extname === '.sss' ? 'sugarss' : false,
  plugins: [
    require('stylelint')({
      configFile: path.join(__dirname, '.stylelintrc.yml')
    }),
    require('postcss-import')({
      plugins: [
        require('stylelint')({
          configFile: path.join(__dirname, '.stylelintrc.yml')
        })
      ]
    }),
    require('postcss-nested'),
    require('postcss-simple-vars')({
      variables: cssVariables
    }),
    require('postcss-hexrgba'),
    require('postcss-calc'),
    require('postcss-reporter')({
      clearReportedMessages: true,
      throwError: true
    }),
    require('autoprefixer')({
      browsers: ['last 2 versions']
    })
  ]
});
```

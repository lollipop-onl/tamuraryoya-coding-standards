# StyleLint 標準ルール

# はじめに

* これはPostCSSでのStyleLintの設定です。Parserをつかわない場合は適宜読み替えてください

## 必須モジュール

```
$ yarn add -D stylelint stylelnit-config-sugarss-recommended stylelint-order
```

## 標準ルール

```
---
extends: stylelint-config-sugarss-recommended
plugins:
  - stylelint-order
rules:
  font-family-name-quotes: always-where-recommended # Font名のクォーテーションを省略する
  function-url-quotes: never # url()などの引数ではクォーテーションを省略する
  number-leading-zero: never # 1未満の場合は0を省略する
  order/properties-alphabetical-order: true # プロパティをアルファベット順に並べる
```

### 概要

* プロパティはアルファベット順に並べる
* １未満の0は省略する
* Font名のクォーテーションを省略する
* url()などの引数ではクォーテーションを省略する

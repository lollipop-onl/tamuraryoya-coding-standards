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
  number-leading-zero: never # 1未満の場合は0を省略する
  order/properties-alphabetical-order: true # プロパティをアルファベット順に並べる
```

### 概要

* １未満の0は省略する
* プロパティはアルファベット順に並べる

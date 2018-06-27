# TSLintの標準ルール

## はじめに

* TSLintを使用する際は可能な限りPrettierを併用し、`git add`時にも検証するようにする。
* `--fix`オプションを有効にする。
* **関係のないプロジェクトで暴発しないように注意する**

## tl;dr

* お作法系のスタンダードなものはPrettierとTSLintが自動整形してくれる
* クラスメソッドにはアクセス修飾子を必ず書こう
* 関数の返り値の型はvoidであっても必ず書こう
* （importやオブジェクトのパラメータはアルファベット順に並べる）
  - 引き継ぐ場合はこの指定を外す
* console系は許容される

## 必須モジュール

```
$ yarn add -D prettier tslint tslint-config-prettier tslint-plugin-prettier
```

## 標準ルール

```yaml
---
extends:
  - tslint-config-prettier

rulesDirectory:
  - tslint-plugin-prettier

rules:
  prettier: # Prettierの設定
    - true
    -
      arrowParens: always # Arrow Functionのカッコを付与する
      bracketSpacing: true # Objectのカッコの両側にスペースを付与する
      semi: true # セミコロンを付与する
      singleQuote: true # シングルクォーテーションに揃える
      trailingComma: none # ケツカンマをなくす
  class-name: true # クラス名をパスカルケースに強制
  member-access: true # public,protected,privateの付与を強制
  newline-before-return: true # returnの前に改行を強制
  no-boolean-literal-compare: false # Prettierがやってくれるので無効化
  no-console: false # デバッグするときにうるさいから許可
  no-inferrable-types: true # 型推論可能な場合は型を書かない
  no-string-throw: true # 文字列のthrowを禁止
  no-unused-expression: false # 使用していない変数の定義を許可
  object-literal-sort-keys: true # オブジェクトリテラルをアルファベット順に並べる
  prefer-method-signature: true # foo: () => voidではなくfoo(): voidを推奨する
  prefer-object-spread: true # Object.assignより分割代入を推奨する
  prefer-template: true # 文字列結合よりテンプレートリテラルを推奨する
  switch-default: true # switch文にdefault caseを強制
  switch-final-break: # switch文の最後にbreakを強制
    - true
    - always
  typedef: # 型の定義を強制する
    - true
    - call-signature # 関数の戻り値
    - parameter # 関数の仮引数
```

### 概要

* Prettierは以下の修正をしてくれる
  - Arrow Funcionにカッコを付与
    + `x => x * 100` → `(x) => x * 100`
  - Oneline Objectの両側にカッコを付与
    + `{x: 100}` → `{ x: 100 }`
  - セミコロンを付与する
    + `const a = 100` → `const a = 100;`
  - シングルクォーテーションに統一
    + `"hello world"` → `'hello world'`
  - ケツカンマをなくす
    + `{ a: 100, b: 200, }` → `{ a: 100, b: 200 }`

## 参考

* http://neos21.hatenablog.com/entry/2017/10/25/080000

# React Coding Standards

## Base of React

* ReactのImportは`import React from 'react'`とする
* Classの定義は以下の通り
  * `class SampleComponent extends React.Component {}`
* （任意） ComponentのExportは`export const Sample = SampleComponent`とする
  * 可能な限り`export default`は使用しない

### Constructor

* Contructor内での記述順は以下の通り
  1. `super(props)`
  2. Stateの初期化
  3. メンバーメソッドのバインディング
  4. DOMを参照・操作しない処理の実行

# Git Communications

より良い Git Life のために...

## Commit Message

### 絵文字

Commit Messageの先頭には絵文字を置き、絵文字だけで編集内容がわかるようにしましょう

|Commit type|Prefix|Emoji|Snippet|
|---|:---:|---|---|
|初めてのコミット|`init:`|:tada: `:data:`|`cminit`|
|機能追加|`feat:`|:sparkles: `:sparkles:`|`cmfeature`|
|ドキュメント、README|`docs:`|:books: `:books:`|`cmdoc`|
|アップデート|`update:`|:zap: `:zap:`|`cmupdate`|
|文章・タイポ|`text:`|:pencil: `:pencil:`|`cmtext`|
|開発環境・設定ファイル|`conf:`|:wrench: `:wrench:`|`cmconfig`|
|スタイル・デザイン|`style:`|:lipstick: `:lipstick:`|`cmstyle`|
|ブランチのマージ|`merge:`|:twisted_rightwards_arrows: `:twisted_rightwards_arrows:`|`cmmerge`|
|バグフィックス|`fix:`|:bug: `:bug:`|`cmfix`|
|Hotfix|`hotfix:`|:ambulance: `:ambulance:`|`cmhotfix`|
|WIP|`wip:`|:construction: `:construction:`|`cmwip`|
|Lint|`lint:`|:shirt: `:shirt:`|`cmlint`|
|コードレビューの反映|`review:`|:ok_hand: `:ok_hand:`|`cmreview`|
|多言語対応|`lang:`|:alien: `:alien:`|`cmtranslate`|
|GA・解析ツール|`analyze:`|:chart_with_upwards_trend: `:chart_with_upwards_trend:`|`cmanalytics`|
|よくないコード・応急処置|`bad:`|:hankey:　`:hankey:`|`cmbad`|

### メッセージ

コミットメッセージは**なんのためのコミットなのか**が伝わるような内容にしましょう

* 「どこ」を変更したかよりも「なぜ」変更したかを重視して書く
* 具体的すぎる変更内容はDiffでわかるので書かない

### 余談

#### 具体性

```
// Bad
> Fix bugs
> Add new class

// Good
> ヘッダーナビゲーションのボタンタップが正しく反応するようjQueryのセレクタ名を修正
```

#### 人間的意味

```
// Bad
> OLD_CONST2, OLD_CONST2を削除

// Good
> ver2.0で廃止した登録関連の古い定数を削除
```

### 参考

* https://dev.classmethod.jp/study_meeting/git-workshop-20180327/

## Pull Request

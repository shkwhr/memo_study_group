# JavaScript メタプログラミング勉強会@さくらインターネット metapro.es

## 概要
* 日時: 2018/02/20
* 場所: さくらインターネット


## session

-----
### メタプログラミングと生産性向上
* Speeker: @erukiti

#### メタプログラミング
##### とは
* ロジックを生成するロジック
* DBスキーマ定義からモデル、リポジトリパターン生成
* データモデルからSQL分を自動生成
* 関数を受け取って合成する関数
* Lisp: 構文を自分で定義
* Scala: マクロ
* テンプレート言語
* リフレクション
* 簡単に黒魔術化する

##### メタ？
* データを管理するための情報を付与する「メタデータ」
* 抽象化
  - 詳細をすて本質のみを抽出

##### 抽象度とメタプログラミング
* 抽象度が高い高レベルプログラミング
* 日常的に抽象化する作業はある

##### プログラマの生産性
* かかった時間に対する成果物
  - 指標が難しい
  - 相対的には算出できる
* 10~100倍の差を持つ人がいると言われる
  - 個々人の能力？
    - 同じ思考方法なら差はそれほど広がらないはず
  - スペックよりやり方の違い？
* 目標達成にとっていさ提言な工程だけを突き詰めればそれが最速なのでは？

##### よくある無駄
* その時点でやらなくていいことをやっている
* その時点でやってないといけないことをやっている
* 捨てた方が早い時に、無理に再利用する
* 冗長な設計、コード
* よりよい手法・道具があるのに知らない、使えない

##### 無駄を防ぐ
* 正しい工程管理
  - 戦略の謝りを戦術で取り戻さないことが重要
* よりこうりつてきな手段を選べるように手札を増やす
* その中から適切な選択をする

##### メタプロ種類
* リフレクション機能
  - メソッド呼び出しやプロパティアクセスをhackする
  - 本来取得しなくていい情報をを取得する
    - @reflet
    - 使わなくても実現できる…
* 静的なもの合わせ技
  - Babel
  - Webpack
  - peg.js
  - babel-register(require hack)

##### つかわなくても
* 関数型言語の設計は参考になる(メタプロ視点)
* 言語内DSL
* O/RMapperも
* メタプログラミングは選択肢の一つ

##### 感想
* 具象的なコードが増えると管理が大変
* 抽象化がすぎるとコードが難読化する
* 高レベルプログラムには性能的な無駄があるといわれてる
  - メタプロである程度防げるのではないか
  - 具象的なコードを減らす手段としてもっと評価されてもいいのでは？
* DRY, KISS, YAGNI

##### まとめ
* メタプロはプログラムをあつかうプログラム
* 難しそうだけどそうでもない
  - 場合によっては面倒だったり黒魔術化する
* 抽象と具象を行き来するのがプログラマ
  - 生産性がバランスの撮り方により大きく左右される

-----
### AST
* Speeker: @akameco

#### KILL ALL HUMANS
* 人間は必ず間違いを犯す
* 一貫性を保つのに向かない

##### ASTツール
* ESLint

##### codemod
* object.assign({})
  * reducer
    * つらい
* jscodeshift
  - facebook
  - ASTベースの変換ツール
  - Object rest spread
* react-codemod
  - bindをクラスプロパティに書き換える

##### 自分で作る場合は(ほぼreactの話)
* babel-codemod
* babel-react-optimize
* babel-plugin-macros
  - preval.macro
  - import-all.macro
  - ms.macroが参考になる
  - フロントエンドでfsとか使い放題

##### デメリット
* Babel前提



-----
### Swaggerファイルからnormalizrを手軽に使いたい
* Speeker: @Mt_blue81

##### normalizr
* 正規化ツールライブラリ

##### swagger
* API定義
* TheOpenAPI
* YAMLファイル

##### つくった
* YAMLからJSスキーマを作成

##### まとめ
* API定義ごとに書くコード量が減った
* リリース取り間違え不具合を減らせた
* 型定義も生成

-----
### TypeScript Compiler API で遊ぶ
* Speeker: @kstn

##### TypeScript Compiler API
* ASTを走査してコード解析
* ASTからコード生成
* 型チェッカーから情報取得
* astexplorerつかうといい

-----
### 5分でわかるbabel pluginの作りかた
* Speeker: @potato4d

##### メタプロ
* 実行時の注入なら簡単そう
* プロダクト導入は大変そう
* 静的解析便利そう

##### 作り方
* 作りたいものを決める
* Babelプラグインの初期設定をする
  - デフォルトでついてくる
  - CLIインターフェースとかオプションとか依存できる
  - yarn initからはじめれる
* 構文として何に属するかを調べる
  - ASTエクスプローラにコードを投げつける
* プラグインテンプレートを流用する
* Babel Plugin Handbookをみて調べる
* 書く
* 完成

##### 地検
* BableプラグインにするとJSパーワーを用意しなくていい
* ASTエクスプローラを使用すればなんとなくわかる
* ASTって構文の木をいしきする
* 置き換える系はTypeを調べればだいたいできる
* ASTエクスプローラー
* BablePluginHandbook
* babel@6プラグインの単純な作成方法について(Qiita記事)

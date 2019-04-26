# html5 confarence 2018

## 概要
* 日時: 2018/11/25
* 場所: 東京電機大学
*


## EveningActivity: LightningTalk


### 1000万以上の記事ページをAMPにした話
* Speaker: 平野昌士 @shisama_ (weblio)

#### AMP対応
* 速度改善
* SEO

#### どうやったか
* 段階的
  - <link>でAPMと非APMに分ける
* 有効なAMPページか検証
  - AMP Validator
* AMPコンポーネントを利用
  - 100種類くらい公開されている
    - 非AMPページにも有効


### PureScriptによるSPA開発
* Speaker: @e_ntyo

#### PureScript
* AltJSの1つ
* Haskelライクな関数型プログラミング
* 型クラス
* 圏論の世界の概念を利用できる

#### purescript-halogen
* VDOMを利用したPureScriptライブラリ
* 安全なSPA開発をすることが可能


### ビルドプロセスから考えるCSSアンチパターン
* Speaker: 今村謙士(カブク)

#### アンチパターン
* コンポーネントベースなのにCSSがグローバル
  - ページ表示が遅くなる
  - ポータビリティが下がる
  - CSSをコンポーネントに含める
    - CodeSplittingができる
* コードがDry、出力が非Dry
  - スタイルをコンポーネント化する


### Preload, Preconnectを使った最適化
* Speaker: 弥吉修英 @yayoc ファストリテイリング

### Preconnect
* DNS Lookup, TCPhandshakeなどを早期に行いコネクションロスを少なくする

### Preload
* 指定リソース早期に取得する(先読み)
* as fetch
  - APIリクエストも指定することができる
  - JSの実行前にリクエスト可能
  - 動的に挿入可能


### CSS組版の救世主Vivliostyle
* Speaker: spring-raining

#### CSS組版
* HTMLで原稿を書き、CCSSでページにレイアウト

#### Vivliostyle
* Webベースの組版システム
  - ブラウザの印刷機能でPDFを出力
* まだブラウザにない機能を先取り実装
  - W3Cにより将来標準化される可能性のある仕様だけ対応している
  - CSS Paged Media
    - ページ番号(footer系)
  - CSS Generated Countent for Paged Media
    - ページ番号、counterの参照


### みんながしらないブラウザの
* Speaker: こさまり @kosamari

#### Inputの話
* BrouserProcess
  - RenderProcess
    - Compositor
* イベントは欲しいけど横スクロールはそのままとかしたい場合
  - `{pass: true}`

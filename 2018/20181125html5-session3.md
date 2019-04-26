# html5 confarence 2018

## 概要
* 日時: 2018/11/25
* 場所: 東京電機大学
*


## WebComponentsのリアル
* Speaker: FRAME aggre @aggre_
* Slide:

### 近況
* モダンブラウザは対応
  - Edgeは一部開発中
    - Polyfillsである程度は動かせるようになる
  - Win8.1版IEは2023年までサポート…

### 基礎
* 仕様群
  - CustomElements
  - ShadowDOM
  - ESModules
* 基本
  - `<x-app>` tag
  - customElementsクラス定義
    - `windows.customElements.define(x-app, App)`
* CustomElements
  - 標準のコールバック機構を持ったクラス
    - constructor()
    - connectedCallback()
      - 親要素の子要素として接続された時
    - desconnectedCallback()
    - attributeChangedCallback()
      - 指定した属性値が変更された時
      - Domツリー構築時に属性が存在する時
    - adoptedCallback()
* ShadowDOM
  - 要素内にカプセル化されたDOMを追加
    - `Element.attachShadow({mode: 'open'})`
  - ShadowDomを持つ要素は子要素を表示しなくなる
    - `<slot>` 子要素を配置(表示)する

### 使い所
* プロジェクトを超える共通コンポーネント
  - 重複コードを防ぐ
* コンポーネントライブラリ
  - ライブラリを問わず使えるコンポーネント
    - いくつか公開されている
* マイクロフロントエンド
  - マイクロサービスをフロントエンドに持ち込む
    - 例) WCの中にReactを隠蔽する(WCの中身はReact)
  - ページの関心ごとと技術的関心ごとを分離する
  - モノリス:マイクロサービス
* SSR
  - ShadowDOMとslotを利用したHydrate不要のSSR
* 標準なので使えるところで使うべき

### 現実的な開発
* バニラでかく
  - 疲弊する
* lit-htmlを使う
  - polymer
  - lit-htmlアプリをWCにする
  - テンプレート更新処理の場合便利
  - FunctionalProgramingならlit-html
  - lit-elementが上位五感
* lit-elementを使う
  - lit-htmlベースのReactConponentのようなコンポーネントクラス
  - TypeScriptNative
  - lit-htmlのベネフィットを持ち込める
  - WCライフサイクルを熱い買いやすくしてくれる
  - `@property`で柔軟な属性値を扱える
  - DerectiveAPIが便利
  - 全てが関数、全てが型付き
  - Vue/AngularのようなHTMLと親和性、Reactのようなプログラマブルな文法
* Angular/Vueを使う
  - FWの機能によってWCを作る

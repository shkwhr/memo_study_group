# VueFesJapan

## 概要
* 日時: 2018/11/03
* 場所: UDX


## Vue.js と Web Components のこれから
* The Good relation between Vue.js and Web Components To the future
* Speeker: Takanori Oki(@takanorip)
* Slide: https://speakerdeck.com/takanorip/vue-fes-japan

## talk
### WebComponents
* Web標準技術
* カプセル化された概念
* Edge,IE以外はOK

### 特徴
* CustomElements
  - 独自の機能や見た目をもったHTML要素を定義できるようにする使用
  - カスタム要素
* ShadowDOM
  - DOMのカプセル化を実現するための仕様
    - Shadow Root,Tree (NodeTree)
* HTML Template
  - <tempates>要素を使用しHTMLドキュメントでHTMLの雛形を扱うための仕様
* ES Modules
  - 外部で定義されたカスタム要素を読み込む
  - HTML Imports仕様は廃止された
    - ES Modulesの仕様が安定しブラウザ実装が出揃った
    - GoogleChromeも2019春に削除よてい
  - HTML(CSS) Modules検討中
    - HTMLをJSの中に直接Importｓ可能にする仕様
      - html-loaderに似た機能をブラウザで

### How to build
* VueCLI 3 Build Targets
  - `--target wc`: Vue.jsのコンポーネントをWebComponentsに変換ビルド
  - `@vue/web-component-wrapper`
    - Vueコンポーネントをラップしてカスタム要素として登録
  - 作成したComponentをWeb Componentsにしたい時によい

### Why we use
* 機能面では劣っても負債を溜め込まない仕組み
1. 同じコンポーネントをどのライブラリでも使用できる
  - UIフレームワークを統一したい
    - Vue.js React.js ... で使用できる
  - FWを変更する場合UI部分を使いまわすことができる
2. 完全なScoped
  - Vue.jsでは完全なスコープではない
  - コンポーネントの依存がglobalに影響されない実装が可能
  - 属性値にString型しか渡せない
  - 外部から渡されるイベントのハンドリングが難しい
  - DOM要素の取り回しが面倒
    - 生DOMの取り扱い
  - CSS設計を大幅に見直す必要がある
    - 第一階層までしか当てられない
    - 自分の子要素のみに当てていく設計
  - 現状Vue.jsの機能を使ってコンポーネント作った方が現実的…
3. Micro Frontends
  - Webアプリケーションを機能の集合体としてみなす
  - 変更に対し柔軟なWebアプリケーション
    - WebComponentsならScopeを特定して変更が可能

### What will be become to
* Vue.jsはWebComponentに置きかえられる？
  - No.　目的が違うので共存するもの
  - WebComponentsはあくまでHTMLをカプセル化するもの
    - Webアプリケーションをつくるものではない
  - Vue.jsはアプリケーションを構築するもの

### まとめ
* production-readyだが課題も多い
* Vue.jsとWebComponentsは共存できる
* UIをWebComponentsに任せることで、負債をできる
  - マテリアルデザインのWebComponentsが作成中らしい

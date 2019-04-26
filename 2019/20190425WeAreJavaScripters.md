# We Are JavaScripters! @31th

## 概要
* 日時: 2019/04/25
* 場所: Retty
* #wejs


## session
-----
### Gatsby.js で導入事例をバシバシ読めるSPAなLPを作った話
* Speeker: @kikunantoka (giftee)
* Slide: https://speakerdeck.com/kikunantoka/gatsby-js-for-biz-lp-a5b9dafd-e9ea-453a-8989-6e3792ec7962

#### Gatsby.js
* 静的サイトジェネレータ
* React
* SAP
* 最近ホット
* markdownから生成

#### 導入背景
* XDに書いた内容を実現したい
* ホスティングはNetlify

#### 導入
* starterの選定
  - SemanticUI
  - 公式でも探せるもの
    - v2
- ひたすらコンポーネント実装
- ビジネスサイドはページを作る
  - コンポーネントサンプルがあるとつまづきにくい
* CSS
  - CSS Module
    - 他の案件で使用しているSaaSを流用
    - コンポーネントのjsファイルと1対1
      - コンポーネント側でスタイルの差分をカバー
        - 保守観点
* gatsby-image
  - 読み込みによるがたつきを防げる
    - 画像リサイズ・圧縮
    - レイジーロード
* ホスティング
  - Netlify
    - ビルドこけても本番は稼働状態
    - リダイレクト設定可能
      - 旧構成からの変更でも対応可能
    - 注意点
      - deploy preview
        - PR毎にPreview環境を作ってくれる
        - 消せず残り続ける…
* その他
  - GA、GTMもgatsbyプラグインがある

#### 完成品
* giftee.biz


-----
### CG in Web最前線
* Speeker: @kyasbal_1994 (修士生)
* Slide: https://speakerdeck.com/kyasbal1994/cg-in-web-zui-qian-xian-jin-sokodehe-gaqi-kiteirufalseka

#### WebGL
* GPUが使える
* Unityランタイムがリリースされた
* MRT
* iSOが2.0使えない…
* OffscreenCanvas
* 3DCGフォーマット: glTF
  - メタ情報はJSON
  - バッファはバイナリ
  - WindowsPaint3D
  - 他にはVRMも

#### 新時代
* WebGPU
  - iSO/macOSでのOpenGLが非推奨で
  - ドラフト中
  - 低レベルAPIと繋ぐ
  - マルチスレッド
  - 機械学習などにも応用できそう
* GameStreaming
  - STEDIA
  - W3C仕様作成が6月
  - 5G時代に対応
* WebXR DeviceAPI
* ImmersiveWebBrowser
* @altlayer_inc


-----
### javascriptはどのように動くのか？
* Speeker: @brn0227 青野 @brn(サイバーエージェント)
* Slide: https://speakerdeck.com/brn/how-javascript-works

#### 実行(変換)順
* Sourcecode
  - Parsing
    - パースしてツリーを作成
    - PreParsing
      - パースする必要のあるものを決める
* Abstract Syntax Tree
  - ツリーをなめてBytecodeを作成
* Bytecode
  - Interpreter
  - Pipelines
    - BaseLineJIT
      - アセンブラ
    - OptimizedJIT
      - BJITをさらに最適化
    - Deoptimize
      - 脱最適化
      - JSに型はないが内部で持っている
        - 頻繁に型を変える処理をすると遅くなる
* Binary


-----
### Google I/Oに備える Polymer Project最新動向
* Speeker: OkiTakanori @takanorip (Folio)
* Slide:

#### PolymerProject
* WebComponent利用手助け
* 作成
  - ライブラリ
  - テンプレート
* GoogleChromeプロジェクト
* 発表
  - Polymer3
  - LitElement
    - WebComponensを使いやすくするライブラリ
    - 1WayBinding
    - 軽量WebCベースクラス
      - TypeScript使用
    - Lit-HTML
      - 軽量なHTMLテンプレートライブラリ
      - ShadowDOM関係ない
      - VDOMは使っていないが静的解析して動的更新
      - HTMLTemplateInstantiationと近い実装
  - PWAStarterKit
  - MaterialWebComponents
    - MaterialDesignのWebComponents実装
      - まだ一部実装
    - LitElement
      - importで使える
* Polimer v1 がChromeから近々削除される
  * LitElementへ？？？


-----
### Web Components時代に備える Aureliaのすすめ
* Speeker: @panchan9 濱田(Voicy)
* Slide:

#### WebComponents
* ライブラリやフレームワークがやっていたことがブラウザネイティブで
* 再利用可能な独立したコンポーネントの生成
  - フレームワークを超えたコンポーネントの共有
  - BEMなどを使わずにCSSScope化
* 推し
  - Aurelia(Aureliaの人)
    - WebStandardに準拠


-----
### 書いて覚えるUtilityTypes
* Speeker: @yamatatsu193
* Slide: https://slides.yamatatsu193.net/typescript/

#### 実演
* Typesの説明と実演


-----
### NextRedux と unstated
* Speeker: @okamuuu
* Slide: okamuu.com

#### Redux
* 純粋関数にこだわりすぎ
* 非同期処理がややこしい
* 状態管理が必要

#### 大事なこと
* 要件を満たす
* 属人化させないこと
* 強いチーム

#### unstated
* stateの管理をReactでできるようになった
* ContextAPIを拡張したライブラリ
* 学習コストが低い
*


-----
### やさしい仮想
* Speeker: RyoNkmr_
* Slide: https://speakerdeck.com/ryonkmr/yasasiijia-xiang-dom

#### 仮想
* JSX
  - preset-react
* DOM
  - DOM Tree
    - HTMLを階層化
* DOM API
  - JSとDOM Treeを繋ぐ操作
* 仮想DOM
  - DOMの設計書
* jQuery
  - 併用してはいけない
    - 仮想DOMとの同一性(差分)が取れなくなる



-----
### JavaScript binary data handing 101
* Speeker: @chikoski
* Slide:

#### binary
* DataView
* データは数値に紐づけられる
  - 集めたものがbinary
  - (巨大な)配列
    - ではない
  - エンディアン(データを突っ込まれる順番)に気をつける必要がある
    - どこにも書いてない
      - CPUの仕様書
      - ファイル形式仕様
        - ByteOrder
* JSでも扱える
  - デバッグ大変…



-----
### a
* Speeker:
* Slide:

#### a
* a

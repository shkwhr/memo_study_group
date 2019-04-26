# VueFesJapan

## 概要
* 日時: 2018/11/03
* 場所: UDX


## note のフロントエンドを Nuxt.js で再構築した話
* Speeker: 福井 烈
* Slide: https://note.mu/r82/n/ne217ba36d233

## talk
### SPA課題
* 初期表示の遅さ
* 技術的制約
  - Angular.js1
  - Railsの上に乗ったフロントエンド
* 技術的負債
  - コーディング規約

### 技術選定要件
* SSR
* 学習・運用コスト
  - デザイナーへの配慮
* 開発・コミュニティーの活発さ

### Vue.js採用理由
* 実行速度と開発効率の両立
* 学習コストの低さと親しみやすさ
* ドキュメントの充実度
* 国内コミュニティの活発度
* Vue.jsエキスパートをコンサルに

### Nuxt.js
* 規約が手に入る
* モダンな環境が手に入る(Vue.js)

### 移行
* APIはRoR
* ViewをNuxt.jsでリプレイス
* 既存UIを確実に移行させる
  - 大幅な変更はしない
* 苦労
  - 並行して現行版(angular)の改修は続く

### 状況
* コンポーネント数:216
* Lighthouse: 3 -> 41
* WebPageTest: StartRender等初期表示系スコアがほぼ倍の改善

### コンポーネント設計
* Vuex&AtomicDesign
* Vuex
  - モジュールモード
  - mutations/actions/gettersのタイプには定数を使用
  - ストアに状態をもたせる基準設定
  - モジュール肥大化問題
    - Nuxt.js v2 でファイル分割可能に
    - それでもモジュール分割が必要そう
* AtomicDesign
  - コンポーネントでデザイン
  - レイヤーの責務がある程度明確に
  - Atomsルール
    - 内部に他のコンポーネントを持たない
    - 再利用を加味
    - Vuexモジュールへの参照させない
  - Molecules
    - 内部に他のコンポーネントを持たない
    - 再利用を加味
    - Vuexモジュールへの参照させない
  - Organisms
    - Vuexモジュールへの参照可
* StoryBook
  - ストーリーのメンテナンスが大変

### ユニバーサルJS
* クライアントとサーバどちらでも動く
* SSR必須
* DocumentAPIが使えない
  - jadom: DOM APIパーサパッケージ

### Polyfill.io
* UserAgent毎にひつようなPolyfillだけをまとめて配信

### Infrastructure
* AWS Lambda
  - FaaS
  - HTTPSクエリをトリガ
* トレードオフ
  - バージョンがLambda依存
  - デプロイできるパッケージ容量(50M)
  - cold start問題

### まとめ
* パスベースで小さく移行するのは有効
* Nuxt.jsのSSR導入は簡単
  - Node.jsの運用が必要になる
* 環境基盤のサポート・規約が非常に協力
  - 本質的な開発に集中できる
* https://note.mu/noteeng/m/me7637ba82821

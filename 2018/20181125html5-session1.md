# Laravel/Vue.js勉強会#6

## 概要
* 日時: 2018/11/12
* 場所: 株式会社 レアジョブ
* Tag: #laravue


## a
* Speeker: ZOZO
* Slide:　a

### 問題
* 状態管理
  - Single source of truthを実現できていなかった
    - 　Stateを信頼できる唯一の情報としなかった

### アーキテクチャにおける理想と現実の乖離
* 理想
  - プレゼンテーション層とアプリケーション・データ層の完全な権限分離
* 解決方法
  - フロントエンドにプレゼンテーション・アプリケーション層を持たせる
    - 再実装しなおす必要がある
      - クロスプラットフォーム実装
        - ReactNative,Flutterとか
          - WebViewベース動作は重い
        - Kotlin/Native, Kotlin/JS
          - セキュリティを考えると難しそう
            - 認証ロジック
            - インフラ層へのアクセス
              - ロジックが残る
    - 現実的でなさそう…
  - フロント・バックエンドに３層をそれぞれ持たせる
    - クリーンアーキテクチャの思想
      - 外の円は内の円に依存
      - DBなどのインフラに依存する部分もUI同様外側として定義
      - プレゼンテーション層やデータ層への依存に該当する部分がInterfaceAdapterという形で抽象化

### 実装
* Vue.jsのコンポーネントがUseCaseを梱包
* domain配下にRepositoryの抽象クラス、Entityなどを配置
  - Apprication層はいかにサービスやモデルを配置
  - Interface配下にVue.jsのコンポーネントとVuexに属するものを配置

### APIに求めること
* フロント
  - APIリクエストを複数行いたくない
* バック
  - できる限りシンプルにしたい

### 案
* Backends For Frontends
  - FEとBEの中間処理
  - 実装の手間が減るわけではない
  - 経由するサーバーが増えるためパフォーマンスに影響がある
* GraphQL
  - フロント: １回で必要なデータが得られる
  - バック: ドメインロジックに集中して開発できる

### まとめ
* EndPointによって異なる型
  - リソース単位で管理ではなくPage単位
* 状態の変更を含むAPIを利用する際に起こる不具合
  - 状態の変更を検知できず、自動的に更新されない
    - レスポンスで変更したリソースを返す
      - API内部で非同期に変更される場合に対応できない
    - ポーリング
      - 定期的にAPIリクエスト、最新の状態を反映
        - リアルタイム性を増すほどサーバ負荷が大きくなる
    - サーバ側から変更をプッシュ
      - WebSoket
      - Server-sent Events
      - gRPCの双方向ストリーミング
      - クライアントの増加に伴うコネクションの増加について考慮が必要
    - サーバ側での状態の変更検知についての考え
      - バックエンド含めての大きな改修が必要
      - コストに見合うだけの価値があるかの検討が必要
### Vuexのつかいかた
* State単位でのかんりをやめPage単位で管理
* ヘッダーなどのサイト全体で共通のものはcommonネームスペースで管理


### まとめ
* Vuex利用方法を最高
* クリーンアーキテクチャの考えを導入
* チームの状況に即したアーキテクチャの選定が重要

# CI/CD TestNight #2

## 概要
* 日時: 2018/11/08
* 場所: DeNA


## CI/CD Test on ReRep
* Speeker: @Spring_MT(DeNA ReRep)
* Slide:　https://speakerdeck.com/spring_mt/ci-cd-test-on-rerep

### Development Policy
* 便利なツール
  - Fastly
  - CircleCI
  - BitriseCLISentry
  - Firebase
* EnvironmentParity
  - 成果物の同一性
    - 挙動の同一性
    - Stateless & Immutable
      - クライアントでは難しいが検討して対応
  - インフラの同一性
    - 同じDocker環境で動作すること

### CI/CD Test
* 成果物
  - Server
    - DockerImage
  - Client
    - ipa
    - apk
  - ContentsDataForservice
* ポリシー
  - リポジトリにpushするタイミング
  - 成果物は全て保存
  - デプロイできる状態で保存
* CI
  - Tool
    - Server: CircleCI
      - シンプルで手軽さを重視した
      - 1. github
      - 2. CircleCI
      - 3. GCI
    - client: Bitrise
      - Bitrise Workflow
        - 1flow 17min
* Test
  - UT
    - Server: rspec
    - Client: No test yet
  - テスト専門QAチームあり
* CD
  - 主導
### まとめ
* サーバトラブルはほとんどない
  - バグもほとんどない


## 私がAndroid CI/CDをBitrise/CircleCIに移行して得られたもの
* Speeker: nemoto_tadashi(メルカリ)
* Slide: https://speakerdeck.com/tadashi0713/cdwo-bitrisecirclecini-yi-xing-sitede-raretamofalse

### CircleCIからBitriseに移行した
* PlayStoreデプロイ オペミス対策で
* GUIから可能（簡単)

### BitriseからCircleCI2.0に一部移行した

### 学んだこと
* Done is better then Perfect
  - 他のCIサービスで苦労するよりbitriseでとりあえずデプロイだけで始めれる
* 徐々にコード化していく
  - GUIだけに頼りすぎるとツラミも出てくる
    - ローカルで実行できない・しづらい
    - 他のCIサービスが試しにくくなる
  - fastlaneを使って徐々に移行
    - コード化 < 自動化
    - ある程度ワークフローが決まってからでも十分
* 組織・チームの状況に合わせていく
  - 組織が大きくなるとCIの待ち時間が増える
  - CircleCI
    - PR単位でのJOBの並列実行
    - 職人芸になりがち


## アプリの検証がどのくらい行われているか調べてみた
* Speeker: @henteko07(DeplyGate)

### CDってなんでやるんだっけ？
* 品質を高める
  - コストを最小化
  - 検証回数を増やす
* フィードバックをもらう機会を増やす
  - アプリ配布の自動化
  - インストールを手軽に
  - フィードバックの精度を高める


## React NativeアプリをBitriseでCDする
* Speeker: れこ(ShingoInoue CureApp blog.leko.jp)

### Bitriseデプロイ
* Github
  * Bitrise
    - PlayStore
    - iTuens
  * circleci
    - AWS
### Bitrise
* 目標
  - ビルド
  - デプロイ
* 公式ステップを使う
* git tab で push


## 社内ライブラリのアップデートフロー
* Speeker: Ryo Sakaguchi(@wakwak3125 wantedly)
* Slide: https://speakerdeck.com/wakwak3125/she-nei-raiburarifalseatupudetohuro

### 考えてる
* Repository
  - どこにライブラリを配信する？
    - AWS S3 採用
  - セキュア？
    - 社内ネットワークからのみアクセスできるようにする
      - 社外からはVPN
      - CIからはクレデンシャル
* Update
  - 常に最新のものを安全に使いたい
    - 安全なフロー
      - push -> github -> Bitrise -> PR -> UT Test
      - 更新に気づける
        - PRが投げられるから
      - UIテストが実行できる
        - スクショでPRで差分チェック
      - 常に最新のデザインアップデートを取り込める
        - デザイナの意思を最速で反映できる


## CI/CD専用モニタと心理的安全性
* Speeker: nakasho(@nakasho_dev)
* Slide: https://www.slideshare.net/shinyanakajima37/cicd-122405581

### CIの価値
* リスクを提言する
* 繰り返し手作業を削減
* いつでも、どの環境にもデプロイ
* プロジェクトの可視性を改善
* 開発チームの自信を深める

### CI/CD専用モニタ
* チーム全員がプロダクトの状況が理解できる
* タスクが動作していることが確認できるので自信を持てる
* 正常だと安心できる
* 問題が発生した際は誰かがすぐに気づける
  - Slackよりも
* コミュニケーションが生まれる
* チームの心理的安全性が高まる

### Pipeline表示
- 一目で状況がわかる
* ConcoursePipeline
* JenkinsPipeLine
* AzurePipelines
* BitrizePipeline

### まとめ
* CI/CDは最高のチームを作るという目的
* プロダクトの状況はチーム全員がわかるようにする

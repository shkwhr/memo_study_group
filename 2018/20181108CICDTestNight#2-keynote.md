# CI/CD TestNight #2

## 概要
* 日時: 2018/11/08
* 場所: DeNA
* #cicd_test_night


## title
* Speeker: Viktor Benei
* Slide: https://docs.google.com/presentation/d/1YQWmngGvttZp9-NwCo4OTjPPOx79iJTNFSXcE1iDSA4/edit#slide=id.p

## Session
### Agenda
* Automate Everything
* Flank
* Roadmap
* Annoucement and Q&A

### Bitrise
* mobile ci/cd プラットフォーム
* 自社で抱えている問題を解決する形で成長

### Automate Everything
* 全てを自動化するプラットフォーム
  - マニュアルタスク
    - 高コスト
    - 時間がかかる
  - 自動化
    - 複雑なタスクも簡略化
    - 時間の節約
    - プロセスの継続
    - 効率化
  - manyuaru deyatteirukoto wo 記述する
  - bitrise.io 自動化
* Steps
  - 構成要素を集めて実行
  - OSS化している構成要素
* BitriseCLI
  - ローカルで実行が可能
    - デバッグも可能
  - $ bitrise init --minimal
  - $ bitrise run workflow-id
  - Bitrise.ioから設定ファイルダウンロード可能
* iteration
  - 変更は常に発生する
    - 常に更新し続ける必要がある
  - BitriseCLIでバージョン管理が可能
  - $ bitrise :workflow-editor

### Danger
* OSS
* チェック対象の指定ができる
  - Danger + ktlint
  - UT対象か
  - PullRequest size のcheck

### iOS Code Sining
* iOSコードサイニングの自動化
  - 非常に難しい
* AutoProvisionig

### Bitrise.io API
* Parallel builds
* Pass parameters to builds
* Abort with Success

### Flank
* OSS
* FirebaseTestLabのパラレルテストランナー
  - Android
  - iOS
* 複数のTestCaseを複数のデバイスに分けて実行できる
  - テストの効率化
  - 過去の実行からコストの振り分けをやってくれる
- コストレポートを作成
- HTMLレポート
- JUNIT XML レポート

### Bitriseロードマット
* Firebaseアカウントなしで実行可能に
* Dashboardの改良
* OSS Support
* Public / Private
* 2FA
* New build system

### Bitrise for the Enterprise
* Hosting
  - private cloud
    - ニーズに従ったビルド構成
  - on premise
* Support
  - 英語以外のサポートも(Premium support)
  - customer Success engineer
* Security

### for Japan
* 関心が高まれば東京に2つ目のデータセンター設置
* 日本語サポートも
* 日本語コミュニティーが活発
* 日本から提供する
  - Contributors
  - Ambassadors
  - Events
* 日本での採用開始
  - CustomerSuccessEngineer

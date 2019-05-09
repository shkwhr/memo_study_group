# Tech Lead Engineerから最新技術を学べ！Laravel編

## 概要
* 日時: 2019/05/08
* 場所:
* https://shuuu-mai.connpass.com/event/127158/
* #shuuumai


## session
-----
### Laravel EchoとPUSHERでリアルタイムを手に入れる
* Speeker: 鳩 洋子氏＊株式会社プラムザ Tech Lead
* Slide: https://speakerdeck.com/fromarm4/make-it-happen-in-realtime-with-laravel-echo-and-pusher

#### データー同期
* Polling
  - メリット
    - 実装が楽
  - デメリット
    - リアルタイム性に欠ける
    - 通信量の増加
    - サーバー不可
* LongPolling
  - メリット
    - リアルタイム性の工場
  - デメリット
    - サーバの同時接続数が増える
    - 更新頻度が高い場合変化に弱い
    - HTTPコネクションが占有される
* ServerSentEvents
  - メリット
    - Web標準
    - 接続がきれない
      - 再接続
  - デメリット
    - サーバー負荷が高い
    - IE/Edgeが対応していない
    - 通信がHTTP
* WebSocket
  - メリット
    - 専用プロトコル
    - 双方向通信
    - 通信コストが低い
  - デメリット
    - 専用サーバーが必要
    - コネクションを保持し続ける

#### 問題
* インフラ作業が増える
* 顧客要望はコストほど高くない

#### PUSHER
* WebSoketを使ったPush通知専用サービス
* LaravelEchoを使って実装できる
* 有料
  - 自前でWebSocketサーバーで代替可能

#### Firebase
* 無料の通知サービスがある
  - が、CORSエラーがでるので有料プラン…
    - オリジン間リソース共有(Cross-Origin Resource Sharing)


-----
### SOLID Principles in Laravel
* Speeker: 濱崎 竜太氏＊株式会社クラシコム Tech Lead
* Slide: https://slides.com/avosalmon/solid-principles-in-laravel#/

#### SOLIDの原則
* SingleRepositoryPrinciple
  - 1つのクラスは1つのことだけに責任をおう
  - クラスを変更する理由は複数存在しなければいけない
  - 責任を適切に分けることで読みやすくメンテしやすいコードになる
* OpenClosedPrinciple
  - 新しいコードをゼロから書くより既存のコードにロジックを追加する機会の方が多い
    - 肥大化
    - 複雑化
  - 新規コードを書く感覚で素早く安全に機能を追加できるようにする
* LiskovSubstituionPrinciple
  - あるクラスがInterfaceに依存している場合そのInterfaceを実装したclassであればどれでも置き換え可能であるべき
* InterfaceSegmentationPrinciple
  - インターフェイスに詰め込みすぎない
* DependencyInversionPrinciple
  - インターフェイスに依存しましょう


-----
### サービスコンテナの実践的な活用
* Speeker: 荒井 和平氏＊株式会社M&Aクラウド CTO
* Slide: https://speakerdeck.com/kazuhei0108/sabisukontenafalseshi-jian-de-nahuo-yong

#### ServiceContainer
* DIコンテナーの役割
  - インスタンスの生成
- 生成を分離できる
  - テスト時に便利

#### 積極的に使う設計
* データクラスに依存しないドメインクラスを作る
  - ModelをDomainにマッピング
* Interfaceを活用
  - リポジトリパターン


-----
### Laravel×DevOps －インフラ構築の自動化から運用ログの監視まで－
* Speeker: 吉田 紳一郎氏＊株式会社スタジオ・アルカナ／株式会社ナシエルホールディングス CTO
* Slide: https://www.slideshare.net/yossy222/laraveldevops-144306354

#### Laravelアーキテクチャ問題
* バリデーションを実行する責務
  - Requestクラスの拡張
* 権限チェック・認証の責務
  - Middleware
* ヘッダ・フッタ共通処理
  - ViewComposer
- サービスレイヤー導入
  - ビジネスロジック
* リポジトリレイヤー
  - RDBへの依存度を抽象化

#### インフラ構成
* AWS
  - .envはAWSのサービスによせた
* ローカルはchefで共通構築可能な状態に
  - レシピは本番と共通
* Gitflow
  - developにmergeするとstagingへdeploy
    - AWS OpsWorks

#### 監視
* Laravelデフォルトログ
* HTTPリクエストログ
* メール送信ログ
* Apacheエラーログ
* NgnXエラーログ
* MySQLエラーログ
* サーバー状態
* 通常アラートはメール通知
  - AWS CloudWatch
  - AWS SimpleNotificationService
* 緊急アラートはSlack通知
  - 通常アラートと同じ仕組み

-----
### a
* Speeker:
* Slide:

#### a
* a


-----
### a
* Speeker:
* Slide:

#### a
* a


-----
### a
* Speeker:
* Slide:

#### a
* a


-----
### a
* Speeker:
* Slide:

#### a
* a


-----
### a
* Speeker:
* Slide:

#### a
* a


-----
### a
* Speeker:
* Slide:

#### a
* a


-----
### a
* Speeker:
* Slide:

#### a
* a


-----
### a
* Speeker:
* Slide:

#### a
* a

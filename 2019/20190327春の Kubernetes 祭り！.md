# 春の Kubernetes 祭り！

## 概要
* 日時: 2019/03/27
* 場所: 富士通クラウドテクノロジーズ株式会社


## session
### Kubernetesを運用してきた半年間でハマったこと
* Speeker: 株式会社サイバーエージェント 浦野紘一氏(https://qiita.com/lanocci)
* Slide: https://speakerdeck.com/lanocci/how-ive-operated-kubernetes-on-prod-for-half-a-year-fjct-meetup-on-kubernetes-number-14

#### 注意
* 環境はGCP
* サイバーエジェントadtech studioでのお話
* アプリはscala

#### よかったところ
* リリースが楽
  - ローリングアップデート
    - 無停止更新
  - GitOpsとの親和性が高い
    - weaveworks社提唱
      - Gitを唯一の真実の情報源とする
      - アプリコードとインフラ設定を全てGit管理
  - カナリアリリースとの親和性が高い
* VMにくらべてリソースの最適化が楽
  - オートスケーリング
    - Horizontal Pod Autoscaler
    - 目標とする指標をしておけば、自動でスケールアウト/インしてくれる
      - CPU
      - メモリ
      - リクエスト数
      - etc
* エラー対処が減った
  - ヘルスチェック
    - livenessProde
    - Podが健康であるとみなす条件を定義
    - 自律的に再生成してくれる
* 性能も良好
  - リクエスト90%以上を15ms以内に返せている

#### 悪いところ
* RollingUpdateしてるはずが
  - リリース中にレスポンス返せない時間が発生していた
  - Pod作りすぎ疑惑
      - RollingUpdateStrategy
        - maxSurge
        - maxUnavailable
      - ダメだった
  - 稼働可能状態になる前にリクエスト振られてる疑惑
    - JVM稼働条件
    - ReadinessProde
      - Podトラフィックを受けられる条件を定義
    - 解決
* 古くなるk8sのバージョン
  - いつの間にか使ってるK8sのバージョンがサポート対象外に…
    - Nodeのバージョンをあげるには再起動しないといけない
      - 再起動で一気にPodが死んだら困る…
    - PodDisruptionBudget
      - DeploymentごとにいくつまでPodを落としていいか定義

* Podが偏ってる
  - ある種類のPodが特定のNodeに偏る
    - Inter-pod anti affinity
      - 分散して配置させる定義
* システム系Podが落ちてる
  - リバースプロキシが落ちていてPodへのアクセスに失敗する
    - 問題のあるPodを削除すれば自動再作成される
      - 障害の切り分けが難しい
        - GKEならstackdriver
        - watchdog

#### 日々気をつけていること
* チームで勉強会
* ドキュメント共有
  - scrapboxおすすめ
* 自動化
  - kubectlをなるべき人間が叩かないようにする
    - GitOps
    - Jenkinsを使ったオペレーション自動化

#### まとめ
* リリース作業が簡単で安全
  - 高速リリース
* 自律的な正常な状態を維持してくれる
  - 定義が必要
  - 省力運用
* 問題は色々でてくる
  - K8sの機能でだいたい対応できる

-----
### ニフクラにk8sを入れてみた
* Speeker: 日本仮想化技術株式会社 宮原徹氏
* Slide:

#### Hatoba(β)つかってみた
* クラスターを作成
  - リージョンはコンピューティングとリージョンは別
    - マニュアルに書いてある…
* kubectlを使えるクライアント用意しないといけない

#### ニフクラにk8s入れるポイント
* DNSの設定
* UFW設定

#### 感想
* 検証済み手順を教えてもらってやったので簡単だった
* ネットワーク周りはまだよくわからない
* 本番運用を考えるとなかなか大変そう
* 次回hatobaに入れる手順を作りたい…


-----
### ニフクラ Hatoba（β）リリース！！
* Speeker: 富士通クラウドテクノロジーズ株式会社 世良迪夫
* Slide:

#### ニフクラ
* VMWareベースのインフラ基盤をクラウド提供
* 10年目
* 利用6500件
* IaaS/PaaS領域を中心にラインナップ

#### コンテナ/K8sがもたらす変革
* リソース最適が・スケーラブル
* 高可用・高稼働

#### ニフクラHatoba
* コンテナ積載の拠点になるサービス
* ニフクラ上にマネージドなK8sクラスタを作成可能
* まだclosedベータ
  - 法人向けなので…
  - 本番で使用しないで…


-----
### k8sを拡張する方法のまとめ
* Speeker:　@kuromt_(富士通研究所)
* Slide:

#### k8sの基本的な処理の流れ
* ReconciliationLoop
  - Controllerがリソースを望む状態に近づける
  - 検知、確認、実行
* AdmissionController
  - 認証、認可を済ませた後にリクエストをハンドルする拡張
* CustomResourceDefinition
  - APIServerに独自のリソースを登録する仕組み
  - 対応するControllerを自分で実装する必要がある
* AggregatedAPIServer
  - APIServerの役割を持つサーバーを別途用意する拡張
    - AggregatedLayerがプロキシとして振る舞う

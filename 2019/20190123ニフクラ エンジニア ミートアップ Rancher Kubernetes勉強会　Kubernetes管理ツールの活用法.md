# ニフクラ エンジニア ミートアップ　Rancher/Kubernetes勉強会　Kubernetes管理ツールの活用法

## 概要
* 日時: 2019/01/23
* 場所: 富士通クラウドテクノロジーズ株式会社


## session

-----
### Rancherでサクサクコンテナ管理！〜Rancherならk8sも怖くない〜
* Speeker: Rancher Japan　新藤　洋介(Shindo Y)

#### Rancher
* Rancherを立ち上げてどこにプロビジョンするかをする
* コンテナ管理ツール
* RancherOSもある
* DockerをGUIで管理
* クラウド・オンプレをまたいで管理することができる(インフラの基盤差異を保管)
* PasSは導入箇所がブラックボックス・ロックインされてしまう
* Licence
  - パートナー経由
* Support
  - rancher support maintenance でぐぐる
* コミュニティ
  - rancherjp.coｍｍpass.com
  - #rancherjp


### Kubernetesで変わるインフラ
* Speaker: スタイルズ　矢野　哲朗(FB: tetsurow.yano)
* Slide:

#### Kubernetes
* Dockerコンテナをオーケストレーションするツール
  - コンテナを動かすための整備を行うツール
* アプリケーションのプロセスを複数・複合管理し、動作させ必要な環境情報も管理する
##### できること
* 統一したインターフェースとファイルで設定・管理・自動化してくれる
* マニュフェスト
  - 冗長化
    - サービスロードバランス
  - 負荷分散
    - オートスケーリング
  - アプリ更新
    - コンテナ ローリングアップデート
    - コンテナ ロールバック
  - HA構成
    - セルフヒーリング
  - 死活監視
  - log監視
  - リソース監視
  - アプリ設定(config map)
    - 設定の自動ロード
  - cron(ジョブ)管理
  - IPアドレス管理
  - 内部DNS管理

#### 変わるインフラ
* Google
  - KubernetesはクラウドのLinuxになりつつある
* CentOS ->　UbuntuいれてKubernetesになる？
* 設定はYAML
* ハード面は変わらない
* 管理・監視・運用がかわる

#### Kubernetes特徴
* Immutable Infrastructure
  - 変更を積み重ねず、都度作る/作り直す
    - 手順書よさようなら
* 宣言的設定
  - あるべき姿を宣言し、その姿に収束する
    - マニフェストが全て正
    - インフラの全てをコード化する
* 自己修復
  - どこかが壊れても、人を介さずに修復する
    - Kubernetesが全てをコントロール

#### 勉強
* git -> docker -> CI
* YAML -> Kubernetes


### ニフクラ × RancherでつくるKubernetes環境
* Speaker: 富士通クラウドテクノロジーズ　世良　迪夫
* Slide

#### Rancher ニフクラ基盤
* ニフクラデフォルトで対応してない…
* 対応
  - Custom
    - 最低限Docker環境があればOK
    - Docker環境でセットアップコマンドを実行であとはよしなにやってくれる
  - Node Driver
    - Docker Macine Driver が作れる
    - 画面に従って作業する
    - ただし特定のイメージにしか対応していない

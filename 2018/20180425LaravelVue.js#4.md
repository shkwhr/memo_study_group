# Laravel/Vue.js勉強会#3

## 概要
* 日時: 2018/04/25
* 場所: 株式会社ITプロパートナーズ
* https://laravue.connpass.com/event/82296/

## session

-----
### LaravelとNuxt.jsを業務で取り入れる際にエタ知見
* Speeker: @IsaoEbisujima(ITプロパートナーズ)
* 資料

#### 認証 LaravelPassport
* 使い方
  - 使用するテーブルを作成する
* facebook認証
  - laravel-passport-facebook-login
  - passportと同様のエンドポイントをしようする
  - ID/Passの代わりにFacebookアクセストークンIDを使用する
* 追加実装
  - /api/追加
  - 有効期限制御

#### Nuxt.js環境設定読み込み
* nuxt.config.js
  - laravelと同じようにenvファイル定義した
  - gitignore
  - env.jsをnuxt.config.jsでrequireした（ES5）
* axiosラッパー
  - ヘッダーにデフォルト値を設定したかった
  - Nuxtなのでユーザー環境とSSRでアクセスURLを変えた

#### 便利ツール
* Clockwork
  - chrome拡張
* sequerl-pro-laravelexport
  - migrationを自動生成するsequerlPro拡張
* SQL to Laravel Builder
  - SQLからlaravelクエリビルダーへ変換してくれる
* Vue.js devtools
  - chrome拡張
* コーディング規約 PSR-2
  - ES-6はAirBnb
* Lint PHP_CodeSniffer
  - ES-6は

-----
### AWSで構築するNux.jsのインフラ構築3選
* Speeker: @KotaMatsumoto(scouter cto)@kotamat
* 資料

#### Nuxt.js
* Vue.jsのいろんんたTipsを凝縮したフレームワーク
  - VueRouter
  - SSR
  - Babel
  - etc...

#### Laravel * NUxt generate
* スタンス
  - laravel Nuxt.jsを同じリポジトリに置く
    - LaravelTopディレクトリにNuxtディレクトリ構成を置く
    - Laravelのリソースディレクトリは消す
  - nuxt.config.jsを調整
    - client/を認識するように設定を追加(module.exports)
  - TravisでNuxtGenerateする
    - nuxt generateで失敗したときもキャッチできるようにしておく
  - dist込みの全体をCodedeployで設置
  - Nginxでリバプロする
    - locationでapiとそれ以外のロケーション設定をする
    -
* WordPress + NuXT SSR
  - Nuxtのみのリポジトリ設置
    - WordpressAPI使用
      - Specが決まってるので共存の必要がない
  - Trubis Build
  - Codedeployで設置
  - Forever対象プロセスを切って再起動
    - ファイルをあげただけではデプロイにならない
    - Foreverはプロセス監視し、プロセスが切れたら再起動
* Express 構築
  - サーバーサイド
  - Nuxt nuxt start は使えなくなる（起動コマンドの実装が必要)
  - サーバーサイド用のjsファイルを作成
    - nuxtやexpress等必要なものをrequre
    - express設定の記述
    - postなどのエンドポイントを記述
    - production判定をnode.env判定
      - devならbuildする
  - 起動設定を対象のjsに向ける
    - 再起動スクリプトをserver.jsに向ける

#### まとめ
* いろんなパターンの配信方法がある
* 各々のインフラ構成をしておけば武器になる


-----
### Elementのすすめ
* Speeker: @takenakasuji(FabricTokyoCTO 中筋)
* 資料

#### Element
* Vue.js用UI framework
* 豊富なComponent
* ドキュメントが整備されている

#### 検討のきっかけ
* 制御・操作を考慮して実装するのは大変…
  - 大中小分類制御…
    - Cascader便利
#### まとめ
* ComponentのしようがProgrammableな設計になっているので開発が使用しやすい
* 統一感を持たせるのに寄与する

-----
## LT

-----
#### VueでJSXをつかうのはありなのか
* Speeker: @RyotaKodaira(SCOUTER)
* 資料:

#### JSX
* JS内でHTML風の記述
* React.jsデフォルトで使える
* VueはふつうVueTemplate

#### やってみて
* 描画する要素を組み立てる時にメソッド毎に役割を与えることで関心を分散できる
* v-modelはパッケージを入れれば使える
* Template内のロジックが複雑化してしまったらJSXの使用検討してもいいかも

-----
### Laravel5.6 デフォルトの例外ハンドリングをまとめてみた
* Speeker: @okashoi(ウィルゲート)
* 資料: https://www.slideshare.net/ShoheiOkada/laravel-56

#### ErrorHandling デフォルト
* report()
  - 指定された例外については何もせず終了
  - 例外自身がreport()メソッドを待っていたら優先的にそちらの処理を行って終了
  - それ以外は$logger-error()でログ出力
  - abort()の中身はhttpexceptionを早出するだけ
* render()
  - 例外自身がrender可能なら優先的に利用して終了
  - 特定の例外を変換
  - 特定の例外については専用の処理を行って終了
  - json resopnseならエラーレスポンスを返す
  - debugなら詳細表示
  - 例外をHttpExceptionに変換してエラー画面描画

#### まとめ
* reportの設定はいじる必要はない


-----
###
* Speeker: @a()
* 資料

#### a
* a

-----
### a
* Speeker: a()
* 資料

#### a
* a

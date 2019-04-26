# Laravel/Vue.js勉強会#2

## 概要
* 日時: 2017/11/24
* 場所: アイスタイル
* https://laravue.connpass.com/event/70674/

## session

-----
### Laravel5.5とNuxt.jsを同一レポジ砦運用した時の構成とつまづきポイント
* Speeker: @kotamat(株式会社SCOUTER CTO)
* 資料

#### Laravel
* 職人のためのフレームワーク
* ドキュメントが充実してる

#### Vue.js
* Progressive JS framework
* HTMLファイルのような記述出かける
* 周辺ライブラリとの併用でいろいろかける

#### Nuxt.js
* UniversalVue.jsFramework
* Next.jsのVue.js版
* サーバーとフロント間コントロール
* SSRを手軽にVue.jsベースで実装できる
* アプリケーション実装に集中できる環境を簡単に構築できる
  - Webpackとかはいってる
* 通信の最適化
  - Etag, Http2で通信データ量を最適化

#### 選んだ背景
* Laravel, Vue.jsの地検があった
* 開発環境立ち上げがはやい
* サーバーとクライアントの関心が分離できる

#### 同一リポジトリで管理
* APIバージョンを考えたくない
* 肥大化してもクラサバを簡単に分離できるようにしたい
* composerやyarnで実行できる環境にしたい

#### 構成
* 設定ファイルでclient/を読みにく
* Laravelデフォルトフロント関連ファイル削除
* クラサバ通信モジュール追加
* nuxt generateで静的ファイル生成
  - SSR使用しないので不要
  - 静的ファイルにすることで本番サーバー設定を簡略化
  - ルーティングごとにdist生成
* Nginxでlocation分岐

#### 認証
* Passport使用
* Client側 @nuxtjs/auth...がいまいちだったので自作

#### 注意
* nuxt.js rc11ではVue.js2.4系
  - ElementUI等で2.5前提のものとかあるので注意
* nuxt generateとnuxtコマンドで挙動が違う
* rc3と現行で変更点が結構ある
* SSRでのみ発生するエラーがある
  - SSRでのみ発生するエラーを追うのが大変
  - 1.0でOn/Offの選択ができる
* localstrage vs cookie
  - Node.js -> Cookie
* Credential
  - Cookieを別ドメインから受信する場合は

#### まとめ
* ちょっとした下準備が必要
* SSRを前提としないサイトでも構成可能
* Nuxt.jsのバージョンは要注意


-----
### LaravelでAPI定義を管理する
* Speeker: 株式会社アイスタイル 久保田賢二朗
* 資料

#### ADR
* ActionDomainResponder
* MVCから派生したUIアーキテクチャパターン
* 一つのエンドポイントに一つのアーキテクチャー
* RouterでDispatchされたClassは__invokeされない

#### Rest API Level3
* Restの4段階のModel(Level 0~3)
* Level3 ハイパーメディアコントロール
  - Hateos(へいてぃおす)
  - RestfulAPIを拡張するアーキテクチャパターン
* willdurand/hateos
  - laravelでアノテーションして使えるようにする必要がある
* おまけ
  - Zendframework/hydrator
  - protected, privateメソッドに対してSetterが記述不要になる

#### Swagger
* 定義書を生成してくれる一連のツール
* 実装 = 定義書
* ライブラリ
  - DarkaOnLine/L5-Swagger

#### まとめ
* ADRで責務を明確に
* Level3 はhateoasで実現
* Swaggerを利用してい実装=定義書

-----
### Laravel/Vue.jsでPWA作ってみた
* Speeker: GMOペパボ株式会社　川島慧
* 資料

#### PWA
* ProgressiveWebApplication

#### ServiceWorker
* client side process
* ネットワーク、キャッシュに応じて通信を制御する
  - サーバーへ取りに行く or ローカルデータを使用する
  - Offlineでもある程度動作する
* localcachestrageを使用することができる
* WebPushも使用している
* browserを閉じてもプロセスは動作してる
* background同期が可能となる
* 更新はバックグランドでインストールし、表示しているタブが全て閉じられた時に更新する
  - 新旧データ混在を防ぐ仕組み

#### AppShellモデル
* PWAを構築するアーキテクチャ
* UIを表示させる最低限のアセットを事前キャッシュする(ApplicationShell)


-----

## LT

-----
### laravel Autoloader
* Speeker: ＠irihit
* 資料

#### 高速化
* optimizer option
* もっとはやくならない？

#### 自作(phalcon)
1. dump-autoload
2. loaderの設定(phalcon)
3. vendor/autoloadで読み込む

#### 結果
* 20ms早くなった(ベストエフォート…)
* 遅くなることが多い…

#### まとめ
* -o はやい
* 基本に忠実に
* phalconとも組み合わせられるよ


-----
### よくも俺のブルマを！！
* Speeker: ＠deadcheat
* 資料

#### Bulma.io
* Flexboxを使用しているCSS flamework
* レスポンシブ
* Bootstrapの代替
* Vue向けComponentあります

#### laravelは?
* youtubeに採用した動画がある…(English)

-----
### パフォーマンス劣化を和らげるお薬のお話
* Speeker: ＠tnker
* 資料

#### コンポーネント[agGrid]
* グリッド
* MID License
* 色々なフレームワークに対応してる
* イベントが代替そろってる
* infinite Scroll が優秀
  - カラム数が多くてもうまくキャッシュしてくれる(横スクロール)
  - ディスプレイ設定とマシンスペックが一致しないとパフォーマンスが落ちる


  -----
#### Laravel mix事始め
* Speeker: ＠ciger47(ささきりょうすけ)
* 資料

#### とは？
* Webpack Wrapper
* ES2015がつかえる
* autoprefixerしてくれる
* ブラウザキャッシュにたいしてはバージョンハッシュがつけられる
* .env で環境変数使える

#### 使い方
* composerでインストール

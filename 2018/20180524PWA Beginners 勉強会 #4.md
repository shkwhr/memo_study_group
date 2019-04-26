# PWA Beginners 勉強会 #4

## 概要
* 日時: 2018/05/24
* 場所: G's academy



## session


### iOSでの実装を試してみた
* Speeker: 掘 正斉
* 資料:

#### PWAとは？
* Webとネイティブアプリの間
* エンゲージ面で効果大

#### ServiceWokerでできること
* 対応状況
  * IE11,Operamini 以外はだいたい対応している
* オフラインでのコンテンツ表示 CacheAPI
* プッシュ通知 PushAPI
* ネイティブっぽい挙動 manifest.json
* ホーム画面に追加 manifest.json
* a

#### iOSでできること
* 11.3からできる
* androidと同じことができるわけでない
  * 50MB以上のデータ保存
  * Push通知
  * Bluetoothアクセス
  * バックグラウンド同期
  * スプラッシュスクリーンのカスタマイズ
    - metaタグとlinkタグで対応することはできる…

#### iOSでやってみた
* デモ
* manifest.jsonを編集してもiOSでは動かない
* linkタグで存在しないファイルを帯出そうとするとスプラッシュが起動しない
* 画像サイズがあってないとうまく動かない
* homeアイコンをmetaタグで読みむ方法ではうまく動かない

#### まとめ
* iOSとandroidでは少し実装が異なる
* iOSでやれることはまだ限られている
* まだネイティブに分がある
* これからの技術と感じる



### GraphQLのオフライン対応した話
* Speeker: TakanoriOki(@takanorip)スマートドライブ
* 資料:

#### GraphQL
* APIリクエストするためのクエリ言語
* RESTApiみたいなの
* 1つのエンドポイントにクエリを投げてレスポンスをもらう

#### apollo-client
* フロントエンドからGraphQLへ投げる
* ServiceWokerでキャッシュされない
  * POSTメソッドはキャッシュされない
* Optionせってい
  * cache first
  * オフライン時にこけにくい
    * キャッシュを強く持つ場合があるので回避処理が必要

#### どうする
* リクエスト結果をIndexedDBにキャッシュする

#### apollo-cache-persist
* ライブラリ

#### localForage
* localストレージライクに使えるライブラリ
* 非同期ストレージ
  * localストレージは同期的

#### apollo-link-retry
* オフライン時にリクエストを保持してくれる
* オンラインに戻るまで再施工する

#### まとめ
* GraphQLはServiceWorkerだけじゃオフライン対応できない
* LocalForageが有能
* キャッシュに対してクエリを投げる



### Nativeアプリの代わりにPWAアプリで戦う選択肢
* Speeker: @mottox2(フリーランス)
* 資料:

#### PWA
* PWAはネイティブを置き換えるものではない
* Webでよい体験を生み出すアプリケーション

#### 使える時
* ネイティブアプリの失敗を避けたい
  * ダウンロードされないとか
  * ハードルが高くコストもかかる
  * フィードバックを回す速度が遅くなりやすい
* ストア審査をすっとばしたい
  * 時間がかかる
  * アダルト系
* Webのグロースに地皮を入れたい
  * エンジニアに高いレベルが求められ仕事レベルがあがる
  * 新規施策が打ちやすい
  * Webでの施策してからうありやすい
* ネイティブエンジニアがいない
* iOSよりAndroidのがユーザーが多い場合
  * iOSではまだ機能限定がある

#### トレードオフを意識する
* PWA非対称ユーザーへのエンゲージメントが弱くなる

#### きになるとこ
* WindowsStore, GooglePlayに出せる
* Pixiv chatstoryがやってる

#### 問題点
* ページ構成が難しい
* Webとモバイルの性質を持ったデザイン
* SEOの考慮
* モバイルファーストなレスポンシブ



### Add to homescreenのちょっと深い話v2
* Speeker: 神野(yahoo)
* 資料:

#### Add to homescreen
* Webアプリ風ホーム画面追加のこと
* A2HS
* 対応ブラウザ
  * chrome, iOSSafari, Edge
* どうやってできるの
  - ｈｔｔｐｓ通信
    - ServiceWorkerで必須
    - localhostだけなら不要
  - manifestの作成
    - webアプリ設定
    - jsonファイル
* chromeで動作確認できる

#### AppInstallBanners
* インストール訴求バナー
* 条件設定できる

#### bannerinstallpropt
* バナーを非表示にできる

#### A2HSのログが取得できる
* KPIとかにどうぞ

#### AppInstallBannerの非表示を先送りできる
* 先に自前の訴求バナーが出せる
* Instagramがやってる

#### Android以外での動作(現状)
* Safari
  - Xだとナビバーが表示されない…
  - 別ドメインリンクをクリックするとSafariが開く…
  - AppInstallBannersがない
  - 必須アイコンサイズがある
  - standaloneとfullscreenの差がない
  - スワイプで戻るとかない
* PC
  - Macだとランチャーに追加されるがWebショートカット
    - 開くとただのchrome
  - Windowsだと検索ペインのないchrome

#### メリット
* 手軽にネイティブっぽいのがつくれる
* 起動起点が取れる
* 別サイト流出が防げる
* SPAとの親和性が高い

#### 気をつけること
* 一部のブラウザ機能がなくなる
  - 既存の使われ方を意識する必要がある
* ブラウザの実装に左右される
* ブラウザによってマニュフェストの解釈が違う
  - UA見る必要がありそう
* 別ウィンドウを開く処理は別アプリ(ブラウザ)が開く
* iOSはまだ様子見した方がいい
  - PWA用Googleマップの提供がまだない
  - ログインがブラウザになってしまう(UX的に…)
* GoogleなんかABテストしてるっぽい


### a
* Speeker: a
* 資料:

####



### a
* Speeker: a
* 資料:

####

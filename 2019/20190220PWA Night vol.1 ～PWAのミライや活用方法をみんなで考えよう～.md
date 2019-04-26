# PWA Night vol.1 ～PWAのミライや活用方法をみんなで考えよう～

## 概要
* 日時: 2019/02/20
* 場所: TAM COWORKING TOKYO
* #pwanight


## session

-----
### PWAの今とこれから
* Speeker: 宍戸Shunya@Google @sisidovski
* Slide:

#### PWA
* 20%
  - PWAにしたあとのコンバージョン率の改善率
* モバイルとデスクトップで同じ体験
  - レスポンシブ
* 対応企業
  - スタバ(US)
  - GoogleMapsGo
    - 新興国市場ターゲット
    - PlayStore
  - GoogleSearch
  - GooglePhotos
  - 日経電子版
    - 最近はMBA
#### 要素
* 高速表示
  - Webパフォーマンス
    - 3秒遅れる
      - 53%離脱
    - パフォーマンス
      - 79%もう来ない
* 信頼性
  - ServiceWorker
    - デバイスのキャッシュを有効利用
    - CacheAPI
    - Workbox便利
  - オフライン時はフォールバックページを返す
* エンゲージメント性
  - 購買UX
  - リエンゲージメント
  - ホームスクリーンに追加
    - manifest.json
    - beforeinstallprompt
      - prompt表示の制御
    - オムニボックスへの移行予定
  - Push通知
    - ページ表示時に通知許可を求めない
      - 離脱率が上がる
      - ユースケースがイメージできるタイミングがよさそう
  - ログイン
    - ログインは大きな離脱ポイント
    - 簡易化
      - 自動ログイン
      - 指紋認証
  - 支払い
    - PaymentRequestAPI
      - 支払いフォーム統一
    - GooglePay
      - 支払い方法の簡易化
#### Next
* Mobileが伸びている
  - Desktopもまだ伸びている(伸び率の違い)
* DesktopPWA
  - Spotify
  - フールー
  - Macは今年の上半期
* GooglePlay配信
  - WebViewでない
  - ChromeCustomTabsで動かしている
    - Cookie,Strageの共有
  - TrustedWebActivity
* Capabilities&NewPlatformFeatures(Chrome)



-----
### PWA はビジネス的に美味しいか
* Speeker: 橋本将功@パラダイスウェア
* Slide: https://speakerdeck.com/paradisemaker/pwa-habizinesude-nimei-wei-siika

#### PWAのイメージ
* PWA=アプリ未満なイメージ

#### メリット
経費・事業リスクを回避できる
- ネイティブより低工数
  - 開発・運用
- 体制をはりやすい
- フレームワークが速い
  - ネイティブの1/3体感
- 後からアプリ化できる
- ネイティブの担当者問題リスク回避
- Apple/Google税の回避

#### ビジネス的には？
B2Bで真価を発揮する
* 早期に動くものが作れる
  - データが載っている画面を触れる
    - 意思決定が早い
  - 要件・使用の抜け漏れ齟齬の把握が早い
  - フロント・サーバーサイドを分離しやすい
* 工数・費用の圧縮が可能
  - ネイティブに比べて
* フェーズごとに合意形成がしやすい

#### オススメ構成例
* フロント
  - Vue.js
* サーバー
  - Firebase
* iOSプッシュ通知の代替
  - twilio
* スクラム
  - カンバン
* それぞれの技術は使いやい
  * 疎結合


-----
### リーンスタートアップとPWA～Webサービス立上げ時こそPWAを検討したい！～
* Speeker: 角谷仁@TAM @hitoshisum
* Slide:

#### リーンスタートアップ
* MVP
  - 最低限実用に耐えうる製品を
  - 検証しながら成長を
  - プロトタイプ
    - テストユーザに使用してもらう
    - フィードバックを得る
  - オズの魔法使い
    - フロントのみを作る
      - バックエンドは人力
      - スモールスタート
    - ユーザーニーズを確かめる手法
  - スモークテスト
  - コンシェルジュ
* PWA向き
  - プロトタイプ
  - オズの魔法使い
  - 新しい取り組みで予算も人員も潤沢にあるケースは希

#### ネイティブあるある
* アプリエンジニアが高給会社に転職
* ダウンロード数が1000以下
* 低評価
* 全てがダブルコスト
* 改善サイクルが遅い
* OSバージョンアップに伴う対応
* リリースの度に審査

#### 予算感
* 基本構成
  - Web構築費
  - PWA対応費

#### パフォーマンス向上策
* CDN導入
* リソース軽量化
* HTTP/2導入

#### PWA効果
* パフォーマンス改善
* ビジネスインパクト

#### SEO
* SEOに引っかからないと機会損失
* webmasterにPWAのSEO対応記事あり


-----
### PWA×CMS活用アイデア
* Speeker: 早瀬将一@six apart https://hayase.tv
* Slide:

#### PWA対応に必要なこと
* HTTPS化
* manifest.json
* ServiceWorker
* Push通知



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

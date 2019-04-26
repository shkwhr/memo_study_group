# We Are JavaScripters! @29th

## 概要
* 日時: 2019/02/21
* 場所: シェアフル株式会社
* #wejs


## session
### React初学者が知らないコンポーネント分割テクニック
* Speeker: 根岸@NeGI (ランサーズ)
* Slide:

#### Reactコンポーネント
* HTMLの独自タグのように使えるパーツ
* デザインや動作をカプセル化

#### 意識していること
* 共通化できるところを見落とさない
  - レイアウト
  - マウスホバー時動作
  - クリック時動作
* コンポーネントに階層を持たせる
  - 分割不可能な最小の単位atom
    - テキストラベル、テキストエリア
    - 表示エリア
  - 再利用可能で機能が規定化しない単位Molecule
    - Atomのグループ化する仕組み
  - 機能が固定化された単位Organism
* 依存性をなくした実装


-----
### 前回の続き（ポートフォリオサイトを作ってる話）
* Speeker: @boiyaa_
* Slide:

#### テンプレート
* 時間・知識が必要
  - デザイン
* GoogleAppsScript
  - スプレッドシート感
  - github: gas-sitegen
  - + Firebase


-----
### 初心者に優しい技術記事の見分け方
* Speeker: @udayan28
* Slide:

#### 公式ドキュメント
* 初心者には難しい(...?)
  - そもそも公式とは
    - 英語？
    - 日本語？
    - GitHub？
  - ドキュメントが整備されていない
    - 更新が
  - 英語

#### 見分け方
* 正しいかは自分で判断するしかない
* 新しい記事=いいではない時がある
  - メモ記事
  - 古い情報そのまま
* 環境・バージョンが書かれている
  - 学習したいことに集中できる
* 参考記事・ドキュメントが書かれている
  - 動かない時参考文献に飛べる
* ソースコードが全体公開されている
  - 依存関係がわかる
* **結局公式ドキュメントから逃げられない**


-----
### SPA×SEOはRendertronで全て解決したと思った話
* Speeker: 深見@fukamiiiiinmin (taskey)
* Slide: https://www.slideshare.net/masakazufukami/20190221-28-wearejavascripters

#### SEO
* サイトのポテンシャルをあげる
* サイトのポテンシャルを検索エンジンに伝える
  - 正しいタグを使う

#### フロントエンドとCSS
* 昔は1アクセス1ページ
* 最近SPAが増えてきた
  - SEO...
  - SSR...
* g-botにはSSR、ユーザにはSPA
  - 結局SSRサーバが必要
* DynamicRenderingしよう

#### Rendertron
* GoogleChrome/Rendertron
* UR表示を無くしたブラウザ
  - SSRの代替


-----
### VueVuexDI ClassBasedStoreOption
* Speeker: @kahirokunn @k-okina
* Slide: https://t.co/FZ7TkDq0tP

#### 綺麗な設計
* CleanArchtechure
  - 外部通信への依存をOOPのDIPを利用してぎゃくてんさせ、ロジックがそのままの意味デコードの一番深いところに持っていく
#### ClassBaseStoreOptionサンプル作った
* InversJSまかせ
* 恩恵
  - テスト
    - 外部コンポーネントへの単体テストが可能
      - mock用しなくてもいい
* typescript-fsa-vues
  - vuex-typescript-fsaのfork
    - vuexの諸々の問題を解決
* Getter
  - mapComputed
    - selecterの実装
    - bindが楽


-----
### JavaScriptでリレーショナルデータベースを自作してみた->る
* Speeker: とばち@toda__kk (asoview)
* Slide:

#### RDB
* テーブル作成
* CRUD

-----
### nuxt
* Speeker: 大武@mqtsuo02
* Slide:

#### Nuxt.js
* Vue.jsフレームワーク
  - Vue.jsはUIライブラリ
* ビルドプロセスに悩まなくて済む
* SPA, SSR、静的サイトがすぐできる

#### 始め方
* create-nuxt-app
  - npm
* スクラッチ
  - GitHub: mqtsuo02/nuxt-handson
  - ゼロからnuxtパッケージをinstall
  - 最小の構成
  - ルーティング実装
  - axios
  - Vuetify



-----
### A/B test
* Speeker: takanori_p
* Slide:

#### reqctでa/bテスト
* SSRで
  - reqct-ab-test
    - 古い…
      - ので移植して改修
  - cookie共有(クライアント/サーバー)
    - BFFでコンテキストにcookie突っ込んで使った…
      - core js
  - akamai cacheが…
    - 軽くしてakamai通さなくても大丈夫にしてるとこ


-----
### RailsエンジニアがStimulus + 生JSだけで約半年のプロジェクトを終えた今思うこと
* Speeker: 徳元@masa (みんなのウェディング)
* Slide: https://speakerdeck.com/masayoshi2018/railsenziniagastimulus-plus-sheng-jsdakedeyue-ban-nian-falsepuroziekutowozhong-etajin-si-ukoto

#### JSフレームワーク選定
* Stimulus
  - HTML拡張とJSを繋ぐ機能に特化
    - DOM生成機能がない
      - RailsのTurbolinksと一緒に使えばOK
        - ONにしてない…
  - その他は生JS
    - 変更に弱い…
      - JSの使い方次第で強く慣れる
* Jset
  - RSpecに似ている
  - これからReactつかうかも


-----
### JSで画像ファイルを壊してみた
* Speeker: 清水@chikoski
* Slide:

#### glitch
* そういうジャンルがある

#### どう壊す
* JPG
  - データの配列として解釈
  - 壊す
  - new Blob
  - create object url
  - ブラウザで表示
    - 壊れてる！
* コード
  - ランダムにランダムの値を入れる
  - ランダムにデータをコピペする
  - 一旦オーディオ化していじって戻す
    - WebAudioAPI
* PNG
  - 難しい
  - チャンクの列
  - 圧縮データ処理がめんどくさい
* 罠
  - バイナリ数値
    - 勝手に符号付値に変える


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

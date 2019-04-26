# We are javascripters 22st

## 概要
* 日時: 2018/07/23
* 場所: 日本 MS



## session


### ピピピのPWA
* Speeker: @mqtsuo02(Free)
* 資料: https://t.co/ByV5zWu2ax

#### ホーム画面に追加を実装してみた
* mqtsuo02.github.io/add-home-minimum

#### manifest
* json形式設定ファイル
* ホームアイコン
* スプラッシュ
* 起動後のブラウザ

#### manifestファイルを作る
* WebAppManifestGenerator
    - 自動生成してくれる

#### index.htmlに読み込む
* linkタグでmanifest.jsonを指定

#### まとめ
* iOSはマニュフェスト通りにならない（追記：固有の記述があるよ）


-----
### Node.jsではじめるオレオレツールの世界
* Speeker: @h_reader(堀内)
* 資料: https://t.co/XZHL1kXnsJ

#### オレオレツール
* ローカル環境で使うツール

#### Node.js
* ファイル操作
    - fs
    - `require('fs');` で使用可能
* npmライブラリ
    - xlsx
        - Excel操作
    - axios
        - httpクライアント

#### できる
* Excel探して
* Excel読み込んで
* Web送信

#### 配布
* Webpack
    - webpack
    - webpack-cli
    - npx Webpack ~ で作成してくれる


-----
### Firebase+Nuxt+buefyで悩んでいる話
* Speeker: @ESkmt3P(坂本)
* 資料: https://speakerdeck.com/skmt3p/midoriiromozaiku-di-2hua-firebase-plus-nuxt-plus-buefybian

#### Component開発にいい
* 軽い
* ロジック切り分けが用意
* 導入障壁画低い


-----
###  closureについて再確認した
* Speeker: @ariaki()
* 資料: https://speakerdeck.com/ariaki/what-we-should-know-when-using-closure

#### function
* 書き方がたくさんある
    - アロー
    - 無名
    - 即時
* 関数の代入ができる

#### closure
* 外側の関数で定義された変数が内部の関数で操作できる

#### scopeと生存期間
* 静的スコープ
* 浅いアクセス
* shadowing: スコープを挟んで名前を重複定義できる
* masking: 一番近い変数が優先される

#### activation object
* scope chain
* prototype chain

#### memory leak
* closureによるメモリリークの可能性
* Timer / ventlisner
* Valiables
* Circular reference

#### まとめ
* 第一級オブジェクトはいろいろな書き方ができる


-----
### Practical Typed React App
* Speeker: @kdnk(Wantedly)
* 資料:

#### React Redux
* TypeScript
* ContainerでのActionの型定義
* ComponentでのPropsの型定義
* 型定義を楽にしたい
    - Inferring within Conditional Types
        - TypeScript2.8
        - ConditionalTypeで推論された肩を再利用できる
    - WtdModels.Union
        - Union

#### まとめ
* infer便利
* 型定義はなるべく楽に


-----
### VisualStudioCode
* Speeker: @sakkuru(本間咲来(日本MS))
* 資料: https://www.slideshare.net/sakkuru/visual-studio-live-share-107112844

#### LiveShare
* リンクシェアする
* コラボレーションセッション始めるよ
* VisualStudio(Code)立ち上げる
* 親のファイルを子がダウンロード
* コードが共有されるよ
* ブレイクポイントが共有されるよ
* ターミナルも共有できるよ
* ローカルホスト(サーバ)の共有もできるよ


-----
### vim.wasmがすごい（WebAssemblyを勉強し始めた）
* Speeker: @yukpiz(redish Inc)
* 資料: http://yukpiz.s3-website-ap-northeast-1.amazonaws.com/vim.wasm.html#/

#### vim.wasm
* https://rhysd.github.io/vim.wasm

#### WebAssembly
* ブラウザ上で実行可能なバイナリフォーマット
* C/C++, Rust, Go, C# -> wasm
* https://t.co/FvoSvzEabm
* Qt for WebAssembly
* OpenCV

#### まとめ
* パフォーマンス面でJSで実現の大変だったところをサポート
* webassembly は、ブラウザからアセンブリ(機械語)を実行できるようにする技術。ウェブに必要なファイルが小さくなり、高速化する。将来的にはJavascript をかかずにDOM、WebAPIを操作できるようにすることを目的としている。


-----
### OSSはじめのいっぽ
* Speeker: @isoppp(ゲームサウンド系)
* 資料: https://isoppp.com/note/2018-07-23/lets-join-open-source-project/

#### きになるとこ
* 英語力
    - issue
    - PR
    - Google翻訳で頑張る
    - コードはコードで語る
* 技術力
    - レビューしてくれる
    - コメントがかなり親切
    - わからなければ素直に聞いたほうがいい

#### 気をつけること
* CONTIBUTING GUIDE
    - Issue/PR関連は注意点が書いてあるのでとりあえず読む
        - Nuxtはサービスから立てるらしい
    - パッケージをインストールしてから修正する
        - pre-commit系のパッケージが入ってたりする
    - 絶対指示通りテストを実行する
        - PRでCIが回って別のところでこける可能性…

#### その後
* コードへの抵抗が軽減
* コードを読む機会が増えた


-----
### Array.prototype.sliceのはなし
* Speeker: @chikoski(清水)
* 資料:

#### どんな感じで調べてたか
* jsvu / eshost めっちゃいいよ
    - nodeでいれる
    - JSEngineのそれぞれの実行結果の表示
    - JSEngineをコマンドラインから実行できる
* MDNみる
    - 人がわかりやすいように書かれてる
    - 実挙動とはちょっと違う
* 仕様
    - ECMAみる

#### Array
* コピーって結構重い
* Slice
    - 本当にコピーしてるの？
    - どうやってるんだろうか…
    - ソースを読む
    - JSEngineの中身をみる
        - 公開してる


-----
### a
* Speeker: @a()
* 資料:

#### a
* a

#### a
* a

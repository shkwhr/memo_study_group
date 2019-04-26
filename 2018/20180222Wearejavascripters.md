# We are javascripters 16th

## 概要
* 日時: 2018/02/22
* 場所: Microsoft Shinagawa



## session


### Riot.jsの今とこれから
* Speeker: @@kuwahara_ngv5(ion3)
* 資料: https://speakerdeck.com/clown0082/present-and-next-riot-dot-js

#### RIOT（らいおっと）
* シンプル・軽量
  - Vueの1/3
* JSコンポーネント
* React Like
  - もとにして作成
* UI ライブラリ
* カスタムタブ
* Ver.2まではおそかった
* 夏ごろVer.4


-----
### emacs helm likeな WebExtensions を作った話
* Speeker: @kumabook(Spincoaster)
* 資料:

#### WebExtensions
* ブラウザ機能拡張
* クロスブラウザ
* Webコンテンツ変更
* ブラウザカスタマイズ

#### 作ったもの
* Emacs helm on Extension
* 履歴窓から履歴削除
* VimperatorがFirefoxアドオンで死んだ
* シンプルなのが欲しかった

#### アーキテクチャ
* background javascript
* popup
* content script
* options ui

#### 難しさ
* callback hell
* 状態管理
* react redux redux-saga と相性がいい
  * react コンポーネント再利用ができる
  * ローカルからスクリプトを読むのでサイズは気にならない
* ブラウザによってAPIの有無の差異がある
  - 別名で同機能とかはない

-----
### ES2015のProxyを使ってみた
* Speeker: @tipo159
* 資料:

#### Proxy
* 基本的な走査について独自の操作を横取りして独自定義ができる
* var p＝ new Proxy(target, handler);
* IE以外で使用可能

#### Vue 3
* IEはサポートしない
* Ver.2 では Vue.set を使用する
* Ver.3 では new Proxy で他のプロパティと同じ書き方で使用できる

#### メタプロ ES6
* 無限にchain可能なAPI
* method missing フック実装
* 列挙型から getOwnPropertyNames, Objectkeys, in 演算子を隠蔽
* Observerパターンの実装


-----
### 僕のフロントエンド奮闘記 すったもんだ
* Speeker: @Nao-bt
* 資料:

#### コンポーネント
* props
* emit
* 親は子を必ず知っておかなくてはいけない
* どのくらいの粒度でコンポーネントをきればいい？
  - Atomicデザイン
  - 5つの大きさに分けて考える
  - z初期は大変
  - 規定の回数同じコードを書いたらコンポーネント化する手もある

#### Vuex
* 親子間のバケツリレーしなくてよくなる
* 親子関係以外にもできる
* Vuex用の記載が増えた…
  - action, mutationをしらないと成り立たないコンポーネント量産…
* Pagesでデータをまとめて利用した方がいいのでは


-----
### アプリ開発未経験者がReactNativeでProgateアプリをリリースした話
* Speeker: @wyvernMurai(Progate)
* 資料:

#### ReactNative
* ネイティブ用React.js
* 基本React.jsと同じ
* Good
  * コンポーネントタグがReact.jsと違う
  * ビルドがJava,Swiftよりはやい
  * React-devtoolsが便利
* Bad
  * 日本語ドキュメントが他に比べ少ない
  * 基本がJava/Swiftなので別言語の理解が必要

#### 知見
* redux使った方がいい
* 静的型づけはした方がいい
* bagの原因になる
* テストは早めに書こう
* パフォチューは必須
  - ReactNative標準の簡易プロファイラ
  - Chrome performanceツール
  - xcode instruments
  * デバッグとリリースではアプリ速度が違う(リリースが早い)


-----
### Javascript でパワポをつくろう
* Speeker: @sakkuru(MS)
* 資料:

#### JavascriptAPI for Office
* Officeドキュメント内コンテンツを操作できるAPI
* HTML, CSS, JS
* Officeアプリ内でWebアプリが展開できる

#### Officeアドイン
* コマンド: yo office


-----
### JavaScript用語を簡単に説明してみよう!
* Speeker: @fukamiiiiinmin
* 資料:

#### jQuery
* 各ブラウザDOM APIを一つにまとめて簡単にかけるようにしたもの

#### HTMLCSS,JS
* Webでなんでもできる

#### Ajax
* 非同期通信

#### ReactとかAnguler
* 設計図をもとに画面を作ってくれる

#### まとめ
* 言葉にすると自分の中でも整理ができる
* エンジニアとして省いたらやばいって思うところを優先して理解


-----
### Unit testing for React components
* Speeker: @camcam_lemon（日本事務器)
* 資料:

#### React Compornent Test
* refコールバック
  - 文字列属性かどうかでテストが変わる
  - ref hundle input forcus がmockされるとかとか…
* DOMオブジェクトアクセス
  - テスト環境では空オブジェクト
  - 一部メソッドはmout()でレンダーできる
* 引数ありのイベントハンドラ
  - simulate()の第二引数以降にモックオブジェクトを渡すことができる
* 時間が絡む処理
  - 時間を上書きして止める
* グローバルオブジェクトへのアクセス
* jsdomのuserAgent等は直接書き換えることはできない
  - Windowを明示するかどうかでテストの仕方と難易度が変わる
    - setterがない -> 作り変えて対応する(helper)


-----
### モジュールと名前空間について
* Speeker: @chikoski
* 資料:

#### type="module"
* webpack
  - browserが解釈

#### 変数とは
* 代入
  - 空間に対して値を入れる
* 束縛
  - 関数的概念
  - データーに対して名前をつける
* scope
  - javascript -> block scope
  - 環境
    - 名前と値の対応表
    - ネストしてる
    - スコープも環境で実現
    - 特別な環境もある
    - closerは環境の表をもってる

#### 良い名前思いつかない問題
* 名前空間
  - ライブラリ
  - クラス
  - …
* 昔のJSには名前空間がなかった
  - -> common.js
    - -> ES2016 module
      - export
        - 複数をまとめて一つのモジュールとしてexportできる
      - import
        - read only(直接操作はできない)

#### いいところ
* グローバルを汚染しない
* 安全なプログラムを描きやすい
* 自分の名前をつけられる
* 依存関係のネットワークサイクルも解決可能

#### テスト
* 露出しない関数
  - どうやって書く？
    - テストをモジュールに埋め込む
    - 名前を隠すモジュールを別に作る

-----
### a
* Speeker: @a
* 資料:

#### a
* a

#### a
* a

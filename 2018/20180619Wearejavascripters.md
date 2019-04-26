# We are javascripters 21st

## 概要
* 日時: 2018/06/19
* 場所: repro



## session


### Vue.jsと守りのFirebase、そして何なのJWT！！
* Speeker: @po3rin()
* 資料: https://t.co/kxzOkrLxGJ

#### firebase
* 認証基盤

#### JWT(じょっと)
* json web token
* jwt.ioでデコードできる
* サーバー送信時にRequestHeaderに付与して送信
* サーバーサイドはfirebaseで認証

#### まとめ
* 外部基盤で認証処理かけると分離しやすくなる


-----
### ExtendScriptという名のJavaScript
* Speeker: @onebitious(大澤一志(（株）CTE))
* 資料: https://t.co/iIidm8dgQx

#### ExtendScript
* Adobe拡張JS
* Adobe製品をある程度自動化できる


-----
### window.windowとは何か
* Speeker: @Edward Fox(repro)
* 資料: https://t.co/FNQ8qRid5W

#### window.window
* window === window.window => true
* 標準プロパティ
* 実はWindowProxy Object
  - アクティブなwindowへのプロクシとして動作
  - windowのラッパー
  - outer window

#### WindowProxy
* 非表示となったナビゲーション前のwindowにアクセスし続けることがなくなる
* クロスオリジンなDOMアクセス
* セキュリティ関連昨日の実現
* OutOfProcessIframes(OOPIFs)にも関わっている
* ブラウザあーきて弾く茶の一端を担っている

-----
### 2018年、IE6対応サイトを作る
* Speeker: @boiyaa(パーソル)
* 資料: https://t.co/JuZ4PU4WpG

#### やけくそでやってみた
* しばり
* 今時の技術を使う（バージョンも）
  - 今時はES5準拠
* 環境も
  - XP
  - BrowserStack

#### Next.js
* 動いたけどJSエラーでた
* デバッグはIE10のIE8モードで

#### Parcel
* 動かない
* いろいろ誰かが作ってるので使った
* 動いた

#### 要
* getter / setter が結構分かれ目


-----
### 毎日js書いてたらアプリ作ってた
* Speeker: @nanntorokusei(nakamura minato(memoryst))
* 資料:

#### 毎日コードを書く
* code write away
* コードについて考える習慣がつく
* パートナーとの理解

#### js
* 毎日書きやすい
* ドキュメントが多い
* 動くところが見える

#### やったこと
* ToDo App
* 写経
* 欲しい機能追加
* サービスとして提供するということを前提とする
  - vue-cli
* サービスとして公開する
  - 設定の見直しがはいる
* フィードバックを地道に進める
* Monacaで作り始めた

#### やってると
* JSなんでもできる
  - front
  - backend
  - app

#### 不向き
* インフラ系
* 機械学習系
  - 時間がかかる

#### やってた時間
* 朝早く起きてから
* 昼休み
* 通勤中
* 帰ってから

#### 得られたもの
* コードのことを考える癖
* サービスを作った満足感
* 仕事とは別の考え


-----
### 電池を消耗しないwebサイトの作り方
* Speeker: @fukamiiiiinmin(深見将一[taskey])
* 資料:

#### SPのバッテリー消費節約
* 複雑な処理をしない
  - CPUの負荷が低い処理
* アニメーションさせない
* スクリーンの電力消費を下げる
  - 消費電力にあわられやすい
  - OLEDとLED
  - OLED
    - 黒:RGB発光しない
    - 白:RGB発光する

#### 勉強したいこと
* PCがいつ電気を使っているか
* モジュール取得方法による消費量の違い


-----
### Vue.jsのエラーハンドリングの話
* Speeker: @takanorip(TakanoriOki[スマートドライブ])
* 資料:

#### エラーハンドリング
* 様々な種類・状態
* 基本やコンポーネント内がいいのでは
* グローバルで扱うときはStore
* Storeに格納するエラーはアプリケーション全体に影響があるもの
  - Storeが肥大化すると混乱を招く
* Q「エラー処理ってカオスになりがち。どうしてる？」
A「典型的なハンドリング用のコンポーネントをいくつか作っておいて、(Vueなので)mixinを使ってパターンによって使い分けてます」

#### 適切なUI
* ユーザー操作を邪魔しない
* わかりやすく伝える
* モーダル便利ゆえの難しさ
  - 閉じるとき
  - 背面スクロール

#### 監視
* Sentry
  - エラー追跡ツール
* フロントエンドのエラーはUI崩れに直結する


-----
### typescriptの型の今
* Speeker: @brn0227(青野健利{cyber})
* 資料: https://t.co/pzQB2jSrRV

#### 最近の型
* だいぶ柔軟性がでてきた
* MappedType: 型の写像
* ConditionalType:
* Infer operator:



-----
### 繰り返しのはなし
* Speeker: @chikoski()
* 資料:

#### 繰り返し構文
* for
* while
* loop
* for of
* 高級関数
  - map
  - reduce
  - foreach
* 再帰呼び出し
* 同じ作業と小さくなる問題

#### コンパイラを作ろう
* Brainfu*k
  - ポインタで操作
* 文字列 -> トークン列 -> AST -> BinaryenIL -> WASM
* 繰り返しをうまく使えば冗長な繰り返しも少ない繰り返しでできる



-----
### a
* Speeker: @a()
* 資料:

#### a
* a

#### a
* a

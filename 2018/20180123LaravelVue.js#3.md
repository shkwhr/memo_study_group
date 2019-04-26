# Laravel/Vue.js勉強会#2

## 概要
* 日時: 2018/01/23
* 場所: 株式会社DMM.comラボ
* https://laravue.connpass.com/event/75495/

## session

-----
### Vueコンポーネントを抽象化して複数リポジトリのソースを共通化した話
* Speeker: @ryotakodaira(SCOUTER)
* 資料

#### 問題点
* ソース・リポジトリが共通化されていない
  - 類似共通処理を回収するときはリポジトリを跨いで改修が必要
* マイグレーションが大変

#### tool
* storybook
  - vue.js compornent確認ツール

#### パッケージの準備
* Vueプロジェクトの準備
  - vue-cliで作成して不要なものを削除するのがおすすめ
  - yarn add でcompornentを追加
* storybookの導入
  - 開発効率UP
  - コンポーネントの仕様が残せる

#### アプリケーション
* コンポーネントをimportして使用
* install (Vue ... Vue.use('名', {'object'}) ...)

#### まとめ
* Vueプロジェクトでstorybookを使うことでコンポーネント単位での開発が効率的になる
* 設定ファイルを用意するとアプリケーション固有値にリポジトリ個別に管理するよう対応できる


-----
### Larvel Echo + Vue.js + axiosで簡単チャットアプリ開発
* Speeker: @Yorinton(個人)
* 資料

#### 作ったの
* Peeech
  - 友達作りサービス
  - Laravel Echoを使用
  - リアルタイムメッセージ
  - 既読判定
  - メッセージ永続化
  - 通知

#### Laravel Vue.js の連携
* Laravel Echo での非同期通信(exios)を送り、laravelで処理
* laravel Echo でlaravel処理したメッセージを受信し処理

#### Laravel Echo
* LaravelでトリガーされたリアルタイムイベントのリッスンができるJavascriptライブラリ
* 認証が必要なプライベートチャンネル等の作成・購読が可能
* ドライバとしてPusher、Socket.ioが使える
  - Pusher: Pub/Subプラットフォーム(有料)
* bootstrap等でインスタンス生成

#### Exios
* 非同期処理のHTTPクライアント(Promise base)
* ブラウザからの非同期処理を作る場面で使用した

#### Vue.jsのデータの扱い
* data object
  - 記述されたプロパティの変更を検出する
* データの受け渡し
  - 親→子: v-bind → props
  - 子→親: emitでイベントコール

#### 通知・既読の簡単な実装
* Notification: Laravelライブラリ
  - 簡単に通知処理が作れる

#### まとめ
* Vueライフサイクルを理解すると適切なタイミングで処理を行える
* data objectはリアクティブ
* 親->子はv-bind + props
* 子->親はvm.$emit
* LaravelEcho + pusherにリアルタイムの実装はお任せできる
* Vue.js + Exiosで非同期処理が簡単にできる
* Notificationで通知処理が簡単にできる

#### やりたいこと
* Push.jsを試してみたい

-----

## LT

-----
### LaravelBlade x vue.js 混在させる場合の注意点
* Speeker: @s.kurihara(クリエイターズマッチ)
* 資料

#### 注意点
* Bladeの記述とVue.jsの記述の衝突
  - 中括弧の記述
  - v-onの省略時
    - clickイベントでshowというイベント
      - bladeの@showと衝突
        - v-onを必ず書くしかない
* ブラウザのDOM解析依存
  - スタイル属性のバインディング
    - @{{width}} で記述すると無視される
      - v-bind を必ず書く
* ブラウザのjavascriptの動作
  - modelの実装をvueでそのまま書いてみる
    - bladeではコンパイルされないのでie11でエラーになる
* filter
  - 追加引数なしでfilterがIEでエラー
    - ()を省略する
* 未定義のプロパティを定義(data{obj: {}})
  - IEでエラーにならない
    - 未定義のプロパティを作成しない

#### まとめ
* 混在させないほうがいいよ

-----
#### laravelとvueでスクラムのベロシティ管理ツールを作った
* Speeker: RyutaHamasaki @avosalmon(暮らし.com)
* 資料:

#### 成果物
* Github: laravel-vue-scrum
  - Laravel
  - vue.js
  - vuex

-----
### laravelお役立ちネタ
* Speeker: @mpyw(DMM Lab.)
* 資料

#### ネタ
* マイグレーションファイルを整理整頓したい
  - マークダウンで書いた仕様書をスクレイピングして書く
  - 全部初期日付で書いたことにする
  - カラム定義だけ書く
  - 外部キー制約定義だけ書く
  - 1970_01_01_0000_create_xxx_tables.php
  - 最初に全テーブル作って、後から外部キーをつける
* Dockerコンテナ上でのテストマイグレーションが遅い
  - テストメソッド一つ一つにたいしてsetUp()が走る
  - 方針
    - マイグレーションは一回だけ
    - テストデータ作成はファイルごとに１回だけ
* カウンターキャッシュをできるだけ正確にしたい
  - select count(\*)じゃないカウント
  - laravelのDB::transaction()はネストできる
    - DB::transaction(function() use($alon) { ... });
* ずれないはやいページネーションがほしい
  - 遅い
  - lampager
* ルートモデルバインディングでメソッドを共有した
  - 複数の呼び元で同じメソッドを使いたい
  - 詳しくはQiitaで
* ユニークキー制約と論理削除を両立させたい
  - [MySQL Only] $table->uniqe();

-----
### 5.6 changelogを斜め読み
* Speeker: @k-kurikuri(DMM.com Lab.)
* 資料

#### Laravel5.6
* 必要なPHPバージョン
  - composer: ^7.1.3
* changelogからいくつか抜粋
  - ApplicationクラスにrunningUnitTestメソッド追加
    - UnitTest実行中判定
  - illuminate/Support/Arr::wrap(null)がから配列を返す
  - ArtisanConsle
    - optimizeコマンドの削除
      - Opcacheの最適化
    - migrate:statusの出力結果にカラム追加
      - Batch(実行順)
  - Database
    - Blueprint::morphsによる複合index定義順が変更
    - id,typeからtype,id
  - Queues
    - JobのifにgetJobId(),payload()追加
  - Response
    - createをコールすると201を返す
  - Blade
    - csrf,methodディレクティブ追加
      - @csrf, @method で記述できる
* 所感
  - 特に大きな変更点はなさそう

-----
### Excel連携してみた
* Speeker: たけなか(Spinno)
* 資料

#### PHPExcel
* 後継: PHPSpreadsheet

#### Handsontable
* vue.js等のwrapperがある
* GoogleSpreadsheetみたいなのができる

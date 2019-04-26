# We are javascripters 16th

## 概要
* 日時: 2018/03/30
* 場所: mercari



## session


### チームをCQRS
* Speeker: @boiyaa(persol)
* 資料:

#### CQRS
* コマンドクエリ責務分離
* ドメインロジックあり
* データ整合性
* Akkaが有名
* Redux

#### 人の役目
* フロントエンドとバックエンド
* 時代にフィットしていない？
* 役割の再定義
* 更新系と参照系で分離できそう

#### JS
* クラサバどちらも作れる
* サーバーサイド
  - Nuxt.js
  - Next.js
  - Redux
  - AMP
* フロントエンドサイド
  - CloudFirestore
  - CloudFunctions for Firebase
  - Firebase Hosting
  - AWS AppSync


-----
### フロント未経験者のReactプロダクト改善
* Speeker: @shikichee(Ubie)
* 資料:

#### UIの問題点解決
* 対象が高齢者
* 機器はiPad
* WebUI
* Safariなのでタップできるところがたくさん
  - フルスクリーン化
* コピペポップアップがでやすい操作感
  - 出にくいように改修

#### 技術的負債解決
* JS
  - ESLint導入
* 巨大CSS
  - css-modulesで分割

#### 対応中
* flow
* PWA
* etc...

#### 知見
* Webでネイティブ動作させるの大変
* 選定する技術が負債化する恐怖

-----
### new version of context in React 16.3
* Speeker: @sottar(mercari)
* 資料:

#### React v16.3 Release

#### Context API
* 新しく作り直された
* ReduxのStore的な感じ
* Provider と Consumer


-----
### What is necessary for developer friendly UI
* Speeker: @kuwahara_jsri(Yumemi inc)
* 資料:

#### Web
* 重い
* 使い勝手が悪い

#### まとめ
* 情報設計
* 情報を減らして必要なものだけ残す
* DOMをコンポーネントごとに
* 共通化とDOMに意味を持たせる


-----
### Vuetifyで学んだあれこれ
* Speeker: @10tomok0()
* 資料:

#### Vue.js
* リアクティブ
  - 宣言的レンダリング
* コンポーネントシステム

#### WebCompornent
* WebUIのコンポーネント化するしくみ
* 再利用性
* メンテナンス性

#### Vuetify
* CSSフレームワーク
* マテリアル
* 日本語対応進行中

#### まとめ
* お手本がいったほうがオラオラ実装になりにくい
* やってみた系記事は情報量が少ない
* OSSはソース読み放題
* マテリアルの勉強になった


-----
### HyperappでMarkdownエディタを作って薄い本を書きたい
* Speeker: @atsuco_02()
* 資料:

#### Hyeprapp
* viewライブラリ

#### よい
* ステートの監視・更新特化なのでシンプル
* JSXが使える

#### どうしよう
* JSXの文字列になるけどJSXとして認識しない


-----
### Osushiに見るフロントエンドのセキュリティ
* Speeker: @shibe97(ウォンタ(osushi))
* 資料:

#### osushi
* 炎上
* 公開時間7時間

#### 炎上
* セキュリティ面
* 法律面

#### 原因
* 考えの甘さ
* 早くリリースしたい思いが先行した

#### 何が起こったか
* アクセストークンが可逆暗号
  - 乗っ取りが簡単…

#### 再リリースにむけて
* 大量攻撃が想定できる
* セキュリティ対策
  - 攻撃の数を減らす
    - DevToolハック
      - とにかく攻撃意欲をなくす
      - 話をそらす
      - 話題作り
      - 一時的に対策として使えれば…
  - 攻撃を防ぐ
    - バリデーション厳格化
    - セキュリティ系ヘッダ
      - S-Frame-Options
        - クリックジャッキング対策
      - HSTS
        - HTTPで接続されてもHTTPSでリダイレクト
      - X-XSS-Protection
      - X-Content-Type-Options
  - 被害を最小限に抑える
    - 盗られるものをなくす
      - API返却値から個人情報をなくす


-----
### 継続的 npm update のために実践していること
* Speeker: @codenote_net(TokyoOtakuMode)
* 資料:

#### npm update の課題
* 事業サービス開発が優先される
* npm moduleが古いまま…
* 新機能を導入したいときには差分が多く影響範囲が多くなる

#### npmローカルモジュール
* 新旧バージョンを共有しつつnpm moduleを利用できる
  - 旧: require('moment');
  - 新: require('latest_modules/moment');

#### npm update & pull request サービス
* GreenKeeper.io
* Dependabot

#### 旧から新へ
* 徐々にlatest_moduleへ痴漢


-----
### WASMとES modulesの話
* Speeker: @chikoski
* 資料:

#### WebAssenbly
* ブラウザ上で動作するバイナリ
* モジュール

#### 作り方
* コンパイルしてビルド
* C (LLVM)
* C++
* Lasp

#### WASM Web embedding API
* import/exportできる
* コンパイル手動
* インスタンス化手動

#### ES2016 Module
* import/exportできる
* コンパイル不要
* インスタンス化自動

#### module
* 名前と値の対応表
  - scopeが近い

#### 使いやすくならないか
* Webpackががんばってる
* 依存関係もいずれ持てるようになる
* 



-----
### a
* Speeker: @a
* 資料:

#### a
* a

#### a
* a

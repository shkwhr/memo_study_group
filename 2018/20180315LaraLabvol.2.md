# LaraLab vol.2

## 概要
* 日時: 2018/03/15
* 場所: 株式会社オールアバウト



## session


### 組織で運用するLaravel
* Speeker: @YuichiKishimoto(@kyuichi2220s)
* 資料:

#### Laravel
* 自由度が高い
* 運用に際しルール作りが必要
* Githubのstar数でrailsを抜いた
* アップデート頻度が高い
  - PHP本体のバージョンアップ対応も忘れずに

#### 技術選定
* 長期的な観点
  - 長期発展の見込み
  - 新しめの技術

#### アップデート対応
* 対応方法
  1. LTSを採用する
    - 2年おきくらい
  2. 積極的に対応する
    * デバッグコスト
      - テストの仕組みづくり(CI)
    * 組織的な仕組み
      - 定期的なアップデート
      - Laravelニュースを定期的にチェック&共有

#### 設計
* 設計方針
* できるだけFWに依存しない
* DDD (レイヤードアーキテクチャ)
* Eloquent Model
  - 機能が多いためfatになりやすい
  - レポジトリパターン
  - Factoryパターン
  - Eloquentから責務を減らす
* Facade
  - 便利すぎるので使いすぎると依存度が上がってしまう
* Collection
* Helper
  - ラッパー
  - Illuminate\Support\App\Arr


-----
### Laravel Zero 触ってみた
* Speeker: @amymd(All About)
* 資料:

#### Zero
* マイクロフレームワーク
* コンソールアプリ
* Web関係のディレクトリがない
* 最小限コンポーネント
  - 追加で欲しい場合はapp:installとかコマンドで取得
* エラー表示がわかりやすい

#### 始め方
* composer

#### パフォーマンス
* blackfire.io でlaravelと比較
* laravelよりちょっと軽くてちょっと速い


-----
### vue-cli3系がでた
* Speeker: @masaakikunsan(フリーランス)
* 資料:

#### vue
* mvvm
* 学習コストが低い
* SPAに特化
  - SSRはNuxt.js

#### cli v3
* 設定周りを隠蔽
* vue.config.jsをいじれば色々できる
* build,router,config周りが消えてる
* まだβ版


-----
### laravelバックエンド選
* Speeker: @Moto Hayashi
* 資料:

#### laravel cms から admin backend
* ASGARD CMS
  - 基本機能は備えるが複雑なページ構成には不向き
  - 既存サイトには追加できない
* OCTOBER CMS
  - インストーラから使用していく(wordpressちっく)
* QuickAdminPanel
  - インターフェースからCRUD設定、権限設定
  - 最後にコード生成されるのでcomposer, migrateでインストール
  - 有料サービス
* Voyager
  - composer
  - 権限設定、CRUDエディター


-----
### これで簡単！Laravelの認証処理をカスタマイズ
* Speeker: @moyashidaisuke(みんれび)
* 資料:

#### やること
* 5つのfunctionを作る

#### まとめ
* マニュアルがわかりにくい
* 仕組みがわかればそんなに複雑じゃない


-----
### a
* Speeker: @a
* 資料:

#### a
* a

#### a
* a


-----
### a
* Speeker: @a
* 資料:

#### a
* a

#### a
* a


-----
### a
* Speeker: @a
* 資料:

#### a
* a

#### a
* a


-----
### a
* Speeker: @a
* 資料:

#### a
* a

#### a
* a

# RecoChoku Tech Night #08 - レガシーとの戦い -

## 概要
* 日時: 2018/07/24
* 場所: レコチョク



## session

-----
### レガシーなフロントエンド環境で心理的安全性を確保するためのチームビルディング
* Speeker: @jaxx2104(株式会社リクルートライフスタイル 岩下 太)
* 資料:

#### 課題
* 機能の優位さが重視され、要望に答えていく必要がある
* hotpepperグルメやAirとのシステム感の連携が多く仕様が複雑
* 納期マストも多い
* Delivery > Quality になってしまいがち
* ジョブチェンジ組が多い
    - スキルセットがバラバラ
* ドキュメントが整備されていない
    - 仕様知ってる人がもういない
* 同じ処理が2つある…
* 一部ES2015で書いてない…

#### 技術的に心理的安全性を確保する
* 0.フロントエンドの改善
    - レガシーな環境での機能改修は影響範囲が大きい
    - まずビルドツールの移行から始めた
        - タスク改善、ビルド時間短縮
    - 次にlinterやformatterの整備
        - 実装・レビューコストの削減
        - 余剰時間で品質改善しやすく
* 1.テスト・ドキュメントの改善
    - Frameworkの以降を見据えて実施
    - Jestへの移行
        - 画面側のテストが可能に
        - 機能開発も取り組みしやすく
    - Storybookの導入
        - コンポーネントのモック化
        - フラジャイルなフロント特性に合わせて画面からコンポーネント単位へ
        - デザイナーさんとのコミュニケーション
* 2.画面側の改善
    - Vue.jsの導入
    - ビルドとテストの改善により高いSLAでの実装が可能となるよう設計
    - 新規画面で導入
    - 事例を増やしていく

#### チーム全員で改善を回していく
* FEチームとして個人をサポートする体制づくり
* 個人としてチーム貢献ができるモチベーション
* 最新のFWの機能や設計を学習できる機会を用意する

#### 改善は参画者のインプットにも
* テストケースを追加の改善
* アサイン予定の画面仕様を事前に把握
* フロントエンドの技術に慣れてもらう

#### フォロー
* いきなり回せる人は少ない
* 改善フローの進め方はもくもく会とかレビュー会でチームとしてサポート
* 技術面ではFW横断でしえん　
    - すぐにフォローできる体制を
* チーム全員が事業成長のために！


-----
### レコチョクバックエンドの今とこれから
* Speeker: @a(株式会社レコチョク 高橋 克幸)
* 資料:

#### 課題
* 開発工数の肥大化
    - 独自仕様のAPI
    - バックエンドにサービス固有の機能
    - 納期最優先のプロダクト
* システム仕様の属人化
    - 各領域の担当者による運用
* 運用工数の肥大化
    - システム単位で手動による運用
    - システム単位のAWSアカウント管理

#### 実問題
* APIすべて200応答
* http/1.1の仕様に沿っていない
* コンテンツタイプがXML
* メンテンスナンス終了のFW
* テストコードがない
* ドキュメント管理(フォーマット)が統一されていない
* 開発環境構築手順がドキュメント化されていない
* CPU使用率は10%(過剰リソース)

#### 解決
##### システム単位の領域からバックエンド共通へ
* バックエンドの統合
    - アカウント統合によるリソースの共通化
        - コンテナ化
            - リソース共有
            - ポータビリティ性向上
* APIの仕様を標準化
    - ステータスコード
    - JSON
* 新規機能はTDDでテストコードを実装
    - レビュー前にテストを通す
    - 不変性を担保

##### 運用工数の効率化
* システム担当からバックエンド共通担当へ
    - 細分化せずに面倒を見る
* AWSアカウント統合による運用コスト削減
    - 新規サービス時などのマスタ設定を共通化
* ドキュメントの統一
    - API-IF仕様書はSwaggerかPostmanで管理
        - スモークテストを実施可能にする


-----
### レガシーな開発組織で新規サービスを作る話
* Speeker: @yustam_jp(株式会社レコチョク 松木 佑徒)
* 資料:

#### フロントエンド
##### 課題
* コーディング結果をテンプレートに書き換える必要がある
* ソース管理されていない
* CSS FWについて柔軟なカスタマイズができない
* PC/SPの表示崩れ確認に時間がかかる

##### FEエンジニアをたてた
* Fのソースコードを全て開発チームで扱えるように
* CSS FW頼りの状態いから脱却
* ブラウザ毎の挙動の違いのナレッジ蓄積
* Backborn.jsからVue.jsへのリプレイス

#### 品質管理
##### 課題
* 複数チームに説明するのでコミュニケーションコストがかかる
* ツッコミがはいると別チームに影響する
* 企画の資料にない仕様は開発からQAチームへいく
* 仕様変更毎に差分ができるので差分管理が…

##### 企画 -> 開発 -> QAの流れにした
* コミュニケーションコストが減った
* 確認項目が増えた
* QAチームによる確認コストが増大した
* QAで何をするのか基準作成がひつようになった

#### まとめ
* ひとつのサービスを成立させるために様々な役割がある
* 新しいサービスを作るには課題を解決しプロダクトに必要なチームを作る
    - 組織構造
    - コミュニケーション


-----
### フロントエンドエンジニアのDX向上委員会
* Speeker: @YuG1224(株式会社リクルートライフスタイル 山口 祐司)
* 資料: https://speakerdeck.com/yug1224/recochoku-tech-night-number-08

#### DX
* DeveloperExperience
* 開発者が開発を通じて得る経験や体験
    - プロダクトコードの品質が高い
    - テストやCI環境がメンテされている
    - オフィスが快適
* DXはUXの一種

#### 過去のFE組織構造の負
* 各プロジェクト単位でFETeamが閉じていた
    - チーム間の交流がなかった
    - 技術や経験の共有がない
    - 相談相手がわからない

#### いろいろやってみる
* 交流する場の設定と成果物を残すようにした
* プロジェクト枠を越境する共同体が生まれた
    - 公式ではなく
    - 改善と共有を繰り返す兆しが見えてきた

#### まだ戦い
* まだ全てのプロジェクトを跨げたわけではない
* 正のスパイラルを繰り返して広げていく！



-----
### a
* Speeker: @a()
* 資料:

#### a
* a

#### a
* a
# VueFesJapan

## 概要
* 日時: 2018/11/03
* 場所: UDX


## 1年間単体テストを書き続けた現場から送る Vue Component のテスト
* Speeker: 土屋 和良
* Slide: https://speakerdeck.com/tsuchikazu/vue-component-test

## talk
### Componentテスト
* 外部から見た振る舞いについてテストする
  - プライベートメソッドのテストは必須でない
  - Public Interface
    - Lifecycle
    - Props
    - VuexState
    - UserInteraction
  - Output
    - HTML,CSS
    - Event
    - VuexAction
* mount or shallow mount
  - mount
    - child component
  - shallow
    - without child component
* 対象
  - routerから読み込むいわゆるPageComponent
  - 複雑 or 共通で使用するComponent

### Lifecycleテスト
* 表示に必要なデータ取得のためにdispatchするぐらい
  - 安心感が低い
  - 他のテストした方がよさそう
  - mock化して他のテストの邪魔にならないようにする手も一つ

### Props/VueStateテスト
* 見た目に関わるテスト
* SnapShotTesting
  - 差分比較テスト
* VisualTesting
  - 実際に描画された内容のScreenShotで差分比較
* Storybook + REG-SUIT
  - Component単位でテストが可能
  - 開発フローに変更が可能
  - Storybookなのでデザイナーでも作業が可能
  - 無料
  - レビュー負荷が下がる
  - 方法
    - Storybookの画面をRegSuiteでキャプチャして比較
    - Storybook
      - propsを渡してテスト
      - VuexStateを渡してテスト
    - reg-suit
      - 画像の差分抽出が可能
    - CIでStorybookを起動しzisuiでキャプチャ画像を取得しreg-suitでブランチ分岐元の画像と比較
  - 改善ポイント
    - クロスブラウザ対応(Chromeベースなので)

### UserInteractionテスト
* クリック、入力 はツールがサポートしている
  - storeのモックを作成しmoutしてテストを行う
  - テスト中にスクリーンショットを撮りたい
    - karma-nightmare
      - screenshot APIを提供
    - スクリーンショット取得後はREG-SUIT

### まとめ
* VisualTestは安心感が高い
  - レビュー負荷も下がる

### QA
* cypressは検討されましたか？
  - 検討していない。知らなかった…
  - https://www.cypress.io/

## other
  * 便利そう
    - https://github.com/posva/vuex-mock-store

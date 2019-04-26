# VueFesJapan

## 概要
* 日時: 2018/11/03
* 場所: UDX
* https://vuefes.jp/


## title
* Speeker: EvanYou
* Slide: https://t.co/CnOPByvbs6

## Vue3.0 Updates
* 2019年中盤に登場予定

### Poit
* より速く
  - 仮想DOMの実装をフルスクラッチ
    - mountとpatch処理が最大100%向上
    - 後方互換性を考慮
      - ライブラリは調整が必要かも？
    - プロキシ監視
      - 完全な言語レベル
      - 速度向上
        - プロパティの追加と削除
        - 配列インデックスと配列長のミューテーション
      - GetterSetterからプロキシへ
        - プロパティの追加削除の監視が可能
        - ネイティブプロキシによるプロパティプロｓ騎士の高速化
          - Object.definePropertyさよなら
      - 実行中のオーバーヘッド削減のためコンパイルヒントを追加
        - RenderReactionはJSXレンダリングに似ている
        - コンポーネント探索の高速化+単型の呼び出し+子要素の種類を検出
          - 不要な条件分岐を省略
          - JSエンジンが最適しやすく
            - 関数の引数を同じにそろえる
            - render()はスロットを導入している。
              - v2 親要素で作成ー＞こは親の要素を参照しなければいけない
              - v3: LazyVunction。子要素は必要によって呼ばれる
                - レンダリング影響が子だけ(必要最小限)
            - StaticTreeHoisting(静的ツリーの巻き上げ)
              - Staticな要素からレンダリング要素だけ取り上げるHistingと呼ばれる
                - ノード自体へのPatch適用省略するが、子要素のpatch適用は実施する
                  - Tree内全体のりレンダリングから内容のみのりレンダリングへ
  - アプリ全体の速度が2灰に、メモリ使用量が半分に      -
    - コード変更の必要がない（フレームワークだから！）
* より小さく
  - Tree-shakingへの対応
    - ビルトインコンポーネント
    - ディレクティブのヘルパー
    - ゆーてぃりてぃー関数
  - 新コアのランタイムサイズ:Gzipで10kb以下
* よりメンテナンスしやすく
  - アーキテクチャの整理
  - パッケージの分離
  - テストセットアップの改善
    - ランタイムテストの容易化
    - スケジューラー
* よりネイティブ向けに作りやすく
  - カスタム連打らAPI
    - iOS,Android
    - 対象はブラウザに限定されていない
      - ブラウザ: 仮想DOM作成->Render
      - CustomRenderAPI: 仮想DOM作成->あとは使用先が決める
* よりコード保守性を向上
  - 理アクティビティAPI
    - データをコンポーネントないから分離できる
      - Observableメソッド
        - どのオブジェクトに対しても監視することができる
        - ステートの変更によりレンラリング関すを呼び出すことができる
        - すてーとをへんこうするだけですべての変更点を変更することが可能
          - Vuexを使わなくてもこれだけで済ますことが可能
  - コンポーネントの再描画を理解する
    - Inspecter Stackで変更を追いやすくする
- TSXによるTypeScriptサポート強化
  - クラスコンポーネントを扱うことが可能に
  - TSXでRender関数記述が可能に
- 実験的なHooksAPI
  mix-in ネームベースの問題
    構成を簡単に
- 事件的なTimeSlice
  - 処理を分解してstackすることがないように
  - ko-dohennkouno hituyouhanaku
  - TimeSliceingを含むVueにするだけでよい




## 他session資料
* Next-level Vue Animations
  - http://slides.com/sdrasner/vuefes-japan#/
* Vue Designer: デザインと実装の統合
  - https://slides.com/ktsn/vue-fes-vue-designer#/
* Vue CLi
  - https://slides.com/akryum/vue-cli-18-3-jp#/

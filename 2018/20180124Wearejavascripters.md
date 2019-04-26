# We are javascripters 15th

## 概要
* 日時: 2018/01/24
* 場所: Microsoft Shinagawa



## session


### webpackと仲良くなろう
* Speeker: @mki_skt()
* 資料: https://speakerdeck.com/mukai21/webpacktozhong-liang-kunarou

遅刻した…


-----
### JavaScriptのE2Eフレームワークを触ってみる
* Speeker: @riririusei99(TeamSpirit)
* 資料: https://speakerdeck.com/riririusei99/javascriptfalsee2ehuremuwakuwohong-tutemiru

#### E2E testing

#### Protractor
* Angular.js向け
* selenium web driver

#### testCafe
* async/await
* Seleniumを使わない
* モダンjsでかける

#### Nightmare
* seleniumを使わない
* electronベース
* ブラウザ自動ツールとしても使える
  - phantom.js系

#### cypress
* CLIでも動く
* 導入が非常に簡単
* 修正を検知してテストが走る

#### cinnamonjs
* DDTを意識したフレームワーク
* 独自のレポーティング機能
* Json形式

#### E2E選定
* クロスブラウザ
* CI
* 描きやすさ
* 導入のしやすさ
##### で
* cypressが目的にあってた
  * clossブラウザとかはseleniumで
  * 役割分担


-----
### CSS書きたくない問題を解決するAngular Material
* Speeker: @h_reader(SI)
* 資料:

#### AngularMaterial
* マテリアルデザインライブラリ
* css, class属性を書かなくてもhtmlタグでマテリアルデザインを構築できる

#### まとめ
* B2B案件くらいなら耐えられる
* datepickerデフォルトでは英語基準
  - 指定は可能

-----
### コードリーディング初心者がhyperappを読んだ
* Speeker: @atsuco(フリーランス)
* 資料: https://speakerdeck.com/atsuco/kodorideinguchu-xin-zhe-gahyperappwodu-nda

#### HyperApp
* 今年はHyperAppの年らしい
* JSライブラリ
* 状態の変化を仮装Nodeを通して見た目に反映する
* 他のライブラリに依存しない
* 1KB
* QuiitaがReactから移行した

#### コンセプト
* vertualNodes
* key
* Compornent
* LifecycleEvents
* Sanitaize

#### h関数
* 仮装Nodesを作ってくれる

#### app関数
* wireStateToActions()
  - stateを更新、適宜scheduleRender()を呼び出し
* scheduleRender() / render()
  * 仮想Nodesをこうしんしつつライフサイクルイベントを実装
* Patch()
  - 仮想Node

#### 読んで見て
* ちょっとしたプロトタイピングとかにはよさそう
* 行数が300ちょっとしかない
* 読めるので何が起こってるかわかるようになる
  * いろいろしたくなるがそれはHyperAppの範疇ではない

-----
### Reactでモダンにスタイリングする方法
* Speeker: @sottar(メルカリ)
* 資料: https://speakerdeck.com/sottar/modannajavascriptapurikesiyondemodannisutairingusurufang-fa

#### Reactでcss
* スタイリング
  - CSS modules
  - CSS in JS

#### CSS in JS
* JS内でStyle定義
* Package種類がたくさんある
  * styled-componentsを使った

#### できる
* componentごとにスコープきりたい
* どこで使われているか知りたい
* cssとjsで値を共有したい
* シンタックスハイライトや補完機能をかつようしたい
* 標準のCSSと同じシンタックスで書きたい
* styleLint使いたい
* 特定のツールを使わなくてもJSエラーが発生しない

#### なぜ
* Reactから使いやすい
* 独立したスタイル用のコンポーネントを作っていく方法
* Reactコンポーネント設計に合わせてスタイルも継承できる
* ReactNativeにも対応している
* __綺麗なコンポーネント設計ができる__



-----
### Abstract Syntax Tree in Javascript
* Speeker: @brn(Cyberagent)
* 資料: https://speakerdeck.com/brn/abstract-syntax-tree-in-javascript

#### ASTとは？
* パースした結果生成される構文を表現した木構造
  * JSコンパイラは処理指示を木構造で解釈、処理する
* ECMAで定義
  * Grammars

#### Javascript
* パースはかなり難しい
  * パーサー自体にかなりの状態を持たせている…

#### AST
* ASTからScopeを生成したりする
* Babel
  - ASTを変換
* istanbul
  - ASTを変換して各コード間に通過した印をつけるコードを埋め込む
  - カバレッジにつかう
* Esprimaを使うことで簡単にASTを生成することができる

#### まとめ
* 一回くらいは試してみたほうがいい


-----
### 生のJSでTodoList作ろうとして苦労した話
* Speeker: @yuri_xxx8()
* 資料:

#### 学んだこと
* 検索ワードに英語を使う
* 他のほうほうで実装できないか可能性を考える
* アクセシビリティを考える


-----
### VJ with JavaScript
* Speeker: @takanorip(smart drive)
* 資料: https://speakerdeck.com/takanorip/vj-with-javascript-1

#### VJ
* VideoJockey
* VisualJockey

#### 作る流れ
* 素材を集める、作る
* 加工する
* Processiong

#### VJ JavaScript
* WebAudioAPI
* three.js
* AnalyserNode
  - リアルタイム時間領域周波数領域分析情報


-----
### 型の話
* Speeker: @chikoski()
* 資料:

#### 型
* 実行させなくてもある程度の予測ができる
1. typeofで型判定
2. instanceofの振る舞いを定義する
  * Symble.hasInstance
3. 高階関数
  * list.map(f).reduce((i, j) > i + j);
    * fの定義が不明
4. TypeScript
  * 型定義
  * 代数型演算子

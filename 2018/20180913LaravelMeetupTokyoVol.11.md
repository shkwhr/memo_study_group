# Laravel Meetup Tokyo Vol.11

## 概要
* 日時: 2018/09/13
* 場所: 愛スタイル


## session

-----
### クラシコムとLaravelとDDD
* Speeker: @takeru0757 クラシコム広瀬
* 資料: https://speakerdeck.com/takeru0757/kurasikomutolaraveltoddd?slide=17

#### DDDやってみた(RailsからLaravelへ移行)
* ドメインロジックをコードで表現
  - ユビキタス言語 = クラス
    - 合計金額の計算
      -> 商品単価クラス, 注文数量クラス
        -> 小計クラス
  - 業務知識を言語仕様によって表現できる(強制できる)
  - 仕様(ロジック)がクラスに内容されているので散逸しない
    - 反していたら実行できない
    - 堅牢製

#### Laravel と DDD の統合
* Entityの永続化
  - RepositoryPattern
    - Entity自体に永続化に関するメソッドを持たせない
    - Repositoryから取得->Entity
*  Contoroller /Validator
  - Contorollerの役割はUIとDomainLayerの間をとりもつ
    - データの生合成はDomainLayer以下で担保
  - Validatorの役割は例外を発生させないこと

#### 感想
* 業務知識に対する理解が深まる。
  - わからないとクラスが作れない
* コードで表現しようとすることで仕様が明確になる
  - 全ての概念を論理的に記述するため曖昧な仕様が存在しえない
  - コードを読めば仕様がわかる
* 業務知識に関するテストが楽になる
* モデリング難しい
  - モデルの境界
  - DBトランザクション
  - パフォーマンスとの兼ね合い
* DDDは有用だがどこまでコードに落とし込むか選択の余地あり
* 堅牢性・安心感

-----
### Laravelを使った既存WebサービスのAPI化
* Speeker: @endo1881 GMO Payment遠藤
* 資料: a

#### 既存の仕様に合わせたRESTfulAPI
#### Why Laravel
* ドキュメントが多い
* 認証と認可ログのライブラリ

#### SwaggerでAPIドキュメント化
* $refを使用してdefinitionsとpathsを分割して管理する
  - definitionディレクトリいかにModel
  - swaggerファイルを分割

#### 責務を分けたディレクトリ構成
* FatController対策
  - サービスロジックを作った

#### DBの仕様に合わせてLaravel側で調整する
* DBが複数存在する
  - .envで複数DB記述できる
  - $connectio定義
* Eloquentでアクセサを定義
  - 複数のシステムが同居しないならOK




-----
### Validation shallow Dive
* Speeker: @tsurushima ストアクラウド 鶴島
* 資料: a

#### Validation
* validated
  - validationされた値
  - ネスとされた値は全て返される。。。
    - PR->Mergeされた！
      - 5.7で反映される
  - 5.6までは全部返ってくるのでFormRequestで上書き修正しよう

#### 知見
* おかしいと思ったらコードとテストをみよう
* DisるんじゃなくてPRしよう


-----
### 駆け出しLaravelerが一人前になるまでを聞きたい
* Speeker: プラムザ　山崎
* 資料: https://speakerdeck.com/hirotaka_yamazaki/presentation-for-laravelmeetup11-plumsa

#### 技術書店出店
* はじめてのLaravel
  - 挫折させない
  - 全9章
    - ToDoリストを３周する

-----
### Laravelで式年遷宮中の現場でうまくいってること・うまくいっていないこ
* Speeker: @blue_goheimochi
* 資料: https://www.slideshare.net/ohashiyuta/laravel-114240992/

#### うまくいってること
* レイヤードアーキテクチャでDDD
  - ３層アーキテクチャ
  - ADR
    - URLとアクションファイルが1対1
    - 変更箇所が推測しやすくなる
* サポートチームの意見の吸い上げ
  - ユビキタス言語をつくるにはコミュニケーション

#### うまくいってないこと
* アプリのキメラ化
  - フェーズが3つくらいある
    - やってみたバージョン
    - やめてみたバージョン
  - 新規参入者への説明がたいへん
* DDDとADRがあまり理解してなかった
* いろいろFatしてる
  - 責務…

#### これからどうする
* わかっていなかったことがわかった
  - 理解してから晋では遅すぎる
  - 学習・実施サイクルを回す

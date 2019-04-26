# WASP Connect in Tokyo #2

## 概要
* 日時: 2019/01/25
* 場所: Yahoo!Japan LODGE
* https://owaspprteam.connpass.com/event/113927/
* OWASPConnect


## session

-----
### 関西発信！繋ぐ・学ぶ・育てる セキュリティの輪
* Speeker: 伊藤 太一さん(オワスプカンサイ ボード)

#### owasp kansai
* OWASP Kansai Doorkeeper
* www.safewebkids.net
* yamatosecurity.connpass.com
* 構成員
  - ボードメンバー
    - 開発者・経営者・弁護士
  - 若い人材が継続して必要
    - 学生向けイベント（NAISTとか)
* 多様性
  - 経営とセキュリティ
* ゆるいつながり
* セキュリティ関係者関西人多い？
  - 多分多い
  - よく外(イベント)に出てる傾向が強い


  -----
### OWASP Project
* Speeker: 石切山
* Slide: https://speakerdeck.com/wireworkes/owasp-project-overview-2018

#### category
* ドキュメンテーション
* ツール
* コードライブラリ
* オペレーショナル

#### stage
* incubator
* lab
* flagship
  - tool
  - code
  - documentation
  - OWASP TOP10
    - IoT版がある
    - github にowaspプロジェクトがある
      - https://github.com/OWASP
    - Docker hubにも
      - https://hub.docker.com/u/owasp

#### use&feedback
* OWASP JAPAN独自のプロジェクトがある
  - https://www.owasp.org/index.php/Japan
    - https://github.com/ueno1000/secreq
* 試して欲しい
  - フィードバックが欲しい
* シフトレフト
  - 「シフトレフト」：より早い段階で（脆弱性の）チェック

-----
### OWASP Internet of Things ProjectのIoT Firmware Analysis Projectの話
* Speeker: @mahoyaya
* Slide:

#### IoT Project
* OWASP Top10 Iot
  - 2014 -> 2018
    - より実務に近い内容に更新された

#### Firmware Analysis Project
* デバイスファームのセキュリティテストを案内することを目的
* Firmware
  - ベンダ提供をダウンロード
    - 提供してない場合
      - アップデート時の通信をキャプチャ
        - wireshark
      - ハードから物理的に取得
* 解析
  - `file`コマンド
    - ファイルの種類調査
  - `md5sum`等でチェックサムを確認する
  - `strings`コマンド
    - 読めそうな文字列出力
  - `hexdump`コマンド
    - バイナリの中身を表示
      - ファームウェアの特徴・情報
  - `binwalk`コマンド
    - リバースエンジニアリング
    - ファームイメージからのデータ抽出
* 抽出
  - `dd`コマンド
    - ファームウェア抜き出し
      - `binwalk`も同様のことができるが、精度が高い
  - `sasquatch`コマンド
    - FirmwareModificationKit標準のunsquashfsにパッチを当てたもの
    - カスタムされたベンダ固有のSquashFS実証に対応
      - 展開先: squashfs-root
* 確認ポイント
  - ssl,password,authorized_keyとかの情報が展開されてるかも
* FirmwareModificationKit
  - ファームウェアの展開・再構築ができる
  - 普通のunsquashfsでないものがある
    - unsquashfs_all.shを試す
      - sasquatchのがおすすめ
  - jffs2ファイルシステム展開
    - `unjffs2`バッチ
  - CPIOアーカイブファイル展開
    - rpm, LinuxKernelの起動RAMとして利用
    - `cpio`
  - UBIファイルシステムの展開
  - `binwalk`があると勝手に展開してくれる
* Mounting the file System

* チェック
  - firmwalker script
    - 重要そうなファイルをピックアップしてくれる
* 動かす
  - デバイス上で実行しない場合に確認する手段
    - QEMU: エミュレーション

#### 試したい場合
* Githubに様々なファイルシステムが置いてある


-----
### OWASP Dependency checkとTrackとその他の脆弱性検知ツールと連携
* Speeker: Inoue Kei (@hogehuga) フューチャー

#### Dependency check
* https://hub.docker.com/r/owasp/dependency-check
* アプリの基地の脆弱性のあるコンポーネントを検出するツール
  - ライブラリ
  - フレームワーク
  - ソフトウェアモジュール
* 構築(運用開始前)段階で脆弱性を認識できる
* 対象
  - Java
    - check自体がJavaアプリ
  - .NET
  - 限定
    - Python
    - Ruby
    - PHP
    - Node.js
* できること
  - アプリをスキャンし、依存するライブラリ等のCPE(共通プラットフォーム一覧)を識別する
  - CPEをもとに、NISTのNVDデータフィードで基地の脆弱性を検出
  - プラグインとして実行が可能(CIに組み込める)
    - Jenkins
    - Maven
    - Ant
  - HTML,XMLで出力可能
* できないこと
  - アプリケーション外のライブラリの検査

#### Dependency track
* checkの状況を継続して収集し分析できる
  - checkと同じくJenkins等でCIに組み込むことが可能
* 今の所リソースを結構食う様子…

#### 他システムとの連携
* OS/ミドルウェア側の脆弱性ツール`Vuls`
  - CheckのXMLと連携が可能

-----
### OWASP Cheatsheetを参考にやられアプリ作ってみた
* Speeker: 幸田将司(@halkichisec)
* Slide: https://www.slideshare.net/mkoda/owasp-cheatsheet

#### やられアプリ
* 脆弱性の学習
* スキャンツールを試す
* 公開されてるアプリ
  - OWASP BWA
    - bWAPP

#### OWASP CheetSheet
* 実装の注意点、スタンダードを網羅
  - 脆弱性ベース
  - 言語ベース
* 脆弱なコードのパターンや攻撃の文字列例


-----

## LT

### OWASP Snakes and Ladders
* Speeker: 柴雑種
* Slide: https://speakerdeck.com/zash_shibainu/elv-sec-2-bodogemudesekiyuriteiwoxue-bou

#### Snakes and Ladders
* ワープアリのすごろく

#### OWASP Snakes and Ladders
* 有識者がいた方が盛り上がる
* 進行方向がわかりづらくなって逆走が…
* A3サイズ用紙でもちいさい

-----
### BurpとZAPの「Faraday v3」へのインテグレーション
* Speeker: @ekio_jp

#### Faraday
* BurpとZapの脆弱性診断結果管理
* ペネトレーションテスト


-----
### OWASP SAMMで可視化してわかったこと
* Speeker: 松田 @KoujiMatsudakdl (神戸デジタルラボ)

#### SAMM
* 開発体制をチェック項目、点数で可視化したもの

#### わかったこと
* セキュリティテストに大きく依存した体制だったー
  - セキュリティ設計とかが弱かった
  - 可視化したことで説得資料に
  - チェック項目に合わせて開発体制を変更

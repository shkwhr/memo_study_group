# html5 confarence 2018

## 概要
* 日時: 2018/11/25
* 場所: 東京電機大学
*


## HTTPの今と未来
* Speaker: 浅井智也(WebDino)、永井泰裕(Softbank)
* Slide: http://urls.jp/http3

### Introduction
* ネットワーク技術の変化を知らないとやばい
  - 通信料を削減する
    - Minify
    - Gzip, Brotli
    - HTTP/2, QUIC
  - サーバの応答を早くする
    - TLS1.3やQUIC, O-RTT接続やBBRの導入

### 5Gの世界
* 5G(りそう)
  - 10Gbps
  - 1ms以下
  - 100万デバイス/km2
  - 2020頃実現
* 5G(サービスネットワーク)
  - 3G(音声),4G(データ)
  * 低遅延特化研究
    - 機器遠隔制御
    - eSports
  * 大容量特化
    - VRコンテンツ
    - 8K映像
* 開発者にとって(Web for 5G)
  - Malti-access Edge Computingの活用
  - エンドユーザへのサービス視点(UX)がないとやばい
    - 土管屋からの脱却の必要性
    - 他企業との連携
      - ARM, nVidia
  - 企業との5Gサービス共創

### HTTP2/TCP
* HTTP1.1,TLS1.2の課題・限界
  - HTTPヘッドオブラインブロッキング
    - 待ち行列の先頭が詰まると待たされる問題
* TCPの課題・限界
  - TCP HOLブロッキング
    - 前方が詰まるとパケット単位で待たされる
    - 不安定なネットワークでは帯域が活かせない
* 1.1 -> 2
  - 単一TCP接続場での非同期並列通信
  - ヘッダ圧縮による通信効率の向上
* TLS1.3
  - 0-RTT実現
    - FullHandshakeでも1-RTT
  - 前方秘匿性がない
  - リプレイ攻撃をTLSレベルで区別できない
    - 第三者に再送されても問題ないようアプリ側で実装しておく必要がある
* TCPにおける輻輳制御
  - ロスや再送なく送信できる帯域を推定し通信速度を調整して送信する仕組み

### HTTP3/QUIC
* QUIC HTTP+TLSoverTCPをUDP場で再実装したもの
  - HTTP/2+TLS1.2+TCPのHOLブロッキングを解消
* 試せるの
  - Litespeed
    - 有償
  - 来年以降NgineXでも使える
* Softbank & WebDINOJapanが調査結果を公表
  - なぜ5G帯域を使いきれないのか
    - 隊服を正しく検出できていない
    - パケロス、RTT変動などが生じない全ん丁の生業は5G環境とは相性が悪い
    - ヘッドオブラインブロッキング
      - Quick以外では頻繁に生じる

---
layout: page
title: "ネットワークマネージャ"
description: ""
group: "reference/network"
---
{% include JB/setup %}

#### startAccept( int port, xtal::FunPtr handler )
接続待機を開始する。`port`に待ち受けるポート番号を、`handler`に接続成功時に呼び出す関数名を指定。


#### stopAccept()
接続待機を終了する。

#### connect( const char* host, int port, xtal::FunPtr handler )
接続する。`host`に接続先のIPアドレス、`port`に接続するポート番号、`handler`に接続成功時に呼び出す関数名を指定。

#### disconnect()
切断します。

#### startKeySync()
キー入力同期を開始する。以降、接続している相手と入力が完全同期される。

入力ディレイは3F、ホストが1P側、ゲストが2P側で固定となる。

どちらか片方が`startKeySync()`を行えば両方が自動で同期状態となる。

同期されるタイミングは不定のため、`isKeySync()`を使って同期の開始を確認すること。

#### stopKeySync()
キー入力を停止する。

#### bool isConnection() const
現在の接続状態を取得する。接続されていれば`true`、切断されていれば`false`を返す。

#### int isKeySync() const
現在のキー同期状態を取得する。

戻り値 | 意味
--- | ---
-1 | 同期していない
0 | 同期している（1P）
1 | 同期している（2P）

#### sendString( const char* str )
指定した文字列を送信する。

#### setRecvHandler( xtal::FunPtr handler )
`sendString`に対応。接続後、予め設定しておくことで文字列を受信した際に`handler`を呼ぶ。

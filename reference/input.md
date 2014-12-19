---
layout: page
title: "入力マネージャ"
description: ""
group: "reference/input"
---
{% include JB/setup %}

#### getInputSingle( int pad, bool pad_only = false )
単一のキー入力を返す。`pad`は0で1P、1で2P、2で3P……と続く。

`pad_only`が`true`の場合、キーボードの入力を無視してパッドからの入力のみを返す。

    key : input_manager.getInputSingle( 0 );
    ( key.to_s ~ "が押されました！" ).p;

#### setKeyConfig( int pad, int target, int key )
キー設定を行う。`pad`は0で1P、1で2P、2で3P……と続く。

`target`に割り当て対象となるキー（便宜上A〜Fだとするなら、A=16, B=32, C=64, D=128, E=256, F=512となる）を指定、

`key`には割り当てるキーを設定する。キーコンフィグの実装には、`getInputSingle`と併用することを推奨。

また、`key`に0を指定することで`target`の入力を無効にすることができる。

    "Aボタンに割り当てたいボタンを押してください。".p;
    key : input_manager.getInputSingle( 0, true );
    if( key != 0 )
    {
        input_manager.setKeyConfig( 0, 16, key );
        ( key.to_s ~ "を割り当てました！" ).p;
    }

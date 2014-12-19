---
layout: page
title: "ランダムユーティリティ"
description: ""
group: "reference/util"
---
{% include JB/setup %}

#### SetSeed( int seed )
シードを設定する。デフォルトでは100が設定されている。

    random_util.SetSeed(45);

#### double Get( double min, double max )
`min` 〜 `max`の範囲で乱数を取得する。

    val : random_util.Get( 5, 10.5 );
    val.p;

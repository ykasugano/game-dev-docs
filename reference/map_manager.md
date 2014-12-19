---
layout: page
title: "マップマネージャ"
description: ""
group: "reference/map"
---
{% include JB/setup %}

#### set( const char* name )
マップを読み込む。

    map_manager.set( "test" );

#### const CMap* get()
現在のマップを返す。

    map : map_manager.get();
    map.getProperty( "reset_x" );

#### reset()
現在のマップを破棄する。

    map_manager.reset();

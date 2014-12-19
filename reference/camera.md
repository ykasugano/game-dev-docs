---
layout: page
title: "カメラ"
description: ""
group: "reference/camera"
---
{% include JB/setup %}

#### setScreenSize( int width, int height )
画面のサイズを設定する。

通常、解像度が変わるタイミングで一回だけ設定する（設定で解像度が変えられないゲームであれば起動時一回のみ設定する）。

    camera.setScreenSize( 800, 450 );

#### setPos( double pos_x, double pos_y )
座標を変更する。

    camera.setPos( camera.getX() + 1, camera.getY() );

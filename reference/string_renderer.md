---
layout: page
title: "文字レンダラ"
description: ""
group: "reference/renderer"
---
{% include JB/setup %}

#### setPos( int pos_x, int pos_y )
文字を描画する位置を決定する。デフォルトでは(0,0)。

    string_renderer.setPos( 100, 150 );

#### setColor( int r, int g, int b )
文字色を設定する。デフォルトでは(0,0,0)。

    string_renderer.setColor( 128, 128, 255 );

#### setFont( const char* name, int size, int thick, int type = 0 )
フォントを設定する。

typeに入れる値 | 意味
---- | ----
0 | ノーマルフォント
1 | エッジつきフォント
2 | アンチエイリアスフォント
3 | アンチエイリアスフォント( 4x4サンプリング )
4 | アンチエイリアスフォント( 8x8サンプリング )
5 | アンチエイリアス＆エッジ付きフォント( 4x4サンプリング )
6 | アンチエイリアス＆エッジ付きフォント( 8x8サンプリング ) )

    string_renderer.setFont( "MSゴシック", 10, 3, 2 );

#### activateFontFile( const char* path )
フォントファイルを指定して、そのフォントを使用できるようにする。

    string_renderer.activateFontFile( "/data/akimai.otf" );

#### render( const char* str )
現在の設定で文字を描画する。

    string_renderer.render( "こんにちは" );

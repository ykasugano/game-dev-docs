---
layout: page
title: "BGM"
description: ""
group: "reference/bgm"
---
{% include JB/setup %}

事前準備として `data/bgm/define.txt` にBGMの定義を記述しておく。

    ファイル名,ループポイント始点,ループポイント終点(設定しない場合は-1),BGM名

とカンマ区切りで定義し、それを複数行に並べる。

#### play( const char* name )
BGMを再生する。nameにBGM名を指定する。

    bgm.play( "ステージ曲" );

#### stop()
現在再生しているBGMを停止する。

    bgm.stop();

#### setVolume( int volume )
BGMの音量を変更する。volumeに指定する値は255〜0（無音）。

    bgm.setVolume( 200 );

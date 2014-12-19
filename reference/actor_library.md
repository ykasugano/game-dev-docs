---
layout: page
title: "アクターライブラリ"
description: ""
group: "reference/actor"
---
{% include JB/setup %}

#### loadXtal( const char* name )
指定したプリセットのXtalバイトコードを更新する。

    actor_lib.loadXtal( "player" );

#### loadPreset( const char* name )
プリセットをファイルから読み込んで追加する。

    actorList : [
        "intermission",
        "player",
        "input"
    ];
    actorList {
        actor_lib.loadPreset( it );
    }

#### finalize( bool async )
既に読み込まれているプリセットの最適化とテクスチャの読み込みを行う。

全てのプリセットの読み込み終了後に一度だけ実行すること。

`async`が`true`になっていると、非同期読み込みを行う。

非同期読み込み時にはすぐに処理が返ってくるので、`doesAsyncLoadFinish()`を利用して読み込みの終了を確認する必要がある。

    actor_lib.finalize( false );

#### unloadPreset( const char* name )
読み込んだプリセットをメモリから削除する。

    actor_lib.unloadPreset( "player" );

#### clear()
読み込んだ全てのプリセットをメモリから削除する。

    actor_lib.clear();

#### bool doesAsyncLoadFinish()
非同期処理が終了しているかどうか確認する。

    finalize( true );
    while( !actor_lib.doesAsyncLoadFinish() ) {
        // 非同期読み込みが終わるまでここで止める
        yield;
    }
    // ここから非同期読み込み終わった後の処理

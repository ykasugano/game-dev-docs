---
layout: page
title: "アクターマネージャ"
description: ""
group: "reference/actor"
---
{% include JB/setup %}

#### init()
全てのアクターを削除し、初期化する。

    actor_manager.init();

#### CActor* add( const char* preset, const char* motion, int z )
アクターを追加する。呼び出されたアクターのポインタを返す。

なお、Z座標は-1000がリミットになっており、それ以下になるとカメラの影響を受けなくなる。

    player : actor_manager.add( "player", "初期化", 0 );

#### xtal::ArrayPtr getAllActor() const
存在する全てのアクターのポインタをリストにして返す。

    actor_list : actor_manager.getAllActor();
    actor_list {
        it.sleep(10);   // 全てのアクターが10Fスリープする
    }

#### int count() const
存在する全てのアクターのポインタをリストにして返す。

    actor_total : actor_manager.count();

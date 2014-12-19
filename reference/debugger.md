---
layout: page
title: "デバッガ"
description: ""
group: "reference/debugger"
---
{% include JB/setup %}

#### pause( xtal::ClassPtr xtal_scope )
実行を中断する。同時にMarigold（エディタ）が立ち上がり、xtalのコードを実行できる。

後述の`getLocalVar`のため、実行時に`this`を与えておくこと。

    debugger.pause( this );

#### resume()
実行を再開する。

    debugger.resume();

#### getLocalVar( const char* name )
`pause`時に与えたスコープで指定した名前の変数にアクセスする。

    debugger : lib::getDebugger();
    debugger.getLocalVar( "foo" ).p;    // "foo"という変数を出力
    debugger.getLocalVar( "bar" )();    // "bar"という関数を実行

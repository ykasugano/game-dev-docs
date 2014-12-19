---
layout: page
title: "アクター"
description: ""
group: "reference/actor"
---
{% include JB/setup %}

#### double getX()
現在のX座標を返す。

    x : me.getX();

#### double getY()
現在のY座標を返す。

    y : me.getY();

#### int getZ()
現在のZ値を返す。

z : me.getZ();

#### setPos( double pos_x, double pos_y, bool collision = false )
座標を変更する。

`collision`を`true`にすると、移動先でのマップとの衝突判定を行う。

    me.setPos( 100, 200 );

#### setZ( int z )
Z値を変更する。

    me.setZ( 5 );

int getTexture() const
    現在のテクスチャを取得する。

    handle : me.getTexture();
    otherActor.setTexture( handle, 5 );     // 自分のテクスチャを別のアクターにコピー

#### setTexture( int handle, int frame )
指定したハンドルのテクスチャを表示する。
OliveにおけるImageステップと同様の効果。`frame`によって表示する長さを変更可能。

    textures =  lib::loadTexture( "tex/hogehoge.png", 4, 3, 32, 32 );
    me.setTexture( textures[0], 10 );

#### double getMoveX();
現在のX移動値を取得する。この場合のX移動値とは、保有している様々な移動ベクトルのX成分を合計したものとなる。

    move_x : me.getMoveX();

#### double getMoveY();
現在のY移動値を取得する。この場合のY移動値とは、保有している様々な移動ベクトルのY成分を合計したものとなる。

    move_y : me.getMoveY();

#### setMove( bool x_enable, bool y_enable, double x, double y );
移動値を変更する。

`x_enable`または`y_enable`に`false`を与えると、それぞれX移動値、Y移動値に影響を与えない。

    me.setMove( true, false, 30, 0 );

#### setVectorMove( double dir, double speed )
ベクトル移動値を変更する。

`dir`に角度、`speed`に移動速度を指定する。

    me.setVectorMove( 30, 20 );

#### setDirection( double dir )
角度を設定する。`setVectorMove`の移動速度指定を省いたもの。

    me.setDirection( 50 );

#### setBlend( int type, int factor, int d_factor )
ブレンドを設定する。`factor`は0〜255までの数値、`d_factor`は動的数値。

OliveにおけるBlendステップと同様の効果。

typeに入れる値 | 効果
--- | ---
0 | ブレンド無し
1 | 半透明
2 | 加算
3 | 減算
4 | 乗算
5 | 反転
6 | 半透明（輝度4倍）
7 | 加算（輝度4倍）

    me.setBlend( 1, 100, 2 );

#### setScale( bool x_enable, bool y_enable, bool d_x_enable, bool d_y_enable, double x, double y, double d_x, double d_y )

拡大率を設定する。

OliveにおけるScaleステップと同様の効果。

`enable`を`true`にすると有効、`false`は無視。`d_***`が動的拡大縮小の値。

    me.setScale( false, false, true, false, 0, 0, 10, 0 );

#### setRotation( bool a_enable, bool d_enable, double angle, double d_angle )
回転を設定する。

OliveにおけるRotationステップと同様の効果。

`enable`を`true`にすると有効、`false`は無視。`d_***`が動的回転の値。

    me.setRotation( true, true, 30, 1 );

#### setFilterHSB( int hueType, int hue, int saturation, int bright )
色相・彩度・明度フィルタを設定する。

`hue`はRGBの色相、`saturation`は彩度（-255〜0の相対値。変更しない場合は0）、`bright`は輝度（-255〜255。変更しない場合は0）

hueTypeに入れる値 | 意味
--- | ---
0 | 相対値（hueの指定範囲は-180〜180）
1 | 絶対値（元の色相の値を無視するのでモノトーン調になる。hueの指定範囲は0（赤）〜120（緑）〜240（青）〜360（再び赤））

この関数は負荷が大きく、その対策として実際に反映されるのはOliveのImageステップ、あるいは`setTexture`でテクスチャを更新した後となるため注意。

    me.setFilterHSB( 1, 240, 0, 0 );

#### clearFilter()
フィルタを削除する。

フィルタを削除した時点で即座に描画が変わるのではなく、OliveのImageステップで次のテクスチャがセットされた際に通常の描画に戻る点に注意。

    me.clearFilter();

#### transition( const char* motion, int step, bool lock = false )
モーションを遷移する。

`lock`が`true`の場合、同一モーションからの遷移を行わない。省略時デフォルトは`false`。

    me.transition( "移動", 3 );

#### CActor* call( const char* preset, const char* motion, double x, double y, int z, int turn = 0 )

他のアクターを呼び出す。呼び出されたアクターのポインタを返す。

`x`,`y`座標指定は、親アクターからの相対座標指定となる。親アクターの反転時は自動で座標も反転される。

turnに入れる値 | 意味
--- | ---
0 | 親の向きに従う（省略時デフォルト）
1 | 通常
2 | 反転

    child : me.call( "enemy01", "移動", 20, 0, 0 );
    child.getX().p;         // 呼び出したenemy01のX座標を表示

X座標とY座標は親との相対値になってるいるので、例えば(15,15)にゲージを配置したければ

    gauge : me.call( "gauge01", "初期化", 15 - me.getX(), 15 - me.getY(), -1000 );

のようにする。

#### bool getCommand( const char* name, int pad = 0 )
コマンドが完成しているかを返す。Irisの生成したcommand.datが必要。

`pad`に`0`を与えると（省略時デフォルト）1Pの入力を返し、1を与えると2Pの入力を返す。

    if( me.getCommand( "A波動" ), 0 ) {
        "コマンド成立したよ！".p;
    }

#### turn()
振り向く。右向き（デフォルト）なら左向き、左向きなら右向きになる。

    me.turn();

#### bool isTurn()
振り向いている（左向き）かを返す。

    is_turn = me.isTurn();

#### xtal::ArrayPtr hitDetect( int group, bool pos = false ) const
他のアクターと当たり判定を行う。

`group`に判定を行いたい当たり判定グループの数値を入れる。

返り値はxtal::Arrayなので詳細は[リファレンス](http://sukai.sakura.ne.jp/xtal/reference/array)を参照。

`pos`が`false`のとき（デフォルト）、`Array`にはヒットした全てのアクターのポインタがまとめて格納される。

`pos`が`true`のとき、Arrayにはアクターのポインタの他に重なった矩形の中心点のx,y座標が格納される。当然負荷があがるので注意。

    result : me.hitDetect( 1 );
    result {
        it.getX().p;    // ヒットした相手のX座標を表示
    }

    result : me.hitDetect( 2, true );
    result {
        it.actor.getX().p;      // actorにポインタ、
        it.x.p;                 // xにx座標、
        it.y.p;                 // yにy座標が入る
    }

#### setReact( const char* func, int type )
マップとの衝突判定時に呼ぶXtalの関数を設定する。
アクターが移動してマップに接触した場合には常に自動でこの判定が行われ、設定されている関数を呼び出す。

typeに入れる値 | 判定する相手
--- | ---
0 | 床
1 | 壁
2 | 天井

    me.setReact( "onGround", 0 );

#### bool isHitMap( int type ) const
マップと接触しているかを返す。

typeに入れる値 | 判定する相手
--- | ---
0 | 床
1 | 壁
2 | 天井

    is_ground = me.isHitMap( 0 );
    if( is_ground == true )
    {
        // 接地時の処理
    }

#### setCollision( bool hit )
アクターの持っている0番目の当たり判定を、マップ同様に他にアクターと衝突する対象に設定する。

    me.setCollision( true );

#### setRenderLimit( int width, int height )
描画範囲を設定する。

画像の(0,0)座標から(width,height)までを四角く切り取って描画するようになる。

拡大縮小、回転は無効になり、カメラの影響も受けなくなる。

    me.setRenderLimit( 100, 200 );

#### playSE( const char* name ) const
SEを再生する。

data/se/define.txt で記述したSE名を引数として与える。

    me.playSE( "ヒット音" );

#### sleep( int frame )
指定したフレーム分だけ、更新を停止する。

更新を停止すると移動や拡大縮小、回転、動的なブレンド、`passive`のコールなどが行われない。

解除したい場合には`sleep( 0 )`で残りフレームを上書きする。

me.sleep( 5 );

#### quit()
終了する。OliveにおけるExitステップと同様の効果。

    if( health < 0 ) {
        me.quit();
    }

#### vars
変数を管理するマップ。
`vars : me.vars;`してから使うと良い。
正体はxtal::Map。詳細は[リファレンス](http://sukai.sakura.ne.jp/xtal/reference/map)を参照。

変数をセットしたい時

    vars["key"] = 100;

変数を取得したい時

    val = vars["key"];

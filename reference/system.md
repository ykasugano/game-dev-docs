---
layout: page
title: "システム"
description: ""
group: "reference/system"
---
{% include JB/setup %}

全てlibを通じて呼び出す。

#### CCamera* getCamera()
カメラを返す。

    camera : lib::getCamera();
    camera.setPos( 10, 200 );

#### CMapManager* getMapManager()
マップマネージャを返す。

    map_manager : lib::getMapManager();
    map_manager.set( "test" );

#### CActorLibrary* getActorLibrary()
アクターライブラリを返す。

    actor_lib = lib::getActorLibrary();

#### CActorManager* getActorManager()
アクターマネージャを返す。

    actor_manager = lib::getActorManager();

#### CActorManager* getActorManager()
アクターマネージャを返す。

    actor_manager = lib::getActorManager();

#### CBGM* getBGMManager()
BGMマネージャを返す。

    bgm_manager = lib::getBGMManager();

#### CSceneManager* getSceneManager()
シーンマネージャを返す。

    scene_manager = lib::getSceneManager();

#### CP2P* getNetworkManager()
ネットワークマネージャを返す。

    network_manager = lib::getNetworkManager();

#### CInput* getInputManager()
入力マネージャを返す。

    input_manager : lib::getInputManager();

#### CRandom* getRandomUtil()
ランダムユーティリティを返す。

    random_util : lib::getRandomUtil();

#### CStringRenderer* getStringRenderer()
文字レンダラを返す。

    string_renderer : lib::getStringRenderer();

#### CDebug* getDebugger()
デバッガを返す。

    debugger : lib::getDebugger();

#### exit()
システムを終了する。

    lib::exit();

#### xtal::ArrayPtr loadTexture( const char* filename, int div_x, int div_y, int div_w, int div_h )
テクスチャを読み込む。

dataフォルダ内のfilenameを読み込んで、縦横に分割してint型のハンドルの配列に格納して返す。

`div_x`は横の分割数、`div_y`は縦の分割数。`div_w`は分割する幅で、`div_h`は高さ。

    textures : lib::loadTexture( "tex/hogehoge.png", 4, 3, 32, 32 );


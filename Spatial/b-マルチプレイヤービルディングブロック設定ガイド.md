---
title: "マルチプレイヤービルディングブロック設定ガイド"
source: "https://developers.meta.com/horizon/documentation/unity/bb-multiplayer-blocks?locale=ja_JP"
author:
published:
created: 2025-06-30
description: "マルチプレイヤービルディングブロックの設定ガイド、トラブルシューティング、および簡単な使用方法"
tags:
  - "Quest3"
---
開発

更新日時:2025/06/05

**重要**: ビルディングブロックには、 [Meta XRコアSDK](https://developers.meta.com/horizon/downloads/package/meta-xr-core-sdk/) が必要です。 [UnityアセットストアからMeta XRオールインワンSDKをインポートする](https://developers.meta.com/horizon/documentation/unity/unity-tutorial-hello-vr/#step-4-import-meta-xr-all-in-one-sdk-from-the-unity-asset-store) の説明に従って、SDKをインポートしてください。

このガイドは、ビルディングブロックについて詳細な知識を持つ読み手を対象に、マルチプレイヤーMeta Quest機能を使ってビルディングブロックを設定するためのガイダンスを提供するものです。

## マルチプレイヤーブロックの概要

![Overview of provided Multiplayer Building Blocks in the Building Blocks window](https://scontent-itm1-1.xx.fbcdn.net/v/t39.2365-6/484090099_3471726516314510_9150937272777819434_n.png?_nc_cat=102&ccb=1-7&_nc_sid=e280be&_nc_ohc=yGs7s5WPLUkQ7kNvwE6scs0&_nc_oc=AdkvP7kTl_s9jUXbW4uu0nuzEQ5499KQHlQ5-nxEytWO4f2w21zrrQCJuOcWD5NNpok&_nc_zt=14&_nc_ht=scontent-itm1-1.xx&_nc_gid=F6pDKr5fIRvPKY3WQUY5DA&oh=00_AfOc4WpUZJglc93PDT8dNRWk65dpFF-HBDZLG8icSoE-OA&oe=687C7E65)

v65以降のコアSDKでは、\[マルチプレイヤー\]タグで以下のビルディングブロックが提供されています。

- **Auto Matchmaking (自動マッチメイク)**: このブロックは、同じルームにいる接続している全プレイヤーを自動的に参加させてマルチプレイヤーエクスペリエンスのプロトタイプを作成するのに役立ちます。
	- Photon Fusionの統合では、このブロックはPhoton Fusion2の共有モードを使っています。- Unity Netcodeの統合では、このブロックはUnityゲームサービスのリレーサービスを使っています。- **Custom Matchmaking (カスタムマッチメイク)** (v71): Photon FusionとUnity Netcodeの両方でルームコード(およびパスワードもオプション)ベースのマッチメイクを実装するのに役立つブロックです。自社のUIと統合して、製品版アプリで提供することができます。- **Friends Matchmaking (フレンドマッチメイク)** (v74): このブロックは [MetaプラットフォームSDK](https://developers.meta.com/horizon/documentation/unity/ps-group-presence-overview) のAPIと統合され、ユーザーはQuestの友達を同じネットワークルームに招待することができます。- **Local Matchmaking (ローカルマッチメイク)** (v74): このブロックは [Colocation Discovery API](https://developers.meta.com/horizon/documentation/unity/unity-colocation-discovery) を活用し、物理的に近くにいるすべてのプレイヤーを同じネットワークルームに自動的にマッチさせます。- **Colocation (コロケーション)**: このブロックは、共有空間アンカーAPI / Colocation Discovery (v74) API / Space Sharing (v77) APIで共有参照ポイントを構築してMRの「ローカルマルチプレイヤー」エクスペリエンスを実現するのに役立ちます。ワールドスペース/ステージスペースで生成されるどのネットワークゲームオブジェクトも、すべてのコロケーションプレイヤーから同じ位置に見えることになります。- **Networked Avatar (ネットワークアバター)**: このブロックは、自分のエクスペリエンスでMetaアバターと統合するのに役立ちます。これはMR/VRの両方で動作します。
	- **注**: アバターに使われるインプットマネージャは **Oculus VRプラグイン** ベースの実装で、現時点では **OpenXRプラグイン** をサポートして **いません** 。- **Networked Grabbable Object (ネットワークグラブ可能オブジェクト)**: このブロックは、オブジェクトネットワークを同期させ、すべてのプレイヤーが利用できるようにします。- **Player Name Tag (プレイヤー名前タグ)**: このブロックは、プレイヤーのQuest名をそれぞれの頭上に表示するサンプルUI導入して、マルチプレイヤーエクスペリエンスのプロトタイプを作成するのに役立ちます。- **Player Voice Chat (プレイヤーボイスチャット)**: このブロックは、Photon Fusionネットワーキングソリューション固有のものです。VOIPをPhoton Voice2パッケージと統合し、リモートで接続しているプレイヤー同士がボイスチャット経由で会話することを可能にします。- **Shared Spatial Anchor Core (共有空間アンカーコア)**: このブロックは、共有空間アンカーの作成、読み込み、消去、共有のためのコア機能を有します。

## プロジェクト設定の手順

### ネットワーキングフレームワークの選択

マルチプレイヤービルディングブロックは、Unity Netcode for Game ObjectsとPhoton Fusionという、人気のある2つのUnityネットワーキングフレームワークとの統合を提供します。

どちらのフレームワークにも、プロトタイプの作成段階では無料利用枠があります。本番段階では、さまざまな価格オプションがあります。各フレームワークのウェブサイトを確認して、どれが自分にとって最適か判断することができます。

- Unity Netcode for Game Objects (ゲームオブジェクト用Unity Netcode): [メインドキュメント](https://docs-multiplayer.unity3d.com/netcode/current/about/) 、 [価格オプション](https://unity.com/solutions/gaming-services/pricing) (リレー用)。- Photon Fusion: [メインドキュメント](https://doc.photonengine.com/fusion/current/fusion-intro) 、 [価格オプション](https://www.photonengine.com/fusion/pricing) 。

**注**: マルチプレイヤービルディングブロック統合の場合、どちらのフレームワークも同じようにサポートされています。ただし、プレイヤーボイスチャットブロックについては例外であり、これを利用できるのはPhoton Fusionだけです。

マルチプレイヤーブロックをインストールする際に使うフレームワークは、自分で決めることができます。また、このダイアログの選択は、マルチプレイヤービルディングブロックを使うシーンごとに一度行うだけで十分です。

![Dialog of choice whether Photon Fusion or Unity Netcode For Game Objects is chosen as integration backend for the block](https://scontent-itm1-1.xx.fbcdn.net/v/t39.2365-6/442426731_1491696468427527_6836706665152484493_n.png?_nc_cat=107&ccb=1-7&_nc_sid=e280be&_nc_ohc=imj4Fi16IEIQ7kNvwGRwgXY&_nc_oc=Adnkk0YEzqEmx3tjq93OuDs77yPH4ozoUtubSVNBfqADwv0wfAYgIi6jhc-5EqGlqGE&_nc_zt=14&_nc_ht=scontent-itm1-1.xx&_nc_gid=F6pDKr5fIRvPKY3WQUY5DA&oh=00_AfO52Ff2WlAbZ663Me_fN8fmwerxBJT1GhcHXrnHmE0Mhg&oe=687C72EA)

### パッケージのインストール

一般に、パッケージ管理を簡単にできるようにするため、パッケージのインストールにはUnityエディターのパッケージマネージャを使うことをおすすめします。

マルチプレイヤービルディングブロックに必要なUnityまたはMetaパッケージのほとんどについては、パッケージマネージャで直接追加できます。Unityエディターのメニューで **\[Window (ウィンドウ)\] > \[Package Manager (パッケージマネージャ)\]** の順に進んでパッケージマネージャを見つけ、 **+** ボタンから **\[Add package by name (パッケージを追加(名前を指定))\]** をクリックします。次に、パッケージID (「com.」で始まる)を名前に入力し、 **\[Add (追加)\]** をクリックしてパッケージをインストールします。

![Install packages by name via Unity's Package Manager](https://scontent-itm1-1.xx.fbcdn.net/v/t39.2365-6/442398151_1491696475094193_5980443324185552971_n.png?_nc_cat=102&ccb=1-7&_nc_sid=e280be&_nc_ohc=xrHp73NbV4QQ7kNvwEN6wvO&_nc_oc=Admpvxb1tYagW9-HSR_9c37rMuHswfaP4ZUaEgCNnT-gbTA0cFMbggBm9ts_jxRJcpA&_nc_zt=14&_nc_ht=scontent-itm1-1.xx&_nc_gid=F6pDKr5fIRvPKY3WQUY5DA&oh=00_AfOAV9_kH2WG58pXK-dZyOpi2b5ZrRtiC66sfc6vcwTU1Q&oe=687C9918)

**注**: このセクションの手順を実行するのは、Unity Netcodeフレームワークを使う場合だけです。

Unity Netcodeフレームワークには、以下の基本パッケージが必要です。

- ゲームオブジェクト用Unity Netcode: `com.unity.netcode.gameobjects`- Unityサービスリレー: `com.unity.services.relay`- Unityサービスロビー: `com.unity.services.lobby`

後者2つのパッケージが必要になるのは、 **自動マッチメイク** ブロック統合でUnityゲームサービスのリレーサーバーを使ってプレイヤーを接続する場合だけです。

**自動マッチメイク** ブロックを使っていない場合は、Unity Netcodeで常に自分のマッチメイクを使い、Unityゲームサービスをオプトアウトできます。他のマルチプレイヤーブロックには、 **\[Auto Matchmaking (自動マッチメイク)\]** をオプトアウトするためのオプションもあります。

![Option of installing Auto Matchmaking for other Multiplayer blocks or not](https://scontent-itm1-1.xx.fbcdn.net/v/t39.2365-6/442478993_1491696465094194_2564979880398542175_n.png?_nc_cat=105&ccb=1-7&_nc_sid=e280be&_nc_ohc=K-4RcTEAuNIQ7kNvwEgu2JW&_nc_oc=AdnADcRJXpVf4Xsc5FKXVZWwKB7m5szNdFl5dKdXENos3m2FXIV82gTeBHClJOPtmxY&_nc_zt=14&_nc_ht=scontent-itm1-1.xx&_nc_gid=F6pDKr5fIRvPKY3WQUY5DA&oh=00_AfMUQ9ym6sDiug6Wk1Cs8eAbYxqTCtrcQbPFFSzqywf4gA&oe=687C7D26)

#### Photonパッケージのインストール

**注**: このセクションの手順を実行するのは、Photon Fusionフレームワークを使う場合だけです。

Photonパッケージのインストールは少し複雑です。まず、Unityアセットストアにアクセスし、Photonパッケージの\[Add to My Assets (マイアセットに追加)\]を選択します。次にUnityエディターで、 **\[Package Manager (パッケージマネージャ)\]** > **\[Packages: My Assets (パッケージ: マイアセット)\]** の順に進んでインストールを実行します。

- Photon Fusion: [Unityアセットストア内のリンク](https://assetstore.unity.com/packages/tools/network/photon-fusion-267958)
	- Photon Fusion統合を使う全マルチプレイヤーブロックで必須- ブロックで提供される統合でFusion2を使っていること。- Photon Voice: [Unityアセットストア内のリンク](https://assetstore.unity.com/packages/tools/audio/photon-voice-2-130518)
	- **\[Player Voice Chat (プレイヤーボイスチャット)\]** ブロックの場合のみ必須- このPhoton Voiceパッケージの場合、ここで必要なのはPhoton Fusionとの統合だけなので、不要なファイルを除外するため、こちらの [公式ガイド](https://doc.photonengine.com/voice/current/getting-started/voice-for-fusion#import-photon-voice) に従ってください。

#### Meta SDKパッケージのインストール

自分のプロジェクトの中に含まれていないMeta SDKパッケージの中には、特定のブロックで必要とされるものがあるかもしれません。必要に応じて、 **\[Package Manager (パッケージマネージャ)\]** > **\[Add package by name (パッケージを追加(名前を指定))\]** の順に進んでインストールを実行します。

- Meta Interaction SDK: `com.meta.xr.sdk.interaction.ovr`
	- **Networked Grabbable Object (ネットワークグラブ可能オブジェクト)** ブロックで必須。このSDKは、Meta XRオールインワンSDKに含まれています- Meta Platform SDK: `com.meta.xr.sdk.platform`
	- **Colocation / Player Name Tag / Networked Avatar (コロケーション / プレイヤー名タグ / ネットワークアバター)** ブロックで必須。このSDKはMeta XRオールインワンSDKに含まれています- Meta Avatar SDK: `com.meta.xr.sdk.avatars`
	- Networked Avatar (ネットワークアバター)ブロックで必須- Meta Avatar SDK Sampleサンプルアセット: `com.meta.xr.sdk.avatars.sample.assets`
	- (任意)プレイヤーのフォールバックではプレイヤー独自のMetaアバターを設定していないため、Networked Avatar (ネットワークアバター)ブロックでサンプルアバターを表示するのに必要

### マッチメイクのためのプロジェクトの設定

どちらのネットワーキングフレームワーク(Photon FusionとUnity NGO)にも、それぞれマッチメイクサポート用のクラウドサービスがあります。マッチメイクブロックを通じてマルチプレイヤープロトタイプの作成 / テスト環境を手軽に設定するためのシンプルな手順を、以下にいくつか示します。

Unity Netcode for Game Objectsの自動マッチメイクを使うには、Unity Cloudプロジェクトのリンクが必要です。プロジェクトをUnityクラウドに接続していない場合、Unity Service Relayパッケージをインストールする際に、Unityのこのダイアログウィンドウが自動的に表示されて、\[Project Settings (プロジェクト設定)\]に移動できます。

![Popup of Unity project linking](https://scontent-itm1-1.xx.fbcdn.net/v/t39.2365-6/442417798_1491696478427526_7380173937588453426_n.png?_nc_cat=101&ccb=1-7&_nc_sid=e280be&_nc_ohc=wrinsa4cXiMQ7kNvwGL0IF8&_nc_oc=AdmrHh2CMk_hLH8etPQAxEBF9-Vt9WZ1rSlDunoVppD7KdurDPhJBakvXyrbs57v47s&_nc_zt=14&_nc_ht=scontent-itm1-1.xx&_nc_gid=F6pDKr5fIRvPKY3WQUY5DA&oh=00_AfORJGQyG893GO5_oNoizyOSKjob4yS3Edz7fnJ5r8bX0A&oe=687C7C29)

ダイアログウィンドウを閉じてしまった場合は、 **\[Edit (編集)\]** > **\[Project Settings (プロジェクト設定)\]** > **\[Services (サービス)\]** の順に進んでリンクを設定します。プロンプトに従って、プロジェクトのステータスに基づいて手順を完了します。

Photon Fusionパッケージをインストールすると、Fusion App IDを入力するためのポップアップが表示されます。Photonアカウントのログイン/登録の手順に従い、Photonダッシュボードでアプリを作成することができます。

![Photon Fusion2 Hub where Fusion App Id can be configured](https://scontent-itm1-1.xx.fbcdn.net/v/t39.2365-6/442440386_1491696495094191_1673453240689477295_n.png?_nc_cat=101&ccb=1-7&_nc_sid=e280be&_nc_ohc=wNTPDUrLoGEQ7kNvwFVGl45&_nc_oc=AdmdDjaaELWhFn_dWFKoMrYlI280u8mLOdGOe6NiuYoEtOj_N-pZgRsIbL4-lDJlU68&_nc_zt=14&_nc_ht=scontent-itm1-1.xx&_nc_gid=F6pDKr5fIRvPKY3WQUY5DA&oh=00_AfNbWmfWQJxhSFdBhj6qbt9UUJ957kDbc3T2puvBQHEkXQ&oe=687C8EFA)

このポップアップを閉じてしまった場合は、Unityの **メニュー > \[Tools (ツール)\] > \[Fusion\] > \[Fusion Hub (Fusionハブ)\]** を使ってもう一度表示させることができます。

**\[Hub (ハブ)\] > \[Fusion 2 Setup (Fusion 2設定)\] > \[Photon App Settings (Photonアプリ設定)\]** からアプリ設定のアセットにアクセスし、さらに多くのアプリIDを入力できます。プロジェクトタブから直接開く場合、通常これは、 **\[Assets (アセット)\] > \[Photon\] > \[Fusion\] > \[Resources (リソース)\]** にあります。

Player Voice Chat (プレイヤーボイスチャット)ブロックを使っている場合、同じような処理を実行してPhotonボイスアプリを作成し、Photonアプリ設定にアプリIDも入力する必要があります。

その他の設定は自分のニーズに応じて設定できます。

![Photon App Settings where Fusion App Id and other app ids can be configured](https://scontent-itm1-1.xx.fbcdn.net/v/t39.2365-6/442426918_1491696488427525_4843220074623369755_n.png?_nc_cat=110&ccb=1-7&_nc_sid=e280be&_nc_ohc=h9Q4b_NT0_4Q7kNvwEar5gC&_nc_oc=AdnIrU5HaqXF1798Nngz1zA06EtRWVBXBiNAvXUnBS9Hv8BEvyXkyE_ZwwAJV-qGHaY&_nc_zt=14&_nc_ht=scontent-itm1-1.xx&_nc_gid=F6pDKr5fIRvPKY3WQUY5DA&oh=00_AfOAKNqSL_1MF2yGGyFMOD_ugRIlUg1HsqbuE8TvcvuQyw&oe=687C81BE)

### Metaプラットフォームのためのプロジェクトの設定

Networked Avatar (ネットワークアバター)ブロックのMeta Avatar、Player Name Tag (プレイヤー名タグ)ブロックのMetaプレイヤー名、Colocation (コロケーション)ブロックの実行時使用をテストするには、プロジェクトでMeta Horizonプラットフォーム用のAppIdを設定する必要があります。エディター内でガイダンスを入手するには、Unityの **メニュー > \[Meta\] > \[Tools (ツール)\] > \[Meta Account Setup Guide (Metaアカウント設定ガイド)\]** にあるMetaアカウント設定ガイドツールを利用します。

![Meta Account Setup Guide helps developer step-by-step setup platform account and app ids](https://scontent-itm1-1.xx.fbcdn.net/v/t39.2365-6/442410320_1491696485094192_8085449563246010855_n.png?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=qdxjf72li6MQ7kNvwEbeGmP&_nc_oc=AdlZ5jUpSAhbAibLTZnq5q4dEpH1lgijYXDhVyAZHF0P6nlK_noCRJOrRMFtN4aATSw&_nc_zt=14&_nc_ht=scontent-itm1-1.xx&_nc_gid=F6pDKr5fIRvPKY3WQUY5DA&oh=00_AfMRf9BY7RmVTLN9vCdQusOR80FoNo7PUs9VQObc3om2bw&oe=687C8740)

データ使用状況の確認について: プロジェクトでMetaアバターを使っている場合は、UserIDとUserProfileに加えて、アバターのアクセス許可をリクエストする必要があります。

### \[Colocation (コロケーション)\]ブロックのためのプロジェクトの設定

ローカルマルチプレイヤーゲームのために\[Colocation (コロケーション)\]ブロックを使う場合、実行時にプロジェクトがうまく実行されるようにするために、追加の設定が必要です。

#### コロケーションセッションで設定する

コロケーションセッションは、Bluetooth/WiFi経由でローカルユーザーをマッチさせる [Colocation Discovery API](https://developers.meta.com/horizon/documentation/unity/unity-colocation-discovery) に基づいており、推奨されるアプローチとしてコロケーション設定プロセスをかなりシンプルにします。

「コロケーションセッションを使用」オプションを有効にしてコロケーションブロックを使う場合、アプリをテストするために必要なのは、認証済みの開発者組織の開発者アカウントだけです。 [組織確認を行うには、このドキュメント](https://developers.meta.com/horizon/resources/publish-organization-verification) に従ってください。この場合にはアプリIDは不要です。

#### コロケーションセッションなしで設定する

- テストユーザーを作成してヘッドセットでテストすると、レビュー未実施の場合にデータの使用状況の確認を行う上で役に立ちます- それらのユーザーを含めるようにアプリリリースチャネルを設定する必要があります。テスト用共有空間アンカーのブロックを解除するため、ビルドapkをチャネルに少なくとも1回アップロードする必要があります。最初のapkがアップロードされれば、Unityからビルドして実行する作業を反復して行うことができます。これが正しくなされたことを示す重要なものは、ヘッドセットの中で\[Unknown Sources (発行元不明)\]からではなく、\[App Library (アプリライブラリ)\]にアプリが表示されることです。それでも動作しない場合は、ヘッドセットを再起動することで、アプリのアクセス許可ステータスが更新されるかもしれません。- テスト時には、ヘッドセットに対して\[Enhanced Spatial Services (高度な空間サービス)\]の設定をオンにする必要があります。

#### 適切なコロケーションオプションを選択する

v77以降、コロケーションブロック内で複数のコロケーションソリューションを提供しています。以下に、ユースケースに適したオプションを選ぶためのガイドをご紹介します。エンドツーエンドのコロケーションソリューションでは、マッチメイクの実行方法と位置合わせの方法という2つの軸を検討する必要があります。

**マッチメイクの実行方法** (\[Use Colocation Session (コロケーションセッションを使用)\]オプション):

- \[Use Colocation Session (コロケーションセッションを使用)\]が無効の場合 - ネットワーキングフレームワークに基づくマッチメイク: ネットワーキングフレームワーク(Photon Fusion、NGO)に基づくマッチメイクを使用します。この場合、共有アンカーはネットワーキングフレームワークと同期されるため、アプリ設定は以下よりも少し複雑になります。\[Install Matchmaking (マッチメイクをインストール)\]オプションで、さらにどのマッチメイクオプションをインストールするかを選択できます。- \[Use Colocation Session (コロケーションセッションを使用)\]が有効の場合 - コロケーションセッションに基づくマッチメイク: BluetoothとWi-Fiを使って近くのプレイヤーを見つけ自動的にグループを作成する、 [コロケーションセッション / Colocation Discovery API](https://developers.meta.com/horizon/documentation/unity/unity-colocation-discovery) に基づいています。アンカーやその他の情報はBluetoothやWi-Fiのローカルネットワークを使って共有でき、設定は簡略化されています(上記の設定セクションを参照)。
- \[Share Space To Guests (ゲストとスペースを共有)\]が無効の場合 - 単一の共有空間アンカー経由: プレイヤーはホストが生成した単一のSSAに対して位置合わせされます。これはシンプルなユースケースに適しています。- \[Share Space To Guests (ゲストとスペースを共有)\]が有効の場合 - スペース共有経由: [スペース共有API](https://developers.meta.com/horizon/documentation/unity/unity-mr-utility-kit-space-sharing) に基づき、すべてのゲストプレイヤーがホストのルーム設定を使うことで、すべてのルームアンカーが位置合わせされます。ゲストも環境とのインタラクションを行いたい場合には、このオプションの方が適しています。例えば、壁に色を飛散させるなど、ゲストが環境に影響を与える場合、このオプションを使うことで、すべてのプレイヤーが同じ色の効果を、同じように実際の壁に正しく位置合わせされた状態で見ることができます。
![Variant options from the Colocation block](https://scontent-itm1-1.xx.fbcdn.net/v/t39.2365-6/504122055_3567070793446748_1984597757169439915_n.png?_nc_cat=110&ccb=1-7&_nc_sid=e280be&_nc_ohc=r1O_kfUggnUQ7kNvwFAkKNE&_nc_oc=Admk1yx6UgKphHD6NGr7h3jfcqH50nN7rZvf_OoNr9ae8t7F5Ze_zxF6fTV6TP0nNNo&_nc_zt=14&_nc_ht=scontent-itm1-1.xx&_nc_gid=F6pDKr5fIRvPKY3WQUY5DA&oh=00_AfPPVWWSxtjJ-MCdslGue125K_pvm-8lK-qZ4gN475mTyA&oe=687C6D68)

すべての設定が完了したら、いよいよお楽しみの時間です。

### 共存シナリオ: マルチプレイヤーVR/MRゲーム、リモート参加プレイヤー

**Networked Avatars (ネットワークアバター)、Player Name Tag (プレイヤー名タグ)、Player Voice Chat (プレイヤーボイスチャット)、Networked Grabbable Object (ネットワークグラブ可能オブジェクト)** を、自分のVR/MR環境と併せてドラッグアンドドロップすることができます。そうすれば、別の場所にいるプレイヤーも、同じセッションに参加して、連携エクスペリエンスを楽しむことができます。その組み合わせの例と、ヘッドセットでマルチプレイヤー共存プレゼンスエクスペリエンスをすぐ使える状態にする方法を以下に示します。

![Editor flow of adding several blocks for composing a copresence scene](https://scontent-itm1-1.xx.fbcdn.net/v/t39.2365-6/442453872_1491696461760861_7545001066243305112_n.gif?_nc_cat=100&ccb=1-7&_nc_sid=e280be&_nc_ohc=9OpmXnmw-oAQ7kNvwERG_BO&_nc_oc=AdnKd1cc9nFzZtuOaIr9FxcEQP3lcDhC6_Qbs6hjNotZa6UE3zAdYdVeXnTr3vgq_bk&_nc_zt=14&_nc_ht=scontent-itm1-1.xx&_nc_gid=F6pDKr5fIRvPKY3WQUY5DA&oh=00_AfPjblC8VVB54VHSD47-_wkc7z68DVagmmPGUPZ9vneWHQ&oe=687C9E62) ![In-headset view of the host/client of this copresence scene](https://scontent-itm1-1.xx.fbcdn.net/v/t39.2365-6/442409943_1491696498427524_4741374808525501589_n.gif?_nc_cat=110&ccb=1-7&_nc_sid=e280be&_nc_ohc=ImIYVmsT8D0Q7kNvwE8OHgI&_nc_oc=AdlcdQui4OuF9jMbr2Cjmj4S2B6edrXs-nBB9eQyn5MqsVFamzT7J_kB0JP3ttwqrhk&_nc_zt=14&_nc_ht=scontent-itm1-1.xx&_nc_gid=F6pDKr5fIRvPKY3WQUY5DA&oh=00_AfMwKQhjxaU-NqPq79H09dH-_6YubP1tS-PNOx6vtIcxcg&oe=687CA4BC)

### コロケーションシナリオ: マルチプレイヤーMRゲーム、同じスペースでローカルに参加するプレイヤー

同じように、Networked Avatar (ネットワークアバター)を使う代わりに、 **\[Colocation (コロケーション)\]** ブロックをほかのブロックと組み合わせてシーンに含めることもできます。同じ物理位置(同じルーム)にいる複数のプレイヤーが、連携エクスペリエンスに参加することも可能です。以下に示されているコロケーションの現実世界エクスペリエンスをチェックしてください。

#### 1\. コロケーションMRチェスエクスペリエンス

この例では、ブロックとして、 **Colocation (コロケーション)** 、 **Touch Hand Grab (タッチハンドグラブ)** (ISDKによる、チェスの駒を触ってつかむためのもの)、 **Networked Grabbable Object (ネットワークグラブ可能オブジェクト)** 、 **Anchor Prefab Spawner (アンカーprefabスポーナー)** (MRUKによる、チェスをテーブル上に配置するためのもの)を、準備されているチェス盤アセットに対して適用します。 **Networked Grabbable Object (ネットワークグラブ可能オブジェクト)** など、シングルトンではないインタラクションブロックのほとんどは、既存の3Dオブジェクトに直接ドラッグアンドドロップして、シーン内で選択された複数オブジェクトと一緒に一括実行することができます。この例では、チェスのすべての駒に **Touch Hand Grab (タッチハンドグラブ)** と **Networked Grabbable Object (ネットワークグラブ可能オブジェクト)** (重力を使う)の両方を適用することにより、それらをネットワーク経由でインタラクション可能かつ同期されるようにします。

2人のプレイヤーが一緒にセッションに参加すると、以下のようになります。

![In-headset view of two players join the colocated chess game and play together](https://scontent-itm1-1.xx.fbcdn.net/v/t39.2365-6/442414563_1491696455094195_1578664982725497417_n.gif?_nc_cat=111&ccb=1-7&_nc_sid=e280be&_nc_ohc=OyIgZwDtXGIQ7kNvwHZWy9r&_nc_oc=AdlrATJGsEe_qtnf0TWMgUcZ8D2nS5tna_Wekywg8h5G3n5Fwe38EC4NaIwJrAyzIQA&_nc_zt=14&_nc_ht=scontent-itm1-1.xx&_nc_gid=F6pDKr5fIRvPKY3WQUY5DA&oh=00_AfOrTyAattoI84Z93iBxLXAoj0EX0V-vhFMaBvf-ar-NfQ&oe=687C7015)

#### 2\. コロケーションセーバー対決エクスペリエンス

上記と同じように、ライトセーバーアセットが準備されている状態で、2人のプレイヤーがセーバー対決エクスペリエンスをプレイできます。ここでは、ブロックとして **Colocation (コロケーション)** 、 **Networked Grabbable Object (ネットワークグラブ可能オブジェクト)** 、 **Anchor Prefab Spawner (アンカーprefabスポーナー)** (MRUKによる、開始時にセーバーをテーブルに配置するためのもの)、 **Distance Grab (遠隔グラブ)** (ISDKによる、遠隔操作でセーバーをつかむためのもの)だけを使います。このブロックでは、以下を実現できます。

![In-headset view of two players join the colocated saber duel game and play together](https://scontent-itm1-1.xx.fbcdn.net/v/t39.2365-6/442435702_1491696481760859_1925847081497441779_n.gif?_nc_cat=104&ccb=1-7&_nc_sid=e280be&_nc_ohc=FSeaEbGeF0cQ7kNvwHPvLZq&_nc_oc=Adm4BPXE9rPk37ERdqpB0bIEZeCWuWAmA8UNnP8Z7eOY_Za4wyNIzz44YVTHX_aHb74&_nc_zt=14&_nc_ht=scontent-itm1-1.xx&_nc_gid=F6pDKr5fIRvPKY3WQUY5DA&oh=00_AfM4U-Fef6zC8XvAA0RHSRUMvkxzPKuN25JsmJWXcRSODg&oe=687C7DC8)

## マルチプレイヤーのテスト

以下に、マルチプレイヤーアプリをテストする上で役立つヒントやリンクを示します。

- [ParrelSync経由でUnityエディターの複数インスタンス](https://developers.meta.com/horizon/documentation/unity/unity-multiplayer-testing/#install-and-configure-parrelsync) を使う。これにより、プロジェクトのシンボリックリンクによりプロジェクトのクローンを作成するようにして、反復作業が1回だけで済むようにします。- [Meta XRシミュレーターの複数インスタンス](https://developers.meta.com/horizon/documentation/unity/xrsim-multiplayer/) を使う。これにより、MR機能対応のインプットインタラクションをテストします。- [プラットフォームSDKでのスタンドアロンプラットフォーム設定](https://developers.meta.com/horizon/documentation/unity/unity-multiplayer-testing/#test-multiple-users) を使う。これにより、複数の異なるエディター内テストユーザーを設定します(アバター、プレイヤー名、コロケーション機能のテスト用)

## トラブルシューティング

**Networked Avatar (ネットワークアバター)ブロックを使用する推奨バージョンは、以下のすべての問題が解決されるコアSDK v76以降およびAvatar SDK v35.2以降です。**

コアSDKとAvatars SDKの旧バージョンの組み合わせのままにしたい場合、以下の既知の問題があります。

- コアSDKの全てのバージョンは、24.1以前のAvatars SDKに対応しています。- Avatars SDKのバージョンが24.1より新しい場合、v74以前のCore SDKを使用すると、Networked Avatar (ネットワークアバター)ブロックの実行時に入力の問題が発生する可能性があります。
	- Networked Avatar (ネットワークアバター)ブロックがシーンにインストールされたら、 **\[Building Block (ビルディングブロック)\] Networked Avatar** GameObjectを探します。このオブジェクトは、 **EntityInputManager** というコンポーネントを含む **AvatarSDK** GameObjectを子として持っています。 **EntityInputManager** をサンプルアセットパッケージの **SampleInputManager** コンポーネントで置き換え、ボディトラッキングモードをNoneに設定します。これは修正され、v76のコアSDKでは不要になりました。- Networked Avatar (ネットワークアバター)ブロックで使用されるAvatars SDKの **SampleInputManager** コンポーネントは、v35.2まで **Unity OpenXRプラグイン** をサポートして **いません** 。Unity OpenXRプラグインを使用する場合は、Avatars SDK v35.2以降を使用する必要があります。

**この問題は、v76のコアSDKで修正されました。** コアSDKの旧バージョンのままにしたい場合、以下の既知の問題があります。

- v71以降、Custom Matchmakingブロックがリリースされましたが、そのPhoton Fusionの実装では、Networked Grabbable Objectブロック(または現在のシーンに存在する基本的なネットワークオブジェクト)を操作する際に、オブジェクトが全く同期されないという既知の問題があります。これは、ネットワークセッションの開始時に、現在のシーンがパラメータに埋め込まれていないことによるものです。- v74では「コロケーションセッションを使用」オプションが有効になったColocationブロックも、同じ問題を抱えるCustom Matchmakingブロックに依存します。- 今後のCore SDKバージョンでこの問題が修正されるまでの間、一時的にこの問題を回避するために、「\[Building Blocks (ビルディングブロック)\] Custom Matchmaking (カスタムマッチメイク)」ゲームオブジェクトの `CustomMatchmakingFusion` スクリプトに適用できるコード変更がありますので、以下にご紹介します。

```
// CustomMatchmakingFusion.cs
        // Step1. define these functions somewhere in the class
        private static NetworkSceneInfo GetSceneInfo()
        {
            SceneRef sceneRef = default;
            if (TryGetActiveSceneRef(out var activeSceneRef))
            {
                sceneRef = activeSceneRef;
            }
            var sceneInfo = new NetworkSceneInfo();
            if (sceneRef.IsValid) {
                sceneInfo.AddSceneRef(sceneRef, LoadSceneMode.Additive);
            }
            return sceneInfo;
        }

        private static bool TryGetActiveSceneRef(out SceneRef sceneRef)
        {
            var activeScene = SceneManager.GetActiveScene();
            if (activeScene.buildIndex < 0 || activeScene.buildIndex >= SceneManager.sceneCountInBuildSettings) {
                sceneRef = default;
                return false;
            }
            sceneRef = SceneRef.FromIndex(activeScene.buildIndex);
            return true;
        }

        // Step2. within several public functions like \`CreateRoom\` \`JoinRoom\` \`JoinOpenRoom\` with \`StartGame\` call
        var result = await runner.StartGame(new StartGameArgs
        {
            GameMode = gameMode,
            Scene = GetSceneInfo(), // <- Add this line as apart of the StartGameArgs
            CustomLobbyName = options.LobbyName,
            SessionName = sessionName,
            PlayerCount = options.MaxPlayersPerRoom,
            IsVisible = !options.IsPrivate
        });
```

A: 残念ながら、Photonパッケージは今のところUPMパッケージではないため、その存在については、Photonパッケージの中で使われているカスタムスクリプト/定義シンボルによって推測するしかありません。しかし、それらのシンボルは、パッケージ削除時に自動的には削除されません。コンパイルエラーは通常、Photonパッケージがプロジェクトから削除されることに起因します。このエラーが発生した場合は、 **\[Project Settings (プロジェクト設定)\] > \[Player (プレイヤー)\] > \[Script Compilation (スクリプトコンパイル)\] > \[Script Define Symbols (スクリプト定義シンボル)\]** から、すべてのプラットフォームのスクリプト定義シンボルをチェックし、削除してください。

- `FUSION_WEAVER`- `PHOTON_VOICE_DEFINED`- `PHOTON_FUSION_PHYSICS_ADDON_DEFINED`

### Q: 私のヘッドセットではコロケーションブロックが機能しません

A: テストに使ったヘッドセットがv65以上にアップデートされていることを確認してください。

A: 原因として考えられるのは、コロケーションが失敗したことです。警告やエラーがないかどうかログを調べてください。また、デフォルトで生成されるリファレンスアンカーの物理位置が全プレイヤーについて同じになっているかどうか調べてください(これはコロケーションが動作しているかどうかを最も明白に示すものです)。

A: これは、ビルドがアプリのリリースチャネルにアップロードされていないためです。上記の設定ガイダンスに従っていることを確認してください。

A: 変更を適用するためにヘッドセットの再起動が必要な場合があります。

#### \- その他の問題が発生します

A: 共有空間アンカーに関する [事前要件](https://developers.meta.com/horizon/documentation/unity/unity-shared-spatial-anchors/#prerequisites) を慎重に確認してください。その後で、実行時に発生する問題を解決するのに役立つ [トラブルシューティングドキュメント](https://developers.meta.com/horizon/documentation/unity/unity-ssa-ts/) も併せてご確認ください。さらに、こちらの [ヒントとテクニックに関するドキュメント](https://developers.meta.com/horizon/documentation/unity/unity-colocation-tips-tricks-faq) は、コロケーションの開発やテストを行う際の参考として役立ちます。

A: これは、最新の [マルチユーザーとアプリ共有](https://www.meta.com/blog/quest/gather-your-party-introducing-multi-user-and-app-sharing-on-oculus-quest/) のメカニズムに関連しています。複数のデバイスでアプリのテストを行うには、異なる複数のアカウント(テストユーザーなど)を使うことをおすすめします。ユーザーは、1つのヘッドセット上で複数の異なるアカウントを使い、 [アプリ共有](https://www.meta.com/help/quest/articles/accounts/multiple-accounts-and-app-sharing/turn-on-app-sharing/) によりほかのユーザーとアプリを共有することがあります。

このページは役に立ちましたか？
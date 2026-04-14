---
title: "UE5 PCGのスプライン機能を用いて、プロシージャルに道を生成する"
source: "https://tech.dentsusoken.com/entry/ue_pcg_spline"
author:
  - "[[dentsusoken]]"
published: 2024-06-06
created: 2025-06-30
description: "こんにちは、電通総研金融ソリューション事業部の岡崎です。 今回はUE5.2の機能であるプロシージャルコンテンツ生成フレームワーク（PCG：Procedural Content Generation Framework）に関して、 前回の記事に引き続き、より詳しい機能の紹介を行っていきます。 今回はPCGのスプラインという機能を使用して、PCGで草を配置し、さらに道を生成する方法を紹介します。 検証環境/ツール OS：Windows 11 pro GPU：NVIDIA GeForce RTX 4070 Ti Game Engine：Unreal Engine 5.2.1 実装手順 PCGを使用し…"
tags:
  - "UE"
---
![](https://media.shodousercontents.com/task_images/983/1006f5e4-b2e2-4b35-b209-b302698c324d.png)

こんにちは、 [電通](https://d.hatena.ne.jp/keyword/%C5%C5%C4%CC) 総研金融ソリューション事業部の岡崎です。

今回はUE5.2の機能であるプロシージャルコンテンツ生成 [フレームワーク](https://d.hatena.ne.jp/keyword/%A5%D5%A5%EC%A1%BC%A5%E0%A5%EF%A1%BC%A5%AF) （PCG：Procedural Content Generation Framework）に関して、  
[前回の記事](https://tech.dentsusoken.com/entry/ue_pcg) に引き続き、より詳しい機能の紹介を行っていきます。

今回はPCGのスプラインという機能を使用して、PCGで草を配置し、さらに道を生成する方法を紹介します。

## 検証環境/ツール

- OS： [Windows](https://d.hatena.ne.jp/keyword/Windows) 11 pro
- [GPU](https://d.hatena.ne.jp/keyword/GPU) ： [NVIDIA](https://d.hatena.ne.jp/keyword/NVIDIA) [GeForce RTX](https://d.hatena.ne.jp/keyword/GeForce%20RTX) 4070 Ti
- Game Engine： [Unreal Engine](https://d.hatena.ne.jp/keyword/Unreal%20Engine) 5.2.1

## 実装手順

1. PCGを使用して草を配置
2. スプラインを作成し、レベル上に配置
3. PCGグラフを変更してスプライン上の草を排除
4. スプラインで任意の範囲を指定して草を配置

## 1\. PCGを使用して森を生成

[前回の記事](https://tech.dentsusoken.com/entry/ue_pcg) と同様、まずはPCGを使用して森を生成します。  
今回は簡潔な手順のみ説明します。詳細な説明は前回の記事を参考にしてください。

「PCGVolume」を作成し、レベル上のViewPort上に配置します。

![](https://media.shodousercontents.com/task_images/983/7c0526c9-3b21-4518-830a-ad9f4badb47e.png)

次に「PCG グラフ」を作成します。  
今回、PDGグラフ名は「Tech1PCGGraph」と [命名](https://d.hatena.ne.jp/keyword/%CC%BF%CC%BE) しました。

![](https://media.shodousercontents.com/task_images/983/e06aff71-6d44-46c5-8689-bcb0f3484c61.png)

[アウトライナー](https://d.hatena.ne.jp/keyword/%A5%A2%A5%A6%A5%C8%A5%E9%A5%A4%A5%CA%A1%BC) 上で先ほど範囲を決めるために作成した「PCGVolume」を選択し、子要素の「PCGComponent」を選択します。

![](https://media.shodousercontents.com/task_images/983/e8c47ee8-b1d8-44a4-a277-7baa55381fc1.png)

[インスタンス](https://d.hatena.ne.jp/keyword/%A5%A4%A5%F3%A5%B9%A5%BF%A5%F3%A5%B9) 直下に Graph を選択する欄があるので、先ほど作成した「PCG グラフ」を選択します。

![](https://media.shodousercontents.com/task_images/983/4ed0ec4a-9b44-4ee6-bd52-6be9dbfbf242.png)

次に森を作成するためのノードを作成します。

PCGグラフを開き、「Input」の「Landscape」から「SurfaceSampler」ノードを作成して繋ぎます。  
さらに「TransformPoints」を接続し、地上に生やしていく草の大きさや向きなどを指定します。

PCGグラフを編集した際に、リアルタイムにViewportに変更が入るので、  
同時に変更点を見る事ができるよう、下記キャプチャのようにエディターを配置をして編集をする方法もおすすめです。

![](https://media.shodousercontents.com/task_images/983/67a65f1c-df81-4ae1-9edc-77388481f104.png)

次に「StaticMeshSpawner」ノードを作成し、草のStatic Meshを配置します。  
「Descriptor ＞ Static Mesh」の順に開き、配置したい草のアセットを選択します。

![](https://media.shodousercontents.com/task_images/983/68286085-1fbe-4e5e-8ffc-8c476a636500.png)

ここまででPCGを使って任意のアセットをランダムに配置する事ができました。

![](https://media.shodousercontents.com/task_images/983/025911cf-872a-4815-b8bd-61d4ade5fd31.png)

より詳しいPCGの作成方法は、 [前回の記事](https://tech.dentsusoken.com/entry/ue_pcg) に記載しています。

次は、現在作成した草原に道を作成して、道の上には草を生やさないルールを作成します。

## 2\. スプラインを作成し、レベル上に配置

ここでは道を作成するためにスプラインを使用します。  
UEのスプラインとは、ポイントとポイントをラインで繋いだ形状のアクターのことを指します。

まずはブループリントアクターを作成し、「BP\_PathSpline」と [命名](https://d.hatena.ne.jp/keyword/%CC%BF%CC%BE) します。

![](https://media.shodousercontents.com/task_images/983/cf6dc417-b1ba-406a-a121-6d195da7af1c.png)

「BP\_PathSpline」を開き、左上のAddボタンから「Spline」を追加します。

![](https://media.shodousercontents.com/task_images/983/a3ea27c8-e604-49b9-a154-f69828360554.png)

レベル上でスプラインを見やすくするために「ScaleVisualizationWidth」を300に設定します。

![](https://media.shodousercontents.com/task_images/983/e2e02899-3729-47e4-a67c-05c7fa6525f2.png)

スプラインも少し伸ばします。

![](https://media.shodousercontents.com/task_images/983/4e50a023-a6f7-4056-adbc-442e2ab7bf38.png)

次に画面上部の「クラスのデフォルト」を押下し、詳細パネルから「タグ」を検索し、プラスボタンからインデックスを「Path」と [命名](https://d.hatena.ne.jp/keyword/%CC%BF%CC%BE) します。

![](https://media.shodousercontents.com/task_images/983/8af89877-1490-4cc6-9c25-d489c04949ec.png)

[コンパイル](https://d.hatena.ne.jp/keyword/%A5%B3%A5%F3%A5%D1%A5%A4%A5%EB) とセーブをして、「BP\_Path」をViewPortに配置します。

![](https://media.shodousercontents.com/task_images/983/37a78127-9804-4dbd-93ac-d2c562d53710.png)

作りたい道の向きに合わせて「Alt」キーを押しながら頂点をドラッグしてPathを伸ばします。  
（スプラインが見えづらかったので、草を一度非表示に変更しています）

![](https://media.shodousercontents.com/task_images/983/69a8676c-000a-455b-b77d-a9fb7a43619e.png)

PCGで配置した草の上に道にしたいスプラインを配置できたら、PCGグラフに戻ります。

## 3\. PCGグラフを変更してスプライン上の草を排除

先ほどのPCGグラフ「Tech1PCGGraph」を開いて、PCGグラフを編集します。  
「GetSplineData」ノードを作成し、詳細パネルの「ActorSelectionTag」を先ほど設定した「Path」にします。  
また、スプラインを複数配置した時にも使用したいので「SelectMultiple」にもチェックを入れておきます。

![](https://media.shodousercontents.com/task_images/983/d48c82d9-bf07-46f4-8b13-5fae5ed7cca5.png)

次に「SplineSampler」ノードを作成し、「Dimension」のセレクトボックスから「OnSpline」を選択します。

![](https://media.shodousercontents.com/task_images/983/d805395b-b8bc-4c7d-bf1c-bbff53c1df37.png)

次に「BoundsModifier」ノードを作成し、「SplineSampler」のアウトプットに繋ぎます。

![](https://media.shodousercontents.com/task_images/983/52015977-7413-4b5d-b9c0-02078a0c5e99.png)

詳細パネルから「BoundsMin / Max」のY/Zを300にして [デバッグ](https://d.hatena.ne.jp/keyword/%A5%C7%A5%D0%A5%C3%A5%B0) モード（ノード上で「D」キー押下）にするとキャプチャのように、スプラインの範囲が白い棒状に表示されます。

![](https://media.shodousercontents.com/task_images/983/04420369-cb35-4415-80a8-08a6c7885f9a.png)

次に、この棒状のスプラインと重なっている草を排除するために「Difference」ノードを作成します。

草を生やしている「 [Surface](https://d.hatena.ne.jp/keyword/Surface) Sampler」ノードのアウトプットから「Difference」の「Source」に繋ぎ、  
「BoundsModifier」のアウトプットを「Difference」の「Differences」に接続します。

![](https://media.shodousercontents.com/task_images/983/17047dca-a13f-4831-b9f2-91f488645ef8.png)

キャプチャのようにノードをつなげる事で、  
スプライン上の道に草のメッシュが排除された形で、ランダム生成された形状を作成する事ができます。

![](https://media.shodousercontents.com/task_images/983/f0b9be51-c797-4c9a-934c-a81c4b2c3c33.png)

## 4\. スプラインで任意の範囲を指定して草を配置

ここでは、スプラインを使用した応用として、スプラインで任意の範囲を指定して草を配置する方法を紹介します。

この記事では、草の生成を「 [Surface](https://d.hatena.ne.jp/keyword/Surface) Sampler」を使用して行いましたが、  
スプラインを使用して、任意の形の内部にのみ、草を生やすことなどができます。

まずは草を生やす形を決めるために新しいブループリントアクターを「BP\_LandSpline」で作成します。

![](https://media.shodousercontents.com/task_images/983/8c416b88-b3af-4bd1-93b0-99f6749429f4.png)

「BP\_PathSpline」の時と同様に、スプラインを作成し、キャプチャのように中心点以外の頂点を削除します。

![](https://media.shodousercontents.com/task_images/983/48f52f7c-60f7-4191-a5e2-0a83ccabb55d.png)

![](https://media.shodousercontents.com/task_images/983/7a61dfe4-c05c-4c78-81b0-1f4b9b079996.png)

残った頂点を選択し、右クリックで「スプライン生成パネル」を選択し、サークルを作成します。

![](https://media.shodousercontents.com/task_images/983/a60945f9-c649-457b-afe4-1ab005ae5112.png)

![](https://media.shodousercontents.com/task_images/983/a434b729-fb11-444c-98e1-1788bd79e415.png)

頂点の数は6にして、半径を2000ほどにしておきます。

![](https://media.shodousercontents.com/task_images/983/72b49ec5-ed42-4763-ae6d-590f8740795b.png)

選択されている頂点をキャプチャのように上に移動して削除して、途切れた円形にします。

![](https://media.shodousercontents.com/task_images/983/edf9d907-02d4-4429-8797-1b6dd73b48e3.png)

![](https://media.shodousercontents.com/task_images/983/2feda039-37e6-4b16-a32f-9398d18d8a80.png)

その後、詳細パネルの「ClosedLoop」にチェックを入れて閉じた丸いスプラインに変更します。

![](https://media.shodousercontents.com/task_images/983/51422e28-eb78-466f-8cc9-ba87a7249455.png)

![](https://media.shodousercontents.com/task_images/983/b7ba000a-96ae-4900-bd49-8a11d9396918.png)

完成したら「BP\_PathSpline」と同様にタグに「Land」と [命名](https://d.hatena.ne.jp/keyword/%CC%BF%CC%BE) して作成します。

![](https://media.shodousercontents.com/task_images/983/895d27e9-acde-400d-bb9e-1306a04848b5.png)

作成した円状のスプラインをViewPortに配置します。

![](https://media.shodousercontents.com/task_images/983/e3093a04-7cad-49fc-9ea4-8ad8f3517764.png)

これから配置したスプラインの内部のみ草を生やします。  
PCGグラフに戻ります。

「GetSplineData」と、「SplineSampler」を作成し、ノードをつなぎます。

![](https://media.shodousercontents.com/task_images/983/754bcae8-aca1-4f56-8537-f61861f1e88c.png)

「GetSplineData」はPathの時と同様に、Tagに「Land」を設定します。

![](https://media.shodousercontents.com/task_images/983/5b75a333-b77d-441b-a5e6-1ecf5759e987.png)

「SplineSampler」の「Dimension」のセレクトボックスから「OnInterior」を選択します。

![](https://media.shodousercontents.com/task_images/983/cd7a9d5a-171c-4216-9bf8-32a25aa2d1ed.png)

これで円の内側にPCGキューブが配置されました。

![](https://media.shodousercontents.com/task_images/983/338c60ea-0a8b-446d-8ace-fe23767aca4e.png)

「InteriorSampleSpacing」の値を200に、「InteriorBorderSampleSpacing」の値を50程度に調整してPCGキューブの表示間隔を調整します。  
また、キャプチャのように大きく隙間が空いている時は、「TreatSplineAsPolyline」にチェックを入れることで均等に配置されます。

![](https://media.shodousercontents.com/task_images/983/75236643-8c79-44c9-8ac4-74e45a0194aa.png)

続いて、PCGキューブの向きや配置をランダムにするために「TransformPoints」を追加します。  
「Projection」のアウトプットから「TransformPoints」に接続して、「RotationMax」のZ値を360に変更し  
「Offset Min/Max」のX/Yの値を-200と200に変更し、キューブの重なりなどを排除するために「SelfPruning」ノードを追加します。

![](https://media.shodousercontents.com/task_images/983/9317cd4a-dd11-407c-a47b-4477821feb02.png)

当初使用していた「SurfaceSampler」を使用してメッシュを配置していた方法と、今回の「SplineSampler」を使用したメッシュを入れ替える事で、  
Landのスプライン上に生成した草から、Pathのスプラインで生成した道上の草を排除する事もできます。

![](https://media.shodousercontents.com/task_images/983/07ba9395-3055-4d79-a4f0-562dedf192c1.png)

さらに、LandのスプラインやPathのスプラインはコピー生成する事もできるので、下記キャプチャのように草や道を自由に配置する事ができるようになります。

![](https://media.shodousercontents.com/task_images/983/10c44618-11fb-4125-ba15-9f422265caac.png)  
（円形のLandのスプラインを2つに複製したパターン）

![](https://media.shodousercontents.com/task_images/983/f5eed233-ae0d-4d53-bd17-fac7df91a859.png)  
（円形のLandのスプラインを変形して複製し、Pathのスプラインも複製して配置したパターン）

今回の機能の紹介はこれで以上になります。

## おわりに

今回は、PCGで使用できるスプラインを利用して、より複雑なルールの作成方法を紹介しました。

どのような仕様でメッシュを配置したいかを、PCGグラフ上でノードに落とし込む方法を調査するのは時間がかかりますが、一度ノードを作成できれば複製や編集が容易になるため、UEで何かを制作する際にはとても有効な方法だと改めて感じました。  
また、スプラインを使用したスタティックメッシュの配置では、スプラインの形や大きさ、数によってさまざまな地形を作ることができそうです。

ひきつづき、PCGに関する知識を学習していきたいと思います。

現在、 [電通](https://d.hatena.ne.jp/keyword/%C5%C5%C4%CC) 総研は [web3領域のグループ横断組織](https://www.dentsusoken.com/news/release/2022/0908.html) を立ち上げ、Web3および [メタバース](https://d.hatena.ne.jp/keyword/%A5%E1%A5%BF%A5%D0%A1%BC%A5%B9) 領域のR&Dを行っております（カテゴリー「3DCG」の記事は）。 もし本領域にご興味のある方や、一緒にチャレンジしていきたい方は、ぜひお気軽にご連絡ください！  
私たちと同じチームで働いてくれる仲間を、是非お待ちしております！  
[電通総研採用ページ](https://www.groupcareers.dentsusoken.com/pgdentsusoken/u/job.phtml?company_code=1)

### 参考文献

- [https://historia.co.jp/archives/34360/](https://historia.co.jp/archives/34360/)
- [https://ue5exp0.com/pcg/](https://ue5exp0.com/pcg/)
- [https://www.youtube.com/watch?v=KZHNyESAyw4](https://www.youtube.com/watch?v=KZHNyESAyw4)

執筆： [@okazaki.wataru](https://shodo.ink/@okazaki.wataru/) 、レビュー： [@miyazawa.hibiki](https://shodo.ink/@miyazawa.hibiki/)  
（ *[Shodo](https://shodo.ink/) で執筆されました* ）

[« Amazon Kinesis Data StreamsでIoTデバイ…](https://tech.dentsusoken.com/entry/2024/06/10/Amazon_Kinesis_Data_Streams%E3%81%A7IoT%E3%83%87%E3%83%90%E3%82%A4%E3%82%B9%E3%81%AE%E3%83%AA%E3%82%A2%E3%83%AB%E3%82%BF%E3%82%A4%E3%83%A0%E7%95%B0%E5%B8%B8%E6%A4%9C%E7%9F%A5) [【UEFN】はじめてのUEFN 基礎編 »](https://tech.dentsusoken.com/entry/uefn_basic)
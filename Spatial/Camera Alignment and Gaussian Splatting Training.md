---
title: "Camera Alignment and Gaussian Splatting Training"
source: "https://medium.com/@heyulei/camera-alignment-and-gaussian-splatting-training-89858549784a"
author:
  - "[[Yulei He]]"
published: 2024-10-26
created: 2025-10-14
description: "Camera Alignment and Gaussian Splatting Training Exploring 3D Gaussian Splatting: A Journey from Concept to Real-world Online Exhibition — Part Two Summary This article is a continuare of Capture …"
tags:
  - "clippings"
---
[サイトマップ](https://medium.com/sitemap/sitemap.xml)

[アプリで開く](https://rsci.app.link/?%24canonical_url=https%3A%2F%2Fmedium.com%2Fp%2F89858549784a&%7Efeature=LoOpenInAppButton&%7Echannel=ShowPostUnderUser&%7Estage=mobileNavBar&source=post_page---top_nav_layout_nav-----------------------------------------)

[サインイン](https://medium.com/m/signin?operation=login&redirect=https%3A%2F%2Fmedium.com%2F%40heyulei%2Fcamera-alignment-and-gaussian-splatting-training-89858549784a&source=post_page---top_nav_layout_nav-----------------------global_nav------------------)[書く](https://medium.com/m/signin?operation=register&redirect=https%3A%2F%2Fmedium.com%2Fnew-story&source=---top_nav_layout_nav-----------------------new_post_topnav------------------)

[サインイン](https://medium.com/m/signin?operation=login&redirect=https%3A%2F%2Fmedium.com%2F%40heyulei%2Fcamera-alignment-and-gaussian-splatting-training-89858549784a&source=post_page---top_nav_layout_nav-----------------------global_nav------------------)

## まとめ

[この記事は「ガウススプラッティング用画像キャプチャ」](https://medium.com/@heyulei/capture-images-for-gaussian-splatting-81d081bbc826) の続編です 。主に、キャプチャしたデータセットを3Dガウススプラッティングシーンに学習させる方法を紹介します。Inriaの3Dガウススプラッティングソースコードの使用方法と関連するパラメータ設定に焦点を当てます。記事の後半では、NerfStudioのsplatfactoとPostshotのセットアップと学習方法についても説明します。## [ガウススプラッティング用の画像をキャプチャする](https://medium.com/@heyulei/capture-images-for-gaussian-splatting-81d081bbc826?source=post_page-----89858549784a---------------------------------------)

3Dガウススプラッティングの探求：コンセプトから現実世界のオンライン展示までの旅 — パート1

medium.com

[View original](https://medium.com/@heyulei/capture-images-for-gaussian-splatting-81d081bbc826?source=post_page-----89858549784a---------------------------------------)

なぜInriaの3Dガウススプラッティングの詳細な紹介に重点を置く必要があるのでしょうか？この技術の発明者として、ソースコードの構成と機能を詳細に理解することは、将来の研究の基盤となります。NerfStudioのsplatfactoとPostshotは、いくつかの点でより高度な機能を提供していますが、いずれもオリジナル版をベースにした再現版です。

## Inriaの3Dガウススプラッティングをインストールする

3DガウススプラッティングのソースコードをUbuntuシステムにインストールする方が簡単だと思います。インストール前に、CondaとCUDA SDK 11.8が正常にインストールされていることを確認してください。

```c
# ソースコードをクローンします
git clone https://github.com/graphdeco-inria/gaussian-splatting --recursive 

# conda env を作成します
cd gaussian-splatting 
conda env create --file environment.yml 
conda activate gaussian_splatting
```

以上です。インストールは簡単です。ただし、Windowsプラットフォームへのインストールには多少の課題があります。Windowsプラットフォームに3D Gaussian Splattingのソースコードをインストールして実行する方法を学びたい場合は、以下の2つの記事を参照してください。## [WindowsにInriaのGaussian Splattingソースコードをインストールする](https://medium.com/@heyulei/install-inrias-gaussian-splatting-source-code-on-windows-7781460518ef?source=post_page-----89858549784a---------------------------------------)

WindowsにGaussian Splattingをインストールするのは簡単ではありません。主な問題は、公式ソースコードがVisual Studio 2013をサポートしていないことです。

medium.com

[View original](https://medium.com/@heyulei/install-inrias-gaussian-splatting-source-code-on-windows-7781460518ef?source=post_page-----89858549784a---------------------------------------)## [WSL経由でInriaのGaussian Splattingソースコードをインストールする](https://medium.com/@heyulei/install-inrias-gaussian-splatting-source-code-via-wsl-5e3a2fce7d73?source=post_page-----89858549784a---------------------------------------)

この記事では、Windows マシンに Inria の Gaussian Splatting ソースコードをインストールする方法について詳しく説明します。

medium.com

[View original](https://medium.com/@heyulei/install-inrias-gaussian-splatting-source-code-via-wsl-5e3a2fce7d73?source=post_page-----89858549784a---------------------------------------)

インストール後、COLMAPとImageMagickという2つの必須ツールをインストールする必要があります。これら2つのツールは、ご自身のデータセットを処理する場合にのみ使用します。COLMAPはカメラの位置合わせと点群の生成に使用します。ImageMagickは、元の画像を1/2、1/4、1/8に縮小する画像を生成するために使用します。ImageMagickのインストールは必須ではありません。処理段階でこの操作を行わなくても、トレーニング中に画像は幅1600ピクセルにリサイズされます。

正直なところ、COLMAPをサーバーにインストールするのは少し難しいです。公式Colmapドキュメントに記載されているインストール方法はデスクトップインストール向けであり、クラウドサーバーにインストールすると「ディスプレイなし」エラーが発生するためです。以下のリンク先では、colmap 3.8をクラウドサーバーにインストールする方法を説明しています。## [Colmapをインストールする](https://medium.com/@heyulei/install-colmap-c9d9e6d3d024?source=post_page-----89858549784a---------------------------------------)

Ubuntu 20.04 cuda:11.8.0 で Colmap 3.8 をインストールします

medium.com

[View original](https://medium.com/@heyulei/install-colmap-c9d9e6d3d024?source=post_page-----89858549784a---------------------------------------)

## コードの概要

Inriaの3Dガウススプラッティングのソースコードは、どちらかといえばツールキットのようなものです。公式ドキュメントでは以下のように説明されています。

コードベースには 4 つの主要コンポーネントがあります。

- SfM入力から3Dガウスモデルを生成するPyTorchベースの最適化ツール
- 最適化プロセスに接続して視覚化できるネットワークビューア
- トレーニングされたモデルをリアルタイムでレンダリングするための OpenGL ベースのリアルタイム ビューア。
- 独自の画像を最適化可能な SfM データセットに変換するのに役立つスクリプト

公式ドキュメントの内容を繰り返すつもりはありません。ここでは最初のコンポーネントと4番目のコンポーネントについてのみ説明します。

PyTorchベースの最適化ツールは `train.py` と を実行し、3Dガウススプラッティングの主要コンポーネントを構成します。画像をデータセットに変換するスクリプトは に対応します `convert.py` 。まず について説明します `convert.py` 。

## カメラの配置

`conver.py` 主にCOLMAP CLIを実行します。カメラの位置合わせとポイントクラウドの生成を完了します。

オープンソースのSFM（Structure-from-Motion）ソフトウェアであるCOLMAPは、このプロセスにおいて重要な役割を果たします。COLMAPは、カメラの位置と回転に関する重要な情報を抽出し、同時に点群を生成します。これらの出力は両方とも、ガウススプラッティングの学習に必要な重要な入力となります。

COLMAPを選ぶ理由とは？ 同様のタスクを実行できるツールやソフトウェアは数多く存在しますが、COLMAPは際立っています。確かに、開発者の間で速度に関する不満がよく聞かれるため、最速の選択肢ではないかもしれません。しかし、そのかけがえのない価値は、オープンソースであることと、SFMのパイオニアとしての地位にあります。COLMAPは誕生以来、多くの研究機関や大学で放射場の分野で広く活用されてきました。この分野におけるCOLMAPの普及は明らかで、多くの研究が放射場の研究にCOLMAPを利用しています。さらに、COLMAPがデータセットをデフォルトで提供していることも、その重要性と幅広い利用を裏付けています。

RealityCaptureやMetashapeといったCOLMAPの競合製品は、速度の点でCOLMAPをはるかに上回っています。しかし、これらの代替製品にもそれぞれ欠点があります。まず、COLMAPのように無料かつオープンソースではありません。ライセンス料は非常に高額になる可能性があり、特にRealityCaptureはプロジェクトごとに課金されます。この価格モデルは、エンタープライズレベルへのスケールアップを困難にし、個々のデスクトップアプリケーションに適している傾向があります。基本的に、MetashapeとRealityCaptureは主にデスクトップユーザー向けに設計されています。

（更新：2024年4月より、RealityCaptureはインディーアーティストとスタジオ向けに無料となります。個人ユーザーにとって、RealityCaptureは良い選択肢となりました。）

## ここでは、Inriaの公式ソースコードからconvert.pyスクリプトについて説明します。

1. 特徴抽出：特徴検出と抽出では、画像内の散在する注目点を識別し、それらの特徴を数値記述子で記述します。ここでは、カメラの種類を指定する必要があります。デフォルトでは、カメラの種類は に設定されてい `OPENCV` ます。ただし、画像が魚眼レンズで撮影されている場合は、カメラの種類を に調整する必要があります `OPENCV_FISHEYE` 。
2. 網羅的マッチング：データセットが比較的少数の画像（通常は数百枚程度）で構成されている場合、このマッチングモードは効率的で、優れた再構成結果をもたらします。このモードでは、各画像が他のすべての画像と体系的にマッチングされます。
3. マッパー: 特徴の抽出とマッチングの後、マッパー コマンドはデータセットのスパース 3D 再構築とマッピングを開始します。
4. 歪み補正：Inrialのソースコードはピンホール内在画像のみをサポートしています。そのため、このコマンドは画像を理想的なピンホール内在画像に変換します。

したがって、convert.py のコマンドは次のようになります。

```c
python convert.py -s data/gallery # gallery/input ディレクトリには入力画像が含まれています。# gallery/input ディレクトリには入力画像が含まれています。
```

## ポイントクラウドの改善を試みる

convert.py スクリプトを実行すると、ポイントクラウドが生成され、points3D.bin ファイルとして保存されます。このファイルは学習に使用され、まずスパースポイントクラウドから開始し、その後3Dガウス分布のセットを作成します。

プロジェクト開始当初、テクスチャのない表面でトレーニング結果に大きなエラー領域が見られました。これは、テクスチャのない表面における入力点群の情報不足が原因ではないかと考えました。点群の最適化を何度か試みましたが、点群の最適化は成功しましたが、最終的なトレーニング結果の改善には至りませんでした。最終的に、テクスチャのない表面の問題はキャプチャ段階に戻って解決されました。

以下はポイントクラウドの最適化の記録です。

![](https://miro.medium.com/v2/resize:fit:640/format:webp/1*jnY3y9Bs2VvpckUD7e2g0g.png)

54,000点のColmapポイントクラウド

このギャラリーシーンの場合、特にテクスチャのない表面領域では、得られた結果は満足のいくものではありませんでした。学習結果を向上させるために、COLMAPの高密度再構成法を試してみることにしました。しかし、このアプローチではテクスチャのない領域で大きな改善は得られませんでした。

![](https://miro.medium.com/v2/resize:fit:640/format:webp/1*HsopB5TO1QPDQv0qEkzuFA.png)

Colmap 570万点の高密度ポイントクラウド、テクスチャのない領域では改善なし

テクスチャのない表面から点群を生成するという課題に取り組むため、研究を深めていく中で、 [ETH3D](https://www.eth3d.net/) という興味深いウェブサイトに出会いました。このプラットフォームは、マルチビューステレオと3D再構成手法における最近の進歩を比較しており、これらの技術の多くはオープンソースです。

テクスチャレス・レジリエント・マルチビュー・ステレオのための適応パッチ変形（ [APD-MVS](https://github.com/whoiszzj/APD-MVS) ）は、テクスチャが欠落している領域が広い領域における点群の強調に用いられる手法です。この手法はオープンソースであり、入力画像から得られる深度マップと法線マップを用いて、テクスチャのない領域に改善された点群を生成します。結果は満足のいくものでした。COLMAPと比較して、APD-MVSは、テクスチャのない表面全体にわたっても均一に分布する、大幅に改善された点群を生成します。

![](https://miro.medium.com/v2/resize:fit:640/format:webp/1*BtuzEQLYHjefpkFxZLxEPg.png)

2260万点のAPD-MVSポイントクラウド。特にテクスチャのない領域が改善されました。

> 驚くべきことに、APD-MVS によって生成された強化されたポイント クラウドは、 ガウス スプラッティングのトレーニング結果の改善にはつながり **ません。**

このため、3D ガウス スプラッティングがどのように動作するのかをより深く理解する時期が来たと私は考えています。

## 3Dガウススプラッティングの仕組み## [リアルタイム放射輝度場レンダリングのための 3D ガウススプラッティング](https://repo-sam.inria.fr/fungraph/3d-gaussian-splatting/?source=post_page-----89858549784a---------------------------------------)

リアルタイム放射輝度場レンダリングのための 3D ガウススプラッティング

リアルタイム放射輝度フィールドレンダリングのための 3D ガウススプラッティングrepo-sam.inria.fr

[View original](https://repo-sam.inria.fr/fungraph/3d-gaussian-splatting/?source=post_page-----89858549784a---------------------------------------)

3Dガウススプラッティングは、複数の写真で撮影されたシーンを新しい視点で合成するために最近登場した放射輝度場法です。3Dガウススプラッティングと他のNeRF法との主な違いは、学習とレンダリングの両方で全く異なるレンダリング手法を使用している点にあります。

3D ガウス スプラッティングのトレーニング プロセスは次のとおりです。

```c
SfM メインループからの初期ガウスモデル

: 結果が十分に良くなるまで改善を続ける
   a. ランダムにカメラを選択する
   b. 現在のガウスモデルの 2D 画像をラスタライズする
   c. この画像と入力画像の違いを比較する
   d. この違いを減らすためにガウスモデルを更新する
   
   e. ガウスモデルを更新するタイミングが来たら:
      ガウスモデル内の各スプラットについて: 
        - スプラットがほとんど見えない、または大きすぎる場合は削除する
        
        - このスプラットに詳細が必要な場合: 
          * スプラットが広がりすぎている場合:
            小さなスプラットに分割する
          * スプラットが小さすぎる場合:
            近くにコピーを作成する
```

魔法のような効果は、微分ガウスラスタライゼーションモジュールがモデルの学習を担当するところで起こります。「微分」とは、ラスタライゼーションが微分可能であること、つまり学習中に勾配を計算できることを指します。これは機械学習において重要です。学習中に誤差の逆伝播が可能になり、モデルのパラメータを調整して精度を向上させることができるからです。

![](https://miro.medium.com/v2/resize:fit:640/format:webp/1*kTOzYNsNa85wAyCZBmSPxw.png)

トレーニング前のSfMからのスパースポイントの初期セット

私は機械学習の専門家ではないので、微分ガウスラスタライゼーションがどのように設計され、どのように機能するかを完全に理解しているわけではありません。しかし、ここでは「ブラックボックス」として扱ってみましょう。その機能は、各スプラットを最適化し、位置、スケール、色、不透明度を最適化することです。

## Yulei Heのストーリーをあなたの受信箱にお届けします

このライターからの最新情報を受け取るには、Medium に無料で参加してください。

前のセクションでAPD-MVSによって生成された強化されたポイントクラウドが、ガウススプラッティングのトレーニング結果の改善につながらない理由がようやく分かりました。これは、APD-MVSがポイントクラウドのみを提供し、シーンのプリロード中に初期ガウスモデルに変換されるためです。法線マップと深度マップは、微分ガウスラスタライゼーションの入力としては使用されません。トレーニング中、最適化の入力は3次元（位置x、y、z）であり、最適化のターゲットはガウスモデルのスプラットの属性です。トレーニングプロセス全体を通して、すべてのスプラットの位置、回転、色が徐々に変更され、場合によってはシーンから削除されることもあります。

2024年以降、放射輝度場に関する研究がいくつか行われ、法線マップや深度マップを導入して、学習の入力として新たな次元（深度と方向）を提供するようになりました。これらの改良された手法は、特にテクスチャのない表面に役立ちます。例えば、 [DepthRegularizedGS](https://robot0321.github.io/DepthRegGS/index.html) 、 [SparseGS](https://formycat.github.io/SparseGS-Real-Time-360-Sparse-View-Synthesis-using-Gaussian-Splatting/) 、 [DNGaussian](https://fictionarry.github.io/DNGaussian/) などが挙げられます。入力の次元を増やすと、理論的には学習結果が改善される可能性があります。しかし、実装レベルでは、多次元入力の導入はエラーの増加につながる場合があります。この点については、別の記事で詳しく説明したいと思います。

## トレーニングパラメータ

典型的なトレーニング CLI は次のとおりです。

```c
python train.py -s <COLMAPデータセットへのパス>
```

このプロジェクトでは、球面調和関数のトレーニングパラメータを0に設定しています。このプロジェクトの最終的な表示インターフェースはWebベースであるため、ファイルサイズを縮小し、表示パフォーマンスを向上させるために、球面調和関数の情報は破棄するのが一般的です。テストの結果、トレーニング中に球面調和関数を0に設定し、その後.splat形式に変換すると、視覚的な結果が改善されることが示されています。一方、Unreal Engineで使用する場合やフライスルービデオとして出力する場合は、球面調和関数を3に設定するのが妥当です。

反復回数は3万回、5万回、8万回、100万回のパラメータでテストされました。8万回反復時に最も良好な視覚効果が見られました。100万回反復では、若干の過剰学習が見られました。

最終的なトレーニングパラメータは次のとおりです。

```c
python train.py -s data/gallery --sh_degree 0 --iterations 80000
```

このデータセットをダウンロードし、上記のトレーニング パラメータを使用すると、ギャラリー シーンと同じ結果を得ることができます。## [ガウススプラッティング用の画像のキャプチャ - ファイルのダウンロード](https://yulei.gumroad.com/l/guassian-splatting-capture?source=post_page-----89858549784a---------------------------------------)

これらはダウンロード用の 527 枚のキャプチャ画像で、記事「Gaussian のキャプチャ画像…」のデータです。

yulei.gumroad.com

[View original](https://yulei.gumroad.com/l/guassian-splatting-capture?source=post_page-----89858549784a---------------------------------------)

その他の便利なパラメータ:

```c
--resolution # 1、2、4、または 8 を指定した場合、それぞれ元の解像度、1/2、1/4、または 1/8 の解像度を使用します
--data_device # 大規模/高解像度のデータセットでトレーニングする場合は CPU を使用し、VRAM の消費量を削減します
--densify_grad_threshold # デフォルトでは 0.0002 ですが、より多くのスプラットが必要な場合はこの値を減らします
```

## ナーフスタジオ

3Dガウススプラッティングのソースコードのオリジナル版は、Inriaとマックス・プランク情報科学研究所によってライセンスされています。このライセンスは非商用であるため、研究ツールとしてのみ使用できます。そのため、利用範囲と開発者コミュニティの規模が制限されます。

Nerfstudioは、NeRF（Neural Radiance Fields）を扱うために設計されたオープンソースプラットフォームです。NeRFモデルの学習と可視化のためのインターフェースを提供します。NerfstudioはApache License 2.0に基づいてライセンスされており、商用利用、コードの変更、再配布が可能です。これにより開発者の自由度が高まり、大規模な開発者コミュニティが形成されています。

現在までに、Nerfstudioは20以上のメソッドをサポートしています。注目すべきものは次のとおりです。

1. NeRF、2020年のラディアンスフィールドの先駆的な研究
2. Instant-NGP は、2022 年に発明された NVIDIA の Radiance Fields 向け高性能トレーニングおよびレンダリング ソリューションです。
3. Zip-NeRFは、これまでで最高品質のRadiance Fieldsトレーニングとレンダリングですが、唯一の欠点はトレーニング時間が長いことです。
4. Nerfacto、NerfStudioのデフォルトメソッド
5. Splatfacto、ガウススプラッティング実装

NerfStudioのインストールドキュメントは公式サイトに詳しく記載されています。UbuntuとWSLへのインストールは成功しました。しかし、Windowsへのインストール時にエラーが発生しました。多くの時間をかけてトラブルシューティングを行った結果、Windows版は正常にインストールされ、 `ns-train` 動作はするものの、 `ns-viewer` 一部 `ns-export` が動作しないという問題が発生しました。Windows環境では、WSLへのインストールをお勧めします。## [インストール](https://docs.nerf.studio/quickstart/installation.html?source=post_page-----89858549784a---------------------------------------)

前提条件：Linux Nerfstudio では Python 3.8 以上が必要です。依存関係の管理には conda の使用を推奨します。必ず…

ドキュメント.nerf.studio

[View original](https://docs.nerf.studio/quickstart/installation.html?source=post_page-----89858549784a---------------------------------------)

NerfStudioのインストールに成功したら、CLIコマンドを使ってテスト用のオープンソースデータセットをダウンロードできます `ns-download-data` 。また、を使用して独自のデータセットを生成することもできます `ns-process-data` 。NeRFモデルをトレーニングする場合は、 `ns-train` 22種類の手法から選択して使用できます。ただし、この記事ではSplatfactoについてのみ説明します。

たとえば、 を使用すると `ns-process-data` 、ビデオ、画像、Metashape、RealityCapture 形式などの入力を前処理できます。

```c
ns-process-data images --data data/gallery_input --output-dir data/gallery # 画像を前処理します
ns-process-data video --data data/gallery_input --output-dir data/gallery # ビデオを前処理します
```

## スプラットファクト

2024年1月、NerfstudioはSplatfactoメソッドをリリースしました。SplatfactoはNerfStudioによるガウススプラッティング実装で、 [gsplatを](https://github.com/nerfstudio-project/gsplat) 3Dガウス分布の微分可能なラスタライズとして利用します。

Splatfactoのパラメータ設定は、オリジナルのGaussian Splattingのパラメータ設定に基づいています。違いは、ユーザーフレンドリーな操作性の向上、パフォーマンスの高速化、メモリ効率の向上、そして活発な開発者コミュニティにあります。

Splatfacto トレーニング CLI:

```c
ns-train splatfacto --data data/gallery # ns-process-data を使用したデータセット
ns-train splatfacto colmap --data data/gallery # colmap データセットを使用している場合
```

## グスプラット

Splatfacto による 3D ガウス分布の微分可能ラスタライズは [gsplat](https://github.com/nerfstudio-project/gsplat) です。これも Nerfstudio によってリリースされており、Apache License 2.0 に基づいてライセンスされています。

> *gsplatは* 最新かつ最高の3Dガウススプラッティング技術を搭載しています

なぜgsplatが別途言及されているのでしょうか？現在の最新バージョンであるgsplat 1.4.0では、splatfactorよりも多くの種類のテクニックが既に提供されているからです。例えば：

1. [双方向ガイド付き](https://bilarfpro.github.io/) ガウススプラッティング を実装します。
2. [AbsGS](https://ty424.github.io/AbsGS.github.io/) を実装します 。
3. [ミップスプラッティング](https://niujinshuchong.github.io/mip-splatting/) を実装します 。
4. [3DGS-MCMC](https://ubc-vision.github.io/3dgs-mcmc/) を実装します 。

これは、魚眼カメラモデルを受け入れる MCMC と Bilateral Guided を使用してトレーニングする例です。

```c
python simple_trainer.py mcmc --data_factor 4 \ 
        --use_bilateral_grid \ 
        --camera_model fisheye \ 
        --data_dir <COLMAPデータセットへのパス> \ 
        --result_dir <出力パス>
```

ますます多くのオープンソースのガウススプラッティングプロジェクトが、微分可能ラスタライズをInriaのdiff-gaussian-rasterizationからgsplatに移行していることは特筆に値します。これは一方では、潜在的なライセンス問題を回避できるという利点があります。他方では、gsplatはオープン性とコミュニティ活動の面で大きくリードしています。

## ポストショット

3Dガウススプラッティングは、コンピュータグラフィックス研究の分野で大きな注目を集めているだけでなく、視覚効果（VFX）、3Dゲーム、広告、ビデオ/映画業界の分野でも大きなユーザーベースを獲得しています。

UbuntuやWSL環境は、ほとんどの「アーティスト」にとって馴染みのないものです。CLIインターフェースは非常に使いにくいように見えます。依存関係のインストールやインストールエラーの解決に関するオンラインリソースやチュートリアルも不足しています。こうした状況を考えると、 「アーティスト」コミュニティにおける [Postshot](https://www.jawset.com/) の人気は当然と言えるでしょう。

潜在的な問題点としては、Postshotがベータ版であり、正式リリース後に有料サービスになるかどうかが不透明であるという点が挙げられます。さらに、Postshotはオープンソースソフトウェアではないため、ユーザーは基本的なプリセット設定からしか選択できず、詳細な設定やカスタマイズのニーズに応えることが困難です。

## 結論

最後に、カメラアライメントとガウススプラッティングのトレーニングについて見てきました。興味深いことに、APD-MVSによって生成された強化点群は、テクスチャのない表面における点の分布を大幅に改善しましたが、ガウススプラッティングのトレーニング結果の向上にはつながりませんでした。後ほど、3Dガウススプラッティングのトレーニングメカニズムについて簡単に説明しました。

さらに、Nerfstudio の splatfacto メソッドは、3D ガウス スプラッティングのトレーニングに、より効率的でユーザーフレンドリーなアプローチを提供します。

## 次へ: 3Dガウススプラッティングをオンラインで実現

3Dガウススプラッティングシーンのキャプチャとトレーニング方法については既に説明しました。次の記事では、3DガウススプラッティングシーンをWebに公開する方法を紹介します。「 **3Dガウススプラッティングをオンラインで公開する」（未公開）**

## サポートしてください

この記事が気に入ったら、コーヒーを一杯買って応援していただけると嬉しいです👇## [Yuleiはイタリアを拠点とするフルスタック開発者です。](https://buymeacoffee.com/heyulei?source=post_page-----89858549784a---------------------------------------)

こんにちは！問題解決や知識の共有を楽しんでください。一緒に素晴らしいものを作りましょう！

buymeacoffee.com

[View original](https://buymeacoffee.com/heyulei?source=post_page-----89858549784a---------------------------------------)[ヘルプ](https://help.medium.com/hc/en-us?source=post_page-----89858549784a---------------------------------------)[状態](https://status.medium.com/?source=post_page-----89858549784a---------------------------------------)[について](https://medium.com/about?autoplay=1&source=post_page-----89858549784a---------------------------------------)[キャリア](https://medium.com/jobs-at-medium/work-at-medium-959d1a85284e?source=post_page-----89858549784a---------------------------------------)[プレス](https://medium.com/@heyulei/)[ブログ](https://blog.medium.com/?source=post_page-----89858549784a---------------------------------------)[プライバシー](https://policy.medium.com/medium-privacy-policy-f03bf92035c9?source=post_page-----89858549784a---------------------------------------)[ルール](https://policy.medium.com/medium-rules-30e5502c4eb4?source=post_page-----89858549784a---------------------------------------)[条項](https://policy.medium.com/medium-terms-of-service-9db0094a1e0f?source=post_page-----89858549784a---------------------------------------)[テキスト読み上げ](https://speechify.com/medium?source=post_page-----89858549784a---------------------------------------)
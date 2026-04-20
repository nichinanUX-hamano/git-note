---
title: "NVIDIA が世界の大きなデジタルモデルを構築する fVDB を発表"
source: "https://cginterest.com/2024/07/30/nvidia-%E3%81%8C%E4%B8%96%E7%95%8C%E3%81%AE%E5%A4%A7%E3%81%8D%E3%81%AA%E3%83%87%E3%82%B8%E3%82%BF%E3%83%AB%E3%83%A2%E3%83%87%E3%83%AB%E3%82%92%E6%A7%8B%E7%AF%89%E3%81%99%E3%82%8B-fvdb-%E3%82%92/"
author:
  - "[[.me]]"
published: 2024-07-30
created: 2025-06-30
description: "2024年7月29日（デンバー, SIGGRAPH ） - NVIDIA は、現実世界の AI 対応仮想表現を生成するための新しいディープラーニング フレームワーク fVDB を発表しました。世界の大きなデジタルモデルを構築する fVDBf"
tags:
  - "Pointcloud"
---
2024年7月29日（デンバー, SIGGRAPH ） **–** NVIDIA は、現実世界の AI 対応仮想表現を生成するための新しいディープラーニング フレームワーク [fVDB](https://developer.nvidia.com/fvdb) を発表しました。

## 世界の大きなデジタルモデルを構築する fVDB

fVDB は、水、火、煙、雲などの疎なボリューム データをシミュレートおよびレンダリングするための業界標準ライブラリである [OpenVDB](https://www.openvdb.org/) 上に構築されています。

現実世界に存在する自律走行車やロボットなどの [生成物理 AI](https://www.nvidia.com/en-us/glossary/generative-physical-ai/) には、「空間インテリジェンス」、つまり 3D 空間を理解して操作する能力が必要です。世界の大規模で超微細な詳細をキャプチャすることは不可欠ですが、AI をトレーニングするために現実を仮想表現に変換することは困難です。

現実世界の環境の生データは、ニューラル ラディアンス フィールド ([NeRF](https://blogs.nvidia.com/blog/neural-radiance-fields-3d-models/)) や LiDAR などのさまざまな手法で収集が可能です。fVDB は、このデータをリアルタイムでレンダリングされる大規模な AI 対応環境に変換します。

![](https://www.youtube.com/watch?v=rx55wDWqSrw)

OpenVDB 標準における 10 年間のイノベーションを基に、SIGGRAPH での [fVDB](https://arxiv.org/abs/2407.01781) の発表は、業界がどのように現実世界のデジタルツインから恩恵を受けるかというその方法においての大きな飛躍を表しています。

現実規模の仮想環境は、自律エージェントのトレーニングに使用され、都市規模の 3D モデルは、気候科学や災害計画のためにドローンで撮影されます。今日では、3D 生成 AI は都市空間やスマート シティの計画にも使用されています。fVDB により、業界はこれまで以上に大規模かつ高解像度で空間インテリジェンスを活用できるようになり、物理 AI がさらにスマートになります。

このフレームワークは、効率的な 3D シミュレーションのための GPU アクセラレーテッド データ構造である [NanoVDB](https://developer.nvidia.com/nanovdb) 上に、NVIDIA アクセラレーテッド AI オペレーターを構築します。これらのオペレーターには、畳み込み、プーリング、アテンション、メッシュ化などがあり、すべて高性能 3D ディープラーニング アプリケーション向けに設計されています。AI オペレーターにより、企業は大規模なポイント クラウド再構築や 3D 生成モデリングなどの空間インテリジェンス用の複雑なニューラル ネットワークを構築できます。

fVDB は、NVIDIA の研究チームによる長期にわたる取り組みの成果であり、大規模で複雑な現実世界の空間の高忠実度モデルを必要とする [NVIDIA Research](https://www.nvidia.com/en-us/research/) 、 [NVIDIA DRIVE](https://developer.nvidia.com/drive) 、 [NVIDIA Omniverse](https://www.nvidia.com/ja-jp/omniverse/) プロジェクトのサポートにすでに使用されています。

## fVDB の主な利点

- 大規模化: 以前のフレームワークより 4 倍大きな空間スケール
- 高速化: 以前のフレームワークより 3.5 倍高速
- 相互運用性: 企業は膨大な現実世界のデータセットをフル活用可能。fVDB は VDB データセットをフルサイズの 3D 環境に読み込む。AI 対応でリアルタイム レンダリングされ、空間インテリジェンスを備えた物理 AI を構築可能に。
- より強力: 以前のフレームワークより 10 倍多くのオペレーター。fVDB は、以前は複数のディープラーニング ライブラリを必要とした機能を組み合わせることでプロセスを簡素化。

## 利用について

fVDB は、まもなく [NVIDIA NIM](https://www.nvidia.com/ja-jp/ai/)  推論マイクロサービスとして利用可能になります。次の 3 つのマイクロサービスにより、企業は fVDB を OpenUSD ワークフローに組み込むことができ、産業デジタル化と生成物理 AI アプリケーションのための開発プラットフォームである  [NVIDIA Omniverse](https://www.nvidia.com/ja-jp/omniverse/) で AI 対応の OpenUSD ジオメトリを生成できるようになります。

- fVDB Mesh Generation NIM — 現実世界のデジタル 3D 環境を生成
- fVDB NeRF-XL NIM — Omniverse Cloud API を使用して OpenUSD で大規模な NeRF を生成
- fVDB Physics Super-Res NIM — 超解像を実行して、OpenUSD ベースの高解像度物理シミュレーションを生成

過去 10 年間、 [OpenVDB](https://www.openvdb.org/about/) は視覚効果業界全体で使用されるコア テクノロジとして複数の [アカデミー賞](https://blogs.nvidia.co.jp/2024/03/14/academy-awards-vfx-openusd/) を受賞しました。その後、エンターテイメントの域を超えて、工業デザインやロボティクスなどの産業および科学用途にまで発展しました。

NVIDIA は、オープンソースの OpenVDB ライブラリの強化を続けています。4 年前には [NanoVDB](https://developer.nvidia.com/nanovdb) を発表し、OpenVDB に GPU サポートを追加しました。これにより、桁違いのスピードアップが実現し、パフォーマンスの高速化と開発の容易化が実現し、リアルタイムのシミュレーションとレンダリングへの扉が開かれました。

2 年前、NVIDIA は [NeuralVDB](https://developer.nvidia.com/rendering-technologies/neuralvdb) を発表しました。これは NanoVDB 上に機械学習を構築し、VDB ボリュームのメモリ フットプリントを最大 100 倍圧縮することで、クリエイター、開発者、研究者が極めて大規模で複雑なデータセットを操作できるようにするものです。

fVDB は NanoVDB 上に AI オペレーターを構築し、現実のスケールで空間インテリジェンスを解き放ちます。 [早期アクセス プログラム](https://developer.nvidia.com/fvdb/early-access-form) に申し込み、fVDB PyTorch 拡張機能へアクセスしてください。fVDB は [OpenVDB GitHub リポジトリ](https://github.com/AcademySoftwareFoundation/openvdb) の一部としても利用できるようになります。

[テクニカル ブログでは fVDB](https://developer.nvidia.com/blog/building-spatial-intelligence-from-real-world-3d-data-using-deep-learning-framework-fvdb/) についてさらに詳しく紹介されています。

---

[Reality Reimagined: NVIDIA Introduces fVDB to Build Bigger Digital Models of the World](https://blogs.nvidia.com/blog/fvdb-bigger-digital-models/)

Translate »

タイトルとURLをコピーしました
---
title: EDGS
source: https://compvis.github.io/EDGS/
author:
  - "[[Olga Grebenkova]]"
published: 
created: 2025-06-04
description: "EDGS: Eliminating Densification for Efficient Convergence of 3DGS"
tags:
  - 3DGs
---
<video src="./static/videos/teaser.mp4"></video>  

**標準的な3DGS（左）** と **EDGS（右）** を 比較した、新しいビュー再構成手法 。本手法は、複雑な領域（例えば、詳細なテクスチャや幾何学的構造）において高い忠実度を実現しながら、収束速度を10倍高速化します。EDGS **は** 、収束速度を向上させるために段階的な改良プロセスを置き換え、高品質で高速な3D再構成を実現します。

---

## 仕組み

緻密化により、個々のガウス分布は最終状態に到達する前に複数の改良を経ます。EDGS **は** *、最終状態に既に近い* 初期化を提供します 。モデルが徐々に欠落している詳細を埋めるのを待つのではなく、複数の入力ビューにわたって稠密な 2D 対応を三角測量することによって、稠密な 3D ガウス分布のセットを事前計算します。各対応ピクセルの視線とカメラのポーズはわかっていますが、それらの光線に沿った深度はわかっていないため、画像ペア間の一致するピクセルを三角測量することによって 3D 位置を復元します。これにより、最初から位置、色、スケールなどの十分な情報に基づいた初期プロパティを各ガウス分布に割り当てることができます。ガウス分布は表面に近い位置で初期化されるため、調整が少なくて済むため、私たちの方法では最終的な座標の変位が大幅に削減されます。3DGS と比較して、私たちのモデルは最終的な座標の移動距離を 50 倍削減し、座標での合計パス長は 30 倍短くなります。色のパスの長さも、軌道に沿って小さな振動が残るため、それほど劇的ではありませんが、約 2 分の 1 に減少します。

![初期化と最終状態間の絶対距離](https://compvis.github.io/EDGS/static/images/Absolute.png)

初期化と最終状態間の絶対距離

![最適化による集約距離](https://compvis.github.io/EDGS/static/images/Aggregated_distance.png)

最適化による集約距離

## 3DGSベンチマークにおける他のベースラインとの比較

![テーブル](https://compvis.github.io/EDGS/static/images/table.png)

## ビブテックス

```
@misc{kotovenko2025edgseliminatingdensificationefficient,
      title={EDGS: Eliminating Densification for Efficient Convergence of 3DGS}, 
      author={Dmytro Kotovenko and Olga Grebenkova and Björn Ommer},
      year={2025},
      eprint={2504.13204},
      archivePrefix={arXiv},
      primaryClass={cs.GR},
      url={https://arxiv.org/abs/2504.13204}, 
}
```

原文

この翻訳を評価してください

いただいたフィードバックは Google 翻訳の改善に役立てさせていただきます
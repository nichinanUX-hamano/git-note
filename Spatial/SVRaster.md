---
title: SVRaster
source: https://svraster.github.io/
author: 
published: 
created: 2025-06-04
description: "Sparse Voxels Rasterization: Real-time High-fidelity Radiance Field Rendering"
tags:
  - 3DGs
---
## 概要

ニューラルネットワークや 3D ガウス分布を使わずに、適応型スパース ボクセルのラスタライズ処理を組み込んだ効率的な放射輝度フィールド レンダリング アルゴリズムを提案します。提案されたシステムには、2 つの重要な貢献があります。1 つ目は、シーン内のさまざまな詳細レベルにスパース ボクセルを適応的かつ明示的に割り当て、高いレンダリング フレーム レートを達成しながら、65536 <sup><font><font>x 3</font></font></sup> グリッド解像度でシーンの詳細を忠実に再現することです。2 つ目は、効率的な適応型スパース ボクセル レンダリングのためにラスタライザーをカスタマイズします。光線方向に依存するモートン順序付けを使用してボクセルを正しい深度順序でレンダリングすることで、ガウス分布に見られるよく知られたポッピング アーティファクトを回避します。私たちの方法は、以前のニューラル フリーのボクセル モデルを 4db 以上の PSNR と 10 倍以上の FPS 高速化で改善し、最先端の同等の新規ビュー合成結果を実現します。さらに、当社のボクセル表現は、ボリューム フュージョン、ボクセル プーリング、マーチング キューブなどのグリッドベースの 3D 処理技術とシームレスに互換性があり、将来の幅広い拡張とアプリケーションを可能にします。

![](https://svraster.github.io/images/teaser.jpg)

## 適応型スパースボクセル表現とレンダリング

Our scene representation is a hybrid of primitive and volumetric model. **(a) Primitive component.** We explicitly allocate voxels primitives to cover different scene level-of-details under an Octree layout. Note that we do not replicate a traditional Octree data structure with parent-child pointers or linear Octree. We only keep voxels at the Octree leaf nodes without any ancestor nodes. **(b) Volumetric component.** Inside a voxel is a volumetric (trilinear) density field and a (constant) spherical harmonic field. We sample K points on the ray-voxel intersection segment to compute the intensity contribution from the voxel to the pixel with numerical integration.

![](https://svraster.github.io/images/representations.jpg)  
  

Adaptive level-of-details is crucial to scalability and quality. Sparse voxels with uniform voxel size can not scale up.

![](https://svraster.github.io/images/main_ablation.jpg)  
  

We sort voxels by ray direction-dependent Morton order, which ensures correct primitive blending order with mathematical proof. Sorting by primtive centers like 3DGS can produce inaccurate rendering. The inaccurate sorting causes 3DGS popping artifact (see left video below) while we don't have this issue (right video).

![](https://svraster.github.io/images/morton_order.jpg) <video controls="" height="100%"><source src="./videos/garden_sidebyside.mp4" type="video/mp4"></video>

## Novel-view Synthesis Results

![](https://svraster.github.io/images/quantitative_nvs.jpg) ![](https://svraster.github.io/images/qualitative/bicycle_ours.png)

Ours

![](https://svraster.github.io/images/qualitative/bicycle_3dgs.png)

3DGS

![](https://svraster.github.io/images/qualitative/stump_ours.png)

Ours

![](https://svraster.github.io/images/qualitative/stump_3dgs.png)

3DGS

![](https://svraster.github.io/images/qualitative/playroom_ours.png)

Ours

![](https://svraster.github.io/images/qualitative/playroom_3dgs.png)

3DGS

![](https://svraster.github.io/images/qualitative/drjohnson_ours.png)

Ours

![](https://svraster.github.io/images/qualitative/drjohnson_3dgs.png)

3DGS

![](https://svraster.github.io/images/qualitative/train_ours.png)

Ours

![](https://svraster.github.io/images/qualitative/train_3dgs.png)

3DGS

![](https://svraster.github.io/images/qualitative/truck_ours.png)

Ours

![](https://svraster.github.io/images/qualitative/truck_3dgs.png)

3DGS

## Adaptive Sparse Voxel Fusion

Fusing 2D modalities into the trained sparse voxels is efficient. The grid points simply take the weighted sum from the 2D views following classical volume fusing method. We show several examples in the following.

**Rendered depths → Sparse-voxel SDF → Mesh**

![](https://svraster.github.io/images/meshing.jpg)  
  

**Image segmentation by Segformer → Sparse-voxel semantic field**  
Check it in jupyter notebook [here](https://github.com/NVlabs/svraster/blob/main/notebooks/demo_segformer.ipynb).

Render view

3D fused semantic field

2D Segformer predction

<video controls="" height="100%"><source src="./videos/fusion_segformer_bicycle.mp4" type="video/mp4"></video> <video controls="" height="100%"><source src="./videos/fusion_segformer_room.mp4" type="video/mp4"></video>  
  

**Vision foundation model feature by RADIOv2.5 → Voxel pooling → Sparse-voxel foudation feature field**  
Check it in jupyter notebook [here](https://github.com/NVlabs/svraster/blob/main/notebooks/demo_vfm_radio.ipynb).

Render view

3D fused RADIO feature field

2D RADIO predction

<video controls="" height="100%"><source src="./videos/fusion_radio_bonsai.mp4" type="video/mp4"></video> <video controls="" height="100%"><source src="./videos/fusion_radio_garden.mp4" type="video/mp4"></video>  
  

**Dense CLIP feature by LangSplat → Voxel pooling → Sparse-voxel language field**

<video controls="" height="100%"><source src="./videos/fusion_langfeat.mp4" type="video/mp4"></video>

## Related work

**Data structure**

- [Sparse Voxel Octrees](https://research.nvidia.com/sites/default/files/pubs/2010-02_Efficient-Sparse-Voxel/laine2010tr1_paper.pdf) uses an Octree to manage the sparse voxels.
- [VDB](https://www.museth.org/Ken/Publications_files/Museth_TOG13.pdf) uses a shallow tree with wide branching factor to manage the sparse volumes. Extensions include [OpenVDB](https://www.museth.org/Ken/Publications_files/Museth_SIG14.pdf), [NanoVDB](https://research.nvidia.com/labs/prl/nanovdb/nanovdb2021.pdf), [NeuralVDB](https://arxiv.org/pdf/2208.04448), and the recent [fVDB](https://arxiv.org/pdf/2407.01781)
- Our method does not use any advanced data structure.
We simply store all the non-empty voxels of different size in a 1D array. Our rasterizer ensures everything is correctly ordered when rendering. One limitation is that we do not support efficient search (ie., given a point, find its covering voxel). Future work needs to sort the voxel and implement a binary search for this purpose.

**Sparse field**

- Global-sparse-local-dense strategy allocates a tiny dense 3D grid to each sparse volume. Classical methods like [Voxel hasing](https://niessnerlab.org/papers/2013/4hashing/niessner2013hashing.pdf), [Bundle fusion](https://arxiv.org/pdf/1604.01093), and [Open3D](https://www.open3d.org/docs/latest/tutorial/t_reconstruction_system/voxel_block_grid.html#voxel-block-grid) uses this strategy to do sensor fusion.
- Implicit sparse neural field like [NSVF](https://arxiv.org/pdf/2007.11571) and [NGLOD](https://openaccess.thecvf.com/content/CVPR2021/papers/Takikawa_Neural_Geometric_Level_of_Detail_Real-Time_Rendering_With_Implicit_3D_CVPR_2021_paper.pdf) employs MLP network to map the latent feature stored in the Sparse Voxel Octree to the target attributes.
- Our method allocate just a single voxel at leaf nodes with explicit density and color parameters, like [Plenoxels](https://arxiv.org/pdf/2112.05131).

**Scalability**

- Uniform-level sparse voxels allocates voxel to a given target level. [NSVF](https://arxiv.org/pdf/2007.11571), [NGLOD](https://openaccess.thecvf.com/content/CVPR2021/papers/Takikawa_Neural_Geometric_Level_of_Detail_Real-Time_Rendering_With_Implicit_3D_CVPR_2021_paper.pdf), [SPC](https://kaolin.readthedocs.io/en/v0.9.1/modules/kaolin.ops.spc.html), [Plenoxels](https://arxiv.org/pdf/2112.05131) follow this design, which encouters scalability issue when using higher grid resolution for better quality.
- Our method allocates voxel on different Octree levels. We only keep the leaf nodes in a 1D array without advanced data structure.
For now, our maximum Octree levels is 16 which implies 65536 <sup>3</sup> maximum grid resolution. Extention to more Octree level should be simple. The increase in rendering time should be minor: 3 extra bits to sort per additional level.

**Novel scene representations**

[LinPrim](https://arxiv.org/pdf/2501.16312), [RadiantFoam](https://arxiv.org/abs/2502.01157), [MeshSplats](https://arxiv.org/pdf/2502.07754) are recent methods that use very different and cool approach for reconstruction and novel-view synthesis tasks.

## BibTeX

```
@article{Sun2024SVR,
  title={Sparse Voxels Rasterization: Real-time High-fidelity Radiance Field Rendering},
  author={Cheng Sun and Jaesung Choe and Charles Loop and Wei-Chiu Ma and Yu-Chiang Frank Wang},
  journal={ArXiv},
  year={2024},
  volume={abs/2412.04459},
}
```
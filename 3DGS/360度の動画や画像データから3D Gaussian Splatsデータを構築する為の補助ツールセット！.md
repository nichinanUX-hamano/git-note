---
title: 360度の動画や画像データから3D Gaussian Splatsデータを構築する為の補助ツールセット！
source: https://3dnchu.com/archives/360-gaussian-laskos/
author:
published: 2026-04-02
created: 2026-04-13
description: Laskos Virtualsによる360度の動画や画像データから3D Gaussian Splatsデータを構築する為の補助ツールセット「360° Gaussian」のご紹介！
tags:
  - 3DGs
  - Tool
---
## 記事の概要：360° Gaussian — 360度映像から3DGSデータを構築する補助ツールセット

---

### ツール概要

Laskos Virtualsによる「360° Gaussian」は、360度の動画や画像データから3D Gaussian Splats（3DGS）データを自動的に学習・構築するための補助ツールセットです。

---

### 構成（2つのツール）

**① 360 Gaussian（無料）**

- 360°動画または画像シーケンスから3DガウススプラットをBrush・Postshot・Lichfield studioを使って自動学習させるソフト
- SphereSFMアライメントに対応
- Windows専用

**② Automasker（$46・有料）**

- Grounding DINOおよびSegment Anything 2を活用し、キーワードに基づいて画像要素をマスキングするスタンドアロンプログラム
- 対応GPU：RTX 40/30/20シリーズ、A100、H100、V100、T4（RTX 50シリーズは実験的サポート）
- Windows専用

---

### まとめ

360度カメラで撮影した動画や画像から、3DGSデータを自動で構築できる実用的なツールです。無料の本体ツールで3DGS生成が可能で、より高精度なマスキングが必要な場合に有料のAutomaskerを追加するという構成になっています。360度カメラを活用した3DGS制作のワークフローを大幅に効率化できるツールと言えます。
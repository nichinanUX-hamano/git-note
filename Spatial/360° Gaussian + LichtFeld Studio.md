---
date: 2026-04-14
source: https://qiita.com/Tks_Yoshinaga/items/dbd9359c9e5ead8195a3
tags:
  - 3DGs
  - 360動画
---
# 動作環境

## PCスペック

|     | 環境                              |
| --- | ------------------------------- |
| OS  | Windows 11 Pro for Workstations |
| GPU | NVIDIA RTX 6000 Ada Generation  |
| CPU | Intel(R) Xeon(R) w5-2455X       |
| RAM | 128 GB                          |

## 360°カメラ

- Insta360 X4

## ソフトウェア

360°Gaussian｜Extract ⇒ Alignment ⇒ Cubemaps
＊AutoMasker｜自動画像マスク👆の中で使用可能（€46）
- [https://laskosvirtuals.gumroad.com/l/360gaussian]()
LichtFeld Studio｜Training
- [https://lichtfeld.io/]()

---

|     | 工程                 | 内容                               |
| --- | ------------------ | -------------------------------- |
| 1   | 撮影                 | 360°カメラでシーン撮影                    |
| 2   | SfM                | 各画像がどの位置から撮影されたかを推定              |
| 3   | 点群生成               | SfMで得たカメラ位置を元に点群生成               |
| 4   | Gaussian Splatting | 点群を元に3D Gaussian Splattingモデルの生成 |

---



---
date: 2026-04-14
tags:
  - prompt
  - movie
---
# **最新動画生成AI (Gen-4.5 / Kling 3.0 Pro / Seedance 2.0) プロンプト作成ガイド**

現在の最新動画生成モデルでは、従来の画像生成AIのような「単語の羅列（タグ付け）」ではなく、\*\*「自然言語での詳細な指示」\*\*が主流となっています。

しかし、モデルごとにテキストを解釈する「癖」や得意分野が異なります。このドキュメントでは、代表的な最新モデルである「Gen-4.5」「Kling 3.0 Pro」「Seedance 2.0」それぞれの特性と、最適なプロンプトの書き方をまとめます。

## **1\. Gen-4.5 (Runway) のプロンプト特性**

Gen-4.5は、**役割ごとに構造化された、明確で簡潔な英語の文章**を最も好みます。ダラダラとした長文よりも、セクションを明確に分けたスタイルが効果的です。

* **得意分野:** 意図した構図の正確な再現、安定した動き  
* **基本構成:** \[カメラ設定\] \+ \[被写体とアクション\] \+ \[背景・環境\] \+ \[照明・スタイル\]  
* **書き方のコツ:**  
  * カメラ設定（視点、レンズ、動き）を一番最初に記述する。  
  * アクションは複雑にしすぎず、一つの明確な動作に絞る。  
  * 各要素を独立した短い文で繋ぐ。

**【プロンプト例：車が走り出すシーン】**

*Bird's-eye view, 50mm lens perspective, high-angle static camera. A modern sports car is slowly starting to accelerate from a stop on a wide, empty road. The scene takes place during golden hour, with warm, low sunlight casting extremely long, elongated shadows. The golden light illuminates the car's paint and the texture of the asphalt. The surrounding environment is a vast, open landscape with rolling hills.*

## **2\. Kling 3.0 Pro のプロンプト特性**

Klingは、物理法則のシミュレーションと、複雑なアクションの「過程」や「質感」を詳細に描写する能力に長けています。Gen-4.5以上に、**小説の情景描写のような連続性のある長文**を読み取るのが得意です。

* **得意分野:** 物理的な相互作用（摩擦、煙、水の跳ね方など）、時間経過に伴う変化  
* **書き方のコツ:**  
  * アクションの「始まり」から「終わり」までを時系列で詳細に書く。  
  * 「後輪が空転して煙が出る」など、物理現象を具体的に言語化する。  
  * 情景全体を一つの繋がった物語のように記述する。

**【プロンプト例：車が走り出すシーン】**

*An incredibly detailed, highly realistic aerial photograph taken from a bird's-eye view (approximately 300 feet altitude), using a 50mm lens that provides a natural perspective with minimal distortion. The scene captures a long, paved suburban road during the golden hour, where the warm, low-angle sunlight casts very long, sharp shadows of the trees and buildings. A sleek, modern silver sedan, parked at the side of the road, is just beginning to accelerate from a complete stop. Its rear wheels are slightly spinning, creating a small cloud of smoke on the asphalt. The camera is steady, following the car as it smoothly speeds up. The golden light hits the car's body, creating brilliant highlights. The entire landscape is bathed in a warm, golden hue, with detailed textures of the road surface and surrounding foliage.*

## **3\. Seedance 2.0 のプロンプト特性**

Seedance 2.0は、**映画的な質感（Cinematic Aesthetics）、高いリアリズム、優れたテクスチャ表現**に定評があります。光と影の劇的な効果や、最終的な映像の「ルック」を強調するプロンプトと相性が良いです。

* **得意分野:** 映画的なカラーグレーディング、微細な質感（アスファルトの目、肌の質感など）の表現  
* **書き方のコツ:**  
  * 冒頭で「Cinematic」などの美学を明確に指定する。  
  * 光の効果（レンズフレア、ドラマチックな影など）を強調する。  
  * 被写体だけでなく、周囲の微細な環境変化（風で波立つ水面など）を書き加えることでリアリティを底上げする。

**【プロンプト例：車が走り出すシーン】**

*A stunning, cinematic bird's-eye view shot (taken from a medium-altitude drone), captured using a 50mm lens for a natural and immersive perspective. A dark blue luxury car is gracefully accelerating on a winding scenic coastal road. The entire scene is bathed in the rich, golden light of the golden hour, with the sun low on the horizon. The low-angle light creates dramatic, ultra-long shadows that stretch across the landscape, and a subtle lens flare in the corner. The focus is sharp on the car's movement and the detailed texture of the tarmac, while the background remains a vast, beautiful vista. The wind creates ripples in the water nearby. The overall aesthetic is one of elegant motion and warm, filmic color grading.*

## **4\. 全モデル共通の「べからず」集**

どの最新モデルを使用する場合でも、以下の書き方は避けるべきです。

* **❌ 単語のカンマ区切り (タグ羅列)**  
  * *NG例:* car, starting, 50mm, golden hour, bird view, high quality, 4k  
  * *理由:* 単語同士の関連性や文脈が伝わらず、要素が混ざったり無視されたりします。自然な文章で関係性を明示してください。  
* **❌ 複雑すぎる物理変化の要求**  
  * *理由:* 「車が走り出し、急ブレーキをかけ、その後バックして変形する」のような、一つの動画内で複数の極端な状態変化を起こす指示は破綻しやすくなります。\*\*「一つの明確なシークエンス」\*\*に絞るのがコツです。
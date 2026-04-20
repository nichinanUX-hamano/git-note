---
title: 🍅イントロダクション｜フォトグラメトリ手順書 v2
source: https://zenn.dev/lilealab/books/how-to-photogrammety/viewer/introduction
author:
  - "[[Zenn]]"
published: 
created: 2025-06-04
description: 
tags:
  - 3DGs
---
このチャプターの目次

1. [更新履歴](https://zenn.dev/lilealab/books/how-to-photogrammety/viewer/#%E6%9B%B4%E6%96%B0%E5%B1%A5%E6%AD%B4)
2. [イントロダクション](https://zenn.dev/lilealab/books/how-to-photogrammety/viewer/#%E3%82%A4%E3%83%B3%E3%83%88%E3%83%AD%E3%83%80%E3%82%AF%E3%82%B7%E3%83%A7%E3%83%B3)
3. [その他フォトグラメトリノウハウ公開資料](https://zenn.dev/lilealab/books/how-to-photogrammety/viewer/#%E3%81%9D%E3%81%AE%E4%BB%96%E3%83%95%E3%82%A9%E3%83%88%E3%82%B0%E3%83%A9%E3%83%A1%E3%83%88%E3%83%AA%E3%83%8E%E3%82%A6%E3%83%8F%E3%82%A6%E5%85%AC%E9%96%8B%E8%B3%87%E6%96%99)

![](https://i.imgur.com/TISXbVS.jpeg)

## 更新履歴

- 2024/11/16：UNREAL FEST登壇した際のスライドが公開となったので、該当記事のリンクを追加しました。

## イントロダクション

フォトグラメトリの手順をまとめてみました。

これからフォトグラメトリを始める方の参考になれば。  
主に建物や町並みを対象にした、 **地上撮影による広域大規模なフォトグラメトリ** の手順を紹介しています。  
主に **RealityCaptureの使い方** を紹介してます。  
最後に3D Gaussian Splatting (ガウシアンスプラッティング) への活用も触れています。

- 🍅事例 (メタバースプラットフォーム起動リンク集等)
- 🍅ワークフロー･機材･ソフトウェア
- 📸写真の撮影･整理･現像
- 🚀アライメント (写真位置推定)
- 🚀メッシュ生成
- 🚀テクスチャ生成
- ✨モデルクリーンアップ (モデル整備)
- 🕹コンテンツ化
- 🌈ガウシアンスプラッティング活用

## その他フォトグラメトリノウハウ公開資料

これまで登壇したものについてスライドを公開しています。  
こちらも参考にどうぞ。

- [『広域フォトグラメトリによるデジタルアーカイブ』@マイクロソフト勉強会](https://www.docswell.com/s/lileaLab/5384XJ-200624)
- [『3Dスキャン勉強会 フォトグラメトリ』@東京大学](https://www.docswell.com/s/lileaLab/KW132X-231004)
- [『Photogrammetry RealityCapture TIPS』@XRKaigi](https://www.docswell.com/s/lileaLab/57VLX1-201116)
- [『レーザースキャナ点群と写真を組み合わせた精細な3Dモデルの生成』@日本写真測量学会](https://www.docswell.com/s/HoloLab/538N7M-2023-11-21-132243)
- [『フォトグラメトリと3D Gaussian Splattingによる3Dデジタルアーカイブの比較と最新事例』@ホロラボテックショーケース](https://blog.hololab.co.jp/entry/2024/10/29/165500#B2-3D-Gaussian-Splatting%E3%81%A8%E3%83%95%E3%82%A9%E3%83%88%E3%82%B0%E3%83%A9%E3%83%A1%E3%83%88%E3%83%AA%E3%81%AB%E3%82%88%E3%82%8B3D%E3%83%87%E3%82%B8%E3%82%BF%E3%83%AB%E3%82%A2%E3%83%BC%E3%82%AB%E3%82%A4%E3%83%96%E3%81%AE%E6%AF%94%E8%BC%83%E3%81%A8%E6%9C%80%E6%96%B0%E4%BA%8B%E4%BE%8B)
- [『Meta Bath デジタルで見る子宝湯 RealityCaptureメイキング紹介』@UNREAL ENGINE FEST](https://www.docswell.com/s/EpicGamesJapan/KYDM93-UE_UF24T_HOLOLAB)
- 『フォトグラメトリによる町並みや建造物の文化財デジタルアーカイブ(仮)』@文化財 XRミートアップ東京 (※後日公開)
- [『360度動画によるフォトグラメトリ - 処理編』@3DスキャンなんでもLT会](https://www.docswell.com/s/lileaLab/ZN119P-240907)
- [『中銀カプセルタワービルVR』メイキング](https://www.docswell.com/s/lileaLab/ZM19E2-221126)
- [『川越小江戸VR』メイキング](https://www.docswell.com/s/lileaLab/K4QMX6-211114)
- [『旧都城市民会館VR』メイキング](https://www.docswell.com/s/lileaLab/5YW73R-201023)
- [『大黒湯VR』メイキング](https://www.docswell.com/s/lileaLab/5ENW27-220522)
- [『銭洗弁天VR』メイキング](https://styly.cc/ja/tips/architectural-digital-archive-01-shooting-technique/)
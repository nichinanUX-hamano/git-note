---
title: これが実装されたらWebARがアツい！2025年絶対来てほしいSafari Feature Flags！ - WebAR Lab - WebARの最新情報がわかるメディア
source: https://webar-lab.palanar.com/developer/webar-2025-safari-feature-flags/
author:
  - "[[SaitoEishi]]"
published: 2024-12-24
created: 2026-04-13
description: 少しずつ進化しているiOSのSafariですが、よりWebAR体験を最適にしていくであろう、準備中の機能（Feature Flags）で期待しているものをご紹介していきます。
tags:
  - WebAR
---
## 記事の概要：WebARを加速させたいSafari Feature Flags 6選

2024年12月時点でSafariで実験的に利用できる（Feature Flagsで有効にできる）注目の機能を紹介しつつ、2025年に正式実装されてほしいという願望を込めた記事です。

---

### 注目の6機能

**① HTML `<model>` 要素**

ブラウザ上で3Dモデルを直接表示するための要素で、`<img>` タグのような感覚でsrc属性にファイルを指定するだけで3Dモデルを埋め込めます。特にApple Vision ProのSafariで真価を発揮し、複数のモデルを一気に展開するボタンなどが設置できます。

**② Image Capture API**

デバイスのカメラと直接やり取りして、写真キャプチャ・ピント調整・露出制御・ホワイトバランス設定などの高度なカメラ制御をブラウザ上で行えるAPIです。従来のWebARではCanvas経由で撮影していたためカメラ情報が失われていましたが、このAPIを使うと4032×3024px（約1200万画素）まで解像度を上げることができます。

**③ ScreenCapture**

ブラウザがページの内容を動画や静止画でキャプチャすることを可能にするAPIで、モバイルブラウザでの画面共有や高解像度の動画撮影が可能になります。ただし現時点ではフラグをオンにしてもうまく動作しない状況です。

**④ Shape Detection API**

顔認識・テキスト認識（OCR）・バーコード認識などをブラウザのネイティブ機能を利用して高速に行うためのAPIです。Safariが本格対応すれば、顔トラッキングによるARアクセサリー重畳やQRコード・バーコード読み取りが、ネイティブアプリと遜色ないスピードで実装できるようになります。Apple Vision Proでバーコードを見るだけでレジ打ちができるような活用も考えられます。

**⑤ Notifications（Web Push）**

iOS 16.4からWeb Push通知が利用可能になりましたが、今後は通知権限の細分化やリッチな通知UIが期待されます。ARコンテンツの更新情報をPWA経由で自動通知できるようになれば、ユーザーの再訪を促し、期間限定のAR企画などに特に効果的です。

**⑥ WebXR Device API（ラスボス的存在）**

ARやVRをブラウザで実現するための標準仕様です。Android版Chromeでは実用的な段階ですが、iOS版SafariではまだフルサポートされておらずJavaScriptライブラリでの代替が多い現状です。本格サポートされれば、SLAM（空間認識）を用いた精密なARエクスペリエンスがネイティブアプリと同等のレベルで実現できます。Apple Vision Proでも外カメラアクセスとImmersive AR Sessionが可能になれば、見た空間をそのままAR演出できる最高のWebARが実現します。

---

### まとめ

iOS 16.4でのWeb Push対応のように、Appleは少しずつWebの拡張機能に前向きに取り組んでいる様子がうかがえます。`<model>` 要素やWebXR Device APIが本格的にサポートされれば、ネイティブアプリ並みの高品質なAR体験がブラウザだけで完結する未来も見えてきます。追い風として、GoogleのAndroid XRも公式にWebXRのサポートを大きく取り上げています。
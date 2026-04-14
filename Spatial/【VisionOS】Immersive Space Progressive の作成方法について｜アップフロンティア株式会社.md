---
title: "【VisionOS】Immersive Space Progressive の作成方法について｜アップフロンティア株式会社"
source: "https://note.com/upfrontier/n/n127b844c6eed"
author:
  - "[[アップフロンティア株式会社]]"
published: 2024-06-26
created: 2025-06-30
description: "はじめに   こんにちは！システム開発部のYです。 Immersive Space Progressiveについて調査したため、まとめていきます。 Appleのサンプルアプリ「Destination Video」にそのような実装があったので、それを参考にしています。  環境    Swift Version: 5.9.2    Xcode: 15.2    visionOS: 1.0    macOS: 14.3.1    Immersive Space とは  https://developer.apple.com/documentation/visionos/adding-3d-c"
tags:
  - "VisonPro"
---
![見出し画像](https://assets.st-note.com/production/uploads/images/146918687/rectangle_large_type_2_1fc7b58c9bed577acb2b1f119086547c.png?width=1200)

## 【VisionOS】Immersive Space Progressive の作成方法について

[アップフロンティア株式会社](https://note.com/upfrontier)

## はじめに

---

こんにちは！システム開発部のYです。  
Immersive Space Progressiveについて調査したため、まとめていきます。  
Appleのサンプルアプリ「 [Destination Video](https://developer.apple.com/documentation/visionos/destination-video) 」にそのような実装があったので、それを参考にしています。

## 環境

- Swift Version: 5.9.2
- Xcode: 15.2
- visionOS: 1.0
- macOS: 14.3.1

## Immersive Space とは

![画像](https://assets.st-note.com/img/1719313560008-aHGNquS9IE.png)

[https://developer.apple.com/documentation/visionos/adding-3d-content-to-your-app  
](https://developer.apple.com/documentation/visionos/adding-3d-content-to-your-app)Immersive Spaceは、空間内にアプリケーションをどのように表示するかを定義する表現方法です。  
以下の3つのスタイルがあります。

![画像](https://assets.st-note.com/img/1719313944009-Eh3tn6Tno6.png?width=1200)

## Mixed immersion

パススルーの上にアプリのコンテンツを融合させて、表示する

## Full immersion

パススルーを表示せずに、アプリのコンテンツのみを表示する

## Progressive immersion

Mixed immersionと、Full immersionの中間のようなスタイル。Digital Crownを操作することで、没入度の調整をすることができる。今回はこの、Progressive immersionを使用します。

## Immersive Space Progressive の作成

動画のように前面に背景が表示され、Digital Crownを操作すると没入度を調整することができます。

![](https://assets.st-note.com/img/1719382441283-mE6bgVqkxz.png?width=1200)

クリックで動画再生

## Assetの追加

Progressiveで表示したい背景の画像を追加します。

![画像](https://assets.st-note.com/img/1719314310355-0dEk74Mtk9.png?width=1200)

## App.swift

テンプレートからプロジェクトを作成、App構造体にImmersiveSpaceを追加をします。  
IDは、”testImmersiveSpace”とします。  
今回は、Progressiveにするため、ImmersionStyleに.progressiveを設定します。

```swift
import SwiftUI

@main
struct sampleVisionOSApp: App {
    
    var body: some Scene {
        WindowGroup {
            ContentView()
        }
        
        ImmersiveSpace(id: "testImmersiveSpace") {
            ImmersiveSpaceView()
        }
        // Immersion Styleを.progressiveに設定すると、ユーザーは Digital Crown を使用して体験を調整できるようになる
        .immersionStyle(selection: .constant(.progressive), in: .progressive)
        
    }
}
```

## ContentView.swift

NewProjectから作成後のサンプルコードに、Buttonを追加しています。  
Buttonが押され、isPressedの変更がかかります。  
.onChangeで変更を検知し、trueの場合、openImmersiveSpaceを実行します。  
引数のidに”testImmersiveSpace”を指定することで、ImmersiveSpaceを表示します

```typescript
import SwiftUI
import RealityKit
import RealityKitContent

struct ContentView: View {
    
    @Environment(\.openImmersiveSpace) var openImmersiveSpace
    @Environment(\.dismissImmersiveSpace) var dismissImmersiveSpace

    @State var isPressed = false
    
    var body: some View {
        VStack {
            Button(isPressed ? "Space Closed" : "Space Opened") {
                isPressed.toggle()
            }.foregroundColor(isPressed ? .red : .green)
            
            Model3D(named: "Scene", bundle: realityKitContentBundle)
                .padding(.bottom, 50)

            Text("Hello, world!")
        }
        .padding()
        .onChange(of: isPressed) { (_, new) in
            Task {
                if new {
                    await openImmersiveSpace(id: "testImmersiveSpace")
                } else {
                    await dismissImmersiveSpace()
                }
            }
        }

    }
}

#Preview(windowStyle: .automatic) {
    ContentView()
}
```

## ImmersiveSpaceView.swift

TextureResource.loadAsync(named: destination.imageName)を使用して、指定された画像ファイルを非同期で読み込んでいます。画像はAssetで追加した名前を設定しています。  
読み込んだ画像を「UnlitMaterial」に設定します。  
その後、画像を設定したMaterialを球体に貼り付けてます。  
球体のスケールに(-1, 1, 1)を掛けることで、球体が水平方向に反転し、内側から画像が見えるようにしています。

```swift
import SwiftUI
import RealityKit
import Combine

struct ImmersiveSpaceView: View {
        
    @State var cancellable: AnyCancellable?
    
    var body: some View {
        RealityView { content in
            let rootEntity = Entity()
            cancellable = TextureResource.loadAsync(named: "beach_scene").sink(
                receiveCompletion: {
                    switch $0 {
                    case .finished: break
                    case .failure(let error): assertionFailure("\(error)")
                    }
                },
                receiveValue: { texture in
                    var material = UnlitMaterial()
                    // 読み込んだテクスチャをUnlitMaterialに設定
                    material.color = .init(texture: .init(texture))
                    // ModelComponentを設定
                    rootEntity.components.set(ModelComponent(
                        mesh: .generateSphere(radius: 1E3),
                        materials: [material]
                    ))
                    // スケールを反転して球体を内部から見えるようにする
                    rootEntity.scale *= .init(x: -1, y: 1, z: 1)
                    // 球体の位置を少し上に移動させる
                    rootEntity.transform.translation += SIMD3<Float>(0.0, 1.0, 0.0)
                })
            content.add(rootEntity)
        }
    }
}

#Preview {
    ImmersiveSpaceView()
}
```

## まとめ

Immersive Space Progressiveの作成方法についてまとめました。  
Progressiveを使用すると、仮想空間に視界を包み込みつつユーザーの操作で没入度を調整することができるため、ユーザーは自身の好みに合わせて仮想体験の深さをコントロールできます。  
これにより、没入感のある面白いアプリケーションを作成することが可能です。  
この記事がお役に立てれば幸いです。また、間違っている点などありましたら、教えていただけると幸いです。

## 参考リンク

- [https://developer.apple.com/documentation/visionos/destination-video](https://developer.apple.com/documentation/visionos/destination-video)

  

[![note会員1000万人突破記念　1000万ポイントみんなで山分け祭　エントリー7/8（火）まで](https://assets.st-note.com/poc-image/manual/production/20250623_1000_top_notedetail.jpg?width=620&dpr=2)](https://note.com/info/n/ncceb4a6506fc)

【VisionOS】Immersive Space Progressive の作成方法について｜アップフロンティア株式会社
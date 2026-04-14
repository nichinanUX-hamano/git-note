---
title: "色調整のマンネリ化を解消？ノード単位で色空間を変える応用メソッド"
source: "https://vook.vc/n/7731?c=b&utm_campaign=website&utm_medium=email&utm_source=sendgrid.com"
author:
  - "[[Kaz Ohata]]"
published: 2024-10-08
created: 2025-06-30
description: "DaVinci Resolve のカラーグレーディング作業のマンネリ化を解消する、Node-Based の色空間の設定を活用した、色調整の応用メソッドを紹介していきます。 ▶︎ YouTube ..."
tags:
  - "Color"
---
- [![LINEで送る](https://vook.vc/_nuxt/img/line.1bd24a4.png)](https://social-plugins.line.me/lineit/share?url=https%3A%2F%2Fvook.vc%2Fn%2F7731)

DaVinci Resolve のカラーグレーディング作業のマンネリ化を解消する、Node-Based の色空間の設定を活用した、色調整の応用メソッドを紹介していきます。

> ▶︎ YouTube 動画版はこちら  
> [https://youtu.be/c-EhPppAdw4](https://youtu.be/c-EhPppAdw4)

![](https://vook.imagepix.app/fit/1920/1920/jpeg/80/uploads/user_image/image/56074/aa76262f-58a4-4cfd-88f7-c0f785ea98ed.jpg)

---

## Color Space Transform の活用法

Apple 製品の Retina Display など、これまでの Rec.709 よりも色域が広いディスプレイに最適な映像を制作するために、最近では、カメラが記録する豊富な階調を最大限に活用する、 ***Scene Referred*** な色管理メソッドが普及しはじめています。

![](https://vook.imagepix.app/fit/1920/1920/jpeg/80/uploads/user_image/image/55998/e5d4a56f-a3d9-4255-9dd8-85358f4f1332.jpg) [Netflix](https://youtu.be/u9Rvm5xiuhk)

Scene Referred な色管理システムとしては、米国アカデミー賞を運営する AMPAS が策定した [ACES](https://www.oscars.org/science-technology/sci-tech-projects/aces) が有名ですが、DaVinci Resolve では、この ACES と合わせて、 ***Resolve Color Management*** （RCM）という Blackmagic Design 独自のシステムが使われています。

RCM は、DaVinci Resolve で Scene Referred なカラーグレーディング作業をする上で、基本となる色管理メソッドになりますが、それを Node Editor 画面のノード上で再現できるようにしたのが、 ***Color Space Transform*** （CST）というエフェクトです。

> 画面右上＞Effects＞Resolve FX Color＞Color Space Transform

![](https://vook.imagepix.app/fit/1920/1920/jpeg/80/uploads/user_image/image/55999/5dcf1b2d-978f-4fa7-af3e-511b7ef0c34a.jpg)

Color Space Transform を活用したワークフローは、視覚的にもわかりやすく、また 32-bit 浮動小数点の処理により、これまで LUT で発生していた明るさのクリッピングも起こりづらくなくなるので、LUT に代わる次世代の色管理メソッドとして、たとえば最近では、 ***Nikon N-Raw*** の運用で使われていたりもします。

![](https://vook.imagepix.app/fit/1920/1920/jpeg/80/uploads/user_image/image/56021/ad86e2b0-ea67-4a65-baa5-3148d25f23f3.jpg) [Nikon Aisa](https://youtu.be/cukGr8p0E1c)

一方、DaVinci Resolve の色管理の設定には、ソフト側で色管理をしない DaVinci YRGB、ソフト側で自動で色管理をおこなう DaVinci YRGB Color Managed の 2 種類のモード（Color Science）がありますが、Color Space Transform を使用する場合は、色空間の管理をノード上ですることになるので、基本的に ***DaVinci YRGB*** で作業をすることになります。

> プロジェクト設定＞Color Management＞Color Space & Transforms＞Color Science＞DaVinci YRGB

![](https://vook.imagepix.app/fit/1920/1920/jpeg/80/uploads/user_image/image/56000/8adf9afc-49da-42e9-993f-a517fa1fa7f0.jpg)

---

PR：Vook school

## Color Space の応用メソッド

色空間（Color Space）の設定は、撮影クリップに対して、またはプロジェクト全体で設定をするイメージがありますが、DaVinci Resolve では、それを ***Node Editor 画面にあるノードごとに設定する*** こともできます。

![](https://vook.imagepix.app/fit/1920/1920/jpeg/80/uploads/user_image/image/56002/2119b772-0550-480b-9c38-fdb88babfcde.jpg)

普段あまり意識することもないと思いますが、ノードに割り当てられる色空間は、初期設定では、プロジェクト設定の ***Timeline Color Space*** と同じものが適応されています。そのため、カラーホイールをはじめとする DaVinci Resolve の調整パラメーターは、Timeline Color Space で設定された色空間に対して最適な挙動をするようになっています。

![](https://vook.imagepix.app/fit/660/371/webp/80/uploads/user_image/image/56003/34da7165-8ce7-401d-b1b1-170230d68112.jpg)

それに対して、意図的にノードの色空間の設定を変えてみると、それぞれの調整パラメーターの挙動が変わり、得られる効果にも変化が現れます。ということで、ここから実際のイメージをもとに、その効果を検証していきたいと思います。

## 実際のイメージで効果を試してみる

まず、プロジェクト設定の Timeline Color Space が ***DaVinci Wide Gamut*** の状態で、ある特定の調整ノード A で色やコントラストに関するさまざまな調整をしてみます。

具体的な調整項目は、以下の通りです。

> Color Temp: -200  
> Tint: -3.00  
> Cont: 0.9  
> Pivot: 0.3  
> Shadow: 50.00  
> Highlight: -100.00  
> Gain R: 0.99  
> Gain B: 1.02

![](https://vook.imagepix.app/fit/660/371/webp/80/uploads/user_image/image/56054/fe1bb0ad-b846-4e04-a7e2-0fae467d96b4.jpg)

それに対して、試しに調整ノード A の Color Space の設定を ***Rec.709*** に変えてみると、以下のようになります。

![](https://vook.imagepix.app/fit/660/371/webp/80/uploads/user_image/image/56055/5052b0f7-d968-45bf-9793-09a8558d75e1.jpg)

あまり大きな変化は見られませんが、Rec.709 にしてみると、色の方向性が、全体的に暖色方向にシフトしています。続いて、調整ノード A の Gamma の設定を ***ARRI LogC3*** に変えてみると、以下のようになります。

![](https://vook.imagepix.app/fit/660/371/webp/80/uploads/user_image/image/56056/af9b72dc-164b-4645-bda1-91080ffb5964.jpg)

今度は Color Space の時より、大きな変化が現れています。Gamma を ARRI LogC3 にすると、ハイライトから中間域の明るさが落ちて、元々の DaVinci Wide Gamut よりもコントラストが低くなっています。続いて、Gamma を ***Rec.709-A*** に変えてみると、以下のようになります。

![](https://vook.imagepix.app/fit/660/371/webp/80/uploads/user_image/image/56057/f51a8093-7eb6-416a-ae48-6dc6a0b6c733.jpg)

Rec.709-A に変えてみると、今度は ARRI LogC3 とはまた違った反応が現れました。効果の具合としては、ハイライトの輝度が白飛び寸前まで明るくなり、それ以下の領域が暗く落ちて、コントラストが ARRI LogC3 よりも、さらにぬるい印象になっています。

このような感じで、ノード単位で Color Space、Gamma の設定を変えてみると、調整パラメーターの数値は同じ状態でも、得られる効果が変化することになります。

---

## あとがき

マンネリ化しがちなカラーグレーディング作業に “変化を与える” という意味では、調整パラメーターの反応を変える、この Node-Based な色空間の設定は、わりと有効なメソッドと言えそうです。

その中でも特に、 ***HSV*** の色空間、 ***ACEScc*** のガンマを適用してみると、独特の\*\*\*\*効果を得ることができるんですが、もし興味のある方は、関連の YouTube 動画、note 記事もご参照ください。

> ▶︎ note 記事全文はこちら  
> [https://note.com/umu\_tokyo/n/n6a8101f8684f](https://note.com/umu_tokyo/n/n6a8101f8684f)

[![KazOhata](https://d1i9y8i5xa5nlc.cloudfront.net/uploads/user/profile_image/3807/thumb_300_c2c03952-23f5-4742-ab27-4d5da574671b.png)](https://vook.vc/KazOhata)

### Kaz Ohata@KazOhata

シネマトグラファー VASC、pict（電通グループ）を経て、2015 年に独立。DaVinci Resolve 歴 10 年。映画・CM・MV の撮影を学べる、技術解説記事を note で公開中。 https://note.com/umu\_tokyo...

[他の記事をみる](https://vook.vc/KazOhata)

[![記事特集一覧をみる](https://vook.vc/_nuxt/img/lists.4b5516c.jpg)](https://vook.vc/list)
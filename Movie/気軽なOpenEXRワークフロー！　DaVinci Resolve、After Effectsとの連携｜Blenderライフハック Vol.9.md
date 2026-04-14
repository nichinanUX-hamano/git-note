---
title: 気軽なOpenEXRワークフロー！　DaVinci Resolve、After Effectsとの連携｜Blenderライフハック Vol.9
source: https://vook.vc/n/6779?utm_source=pocket_shared
author:
  - "[[Vook]]"
published: 2023-10-31
created: 2025-06-06
description: CGアーティストのTaka Tachibanaです。 Blenderのあらゆる効率化TIPSをお届けしている【Blenderライフハック】。第9回目となる今回は、「気軽なOpenEXRワークフロ...
tags:
  - Movie
  - CG
---
- [![LINEで送る](https://vook.vc/_nuxt/img/line.1bd24a4.png)](https://social-plugins.line.me/lineit/share?url=https%3A%2F%2Fvook.vc%2Fn%2F6779)

![](https://vook.imagepix.app/fit/1920/1920/jpeg/80/uploads/user_image/image/49188/fe30a223-ead2-4805-9d8c-a0e156852c52.png)

CGアーティストの [Taka Tachibana](https://twitter.com/taka_tachibana) です。

Blenderのあらゆる効率化TIPSをお届けしている **【 [Blenderライフハック](https://vook.vc/b3d_lfhck/notes) 】** 。第9回目となる今回は、 **「気軽なOpenEXRワークフロー」** をテーマに解説します。

**OpenEXRとは高度な画像フォーマットの1つ** で、もしかしたら複雑なコンポジット向けの難しい形式という印象を持ってる人もいるかもしれません。

確かにそうした面もありますが、 ***実は気軽にそしてシンプルな使い方で技術的な表現力をかなり高めることができます。***

また個人制作におけるコンポジットや編集作業によく使われるのは、DaVinci ResolveやAfter Effectsだと思います。

そこで今回は、これら2つのソフトウェアとBlenderの連携方法やOpenEXR向けのオススメのメディアプレイヤーも紹介します。

みなさんの効率化と技術向上にぜひ役立ててみてください！

> ※ この記事を執筆時のバージョンは「3.5.1」です。

## OpenEXRとは

ではまず、そもそもOpenEXRとは何か？

最も有名なVFXスタジオと言っても過言ではないILMこと、Industrial Light & Magic（ **※1** ）が開発したフォーマットで、主な特徴としては次の2点が挙げられます。

- ***非常の多くの情報量を持つ（32bit浮動小数点）***
- ***複数のレイヤーを1つのファイルにまとめることができる***

> **※1：ILM（Industrial Light & Magic）**  
> アメリカのVFXスタジオ。映画『スターウォーズ エピソード4/新たなる希望』（1977）に用いる特殊効果を制作するためのスタジオとして、ジョージ・ルーカスが1975年5月に設立。　 [https://www.ilm.com/](https://www.ilm.com/)

### 32bit浮動小数点とは

32bit浮動小数点は、 **32bit float(以下32bit）** とも呼ばれますが、簡単に言うと、 ***無限に近いくらいの多くの情報を表現することができます。***

映像業界（録音業界）でも近年、この [32bit floatに対応した録音機材](https://zoomcorp.com/ja/jp/news/zoom-introduces-32-bit-float-audio-interfaces/) が発表されてニッチな話題となりました。何がすごいって、 ***多くの情報表現ができる=音割れがしない（無限に近いから）*** ってことだからなんです。

実写の動画収録だと10bitくらいが現実的な限界なので、32bitはとてつもなくすごい数字なんですね。

それがCGの世界だとわりと普通に使えたりします。 ***つまり白飛びや黒つぶれのない（くらいの）表現ができます。***

例えば、こちらがPNG（16bit）。露出を落とすと全体的に暗くなりますが……  
<video data-src="https://d1i9y8i5xa5nlc.cloudfront.net/uploads/user_video/video/80/27c01386-116a-4e83-a28b-cbf60320488d.mp4"></video>

こちらはOpenEXR（32bit）。露出を落としても、背景などの炎などハイライトの情報は残ったままです。  
<video data-src="https://d1i9y8i5xa5nlc.cloudfront.net/uploads/user_video/video/81/96fa6026-83b4-42a5-94b9-a263a7f329b2.mp4"></video>

静止画での比較。こちらがオリジナル。  
![](https://vook.imagepix.app/fit/660/280/webp/80/uploads/user_image/image/48918/0fe4b2cf-28dd-43d5-b304-884eeff26b8c.jpg)

こちらがOpenEXRで露出を落とした状態。  
![](https://vook.imagepix.app/fit/660/280/webp/80/uploads/user_image/image/48919/ab184e32-fba6-4763-9859-7db798f4a343.jpg)

白飛びしてそうな背景の炎のディテールが残っています。 ***これだけの情報量があると、レンダリング後のコンポジット（合成）やカラーグレーディングを柔軟に行うことができます。***

### 複数レイヤーを1つに

コンポジット（合成）作業をやるときに様々なレイヤーに分けてレンダリングすることがよくありますが、その分ファイル管理が複雑になりがち。

OpenEXRはマルチレイヤーという方式もあり、それだと ***1つの画像ファイルに複数の様々なレイヤーを格納することができ、管理がとても楽になります。***

![](https://vook.imagepix.app/fit/660/236/webp/80/uploads/user_image/image/48897/8bb6f981-6610-4292-969f-14127d98e723.jpg)

After Effectsで読み込んだ画面。「EXtractoR」というエフェクトを使えば、複数のレイヤーから任意のものを選択して使用できる

本記事ではこの機能は大きくは取り上げませんが、OpenEXRの大きな特徴の1つです。

PR：Vook school

## BlenderでのOpenEXRレンダリング

それでは、実際にBlenderでOpenEXR形式でレンダリングしてみましょう。  
![](https://vook.imagepix.app/fit/632/480/webp/80/uploads/user_image/image/48902/4c1052cf-e5e8-4018-98c9-a750ba20c8bc.jpg)

レンダリング設定で「OpenEXR」を選択（複数レイヤー保持したい場合は「OpenEXRマルチレイヤー」を選択）、色深度はFloat(Full)、そしてコーデックはDWABというのを選んでみましょう。

![](https://vook.imagepix.app/fit/660/250/webp/80/uploads/user_image/image/48903/c58dc291-38a3-46de-a554-83a04f595f94.jpg)

他のコーデックと比較すると、なんとデータサイズは1/10~1/20ほどになります。このようにDWAB（またはDWAA）というコーデックでは ***高圧縮でかなりデータサイズが小さくなるのに、実は見た目の画質劣化はほとんどわからないほどの優秀さを持っています。***

> ***POINT***  
> ちなみにDWABの他に「DWAA」というのもありますが、アルゴリズムは同じで走査線読み込み方式のちがいのみらしく、どちらを選んでも実感としては変わりません。After EffectsにおいてはDWABの方が向いていると言われています。

### コーデック比較

![](https://vook.imagepix.app/fit/660/280/webp/80/uploads/user_image/image/48904/69301980-352e-4367-9f6a-11ded6935249.jpg)

OpenEXRで保存したこの画像をAfter Effectsに読み込み、過酷な加工をして比較してみます。

![](https://vook.imagepix.app/fit/660/280/webp/80/uploads/user_image/image/48905/4ad2785d-4219-4378-9aee-b999b2907582.jpg)

このように比較しても、 ***パッと見では画質の違いは感じられません。***

![](https://vook.imagepix.app/fit/660/280/webp/80/uploads/user_image/image/48906/0f0d0a73-804d-44e5-842d-0e49b75da029.jpg)

そしてDWAB含めどのコーデックでも、白飛びしそうな背景の炎のディテールが情報として残っています。

FHDで1フレーム **10MB~20MB** もあると動画の場合その容量は膨大なものになりますが、DWABの1フレーム **1MB** くらいならかなり軽快にデータを取り扱うことができます。

ちなみにPNGやTIFFでも **10MB** ほどいくので、 ***その軽さは圧倒的です。***

僕はしばらくこのコーデックを使っていますが、画質的な不満を持ったことは今のところありません。

## DaVinci Resolveとの連携

CGを用いた映像制作で複雑な合成処理が不要な場合、Blenderでレンダリングした後の作業はDaVinci Resolveで行うのがオススメです。

理由としては、

**＜1＞OpenEXRでもリアルタイム再生ができる**  
**＜2＞動画としての編集、カラーグレーディングがやりやすい**

**＜2＞** は元々DaVinci Resolveはそういうコンセプトのソフトウェアなのですが、 **＜1＞** の再生処理はびっくりするくらい速い、というか ***そのままリアルタイム再生ができてしまいます。*** 驚愕です。（おそらくGPUをフル活用するというソフト上の特性が活かされている？）

### DaVinci Resolve上での設定

DaVinci ResolveでBlenderでレンダリングしたOpenEXRを扱うには、ちょっとしたコツが要ります。

下記のワークフローを参考にしてみてください。

#### 1\. 専用のLUTをダウンロード

まずは [こちらのLUT](https://github.com/sobotka/filmic-resolve) をダウンロードして、DaVinci ResolveのLUTフォルダーに保存します。

![](https://vook.imagepix.app/fit/660/222/webp/80/uploads/user_image/image/48909/af7c7546-8034-4b79-b863-411383d1647a.jpg)

DaVinci Resolveの「 [プロジェクト](https://vook.vc/terms/%E3%83%97%E3%83%AD%E3%82%B8%E3%82%A7%E3%82%AF%E3%83%88/103) 設定→LUT→LUTフォルダーを開く」からアクセスすると楽です。

![](https://vook.imagepix.app/fit/660/341/webp/80/uploads/user_image/image/48910/3c29d615-57bd-4707-b0c6-407f381a3fa7.jpg)

すると先ほどダウンロードしたLUTが使用することができます（わかりやすく「01\_Filmic-Resolve」というフォルダ名になっていますが、好きなフォルダ名を設定してOK）。

#### 2\. LUTの設定

LUTの準備が整ったら、OpenEXRを読み込みタイムラインに載せカラーページを開きます。

![](https://vook.imagepix.app/fit/660/283/webp/80/uploads/user_image/image/48911/d2cd93fe-f223-453a-a1c6-9a01b4790eaa.jpg)

**OpenEXRをそのまま読み込んだ形だと画像のようにコントラストが高い状態での表示** になっていまうので、ここを正しい状態へ修正していきます。

![](https://vook.imagepix.app/fit/660/331/webp/80/uploads/user_image/image/48912/3936acba-66db-43d7-a832-7bfa693a3dde.jpg)

まずは1つ目のノードに、先ほど追加したLUTフォルダの中から「Scene Linear to Base Encording」を適用します。

![](https://vook.imagepix.app/fit/660/341/webp/80/uploads/user_image/image/48913/59ed4163-c052-4827-8e0a-e1709323e260.jpg)

すると今度はコントラストが低い状態になりますが、間違いではないのでご安心を。

この次に2つ目のLUTを適用します。基本的には「Base Contrast」でOKです。

![](https://vook.imagepix.app/fit/660/323/webp/80/uploads/user_image/image/48914/b70db2ba-fd72-430a-ade0-5dce524c585e.jpg)

もしBlenderの［レンダープロパティ→カラーマネジメント］で設定を変更した人は同じものを選択してください。デフォルトでは「なし＝Base Contast」になっています。

![](https://vook.imagepix.app/fit/660/318/webp/80/uploads/user_image/image/48915/ade079f5-ef26-4808-b886-857e1cd483ad.jpg)

2つのLUTの適用によって、Blender上と同じコントラスト・色味になります。

このように ***2段階のLUT適用を最初に行う必要がありますが、あとは好きなようにカラーグレーディングや編集を行なって大丈夫です。***

> ***POINT***  
> 1クリップごとのLUT適用がめんどうなときは、DaVinci Resolveのグループ機能を使うと便利です。

![](https://vook.imagepix.app/fit/660/254/webp/80/uploads/user_image/image/48916/d9a00ecf-a674-4cb9-8ed7-f13d196c59c8.jpg)

32bitなので、白飛びが危なそうな部分も、

![](https://vook.imagepix.app/fit/660/253/webp/80/uploads/user_image/image/48917/395c23c0-ac2e-472a-89ad-fc1023ac47da.jpg)

露出を下げても、ちゃんと情報が残っていることが確認できます。（1つ目のLUTで調整）

そのため非常に柔軟なカラーグレーディングを行うことができます。Blenderでのレンダリング後スピーディに編集やカラーグレーディングを行いたい人は、DaVinci Resolveでの作業がオススメです。

> ***POINT***  
> ちなみにDaVinci Resolveでも一応は複雑な合成処理も可能です。 **Fusion** と呼ばれるVFXツールも専用の [ワークスペース](https://vook.vc/terms/%E3%83%AF%E3%83%BC%E3%82%AF%E3%82%B9%E3%83%9A%E3%83%BC%E3%82%B9/147) があるので、それを活用するという手もあります（……が、あんまり使っている人は多くない印象です）。

## After Effects連携

さて、今度はAfter Effectsの特性と連携について解説してみます。

### プラグインのインストール

#### EXtractoR

まず、［Effect→3D Channel］から「EXtractoR」という [プラグイン](https://vook.vc/terms/%E3%83%97%E3%83%A9%E3%82%B0%E3%82%A4%E3%83%B3/99) が入っているか確認します。

![](https://vook.imagepix.app/fit/660/406/webp/80/uploads/user_image/image/48920/ba73ca4e-e616-4166-92fc-98a9f1b1e42b.jpg)

近年のAfter Effectsを使っている場合デフォルトでも搭載されていたと思いますが、もしない人は [こちら](https://www.fnordware.com/ProEXR/) からダウンロードとAfter Effects [プラグイン](https://vook.vc/terms/%E3%83%97%E3%83%A9%E3%82%B0%E3%82%A4%E3%83%B3/99) フォルダへのインストールをしてください。

#### OpenColorIO

次に「OpenColorIO」という [プラグイン](https://vook.vc/terms/%E3%83%97%E3%83%A9%E3%82%B0%E3%82%A4%E3%83%B3/99) をインストールします。 [こちら](https://fnordware.blogspot.com/2012/05/opencolorio-for-after-effects.html) のサイトからダウンロードし、 [プラグイン](https://vook.vc/terms/%E3%83%97%E3%83%A9%E3%82%B0%E3%82%A4%E3%83%B3/99) フォルダへ格納してください。

![](https://vook.imagepix.app/fit/660/371/webp/80/uploads/user_image/image/48922/7eaab2f3-f08a-4d92-b0f3-d85ae3bd5579.jpg)

無事にインストールできたら［Effect→Utility］にて確認できます。

### 設定

#### Color設定

After Effects上の [プロジェクト](https://vook.vc/terms/%E3%83%97%E3%83%AD%E3%82%B8%E3%82%A7%E3%82%AF%E3%83%88/103) 設定にて、「Color」タブ内のColor Settingで「32bits per channel(float)」を選択します。  
![](https://vook.imagepix.app/fit/660/354/webp/80/uploads/user_image/image/48921/b67d2b6d-59f3-42aa-83e3-ee2fd9645240.jpg)

OpenEXRを読み込みタイムラインに載せます。

![](https://vook.imagepix.app/fit/660/311/webp/80/uploads/user_image/image/48925/ba2f90ec-476f-4cd7-9584-b24b2e4d0744.jpg)

一見これだけで良さそうな気がしますが、若干コントラストが高くダイナミックレンジも狭い状態になっています。

そのため次の手順で正しく表示する設定をしてあげます。

#### EXtractoR

まず [エフェクト](https://vook.vc/terms/%E3%82%A8%E3%83%95%E3%82%A7%E3%82%AF%E3%83%88/131) から「EXtractoR」を適用します。

> ***POINT***  
> OpenEXRマルチレイヤー方式だった場合、ここで各レイヤーを選択することができます。

#### OpenColorIO

その次に「OpenColorIO」を適用します。

![](https://vook.imagepix.app/fit/660/548/webp/80/uploads/user_image/image/48924/888b3beb-3954-49fb-b56c-529d77edba01.jpg)

［Configuration→Custom］から、 **Blenderのデータフォルダ内の「config.ocio」** というファイルを選択します。格納先は下記 [パス](https://vook.vc/terms/%E3%83%91%E3%82%B9/125) になります。

> **datafiles→colormanagement→config.ocio**

![](https://vook.imagepix.app/fit/660/163/webp/80/uploads/user_image/image/48923/fa40b43f-e7f0-4a17-9d45-a8b25031c4a1.jpg)

そして、Input SpaceをLinearに、Output ScapeをFilmic sRGBにします。

![](https://vook.imagepix.app/fit/660/223/webp/80/uploads/user_image/image/48926/80390712-00d1-4c84-a64b-2e6e9c33751e.jpg)

こうすることによって、 ***Blender上のコントラストや色味が同じにすることができます。***

DaVinci ResolveもAfter Effectsもこの最初の設定だけ少し手間がかかりますが、これによって正しい環境で柔軟な作業が可能になります。

## OpenEXR向けのメディアプレイヤー

ここまで解説した通り、非常に優秀なOpenEXRという形式です。  
ただし、 ***ひとつ難点があるとしたら、そのままPC上で再生してチェックすることができない*** ことです。

つまり対応しているメディアプレイヤーが少ないのですが、サクッと見たいのに、その度にAfter Effectsなどを開くのはめんどくさいですよね。

なのでぜひこの **[DVJ](https://darbyjohnston.github.io/DJV/)** というプレイヤーを使ってみてください。

*<iframe src="https://player.vimeo.com/video/427238947" frameborder="0" allowfullscreen=""></iframe>*

***無料とは思えない超高性能メディアプレイヤーでなんでも再生できちゃいます。***

OpenEXRの再生チェック（プレイヤー）としては現状これ一択かなと思います。

BlenderもDaVinci ResolveもDVJも無料で使えるソフトウェアで、ここまでのことができるのはすごい時代だなと感じずにはいられません。

### DVJの設定

こちらもDaVinci ResolveやAfter Effectsと同様にそのままだとコントラストが高い状態なので、正しい設定が必要です。

まずは上部メニューより［Image→Color Space］と進みます。

![](https://vook.imagepix.app/fit/627/205/webp/80/uploads/user_image/image/48927/ca0374a9-f052-47e2-941b-bfc018468c2f.jpg)

次の画像の「+」より、configファイルを読み込みます。After Effectsの設定で解説したものと同じ、

> **datafiles→colormanagement→config.ocio**

……にて「config.ocio」というファイルを選択します。

![](https://vook.imagepix.app/fit/354/624/webp/80/uploads/user_image/image/48928/97dc3103-e02d-4bdd-bbd5-078ad1b31506.jpg)

ViewをFilmicに、DefautをLinearにすると正しい表示がされます。

![](https://vook.imagepix.app/fit/660/389/webp/80/uploads/user_image/image/48929/a3abf37c-bfcc-439c-a276-66e3062927a9.jpg)

DVJでは一度設定すると、前回の設定がそのまま反映されるので毎回設定する必要はありません。

またループ再生や切り返し再生などいろんな機能も搭載しているので、CG制作・映像制作に欠かせないイチオシなメディアプレイヤーだと思います。

---

今回は、以上です。

これからも様々な効率化TIPSを紹介していくので、次回もご期待ください。 ***感想やリクエストもぜひ！***  

[![b3d_lfhck](https://d1i9y8i5xa5nlc.cloudfront.net/uploads/user/profile_image/45862/thumb_300_bc0fcd26-6c56-4162-ade3-83eddd2bb2c7.png)](https://vook.vc/b3d_lfhck)

### Blenderライフハック@b3d\_lfhck

この連載では、実写VFX系のBlenderユーザーとして知られるTaka Tachibanaさん（ @taka\_tachibana ）が、Blenderによる3DCG制作をより効率的に行うためのTIPSを紹介します。 作業効率を高めるためのBlender...

[他の記事をみる](https://vook.vc/b3d_lfhck)

[![記事特集一覧をみる](https://vook.vc/_nuxt/img/lists.4b5516c.jpg)](https://vook.vc/list)
---
title: はじめよう！踏み出そう！VFX！ 第2回：DaVinci Resolve Fusionで踏み込むコンポジット！【ステイホームVFX連動企画】
source: https://cgworld.jp/regular/202104-38912vfx-02.html?utm_source=pocket_shared
author:
  - "[[ CGWORLD.jp]]"
published: 2021-04-16
created: 2025-06-06
description: 「ステイホームだし自宅で映像をつくってみようかな？」「でも3DCGは作ったことあるけど、実写合成...
tags:
  - Movie
  - VFX
---
- [![](https://img94.astrsk.net/uploads/00000000000000000055/23046204cbbc8af3a0d6cbf22e5920cb-20250603171403-img1.png)](https://cdn.astrsk.net/ads00055kvo09ioy3bif/click.cgi?ucd=RV9fpCBfSKf5HYXZ0gu8lh66ec6b46&thru=&cref=aHR0cHM6Ly9jZ3dvcmxkLmpwL3JlZ3VsYXIvMjAyMTA0LTM4OTEydmZ4LTAyLmh0bWw%2FdXRtX3NvdXJjZT1wb2NrZXRfc2hhcmVk&idx=4)

![](https://cgworld.jp/regular/assets_c/2021/04/38912vfx02-main_-thumb-640x427-17139.png)

記事の目次

- [はじめに](https://cgworld.jp/regular/?utm_source=pocket_shared#chapter1)
- [今回作る映像](https://cgworld.jp/regular/?utm_source=pocket_shared#chapter2)
- [各種ダウンロード](https://cgworld.jp/regular/?utm_source=pocket_shared#chapter3)
- [Practice：はじめてのノードベースコンポジット！](https://cgworld.jp/regular/?utm_source=pocket_shared#chapter4)
- [01：最初に「色空間」を定めよう！](https://cgworld.jp/regular/?utm_source=pocket_shared#chapter5)
- [Point！　素材別 Input TransformのSource Spaceの選び方](https://cgworld.jp/regular/?utm_source=pocket_shared#chapter6)
- [02：背景を「キーイング」してみよう！](https://cgworld.jp/regular/?utm_source=pocket_shared#chapter7)
- [Point！ グリーンバック撮影のコツ](https://cgworld.jp/regular/?utm_source=pocket_shared#chapter8)
- [03：「マスク」を切ってみよう！](https://cgworld.jp/regular/?utm_source=pocket_shared#chapter9)
- [04：「マージ」ノードで素材を合成してみよう！](https://cgworld.jp/regular/?utm_source=pocket_shared#chapter10)
- [05：素材の「色合わせ」をしてみよう！](https://cgworld.jp/regular/?utm_source=pocket_shared#chapter11)
- [06：映像に味付けしてみよう！](https://cgworld.jp/regular/?utm_source=pocket_shared#chapter12)
- [07：最後に「レンダリング」で書き出そう！](https://cgworld.jp/regular/?utm_source=pocket_shared#chapter13)
- [おわりに：まずはVFXを楽しもう！](https://cgworld.jp/regular/?utm_source=pocket_shared#chapter14)
- [Profile.](https://cgworld.jp/regular/?utm_source=pocket_shared#chapter15)

「ステイホームだし自宅で映像をつくってみようかな？」「でも3DCGは作ったことあるけど、実写合成は難しそう」......そんなあなたのために、現役大学生の映像作家・三宅智之氏が実写合成のイロハを集中講義！　無償版DaVinci Resolveとダウンロード素材で今すぐ始めよう！！

TEXT＿三宅智之 / Tomoyuki Miyake（ [@38912\_DIGITAL](https://twitter.com/38912_DIGITAL) ）  
EDIT＿小村仁美 / Hitomi Komura（CGWORLD）

[![](https://cgworld.jp/special/remotework-plan/images/640_150_bnr.jpg)](https://cgworld.jp/special/remotework-plan/)

- [![](https://cgworld.jp/regular/images/38912vfx/banner.png)](https://www.info-event.jp/dell/lp/ws_vfx/)
- Dell Presents ステイホームVFX コンテスト エントリー受付中！  
	  
	●審査基準  
	01：自宅での撮影素材を活かした面白い表現ができているか  
	02：CG・VFX技術を駆使した作品であるかどうか  
	  
	●部門  
	プロフェッショナル部門／学生部門  
	  
	●応募方法  
	・エントリー：〜5月15日  
	・審査同意書記入：〜5月21日  
	・作品提出：〜5月24日  
	  
	[www.info-event.jp/dell/lp/ws\_vfx](https://www.info-event.jp/dell/lp/ws_vfx/)
  
  

## はじめに

こんにちは！　古い柱上変圧器が大好きな [38912 DIGITAL](https://twitter.com/38912_DIGITAL) こと、三宅智之です。

[前回](https://cgworld.jp/regular/202104-38912vfx-01.html) はBlenderを使い、実写とCGの動きを合わせる 「マッチムーブ」 をメインに紹介し、素材と素材を合成する「コンポジット」についても少し触れてみました。

今回は無料でほとんどの機能が使える映像編集ソフトDaVinci Resolveを使い、VFXの醍醐味 「コンポジット（合成）」 の工程にさらに一歩踏み込んでいきます。前回より少しレベルアップしますが、わかりやすく説明していきますので、おやつと飲み物片手にのんびりやっていきましょう！　さぁ悩むより手を動かせ！　はじめよう！　VFX!!!

## 今回作る映像

第2回では、この映像を作ります。グリーンバックの人物と背景CGを合成する、ちょっと本格的なVFXカットです。

![](https://www.youtube.com/watch?v=X1gF7TLY-uc)

今回のカットは、おおまかに以下のながれで進行していきます。前回同様、何を言っているのかわからなくても大丈夫です。

[![](https://cgworld.jp/regular/images/38912vfx/vol02/01_v2.png)](https://cgworld.jp/regular/images/38912vfx/vol02/01_v2.png)

## 各種ダウンロード

以下の3つのソフト・設定ファイル・素材データを使用します。※印のあるものは下記の注意事項を読んだ上で、ダウンロードしてください。

●使用ソフト  
DaVinci Resolve 17（※）  
[www.blackmagicdesign.com/jp/products/davinciresolve/](https://www.blackmagicdesign.com/jp/products/davinciresolve/)

●使用する色空間のConfigファイル  
OpenColorIO-Configs（※）  
[github.com/colour-science/OpenColorIO-Configs/tree/feature/aces-1.2-config](https://github.com/colour-science/OpenColorIO-Configs/tree/feature/aces-1.2-config)

●使用映像素材  
ライセンス：CC-BY-NC 4.0  
[CGW\_38912VFX\_02.zip](https://cgworld.jp/data/38912vfx/CGW_38912VFX_02.zip)  

※ダウンロード時の注意事項

＜DaVinci Resolve 17 について＞  
[リンク先](https://www.blackmagicdesign.com/jp/products/davinciresolve/) の「今すぐダウンロード」からダウンロードしてください。サイズはおよそ3GBです。「DaVinci Resolve Studio 17」と"Studio"と名前のついているものは有料版で、今回は無印の「DaVinci Resolve 17」（無償版）を使います。すでにDaVinci Resolve Studio 17を購入されている方は、Studio版を使っても操作にちがいはありません。

＜OpenColorIO-Configsについて＞  
OpenColorIO-Configsのダウンロードは以下の2種類の方法のどちらかで行なってください。どちらか一方だけで良いです。

*方法1：Webブラウザで取得*  
リンク先のページの緑のボタン［Code→Download ZIP］からダウンロードしてください。GitHubの仕様上、Webブラウザからは必要なフォルダだけをダウンロードすることはできません。そのためOpenColorIO-Configsのリポジトリ全体およそ1.88GBをまるごとダウンロードすることになってしまいますが、今回はその中の［aces\_1.0.3］のみ使います。全て展開してしまうと6GB超になってしまうので、ZIPファイル内の［aces\_1.0.3］フォルダのみを取り出して展開するようにしてください。

*方法2：Gitで取得*  
Gitが使える方は保存したいフォルダにcdで移動した後、以下のコマンドで［aces\_1.0.3］のみを直接pullできます。1行で実行できるよう複数のコマンドをつないでいるので、最初のmkdirから最後のmasterまでをまるごとコピーすればそのまま実行できます。

`  ``` mkdir aces && cd aces && git init && git remote add origin https://github.com/colour-science/OpenColorIO-Configs/ && git config core.sparsecheckout true && echo /aces_1.0.3 > .git/info/sparse-checkout && git pull origin master ```  `

## Practice：はじめてのノードベースコンポジット！

[![](https://cgworld.jp/regular/images/38912vfx/vol02/A01_v2.png)](https://cgworld.jp/regular/images/38912vfx/vol02/A01_v2.png)

まずは簡単なCG素材でノードベースの コンポジット（合成） の練習をしてみましょう。

  

【実践】よくわからなくてもOK！まずは手順通り触ってみよう！

〈Step 0〉プロジェクト作成

[![](https://cgworld.jp/regular/images/38912vfx/vol02/A02.png)](https://cgworld.jp/regular/images/38912vfx/vol02/A02.png)

▲ 【1】 DaVinci Resolveを起動するとこのような「プロジェクトマネージャー」が開くので、左上の［名称未設定のプロジェクト］をダブルクリックして新しいプロジェクトを起ち上げます

[![](https://cgworld.jp/regular/images/38912vfx/vol02/A03.png)](https://cgworld.jp/regular/images/38912vfx/vol02/A03.png)

▲ 【2】 このような画面が開くはずです

[![](https://cgworld.jp/regular/images/38912vfx/vol02/A04.png)](https://cgworld.jp/regular/images/38912vfx/vol02/A04.png)

▲ 【3】 画面最下部にはいくつかタブアイコンがあります。［Fusion］と書いてあるアイコンをクリックし、［Fusion］タブを開いてください

下のタブは左から順に一般的な映像制作のワークフローで並んでいます。［メディア］は映像の読み込みと整理、［カット］と［エディット］は映像編集、［Fusion］はVFX、［カラー］はカラーグレーディング、［Fairlight］は音声編集、［デリバー］は映像の書き出しです。今回はコンポジット（合成）を行うため、VFXの機能をもつ［Fusion］タブを使います。

- [![](https://cgworld.jp/regular/images/38912vfx/vol02/A05.png)](https://cgworld.jp/regular/images/38912vfx/vol02/A05.png)
- ◀ 【4】 画面右下の歯車アイコンから［プロジェクト設定］を開きます

[![](https://cgworld.jp/regular/images/38912vfx/vol02/A06.png)](https://cgworld.jp/regular/images/38912vfx/vol02/A06.png)

▲ 【5】 ［プロジェクト設定］を開いたら、①［マスター設定→タイムラインフレームレート］を②［24］に設定しておきます。最後に右下の③［保存］を押します

ここでいったん［Ctrl+S］でプロジェクトに名前をつけ保存しておきましょう。

今回は撮影時に毎秒24フレームの設定で撮影しているので、プロジェクト設定のフレームレートは24を選択しました。最近はスマホのカメラでもフレームレートを指定できることが多くなりましたが、最も一般的な30fpsや29.97fps（アナログ時代の名残です）、設定によっては60fpsなどがあります。映画はフィルム時代から24fpsがよく使われます。あらかじめ、この作品はどのfpsで作る、などを決めておく必要があります。

  

〈Step 1〉メディアの読み込み

- [![](https://cgworld.jp/regular/images/38912vfx/vol02/A07.png)](https://cgworld.jp/regular/images/38912vfx/vol02/A07.png)
- ◀ 【6】 ［Fusion］タブが開けたら、画面左上のメディアプールの空欄（画像のマウスカーソルのあたり）で右クリック→［メディアの読み込み］を選択します

[![](https://cgworld.jp/regular/images/38912vfx/vol02/A08.png)](https://cgworld.jp/regular/images/38912vfx/vol02/A08.png)

▲ 【7】 配布素材の［Practice］フォルダから練習画像3枚を選択し、開きます

  

〈Step 2〉コンポジットノードの作成

- [![](https://cgworld.jp/regular/images/38912vfx/vol02/A09.png)](https://cgworld.jp/regular/images/38912vfx/vol02/A09.png)
- ◀ 【8】 左上のメディアプールに画像が3枚読み込まれました。［Practice\_BG.png］を画面下のノードグラフにドラッグ＆ドロップし、配置します
- [![](https://cgworld.jp/regular/images/38912vfx/vol02/A10.png)](https://cgworld.jp/regular/images/38912vfx/vol02/A10.png)
- ◀ 【9】 このようなノードが作成されました。ノードグラフは中ドラッグで前後左右の移動、［Ctrl］キー＋マウスホイールでズームできます

[![](https://cgworld.jp/regular/images/38912vfx/vol02/A11.png)](https://cgworld.jp/regular/images/38912vfx/vol02/A11.png)

▲ 【10】 右上にピンク色の背景（Practice\_BG.png）が表示されているはずです

- [![](https://cgworld.jp/regular/images/38912vfx/vol02/A12.png)](https://cgworld.jp/regular/images/38912vfx/vol02/A12.png)
- ◀ 【11】 続いて［Practive\_V.png］を先ほどと同じようにノードグラフにドラッグ＆ドロップします。今度は［MediaIn2］ノードのみが追加されたはずです

[![](https://cgworld.jp/regular/images/38912vfx/vol02/A13.png)](https://cgworld.jp/regular/images/38912vfx/vol02/A13.png)

▲ 【12】 ノードの位置はノードをドラッグすれば自由に動かすことができます。［MediaOut1］ノードをドラッグして右に動かし、少し離れたところに置いておきます

- [![](https://cgworld.jp/regular/images/38912vfx/vol02/A14.png)](https://cgworld.jp/regular/images/38912vfx/vol02/A14.png)
- ◀ 【13】 ノードの出力ソケット（ノード右側の白い四角）をドラッグすると、線が伸びます。矢印の通りに、下の［MediaIn2］ノードから伸ばした線を、上の［MediaIn1］ノードの出力ソケット（白い四角）に繋げてみましょう

[![](https://cgworld.jp/regular/images/38912vfx/vol02/A15.png)](https://cgworld.jp/regular/images/38912vfx/vol02/A15.png)

▲ 【14】 すると、［Merge1］ノードが間に追加され、2つの画像が合成されました。ノードを画像の位置に動かします。右上のビューに「V」のCG画像が合成されたはずです

- [![](https://cgworld.jp/regular/images/38912vfx/vol02/A16.png)](https://cgworld.jp/regular/images/38912vfx/vol02/A16.png)
- ◀ 【15】 同様に、［Practice\_Suzanne.png］を左上のメディアプールから下のノードグラフにドラッグ＆ドロップし配置します。矢印の方向に、追加された［MediaIn3］ノードの出力ソケット（白い四角）と［Merge1］ノードの出力ソケット（白い四角）を繋げてみましょう

[![](https://cgworld.jp/regular/images/38912vfx/vol02/A17.png)](https://cgworld.jp/regular/images/38912vfx/vol02/A17.png)

▲ 【16】 このように、全ての画像が合成されました。ノードを画像の位置に動かします

- [![](https://cgworld.jp/regular/images/38912vfx/vol02/A18.png)](https://cgworld.jp/regular/images/38912vfx/vol02/A18.png)
- ◀ 【17】 すでに線で繋がっている入力ソケット（三角形）をドラッグすると、線を取り外すことができます

[![](https://cgworld.jp/regular/images/38912vfx/vol02/A19.png)](https://cgworld.jp/regular/images/38912vfx/vol02/A19.png)

▲ 【18】 ［Merge1］ノードの「緑色」の入力ソケット（foregroundソケット）と、［Merge2］ノードの「緑色」の入力ソケット（foregroundソケット）を入れ替えてみます。このとき、間違って「青色」の入力ソケット（Effect Maskソケット）に繋がないよう気をつけてください。ソケットの色がわかりづらいときは、入力ソケットの上にカーソルを置くとソケット名がホバー表示されます

[![](https://cgworld.jp/regular/images/38912vfx/vol02/A20.png)](https://cgworld.jp/regular/images/38912vfx/vol02/A20.png)

▲ 【19】 線を入れ替えると、CG画像の前後が入れ替わりました

ここまできたら、［Ctrl+S］で保存しておきましょう。

  

【理論】なぜこうするの？

このように、「ノードベース」のUIには様々な機能をもった 「ノード」 という箱がソフトウェア側で用意されており、それらの箱と箱を繋げることで何かしらの処理を行います。

「ノードベースのコンポジット（合成）」では実写素材やCG素材を読み込む 「入口のノード」 （今回はMediaInノードで読み込みました）から始まり、 「処理を行うノード」 （今回はMergeノードで合成しました）を通じて、最終的に映像を出力する 「出口のノード」 （今回はMediaOutノードでした）へ処理が進みます。そのため、線のつなぎ方＝ノードの順番によって処理の順番が変わり、出力される画が変わります。川が合流しながら太くなり海に出ていくように、AとBが合わさり、それにCが合わさって......と処理が順々に進んでいくイメージです。

PhotoshopやAfter Effectsやペイントソフトなどの「レイヤーベースのコンポジット」に慣れている方は「ノードはむしろ面倒では...？」と感じるかもしれません（筆者も昔はそう思ってました）。確かに「ノード」は「レイヤー」に比べ直感的ではないため、難しそうに見えますよね。

しかし合成が複雑になればなるほど「ノード」の方が効率良く合成できるようになるほか、複雑な処理を視覚的にわかりやすく整理できるといったメリットがあります。そのため、複雑な合成処理が必要なVFXの現場ではFoundryの「Nuke」というノードベースのコンポジットソフトが広く使われていたりします。最初は大変だと感じるかもしれませんが、実践を通して少しずつ慣れていきましょう！

[次ページ：  
01：最初に「色空間」を定めよう！](https://cgworld.jp/regular/202104-38912vfx-02-2.html)

## 01：最初に「色空間」を定めよう！

[![](https://cgworld.jp/regular/images/38912vfx/vol02/B01_v2.png)](https://cgworld.jp/regular/images/38912vfx/vol02/B01_v2.png)

さて、ここまでは準備体操、次からが本番です。さっそくコンポジット（合成）に入りたいところなのですが......その前にVFXをする上で大切な土台づくり 「色空間（Color Space）」 の設定をします。

  

【実践】よくわからなくてもOK！まずは手順通り触ってみよう！

〈Step 0〉プロジェクト設定の変更

- [![](https://cgworld.jp/regular/images/38912vfx/vol02/B02.png)](https://cgworld.jp/regular/images/38912vfx/vol02/B02.png)
- ◀ 【1】 画面右下の歯車アイコンから［プロジェクト設定］を開きます

[![](https://cgworld.jp/regular/images/38912vfx/vol02/B03.png)](https://cgworld.jp/regular/images/38912vfx/vol02/B03.png)

▲ 【2】 ［プロジェクト設定］を開いたら、①［カラーマネジメント→カラーサイエンス］を②［ACEScct］、③［ACES出力デバイストランスフォーム］を［sRGB］に変更し最後に④［保存］します

  

〈Step 1〉新しいFusionコンポジションの作成

- [![](https://cgworld.jp/regular/images/38912vfx/vol02/B04.png)](https://cgworld.jp/regular/images/38912vfx/vol02/B04.png)
- ◀ 【3】 画面左上のメディアプール内で①右クリック→［新規ビン］でフォルダ（＝ビン）を作成します。②［Practice］等の名前にしておき、先ほど使った3つの画像を入れておきましょう。次に③右クリック→［新規Fusionコンポジション］をクリックします
- [![](https://cgworld.jp/regular/images/38912vfx/vol02/B05.png)](https://cgworld.jp/regular/images/38912vfx/vol02/B05.png)
- ◀ 【4】 ［新規Fusionコンポジション］を作成する画面が開いたら、今回の映像の長さは2秒なので［長さ］には"00:00:02:00"と入力し、［クリップ名］はお好きな名前（ここでは38912VFX\_Compとしました）に、［フレームレート］は"24"になっていることを確認します
- [![](https://cgworld.jp/regular/images/38912vfx/vol02/B06.png)](https://cgworld.jp/regular/images/38912vfx/vol02/B06.png)
- ◀ 【5】 新しくできたFusionコンポジションの雷アイコンのあたりをダブルクリックして開きます（開くまで数秒かかることがあります）。開くと、下のノードグラフは［MediaOut］ノードのみになっているはずです
  

〈Step 2〉ビューイング用ノードの追加

- [![](https://cgworld.jp/regular/images/38912vfx/vol02/B07.png)](https://cgworld.jp/regular/images/38912vfx/vol02/B07.png)
- ◀ 【6】 ［Ctrl+Space］でノードの検索窓が出ます。①検索枠に"occ"と入力し、②リストから［OCIO Colorspace（OCC）］を選択します。③右下の［Add］を押してノードグラフに追加します
- [![](https://cgworld.jp/regular/images/38912vfx/vol02/B08.png)](https://cgworld.jp/regular/images/38912vfx/vol02/B08.png)
- ◀ 【7】 ［MediaOut1］ノードの出力ソケット（白い四角）から線を伸ばし、［OCIOColorspace1］ノードの「黄色」の三角の入力ソケットに接続します
- [![](https://cgworld.jp/regular/images/38912vfx/vol02/B09.png)](https://cgworld.jp/regular/images/38912vfx/vol02/B09.png)
- ◀ 【8】 追加した［OCIOColorspace1］ノードを選択すると、画面の右上にプロパティが表示されます。［OCIO Config→Browse］で記事のはじめにGitHubからダウンロードしたaces\_1.0.3フォルダ内の［config.ocio］を開きます。［Source Space］は［ACES-ACEScg］にします（リストの一番上の方にあります）。［Output Space］は［Output-sRGB］にします（上の方から探すと見つけやすいはずです）

カラースペースの選択はリストが多く探すのが大変ですが、リストを開いた状態で頭文字を打つことでジャンプ移動できます。例えば、リストを開き"O"と入力すれば"O"から始まるリストに飛ぶので、何度か"O"キーを押して"Output -sRGB"を探すこともできます。

  

〈Step 3〉入力カラースペース変換用ノードの追加

[![](https://cgworld.jp/regular/images/38912vfx/vol02/B10.png)](https://cgworld.jp/regular/images/38912vfx/vol02/B10.png)

▲ 【9】 ［OCIOColorspace1］ノードを選択し、［Ctrl+C］と［Ctrl+V］でコピー＆ペーストします。どこかに繋がった状態でコピーされてしまった場合、［Shift］キーを押しながらノードを移動することで切り離すことができます。今度はコピーした［OCIOColorspace1\_1］の出力ソケットを［MediaOut1］ノードの入力ソケットに接続します

- [![](https://cgworld.jp/regular/images/38912vfx/vol02/B11_v2.png)](https://cgworld.jp/regular/images/38912vfx/vol02/B11_v2.png)
- ◀ 【10】 コピーした［OCIOColorspace1\_1］ノードの［Output Space］は［ACES- ACEScg］にします。その上の［Source Space］は素材ごとに変える必要がありますが、ひとまずこのままにしておきます

[![](https://cgworld.jp/regular/images/38912vfx/vol02/B12.png)](https://cgworld.jp/regular/images/38912vfx/vol02/B12.png)

▲ 【11】 ノードの名前がわかりにくいので、ノードの表示名を右クリック→［Rename...］で変更します。左のノードは「InputTransform」に、右下のノードは「ViewingTransform」にしました

［Ctrl+S］でプロジェクトを保存しておきましょう。

  

〈Step 4〉素材の入力設定

[![](https://cgworld.jp/regular/images/38912vfx/vol02/B13.png)](https://cgworld.jp/regular/images/38912vfx/vol02/B13.png)

▲ 【12】 左上のメディアプール上で右クリック→［メディアの読み込み］で配布素材の［Footage］フォルダ内の3つの素材を読み込みます。実写映像［38912\_SampleFootageB\_ACEScg\_##.exr］はフォルダ内の全ての連番画像を選択して読み込むと1つの映像として読み込まれます

[![](https://cgworld.jp/regular/images/38912vfx/vol02/B14.png)](https://cgworld.jp/regular/images/38912vfx/vol02/B14.png)

▲ 【13】 読み込んだ素材の上で右クリック→［ACE入力トランスフォーム→ACEScg］を選択します。一番下にあるはずです。3つともそれぞれ同じ設定をします。今回のワークフローでは、これはどの素材でも同じACEScgにしてください

  

〈Step 5〉ビューアの設定

[![](https://cgworld.jp/regular/images/38912vfx/vol02/B15_v2.png)](https://cgworld.jp/regular/images/38912vfx/vol02/B15_v2.png)

▲ 【14】 実写素材［38912\_SampleFootageB\_ACEScg\_\[01-48\].exr］をメディアプールからノードグラフにドラッグ＆ドロップし、画像のように［InputTransform］ノードの前に接続します

追加した［MediaIn1］ノードと［InputTransform］ノードは常にセットで扱います。今回、実写素材の色空間はACEScgなので、［InputTransform］ノードの［Source Space］プロパティは変えず、先ほどの［ACEScg］のままで問題ありません。

[![](https://cgworld.jp/regular/images/38912vfx/vol02/B16.png)](https://cgworld.jp/regular/images/38912vfx/vol02/B16.png)

▲ 【15】 ノードグラフ右下の［ViewingTransform］ノードを選択し、キーボードの［1］キーを押します。左に新しくプレビューが表示されたはずですが、実は2つのビューはどちらも色が正しい状態ではありません

[![](https://cgworld.jp/regular/images/38912vfx/vol02/B17.png)](https://cgworld.jp/regular/images/38912vfx/vol02/B17.png)

▲ 【16】 2箇所あるグリッドアイコンの［ビューLUT］のアイコンをクリックしてをOFFにします。一瞬違和感を感じるかもしれませんが、この左のビューが正常な色です。右側のビューはきつい色になったはずですが、いったん無視してください

[![](https://cgworld.jp/regular/images/38912vfx/vol02/B18.png)](https://cgworld.jp/regular/images/38912vfx/vol02/B18.png)

▲ 【17】 ［MediaOut］ノードを選択し［2］キーを押すと右のプレビューが非表示になります

このように各ノードを選択した状態で数字キーを押すとそのノードの段階のプレビューがトグルで表示され、［1］キーは左のビューに、［2］キーは右のビューに対応しています。今回は基本的に最後の［ViewingTransform］ノードを［1］プレビューするようにします。プロジェクトを開き直したり、下のタブを行き来するとプレビューのノードが変わることがあるため、適宜［ViewingTransform］ノードがプレビューされているか確認してください。

これで色空間の設定は完了です。［Ctrl+S］でプロジェクトの保存をお忘れなく。

  

【理論】なぜこうするの？

「色空間（Color Space）」をザックリ説明すると、「色」というふわふわしたものをビシッと「数値」でどう表現するかを決めたもの、なのですが......これが実際はかなり難解です。今回の設定内容にはもちろん全て理由があります。ですが、きちんと説明するにはもう1、2本記事が必要になってしまうので、今回はひとまず「合成するためにはまず色空間（色の規格）を揃える必要がある」と覚えておいてください。今回はVFXをする上で便利な 「ACEScg」 という色空間で揃えています。

[![](https://cgworld.jp/regular/images/38912vfx/vol02/B19_v2.png)](https://cgworld.jp/regular/images/38912vfx/vol02/B19_v2.png)

ちょっと難しいですが、今回はあらゆる色空間の素材をはじめの［InputTransform］ノードで「ACEScg」という色空間に変換し、その色空間の中でコンポジット（合成）しています。最終的に［ViewingTransform］ノードで「ACEScg」色空間から一般的なモニタ向けの「sRGB」色空間に変換しモニタに表示しています。

今回、OCIOノード（Transformと名前をつけた2つのノード）で一括管理するため、〈Step 4〉ではFusionの作業カラースペースである「ACEScg」にすることで標準の色変換を無効化し、〈Step 5〉では標準のビューLUTをOFFにしています。......何を言ってるのかさっぱりでも大丈夫です。

「いちいちなんでこんな面倒なことをするんだろう!!!」と思った方もいるかもしれません。確かに最初に練習したCG画像の合成では、ここまでの設定はせずとも画が完成していました。ですが、CGだけでなく実写やマットペイントなど、あらゆる素材を組み合わせて1つの画にするVFXにおいては「色空間」は全てを支える「土台」です。

「色空間」を管理しないと全て自分の感覚で素材を馴染ませて合成する必要がありますが、「色空間」さえ管理しておけば合成をかなり理論的に考えることができるようになります。その他にもソフトウェア間で色のズレをなくしたり、モニターの色空間もキャリブレーションすることでどのデバイスからも同じ見た目で表示できるなどのメリットがあります。

とにかく 「合成するためにはまず色空間（色の規格）を揃える必要がある」 これだけ覚えておいてください！　今回作成した［InputTransform］ノードのプロパティ［Source Space］は素材の色空間によって変える必要がありますが、その他の設定は他のプロジェクトでも同じように使用できます。

## Point！　素材別 Input TransformのSource Spaceの選び方

▶ 一般的な画像や無加工のスマホの動画などで色空間が不明な場合、［Source Space］は［Utility-sRGB-Texture］にすると良いはずです。

▶ CGのレンダリングは、Blenderの場合OpenEXRで書き出し、［Utility-Linear-sRGB］を選択します。これは他の多くのソフトでも同様ですが、各ソフトのマニュアルや環境設定のカラーマネジメントの項目をご確認ください。

▶ ［Source Space］のリストに撮影で使用したカメラメーカーと記録形式があればそのInputを使用します。（例：Input-GoPro-Curve-Protune Flat）

▶ Log撮影ができるカメラであれば、Logで撮影して［Source Space］から使用したLog形式のInputを選択します。Logの色が淡いからとコントラスト調整で色をいじるのはVFXではご法度です。（例：Input-Sony-S-Log1-S-Gamut）

▶ RAWで撮った場合、現像時にカラースペースを指定し、それに合わせて［Source Space］を選びます。例えばBMPCC4Kであれば、DaVinci Resolveで現像時に［プロジェクト設定→カラーマネジメント→ACES出力デバイストランスフォーム］で任意のカラースペースを選択し、EXR （RGB half）等でレンダリングするようにします。

[次ページ：  
02：背景を「キーイング」してみよう！](https://cgworld.jp/regular/202104-38912vfx-02-3.html)

\[\[SplitPage\]\]

## 02：背景を「キーイング」してみよう！

[![](https://cgworld.jp/regular/images/38912vfx/vol02/C01_v2.png)](https://cgworld.jp/regular/images/38912vfx/vol02/C01_v2.png)

「キーイング」 とは、色や明暗の差などから映像の一部を抜き取る技術です。よく映画のメイキングなどで緑の背景（グリーンバック）で撮影しておき、そこにCGを合成、というのを見かけますよね。それを実際にやってみます。

  

【実践】よくわからなくてもOK！　まずは手順通り触ってみよう！

〈Step 0〉Delta Keyer ノードを配置する

- [![](https://cgworld.jp/regular/images/38912vfx/vol02/C02.png)](https://cgworld.jp/regular/images/38912vfx/vol02/C02.png)
- ◀ 【1】 ［Ctrl+Space］でノード検索窓を表示します。検索窓に"dk"と入力し、［Delta Keyer (DK)］を選択して、［Add］（もしくは［Enter］キー）してください
- [![](https://cgworld.jp/regular/images/38912vfx/vol02/C03.png)](https://cgworld.jp/regular/images/38912vfx/vol02/C03.png)
- ◀ 【2】 ノードグラフに新しい［DeltaKeyer1］ノードが追加されました。何かに繋がった状態で追加された場合は、［Shift］を押しながらドラッグして周りと切り離します。何やらたくさん入力ソケット（色とりどりの三角）がありますね

[![](https://cgworld.jp/regular/images/38912vfx/vol02/C04.png)](https://cgworld.jp/regular/images/38912vfx/vol02/C04.png)

▲ 【3】 このように、［DeltaKeyer1］ノードを［InputTransform］ノードの次に設置します。［Shift］を押しながらノードを線の上にもっていくと割り込ませることができます。［DeltaKeyer1］の「黄色」の入力ソケットに線が繋がっていることを確認してください

  

〈Step 1〉キーイングカラーを指定する

- [![](https://cgworld.jp/regular/images/38912vfx/vol02/C05.png)](https://cgworld.jp/regular/images/38912vfx/vol02/C05.png)
- ◀ 【4】 ［DeltaKeyer1］ノードを選択すると、画面右側にこのようなプロパティが表示されます。［Background Color］横のスポイトアイコンを掴んだままドラッグすると、画面上でキーイングカラー（＝透過する色）をピックできます

[![](https://cgworld.jp/regular/images/38912vfx/vol02/C06.png)](https://cgworld.jp/regular/images/38912vfx/vol02/C06.png)

▲ 【5】 スポイトをビューまでドラッグして、顔の近くのグリーンバック上で色をピックします。何度かピックして一番綺麗に透過される色を探します。グリーンバックがある程度抜けて透明になりました（チェッカー模様は透明な部分を表しています）

キーイングカラーは抜きたい対象（被写体）の近くで最も綺麗に抜ける色を取るのが一般的です。ビューはノードグラフ同様、マウスの中ボタンドラッグで前後左右の移動、［Ctrl+ホイール］でズームできます。

[![](https://cgworld.jp/regular/images/38912vfx/vol02/C07.png)](https://cgworld.jp/regular/images/38912vfx/vol02/C07.png)

▲ 【6】 最後の［ViewingTransform］ノードを選択した状態で［2］キーを押し、右のビューに映像を表示します。右ビューの上部にある3つの円が重なった［Color］アイコンをクリックし、Alpha表示にします

表示した右のビューでは白が不透明、黒が透明であることを表しています。まだ背景には白く残っている部分があり、人物は黒く透けてしまっている部分があります。次のステップからこれを改善していきます。

  

〈Step 2〉Clean Plate ノードの設置

- [![](https://cgworld.jp/regular/images/38912vfx/vol02/C08.png)](https://cgworld.jp/regular/images/38912vfx/vol02/C08.png)
- ◀ 【7】 ［Ctrl+Space］でノード検索窓を表示します。検索窓に"cpl"（最後のlは小文字のLです）と入力し、［Clean Plate(CPl)］を選択して、［Add］（もしくは［Enter］キー）してください

[![](https://cgworld.jp/regular/images/38912vfx/vol02/C09.png)](https://cgworld.jp/regular/images/38912vfx/vol02/C09.png)

▲ 【8】 ［CleanPlate1］ノードが追加されたら、右下の［ViewingTransform］ノードを［Ctrl+C］と［Ctrl+V］でコピー＆ペーストし、［CleanPlate1］の次に接続します

[![](https://cgworld.jp/regular/images/38912vfx/vol02/C10.png)](https://cgworld.jp/regular/images/38912vfx/vol02/C10.png)

▲ 【9】 ①［CleanPlate1］ノードと［InputTransform］ノードを接続します。②［ViewingTransform\_1］を選択した状態で［2］キーを押して右側のビューに表示します。一瞬右のビューが白くなりますが、焦らず③右ビュー上部の先ほどクリックしたアイコンを再びクリックし、［Alpha］ビューから［Color］ビューに戻します。このような表示になるはずです

[![](https://cgworld.jp/regular/images/38912vfx/vol02/C11.png)](https://cgworld.jp/regular/images/38912vfx/vol02/C11.png)

▲ 【10】 ［CleanPlate1］を選択し、右側のプロパティで今度はグリーンバックのみを抽出します。余計な色がフチなどに残らないようにしながら、ギリギリまで背景を抽出できる値を試行錯誤しながら探っていきます。今回は上記の値が最も良い結果を得られたので、この数値を入力してください

今回は使用していませんが、プロパティ一番上の［Method］を［Color］から［Ranges］にすると、ビュー上で四角く選択した範囲の背景を抽出することもできます。これらのプロパティは撮影時のライティングや被写体の色などによって最適な値が変わるため、素材ごとに試行錯誤して良い値を探していきます。

[![](https://cgworld.jp/regular/images/38912vfx/vol02/C12.png)](https://cgworld.jp/regular/images/38912vfx/vol02/C12.png)

▲ 【11】 次に［Grow Edges］の値を上げ、［Fill］にチェックを入れて穴を埋めます。ここで明らかにグリーンバック以外の色が載っている場合は前のプロパティの値を見直してください。先ほどの数値通りであれば、おおよそこのような見た目になるはずです

これでClean Plate＝緑の背景のみの映像が出来上がりました。

[![](https://cgworld.jp/regular/images/38912vfx/vol02/C13.png)](https://cgworld.jp/regular/images/38912vfx/vol02/C13.png)

▲ 【12】 最後に、［CleanPlate1］ノードの出力ソケットと、［DeltaKeyer1］ノードの「ピンク」の入力ソケット（CleanPlateソケット）を接続します

[![](https://cgworld.jp/regular/images/38912vfx/vol02/C14.png)](https://cgworld.jp/regular/images/38912vfx/vol02/C14.png)

▲ 【13】 先ほどと同様右下の［ViewingTransform］ノードを選択した状態で［2］キーを押し、右ビューの上のアイコンからAlpha表示にすることで透過具合を見ることができます。前景が透けているのはそのままですが、背景は綺麗に抜けていることがわかります

［Ctrl+S］でプロジェクトの保存をしておきましょう。

  

〈Step 3〉マットを調整する

- [![](https://cgworld.jp/regular/images/38912vfx/vol02/C15.png)](https://cgworld.jp/regular/images/38912vfx/vol02/C15.png)
- ◀ 【14】 もう少し細かい調整に入るので、ビューを変えます。［DeltaKeyer1］を選択し、画面右側のプロパティから［View Mode］を［Status］に変更します

[![](https://cgworld.jp/regular/images/38912vfx/vol02/C16.png)](https://cgworld.jp/regular/images/38912vfx/vol02/C16.png)

▲ 【15】 ［Status］ビューでは、黒が透過、暗いグレーが半透明、明るいグレーが不透明であることを示しています。前景に半透明な部分が多く、透けてしまっていることがわかります

[![](https://cgworld.jp/regular/images/38912vfx/vol02/C17.png)](https://cgworld.jp/regular/images/38912vfx/vol02/C17.png)

▲ 【16】 タイムラインから5フレーム目に移動します

- [![](https://cgworld.jp/regular/images/38912vfx/vol02/C18.png)](https://cgworld.jp/regular/images/38912vfx/vol02/C18.png)
- ◀ 【17】 ［DeltaKeyer1］のプロパティの、［Matteタブ→Threshold］の範囲を変えてみます。［High］の値を下げると前景の不透明部分が減り、［Low］の値を上げると背景の不透明部分が減ります。［Clean Foreground］の値を上げると前景のマットが滑らかになり、［Clean Background］の値を上げると背景のマットが滑らかになります。数値をいじって一通り試してみたら、元に戻します
- [![](https://cgworld.jp/regular/images/38912vfx/vol02/C19.png)](https://cgworld.jp/regular/images/38912vfx/vol02/C19.png)
- ◀ 【18】 ［Clean Background］の値を"0.001"に上げ、［Threshold→Low］の値を"0.1"に上げます。値を入力したあとは、［Enter］もしくは何もない場所をクリックして決定します。背景に残っていた暗いグレーの部分（不透明部分）が消えました
- [![](https://cgworld.jp/regular/images/38912vfx/vol02/C20.png)](https://cgworld.jp/regular/images/38912vfx/vol02/C20.png)
- ◀ 【19】 ［CleanForeground］の値を"0.001"に上げ、［Threshold→High］の値を少しずつ下げていきます。前景の暗いグレーの部分（不透明部分）が消えていきます。しかし、前景の半透明部分が完全になくなるまで［Threshold］の値を下げると、右手のブレた部分も完全な不透明になってしまいました。また、緑は色かぶりの補正で質が落ちている箇所を示しています
- [![](https://cgworld.jp/regular/images/38912vfx/vol02/C21.png)](https://cgworld.jp/regular/images/38912vfx/vol02/C21.png)
- ◀ 【20】 プロパティ一番上の［View Mode］を［Final Result］に変更して見てみます。一見良さそうに見えますが、よく見ると右手のブレているところのエッジが硬すぎて不自然な見た目になってしまいました。「ブレ」の部分は背景が透けて見えるはずです
- [![](https://cgworld.jp/regular/images/38912vfx/vol02/C22.png)](https://cgworld.jp/regular/images/38912vfx/vol02/C22.png)
- ◀ 【21】 ［Threshold→High］の値を1.0に戻します
  

〈Step 4〉リファレンスカラーの指定

この問題は、衣装の色かぶりが原因です。今回はリファレンスカラーを使用して、この問題を改善します。

- [![](https://cgworld.jp/regular/images/38912vfx/vol02/C23.png)](https://cgworld.jp/regular/images/38912vfx/vol02/C23.png)
- ◀ 【22】 ［Keyタブ→Reference］の色指定によって、色かぶりで抜けてしまった部分を取り戻すことができます
- [![](https://cgworld.jp/regular/images/38912vfx/vol02/C24.png)](https://cgworld.jp/regular/images/38912vfx/vol02/C24.png)
- ◀ 【23】 ［Reference］の右のスポイトを使って右腕の服の袖あたりの明るい色をピックしてみます。同じ値にしたい場合は画像に表示されているRGB値を［Reference］の下の数値欄に直接入力してください

[![](https://cgworld.jp/regular/images/38912vfx/vol02/C25.png)](https://cgworld.jp/regular/images/38912vfx/vol02/C25.png)

▲ 【24】 プロパティ上の［View Mode］を［Status］にしてみると、服の暗いグレーが減りつつ、右手のブレた部分は先ほどよりも残っていることがわかります

- [![](https://cgworld.jp/regular/images/38912vfx/vol02/C26.png)](https://cgworld.jp/regular/images/38912vfx/vol02/C26.png)
- ◀ 【25】 ［Matteタブ→Threshold→High］の値を下げ、服の上の暗いグレー（半透明部分）が全てなくなるギリギリの値を探します。先ほどより値を下げなくても全ての暗いグレー（半透明部分）が消えるはずです
- [![](https://cgworld.jp/regular/images/38912vfx/vol02/C27.png)](https://cgworld.jp/regular/images/38912vfx/vol02/C27.png)
- ◀ 【26】 プロパティ一番上の［View Mode］を［Final Result］にして見てみましょう。ブレた手の半透明部分をある程度残したまま前景を不透明にすることができました
  

〈Step 5〉エッジの調整

- [![](https://cgworld.jp/regular/images/38912vfx/vol02/C28.png)](https://cgworld.jp/regular/images/38912vfx/vol02/C28.png)
- ◀ 【27】 最後に［Matte→Erode/Dilate］の値を"-0.0006"にします。エッジが若干内側に食い込み、細かい違いですが馴染みが良くなりました

ここまできたら［Ctrl+S］でプロジェクトを保存しておきましょう。

  

【理論】なぜこうするの？

そもそもなぜ背景が緑なのでしょうか。これはコンピュータは画像をRGB（赤・緑・青）で処理するため、RGBのいずれかに偏っていたほうが画像の処理がしやすいというのが一番の理由です。そして赤よりも人の色に被りにくく青よりも明るく撮りやすいため、緑がよく選ばれます。しっかりとした照明環境があれば、青（ブルーバック）の方が良い場面もあります。

今回のノードでは読み込まれた映像素材はまず［CleanPlate1］ノードと［DeltaKeyer1］ノードにながれています。［CleanPlate1］ノードでグリーンバックのみの映像を作った上で、［DeltaKeyer1］ノードでそのグリーンバックのみの映像と、元の映像素材を比較して色を抜いているというながれです。ノードで見るとシンプルですね。

ちなみに今回紹介したキーイングの方法はあくまで一例です。他にも被写体のうち絶対に不透明な内側の「芯」と、ブレや髪の毛など半透明な部分がある「フチ」を分けてキーイングして組み合わせる方法や、映像素材に合わせてもっと柔軟にいくつかのキーイングノードを組み合わせていく方法など、様々なアプローチがあります。今回使用したDeltaKeyerはあらゆる機能が入った万能キーヤーですが、慣れてきたら他のノードを組み合わせてみるのもオススメです。

## Point！ グリーンバック撮影のコツ

実は今回、実用的な練習のためにあえてキーイングしづらい照明と衣装で素材を撮影しています。実際には以下の点に気をつけて撮影すべきです。

▶ グリーンバックは色が均等になるように、十分な明るさの照明を当てる

▶ 被写体にグリーンバックの緑色が被らないように距離を置いたり、黒幕等でライティングをコントロールする

......とはいえ、個人制作で十分な光量の撮影用照明を買い揃えたり、自由に配置できる広いスペースを確保するのはなかなか難しいですよね。そこでClean Plateによって不均等な照明下の素材でも綺麗に抜いたり、リファレンスカラーによって色かぶりが強い素材でも比較的綺麗に抜く方法を紹介しました。予算があれば先に照明等の撮影環境を工夫すべきなので、これらの機能は本当は使わないのが理想です。

また、カメラや記録フォーマットによってもクオリティは変わってきます。今回はRAW撮影ができるBlackmagic Pocket Cinema Camera 4K というシネマカメラで撮影していますが、スマホや一般的なデジカメで撮影した素材は圧縮がかかっており、綺麗に抜くのが難しい場合が多いです。ものによっては後処理である程度改善できたりもしますが、かなり上級者向けかつ大きくクオリティが上がるわけではないので、今回は説明を省いています。

Log撮影ができるカメラがあれば、Logで撮るのもオススメです。Log撮影は対数で上手く色情報を濃縮し保存しているので、通常のビデオ撮影よりも良い結果が出せます。Logで撮った映像素材を使う際は、今回作成した［InputTransform］ノードの［Source Space］プロパティから使用したLog形式のInputを選択します。

[次ページ：  
03：「マスク」を切ってみよう！](https://cgworld.jp/regular/202104-38912vfx-02-4.html)

\[\[SplitPage\]\]

## 03：「マスク」を切ってみよう！

[![](https://cgworld.jp/regular/images/38912vfx/vol02/D01_v2.png)](https://cgworld.jp/regular/images/38912vfx/vol02/D01_v2.png)

次に 「マスク」 を切ります。「マスク」では、手作業で映像を切り抜き、どこを透明にするか・どこを不透明にするのかを決めていきます。

  

【実践】よくわからなくてもOK！まずは手順通り触ってみよう！

〈Step 0〉ポリゴンノードの追加

- [![](https://cgworld.jp/regular/images/38912vfx/vol02/D02.png)](https://cgworld.jp/regular/images/38912vfx/vol02/D02.png)
- ◀ 【01】 ［Ctrl+Space］で検索窓に"poly"と入力し、［Polygon(Ply)］を選択して、［Add］（もしくは［Enter］キー） してください
- [![](https://cgworld.jp/regular/images/38912vfx/vol02/D03.png)](https://cgworld.jp/regular/images/38912vfx/vol02/D03.png)
- ◀ 【02】 ［Polygon1］ノードが追加され、ビューの上に何やらツール群が表示されました。左のビュー右上の四角アイコンを押して、シングルビュー化することで作業スペースを大きくします

[![](https://cgworld.jp/regular/images/38912vfx/vol02/D04.png)](https://cgworld.jp/regular/images/38912vfx/vol02/D04.png)

▲ 【03】 ビューを拡大し、透けてしまっている机を表示します。［Polygon1］ノードを選択し、ビュー上部のツール群の中の万年筆アイコンが選ばれていることを確認します

  

〈Step 1〉ソリッドマスクの追加

- [![](https://cgworld.jp/regular/images/38912vfx/vol02/D05.png)](https://cgworld.jp/regular/images/38912vfx/vol02/D05.png)
- ◀ 【04】 ビュー上でクリックすることで、ベジェ曲線の赤いパス（線）を引くことができます
- [![](https://cgworld.jp/regular/images/38912vfx/vol02/D06.png)](https://cgworld.jp/regular/images/38912vfx/vol02/D06.png)
- ◀ 【05】 ベジェ曲線の簡単な操作方法については早見表を作りましたので、ご活用ください。画像をクリックすると大きなサイズで表示されます

[![](https://cgworld.jp/regular/images/38912vfx/vol02/D07.png)](https://cgworld.jp/regular/images/38912vfx/vol02/D07.png)

▲ 【06】 図のように透明部分をぐるっと覆うようにパスを引きます。右側の机のフチ以外はざっくりで問題ありません。最後に引き始めたポイントに戻って線を一周して繋げます。すると、自動的に左上のツールがカーソルアイコンになり、パスを微調整できるモードに入ります。机の右のフチにピッタリ線が重なるように調整します（画像のパスは、説明のため色と太さを変えています）

[![](https://cgworld.jp/regular/images/38912vfx/vol02/D08.png)](https://cgworld.jp/regular/images/38912vfx/vol02/D08.png)

▲ 【07】 ［Polygon1］ノードを［DeltaKeyer1］の「白色」の入力ソケット（Solid Maskソケット）と接続します。「グレー」の入力ソケット（GarbageMattteソケット）と見間違えやすいので注意してください

[![](https://cgworld.jp/regular/images/38912vfx/vol02/D09.png)](https://cgworld.jp/regular/images/38912vfx/vol02/D09.png)

▲ 【08】 接続すると、このように先ほど囲った机の透過がなくなりました

  

〈Step 2〉ガベージマスクの追加

- [![](https://cgworld.jp/regular/images/38912vfx/vol02/D10.png)](https://cgworld.jp/regular/images/38912vfx/vol02/D10.png)
- ◀ 【09】 ［Ctrl+Space］から、先ほどと同じように、［Polygon(Ply)］ノードをもう1つ追加します

[![](https://cgworld.jp/regular/images/38912vfx/vol02/D11.png)](https://cgworld.jp/regular/images/38912vfx/vol02/D11.png)

▲ 【10】 今度はこのように、左上の消したい部分をパスで囲みます。右側はグリーンバックに食い込んでいればザックリで問題ありません

[![](https://cgworld.jp/regular/images/38912vfx/vol02/D12.png)](https://cgworld.jp/regular/images/38912vfx/vol02/D12.png)

▲ 【11】 今回の［Polygon2］ノードは［DeltaKeyer1］の「グレー」の入力ソケット（GarbageMatteソケット）と接続します

[![](https://cgworld.jp/regular/images/38912vfx/vol02/D13.png)](https://cgworld.jp/regular/images/38912vfx/vol02/D13.png)

▲ 【12】 ディスプレイの後ろが透過されました

このように、［DeltaKeyer1］の「白色」の入力ソケット（Solid Maskソケット）には残したい部分を囲うマスクを接続することで、その部分が不透明になります。「グレー」の入力ソケット（GarbageMattteソケット）には消したい部分を囲うマスクを接続することで、その部分が透明になります。

  

〈Step 3〉マスクの追加

[![](https://cgworld.jp/regular/images/38912vfx/vol02/D14.png)](https://cgworld.jp/regular/images/38912vfx/vol02/D14.png)

▲ 【13】 ［Polygon］ノードを追加して、前の［Polygon］ノードの「青」の入力ソケット（Effect Maskソケット）に接続することで、マスクを追加していくことができます。気力のある方は画像を参考に追加してみてください。透明にしたい箇所はグレーの線で、不透明にしたい部分には白の線で表示しています

適宜［Ctrl+S］でプロジェクトを保存するのをお忘れなく。

  

【理論】なぜこうするの？

VFXでは、このマスクはよく使います。今回のように要らない部分を切り抜いたり、一部だけ明るさを変えるのに使ったり、用途は様々です。

さらに動く実写に合わせマスクにアニメーションをつける 「ロトスコープ」 を使う場面も多いです。グリーンバックが使えないカットや、グリーンバックからはみ出したところを「ロトスコープ」したりします。

[次ページ：  
04：「マージ」ノードで素材を合成してみよう！](https://cgworld.jp/regular/202104-38912vfx-02-5.html)

\[\[SplitPage\]\]

## 04：「マージ」ノードで素材を合成してみよう！

[![](https://cgworld.jp/regular/images/38912vfx/vol02/E01_v2.png)](https://cgworld.jp/regular/images/38912vfx/vol02/E01_v2.png)

いよいよ実写素材とCG素材を組み合わせます。

  

【実践】よくわからなくてもOK！まずは手順通り触ってみよう！

〈Step 0〉素材の入力ノード

[![](https://cgworld.jp/regular/images/38912vfx/vol02/E02.png)](https://cgworld.jp/regular/images/38912vfx/vol02/E02.png)

▲ 【01】 ［MediaIn1］ノードの次の［InputTransform］ノードをコピー＆ペーストしておきます

[![](https://cgworld.jp/regular/images/38912vfx/vol02/E03.png)](https://cgworld.jp/regular/images/38912vfx/vol02/E03.png)

▲ 【02】 コピー＆ペーストした［InputTransform\_1］ノードのプロパティの［Source Space］を［Utility-Linear-sRGB］にします。リストを開いて［U］キーを押すと見つけやすいはずです

- [![](https://cgworld.jp/regular/images/38912vfx/vol02/E04.png)](https://cgworld.jp/regular/images/38912vfx/vol02/E04.png)
- ◀ 【03】 CG素材［38912\_CGB\_linsrgb.exr］をメディアプールからノードグラフにドラッグ＆ドロップし、先ほどコピー＆ペーストした［InputTransform\_1］ノードに接続します
  

〈Step 1〉CG画像を合成する

[![](https://cgworld.jp/regular/images/38912vfx/vol02/E05.png)](https://cgworld.jp/regular/images/38912vfx/vol02/E05.png)

▲ 【04】 ［DeltaKeyer1］ノードの出力ソケットと［InputTransform\_1］ノードの出力ソケットを接続します

[![](https://cgworld.jp/regular/images/38912vfx/vol02/E06.png)](https://cgworld.jp/regular/images/38912vfx/vol02/E06.png)

▲ 【05】 接続すると［Merge1］ノードが自動で追加されます。ノードがごちゃごちゃしてしまうので、画像のようにノードの位置を動かして整理してください。［Merge1］ノードの出力ソケットと、［MediaOut1］ノードの「黄色」の入力ソケットを接続します

[![](https://cgworld.jp/regular/images/38912vfx/vol02/E07.png)](https://cgworld.jp/regular/images/38912vfx/vol02/E07.png)

▲ 【06】 CGと実写が合成されました

  

〈Step 2〉マットペイントを合成する

- [![](https://cgworld.jp/regular/images/38912vfx/vol02/E08.png)](https://cgworld.jp/regular/images/38912vfx/vol02/E08.png)
- ◀ 【07】 先ほどと同様にメデイアプールからマット［38912\_MattePaintB\_srgb.jpg］を読み込みます。最初の［MediaIn1］の隣の［InputTransform］をもうひとつコピー＆ペーストし、［MediaIn3］と接続します

[![](https://cgworld.jp/regular/images/38912vfx/vol02/E09_v2.png)](https://cgworld.jp/regular/images/38912vfx/vol02/E09_v2.png)

▲ 【08】 ［InputTransform\_2］ノードのプロパティ［Source Space］は［Utility-sRGB-Texture］にします

[![](https://cgworld.jp/regular/images/38912vfx/vol02/E10.png)](https://cgworld.jp/regular/images/38912vfx/vol02/E10.png)

▲ 【09】 ①［Merge1］ノードの出力ソケットと［InputTransform\_2］の出力ソケットを接続し、②追加された［Merge2］ノードを［MediaOut1］ノードの「黄色」の入力ソケットに接続します

[![](https://cgworld.jp/regular/images/38912vfx/vol02/E11.png)](https://cgworld.jp/regular/images/38912vfx/vol02/E11.png)

▲ 【10】 マットペイントが合成されましたが、上下にはみ出てしまいました。これは、Fusionでは最も後ろの画像のサイズが出力サイズになるためです

[![](https://cgworld.jp/regular/images/38912vfx/vol02/E12.png)](https://cgworld.jp/regular/images/38912vfx/vol02/E12.png)

▲ 【11】 ［Ctrl+Space］でノード検索窓を開き、［Crop(Crp)］ノードを検索し追加します。［InputTransform\_2］ノードと［Merge2］ノードの間に［Shift］キーを押しながらドラッグで割り込ませます

[![](https://cgworld.jp/regular/images/38912vfx/vol02/E13.png)](https://cgworld.jp/regular/images/38912vfx/vol02/E13.png)

▲ 【12】 画像が元のFull HDサイズ（1,920×1,080）に戻りました

- [![](https://cgworld.jp/regular/images/38912vfx/vol02/E14.png)](https://cgworld.jp/regular/images/38912vfx/vol02/E14.png)
- ◀ 【13】 ［Ctrl+Space］で検索し［Transform(Xf)］ノードを追加します。［InputTransform\_2］ノードと［Crop1］ノードの間に［Shift］を押しながら割り込ませると、マットペイントの位置やスケールを自由に変えることができます

［Ctrl+S］でプロジェクトを保存しておきましょう。

  

【理論】なぜこうするの？

今回、単純に重ねただけでもある程度自然に合成できているように見えます。これは土台として色空間が合っていて、かつCGのライティングを実写のライティングに合わせてレンダリングしているためです。

## 05：素材の「色合わせ」をしてみよう！

[![](https://cgworld.jp/regular/images/38912vfx/vol02/F01_v2.png)](https://cgworld.jp/regular/images/38912vfx/vol02/F01_v2.png)

素材と素材の色を合わせて合成を馴染ませていきます。

  

【実践】よくわからなくてもOK！まずは手順通り触ってみよう！

〈Step 0〉明るさプレビュー用のノード

- [![](https://cgworld.jp/regular/images/38912vfx/vol02/F02.png)](https://cgworld.jp/regular/images/38912vfx/vol02/F02.png)
- ◀ 【1】 まず、プレビューの明るさを変えるためのノードを設置します。［Ctrl+Space］から新しく［Brightness/Contrast （BC）］ノードを検索して追加し、ノードの最後の［MediaOut1］ノードと［ViewingTransform］ノードの間に割り込ませます

[![](https://cgworld.jp/regular/images/38912vfx/vol02/F03.png)](https://cgworld.jp/regular/images/38912vfx/vol02/F03.png)

▲ 【2】 追加した［BrightnessContrast1］ノードのプロパティの［Gain］や［Gamma］を変えて、暗いところや明るい箇所が自然に合成されているか確認することができます。空が暗い気がします

［Gain］は明るさ全体を上げ下げするイメージで、［Gamma］は最も明るい点と暗い点を固定したまま中間の明るさだけを上げ下げするイメージです。この2つは、色合わせする際の確認にとても便利です。

  

〈Step 1〉空の露出を合わせる

[![](https://cgworld.jp/regular/images/38912vfx/vol02/F04.png)](https://cgworld.jp/regular/images/38912vfx/vol02/F04.png)

▲ 【3】 新しく［Color Corrector (CC)］ノードを追加し、［Crop1］ノードと［Merge2］ノードの間に割り込ませます

[![](https://cgworld.jp/regular/images/38912vfx/vol02/F05.png)](https://cgworld.jp/regular/images/38912vfx/vol02/F05.png)

▲ 【4】 ［ColorCorrector1］ノードのプロパティ、［Gain］の値を［5］程度まで上げると、窓の外が自然な明るさになりました

  

〈Step 2〉CGの「ブラックポイント」を合わせる

[![](https://cgworld.jp/regular/images/38912vfx/vol02/F06.png)](https://cgworld.jp/regular/images/38912vfx/vol02/F06.png)

▲ 【5】 プレビュー用の［BrightnessContrast1］ノードのGammaを［4.0］くらいに上げてみます。椅子の暗い部分とCGの右の棚の暗い部分をよく見るとわかりますが、実写とCGで 「ブラックポイント（最も暗い点）」 が合っていません。CGの暗部が暗すぎますね

- [![](https://cgworld.jp/regular/images/38912vfx/vol02/F07.png)](https://cgworld.jp/regular/images/38912vfx/vol02/F07.png)
- ◀ 【6】 先ほどと同じように［ColorCorrector］ノードを追加し、［InputTransform\_1］ノードと［Merge1］ノードの間に割り込ませます

[![](https://cgworld.jp/regular/images/38912vfx/vol02/F08.png)](https://cgworld.jp/regular/images/38912vfx/vol02/F08.png)

▲ 【7】 ［ColorCorrector2］ノードのプロパティ、［Lift］の値を［0.004］にすると、実写とCGの「ブラックポイント（最も暗い点）」が合致しました

[![](https://cgworld.jp/regular/images/38912vfx/vol02/F09.png)](https://cgworld.jp/regular/images/38912vfx/vol02/F09.png)

▲ 【8】 ちなみにビュー上にマウスカーソルがあるとき、画面左下にカーソルの位置のRGB値が表示されます。実写とCGで、これが近い値になるように調整していくのがオススメです

- [![](https://cgworld.jp/regular/images/38912vfx/vol02/F10.png)](https://cgworld.jp/regular/images/38912vfx/vol02/F10.png)
- ◀ 【9】 調整が終わったら、プレビュー用の［BrightnessContrast1］の値は右上のリセットアイコンからデフォルト値に戻しておきます

［Ctrl+S］でプロジェクトを保存します。

  

【理論】なぜこうするの？

素材の色を馴染ませるには「露出（明るさ）」「色温度（暖かさ）」「ホワイトポイント（最も明るい点）」「ブラックポイント（最も暗い点）」「彩度（鮮やかさ）」といったものを合わせる必要があります。今回は簡易的に空のマットペイントの「露出」とCGの「ブラックポイント」を実写と合わせました。

[次ページ：  
06：映像に味付けしてみよう！](https://cgworld.jp/regular/202104-38912vfx-02-6.html)

\[\[SplitPage\]\]

## 06：映像に味付けしてみよう！

[![](https://cgworld.jp/regular/images/38912vfx/vol02/G01_v2.png)](https://cgworld.jp/regular/images/38912vfx/vol02/G01_v2.png)

より画に説得力をもたせるために、現実で起こる現象を再現して「味付け」していきます。

  

【実践】よくわからなくてもOK！まずは手順通り触ってみよう！

[![](https://cgworld.jp/regular/images/38912vfx/vol02/G02.png)](https://cgworld.jp/regular/images/38912vfx/vol02/G02.png)

▲ 【1】 新しく［Ctrl+Space］から［Glow(Glo)］ノードを追加し、［MediaOut1］ノードの手前に割り込ませます

[![](https://cgworld.jp/regular/images/38912vfx/vol02/G03.png)](https://cgworld.jp/regular/images/38912vfx/vol02/G03.png)

▲ 【2】 ［Glow1］を選択して、ノードのプロパティから、［Glow Size］は［50］に、［Glow］は［0.0］に、［Blend］は［0.15］に設定してみました

[![](https://cgworld.jp/regular/images/38912vfx/vol02/G04.png)](https://cgworld.jp/regular/images/38912vfx/vol02/G04.png)

▲ 【3】 窓から自然にふんわりと光が広がり、より「明るさ」を感じられるようになりました

  

【理論】なぜこうするの？

グロー効果は空気中の光の拡散やレンズによって起こる「光のにじみ」ですが、これを後処理でつけると「明るさ」を演出することができます。今回「色空間」の設定で「リニアワークフロー」というものになっているので、グローで自然な明るさを表現できます。

## 07：最後に「レンダリング」で書き出そう！

[![](https://cgworld.jp/regular/images/38912vfx/vol02/H01_v2.png)](https://cgworld.jp/regular/images/38912vfx/vol02/H01_v2.png)

最後に映像を書き出します。

  

【実践】よくわからなくてもOK！まずは手順通り触ってみよう！

〈Step 0〉タイムラインに配置する

[![](https://cgworld.jp/regular/images/38912vfx/vol02/H02.png)](https://cgworld.jp/regular/images/38912vfx/vol02/H02.png)

▲ 【1】 画面最下部の［エディット］と書いてあるタブアイコンをクリックし、［エディット］タブを開いてください

- [![](https://cgworld.jp/regular/images/38912vfx/vol02/H03.png)](https://cgworld.jp/regular/images/38912vfx/vol02/H03.png)
- ◀ 【2】 最初に練習で作成したコンポジション［Fusion Composition］がタイムラインに配置されているので、左上のメディアプールにドラッグ＆ドロップして保存しておきます
- [![](https://cgworld.jp/regular/images/38912vfx/vol02/H04.png)](https://cgworld.jp/regular/images/38912vfx/vol02/H04.png)
- ◀ 【3】 ①［Fusion Composition］という名前のコンポジションが左上のメディアプールにできたことを確認したら、②下のタイムラインのコンポジションは③右クリック→［選択を削除］で削除します
- [![](https://cgworld.jp/regular/images/38912vfx/vol02/H05.png)](https://cgworld.jp/regular/images/38912vfx/vol02/H05.png)
- ◀ 【4】 メディアプールから［38912VFX\_Comp］（今回作成したコンポジション）をドラッグ＆ドロップで先頭に配置します

[![](https://cgworld.jp/regular/images/38912vfx/vol02/H06.png)](https://cgworld.jp/regular/images/38912vfx/vol02/H06.png)

▲ 【5】 このように上のタイムラインビューに先ほどコンポジットした映像が表示されています。もしビューに何も表示されないときは、タイムラインの再生ヘッドを少し動かすとリフレッシュされて表示されるはずです

  

〈Step 1〉書き出す

[![](https://cgworld.jp/regular/images/38912vfx/vol02/H07.png)](https://cgworld.jp/regular/images/38912vfx/vol02/H07.png)

▲ 【6】 画面最下部の［デリバー］と書いてあるタブアイコンをクリックし、［デリバー］タブを開いてください

- [![](https://cgworld.jp/regular/images/38912vfx/vol02/H08.png)](https://cgworld.jp/regular/images/38912vfx/vol02/H08.png)
- ◀ 【7】 左上のレンダー設定から、まず①［H.264 Master］のテンプレートを選びます。表示されていない場合はアイコン下のバーを横スクロールすると表示されるはずです。［H.264 Master］を選んだら、②ファイル名と映像の書き出し先を［名称］と［保存先］で決めます。③次に［フォーマット］で［MP4］を選択し、④最後に［レンダーキューに追加］を押します

ここでいったん、［Ctrl+S］でプロジェクトを保存しておきましょう。

- [![](https://cgworld.jp/regular/images/38912vfx/vol02/H09.png)](https://cgworld.jp/regular/images/38912vfx/vol02/H09.png)
- ◀ 【8】 右側のレンダーキューに追加されました。［Render All］を押すと、レンダリング（映像の書き出し）が始まります。書き出しには少し時間がかかりますので、お茶でも飲みながらのんびり待ちましょう

[![](https://cgworld.jp/regular/images/38912vfx/vol02/H10.png)](https://cgworld.jp/regular/images/38912vfx/vol02/H10.png)

▲ 【9】 映像が書き出されました！　開いて見てみましょう！　VFXの映像が完成しました

これにて終了です！　お疲れさまでした!!!

  

【理論】なぜこうするの？

DaVinci Resolveでは、タイムラインの映像がレンダリングされます。今回作った38912VFX\_Compというコンポジションは、読み込んだ映像や画像と同じくメディアのひとつのように扱われるため、これを直接書き出すことはできません。そのため、一度タイムラインに配置して、それをレンダリングしました。

## おわりに：まずはVFXを楽しもう！

個人レベルのVFXにおける唯一の目標は 「ねらい通りの画をつくる」 ことです。VFXで同じ画をつくるにしてもありとあらゆる方法がありますが、「ねらった画」がつくれていればどんなやり方でも正解です。もちろんチームでつくる場合は「ねらった画」だけではなく他の工程で「迷惑をかけない」という縛りが発生しますが、個人でつくる分には何をしたって良いんです。

はじめはそこまで深く考えず、邪道だろうがなんだろうが楽しい！　と思える方法で作品を作ってみてください。慣れて余裕が出てきたり人と映像を作る機会が出てきたら、先人の知恵が詰まった王道を学んだり、テクニカルなロジックを学ぶことでより高いステップに進めるはずです。

今回紹介したコンポジットの手法は、最低限のロジックを取り入れつつ工程をシンプルにするため、王道も邪道も織り交ぜたものになっています。まずは使えそうなところからつまみ食いして「VFX」で楽しく遊んでいただけたら嬉しいです。

では、また次回お会いしましょう！

  
  

## Profile.

- ![](https://cgworld.jp/regular/images/38912vfx/miyake_Profile.jpg)
- 三宅智之／Tomoyuki Miyake  
	2000年、東京生まれ。平成28年度 総務省「異能vation」採択（最年少）。早稲田大学教育学部複合文化学科在学中  
	Twitter： [@38912\_DIGITAL](https://twitter.com/38912_DIGITAL)  
	YouTube： [38912 DIGITAL](https://www.youtube.com/channel/UCht6pU8sj3T8QEZHW5rllIw)  
	note： [note.com/38912\_digital](https://note.com/38912_digital)
  
  
- [![](https://cgworld.jp/regular/images/38912vfx/banner.png)](https://www.info-event.jp/dell/lp/ws_vfx/)
- Dell Presents ステイホームVFX コンテスト エントリー受付中！  
	  
	●審査基準  
	01：自宅での撮影素材を活かした面白い表現ができているか  
	02：CG・VFX技術を駆使した作品であるかどうか  
	  
	●部門  
	プロフェッショナル部門／学生部門  
	  
	●応募方法  
	・エントリー：〜5月15日  
	・審査同意書記入：〜5月21日  
	・作品提出：〜5月24日  
	  
	[www.info-event.jp/dell/lp/ws\_vfx](https://www.info-event.jp/dell/lp/ws_vfx/)

[この連載一覧を見る](https://cgworld.jp/regular/38912vfx/)

- [![](https://cgworld.jp/assets_new2021/icon/x_logo.png)](https://twitter.com/share?url=https://cgworld.jp/regular/202104-38912vfx-02.html&text=%E3%81%AF%E3%81%98%E3%82%81%E3%82%88%E3%81%86%EF%BC%81%E8%B8%8F%E3%81%BF%E5%87%BA%E3%81%9D%E3%81%86%EF%BC%81VFX%EF%BC%81%E7%AC%AC2%E5%9B%9E%EF%BC%9ADaVinci%20Resolve%20Fusion%E3%81%A7%E8%B8%8F%E3%81%BF%E8%BE%BC%E3%82%80%E3%82%B3%E3%83%B3%E3%83%9D%E3%82%B8%E3%83%83%E3%83%88%EF%BC%81%E3%80%90%E3%82%B9%E3%83%86%E3%82%A4%E3%83%9B%E3%83%BC%E3%83%A0VFX%E9%80%A3%E5%8B%95%E4%BC%81%E7%94%BB%E3%80%91)

## CGWORLD特設サイト

- 週間ランキング
- 月間ランキング

- [![](https://cgworld.jp/flashnews/Google_Flow-01.jpg)
	NEW
	Googleがクリエイター向けAI映像制作ツール「Flow」をリリース！　Veo・Imagen・Geminiを統合
	](https://cgworld.jp/flashnews/01-202506-Google-Flow.html)
- [![](https://cgworld.jp/article/_honda-top.jpg)
	NEW
	Hondaが3Dモデルを無償公開！ クリエイター必見のバイクアセット「Honda Super Cub C125」3Dモデル
	](https://cgworld.jp/article/202506-cgw320-honda.html)
- [![](https://cgworld.jp/article/202505-cgkiso-3_a4.jpg)
	セガのゲームで学ぶ 3DCGの基礎／デザイナーの職種
	](https://cgworld.jp/article/202505-cgkiso-3.html)
- [![](https://cgworld.jp/article/202505-cgkiso-1_a1_2.jpg)
	セガの新人研修を紐解く No.1／開発の全体像を理解する
	](https://cgworld.jp/article/202505-cgkiso-1.html)
- [![](https://cgworld.jp/special-feature/741755420dfad2374f72dccaab05defa2d2493a5.jpg)
	明日から活かせる"エフェクトデザイナー育成術"「対面で密に」「データ蓄積による効率化」「教える側を増やす」
	](https://cgworld.jp/special-feature/2505-effect.html)
VIEW MORE

- [![](https://cgworld.jp/article/6d3475e05c048668b7f03b98583b2a30e82c7770.jpg)
	ソニーグループ横断で開発中のアニメ制作ソフト「AnimeCanvas」開発進捗報告 〜ACTF2025 in TAAF（3）
	](https://cgworld.jp/article/actf25-taaf-animecanvas03.html)
- [![](https://cgworld.jp/regular/images/lee/006/Lee_006_Banner.jpg)
	【流流とはじめる、簡単リグ＆モーション制作】第6回：キャラクターモーション＜その1＞
	](https://cgworld.jp/regular/202505-rururig-06.html)
- [![](https://cgworld.jp/article/72452d3bb592ffb9381657e5555d4d5fb740ee94.jpg)
	劇場アニメ『ベルサイユのばら』（1）3DCG制作篇〜 華麗なベルサイユ宮殿と繊細な撮影処理を解説
	](https://cgworld.jp/article/321-verbara01.html)
- [![](https://cgworld.jp/flashnews/EDGS-01.jpg)
	3D Gaussian Splattingよりも精密なモデルを高速生成できる技術「EDGS」発表！　3DGSの密度化プロセス排除して最適化ルートを短縮することで品質と速度を両立
	](https://cgworld.jp/flashnews/01-202505-EDGS.html)
- [![](https://cgworld.jp/special-feature/images/202502-monolithsoft/monolithsoft_banner_v2.jpg)
	Houdiniのプロシージャル技術とOpenUSD活用で進化を遂げるモノリスソフト〜R&Dの最前線と求める人材像を聞く
	](https://cgworld.jp/special-feature/202505-monolithsoft.html)
VIEW MORE

## スペシャルコンテンツ

- [![](https://cgworld.jp/special-feature/assets_c/2025/05/f3fbe6b942ed2e88a8a6940be3ff740eb0b0dab3-thumb-1920x1081-69656.jpg)
	NEW
	CGを始めたころに出会っていたかった！　高性能でスタイリッシュ、軽量なノートPCと4Kモニターで広がる、Rieringo氏の新たなチャレンジ
	](https://cgworld.jp/special-feature/mouse-rieringo-202505.html)
- [![](https://cgworld.jp/flashnews/assets_c/2025/06/168_seminar_autodeskfc_full-%281%29-thumb-800x450-69984.png)
	NEW
	6/12（木）東京で開催！映像チェックバックツール「Autodesk Flow Capture」ローンチイベント
	](https://cgworld.jp/flashnews/02-2506-autodesk-flow-capture.html)
- [![](https://cgworld.jp/special-feature/assets_c/2025/05/741755420dfad2374f72dccaab05defa2d2493a5-thumb-1920x1080-69645.jpg)
	明日から活かせる"エフェクトデザイナー育成術"「対面で密に」「データ蓄積による効率化」「教える側を増やす」
	](https://cgworld.jp/special-feature/2505-effect.html)
- [![](https://cgworld.jp/special-feature/assets_c/2025/05/2505_Jaakko_main-thumb-1000x563-69558.png)
	Substance 3Dを使いこなし、内装のデザイン性を高める 建築ビジュアライゼーションにおける木目マテリアル制作事例
	](https://cgworld.jp/special-feature/2505-Jaakko-Substance.html)
- [![](https://cgworld.jp/flashnews/assets_c/2025/05/unnamed-%281%29-thumb-1000x563-69646.jpg)
	6/13（金）ウェビナー開催！建築×Substance 3D 内装のデザイン性を高める木目マテリアル制作
	](https://cgworld.jp/flashnews/02-2505-jaakko-saari-substance.html)
[VIEW MORE](https://cgworld.jp/special-feature/)

会員登録のメリット

- ![](https://cgworld.jp/assets_new2021/img/icon_modal_icon01.png)
	記事の保存ができる
	CGWORLD.jpで気になる記事や後で読みたい記事などを保存することができます。 ※最大100件まで保存が可能
- ![](https://cgworld.jp/assets_new2021/img/icon_modal_icon02.png)
	セミナーが探せる
	ボーンデジタルが開催しているセミナー情報を見ることができます。また、自分が登録しているセミナーも管理することができます。
- ![](https://cgworld.jp/assets_new2021/img/icon_modal_icon03.png)
	CGWORLDメールマガジンの  
	配信・停止管理
	第一・第三水曜日にCGWORLDのランキングや最新の講座情報などをお届けするCGWORLDメールマガジンの配信管理ができます。
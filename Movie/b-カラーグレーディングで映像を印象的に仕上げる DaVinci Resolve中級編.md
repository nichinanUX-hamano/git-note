---
title: カラーグレーディングで映像を印象的に仕上げる DaVinci Resolve中級編
source: https://www.sycom.co.jp/media/archives/3839/?srsltid=AfmBOor60sTuG4YTealA_HlwpL5N3Pr0sY_5cta2Lc7QGF9nz2qfmIRo&utm_source=pocket_shared
author:
  - sycom
published: 2024-05-09
created: 2025-06-06
description: 色は映像作品の印象を大きく左右する重要な要素です。適切な色調整により、映像はより魅力的で感情を揺さぶるものになります。しかし、色調整には専門的な知識と経験が必要とされ、初心者にとっては敷居が高く感じら
tags:
  - Movie
  - Color
---
![](https://www.sycom.co.jp/media/wp-content/uploads/2024/04/i-49.webp)

色は映像作品の印象を大きく左右する重要な要素です。適切な色調整により、映像はより魅力的で感情を揺さぶるものになります。しかし、色調整には専門的な知識と経験が必要とされ、初心者にとっては敷居が高く感じられるかもしれません。

本記事では、DaVinci Resolveを使った色調整の基本的な考え方とテクニックを解説します。カラーコレクションとカラーグレーディングの違いを理解し、各種ツールの使い方を学ぶことで、映像制作の表現の幅を大きく広げることができるでしょう。

色調整は、撮影時の条件の違いを補正し、映像を自然な色に整えるカラーコレクションと、意図的に色を操作し、作品の雰囲気を演出するカラーグレーディングの2つのフェーズに分けられます。これらを適切に組み合わせることで、視聴者の感情に訴求力のある映像作品を作り上げていきます。

本記事を通して、色調整の基本的な流れを理解し、DaVinci Resolveの各種ツールに慣れ親しんでいきましょう。色の調整は映像制作において欠かせない技術ですが、同時に創造性を発揮できる領域でもあります。色調整の技術を身につけ、自分なりの表現を探求していくことで、映像制作者としてのスキルを大きく向上させることができるはずです。それでは、DaVinci Resolveを使った色調整の世界に飛び込んでいきましょう。

本記事は「DaVinci Resolve」の「Windows」版を基に解説しておりますが「Mac」ユーザーの方にもお役に立てるかと思います。

## カラーグレーディングとカラーコレクション

カラーグレーディングとカラーコレクションは、どちらも映像の色調を調整する作業ですが、その目的と範囲に違いがあります。

![](https://www.sycom.co.jp/media/wp-content/uploads/2024/04/1-1.webp)

オリジナル

![](https://www.sycom.co.jp/media/wp-content/uploads/2024/04/1-2.webp)

カラーコレクション後

![](https://www.sycom.co.jp/media/wp-content/uploads/2024/04/1-3.webp)

カラーグレーディング後

### カラーコレクション

カラーコレクションは、主に撮影時の状況や設定に応じ生じた色を補正して自然な色や明るさに戻すことです。また複数クリップの色合いを合わせることで、作品の統一感を出します。

\- ホワイトバランスの調整

\- 露出の調整

\- コントラストの調整

\- 彩度の調整

### カラーグレーディング

カラーグレーディングは、映像の色調を意図的に変化させる色で演出をする「演色」の作業です。また余計なオブジェクトを消したりする写真でいうレタッチの要素も含まれます。

\- 映像の雰囲気や印象を作る。

\- 色を使って物語の展開や登場人物の感情を表現する

\- 映像の時代設定や場所の特徴を色で表現する

カラーグレーディングでは、色相、彩度、輝度、コントラストなどを意図的に変化させ、色で作品を特徴づけます。  
一般的なワークフローでは、まずカラーコレクションで色を均一化し、その後カラーグレーディングで映像を演色します。  
カラーコレクションを行わずにいきなりカラーグレーディングをしてしまうと色の統一感を出すことが難しくなります。

### カラーページの画面構成

カラーページは、色を調整する為に適した専用のインターフェースです。カラーページの主な画面構成は以下の通りです：

![](https://www.sycom.co.jp/media/wp-content/uploads/2024/04/1-6.webp)

**① ギャラリー / LUT**  
ギャラリーには、プリセットのルックや自分で保存したルックが表示されます。上部メニューでLUTに切り替えるとインストールしてあるLUTの一覧が表示されます。ギャラリーに保存したルックやLUTを適用することで、色の調整を簡略化することができます。

**②ビューア**  
ビューアには、現在色調整をしているクリップが表示されます。

**③ ノードエディター**  
ノードは、簡単に言うとレイヤーのような物ですが、レイヤーに比べカラー調整の手順を視覚的に表現します。各ノードが一つの調整を表し、ノード同士を線で繋ぎ左から右へと順に効果が加わります。ノードはDaVinci Resolve以外でも最近は3Dソフトなどでも多く見られる方式です。

**④プライマリー カラーホイール**  
カラーホイールは、リフト（暗部）、ガンマ（ミッドトーン）、ゲイン（ハイライト）の3つの領域に分かれており、各領域の輝度や色相などを調整します。カラーホイールの上下には、色温度やコントラスト、彩度など一般的によく使う機能がまとまっています。

**⑤カーブエディター**  
カーブは、映像のコントラストや色調を詳細に調整するためのツールです。輝度カーブ、RGB カーブ、カスタムカーブなどを使い分けることで、細かな調整が可能になります。

**⑥クリップ / タイムライン**  
タイムラインに配置されたクリップが表示されます。現在色調整中のクリップは赤い枠で囲まれます。

**⑦エフェクトライブラリー**  
各種エフェクトが入っています。

**⑧スコープ**  
色を調整する際に色の情報をグラフィカルに表示する５種類のスコープがあります。スコープに映し出された情報を読み取ることがカラーグレーディングをする上でとても大切です。

#### 用語解説「ノード」

ノードとは、簡単に言うとレイヤーのような物ですが、レイヤーに比べカラー調整の手順を視覚的に分かりやすく表示します。１つのノードに一つ、もしくは複数の調整を掛けることができます。しかし１つのノードに対しあまり多くの調整を入れてしまうと後で調整しづらくなるので一つもしくは少数の調整にとどめておきましょう。ノード同士を線で繋ぎ左から右へと順に効果が加わり繋げる順番で効果のかかり具合が変わります。ノードはDaVinci Resolve以外でも最近は3Dソフトなどでも多く見られる方式です。

![](https://www.sycom.co.jp/media/wp-content/uploads/2024/04/1-7.webp)

##### 用語解説「LUT」

LUT（ルックアップテーブル）とは、映像のカラーグレーディングで使われる機能でAdobe Lightroomのプリセットのような役割を果たします。様々なLUTがありますが、主に下記の二つに分類されます。

##### ①変換用LUT

カメラの色空間（Log、RAWなど）から、編集や表示に適した色空間（Rec709など）に変換するためのLUT。カメラごとにメーカーが提供している事が多いです。

![](https://www.sycom.co.jp/media/wp-content/uploads/2024/04/1-8.webp)

オリジナルのLog素材を変換LUTを使ってRec.709に変換

##### ②クリエイティブLUT

映像作品の雰囲気を演出するためのLUTです。自分で自作する他、シネマティックLUTやフィルムシミュレーション用のLUTなどが配布、販売されています。

![](https://www.sycom.co.jp/media/wp-content/uploads/2024/04/1-9.webp)

Rec.709の素材をクリエイティブLUTで演色

## カラーコレクション・カラーグレーディングをしてみよう

それでは実際に各工程を解説します。

映像の色を作るにはまずカラーコレクションで全体の色味を整えた後に、カラーグレーディングで色による演出を行います。ポイントはカラーコレクションの段階で全体のばらつきを抑えると、後のカラーグレーディングの工程が作業しやすくなります。

### カラーコレクション

ここではカラーグレーディング（演色）を行う前段階の自然な色に調整するカラーコレクションについて解説します。

#### 露出の調整

まず最初にプライマリーパネルのカラーホイールで明るさを整えます。

![](https://www.sycom.co.jp/media/wp-content/uploads/2024/04/49-2-1.webp)

露出の調整をする際、パレードスコープを見て調整をします。スコープの域外にはみ出している時は白飛びもしくは黒潰れをしている状態です。感覚だけでなくスコープから情報を読み取ることも大切です。

**①オフセットで全体の明るさを調整します。**

**②リフト（暗部）、ガンマ（中間）、ゲイン（明部）を調整します。**

![](https://www.sycom.co.jp/media/wp-content/uploads/2024/04/49-2-2.webp)

調整前

![](https://www.sycom.co.jp/media/wp-content/uploads/2024/04/49-2-3.webp)

調整後

![](https://lh7-us.googleusercontent.com/SQYfquZEZ4VnBCsns8VGlrcnPtekYGctp0j0x0BZ2aTypSLFH5KajiBV3V9pxltmR2zwAgNAPo2vreqhA1aUlrpHvsUecMfffY3Srvl8t5pbHeV8hV-O-CYOZiSjXEhc-rUMh30bVOTe0G_2xuZvTVs)

#### カーブを使ったコントラストの調整

カーブパネルのカスタムカーブを使ってコントラストを付けてみましょう。

![](https://www.sycom.co.jp/media/wp-content/uploads/2024/04/4-2-4.webp)

線上をクリックするとカーブポイントが追加されます。ポイントを上下することで明るさを調整することができます。図のようなカーブをS字カーブと言いコントラストが付きます。

![](https://www.sycom.co.jp/media/wp-content/uploads/2024/04/49-2-5.webp)

#### カラーバランスの調整

プライマリーパネル上部の「色温」「ティント」を使いホワイトバランスと色かぶりを調整します。

![](https://www.sycom.co.jp/media/wp-content/uploads/2024/04/49-2-6.webp)

#### 彩度の調整

プライマリーパネル下部の「カラーブースト」「彩度」を使い彩度を調整します。

![](https://www.sycom.co.jp/media/wp-content/uploads/2024/04/49-2-7.webp)

### 部分的な調整1　パワーウィンドウ（マスク）

マスクの事をDaVinci Resolveではパワーウィンドウと呼びます。パワーウィンドウは、ビューア上で描いた任意の形状の領域に、カラーコレクションを適用するツールです。ウィンドウの位置やサイズ、ソフトネスを調整し、部分的な色の調整を行うことができます。

**①ウィンドウパネルに切り替えます。**

**②円形のウィンドウを選択。**

![](https://www.sycom.co.jp/media/wp-content/uploads/2024/04/49-3-1.webp)

**③プレビューウィンドウに円形のマスクが表示されるので位置や大きさ、ぼかしの範囲を調整します。**

![](https://www.sycom.co.jp/media/wp-content/uploads/2024/04/49-3-2.webp)

**④パワーウィンドウで選択した範囲の色や明るさなどを調整します。**

![](https://www.sycom.co.jp/media/wp-content/uploads/2024/04/49-3-3.webp)

ハイライトボタンを有効にすると選択している範囲だけが表示されます。

#### トラッキングを使ってパワーウィンドウを動きに追従させる

パワーウィンドウは対象の動きに合わせて移動することも可能です。

**①トラッカーパネルに切り替える。  
②ウィンドウに切り替える。**

![](https://www.sycom.co.jp/media/wp-content/uploads/2024/04/49-4-1.webp)

**③「順方向＆逆方向にトラッキング」ボタンを押しトラッキングをかける。**

![](https://www.sycom.co.jp/media/wp-content/uploads/2024/04/49-4-2.webp)

### 部分的な調整２　クオリファイアー

クオリファイアーは、特定の色や輝度を選択し、その領域にカラーコレクションを適用するツールです。色相、彩度、輝度の値を調整することで、選択範囲を限定し、部分的な色の調整を行うことができます。PhotoshopのHSLのような機能です。

**①クオリファイアーパネルに切り替える。**

![](https://www.sycom.co.jp/media/wp-content/uploads/2024/04/49-5-1.webp)

**②プレビューウィンドウ内の抽出したい部分をクリックする。（カーソルがスポイトになっています。）**

**③クオリファイアーパネルで色相、彩度、輝度の範囲を調整し、抽出する範囲の精度を高めます。**

**④抽出した部分の色や明るさを調整します。**

![](https://www.sycom.co.jp/media/wp-content/uploads/2024/04/49-5-2.webp)

オリジナル素材

![](https://www.sycom.co.jp/media/wp-content/uploads/2024/04/49-5-3.webp)

蝶の羽の黄色い部分をクオリファイアを使って抽出

![](https://www.sycom.co.jp/media/wp-content/uploads/2024/04/49-5-4.webp)

![](https://www.sycom.co.jp/media/wp-content/uploads/2024/04/49-5-5.webp)

抽出した部分の色や明るさを調整

#### スタビライズ（手ブレ補正）

スタビライズは、手ブレなどによる映像の揺れを補正する機能です。安定した映像を得ることができます。スタビライズはエディットページのインスペクタ内でも行うことができます。

**①トラッカーパネルに移動**

**②パネル右上のスタビレイザーボタンをクリックします。**

**③「スタビライズ」ボタンを押すと解析が始まります。**

**④結果を確認し、必要に応じて「クロップ比率」「スムース」「強度」を調整します。**

**⑤「カメラロック」にチェックを入れると動きが固定されます。動きの小さいクリップに使うと良いでしょう。**

![](https://www.sycom.co.jp/media/wp-content/uploads/2024/04/49-6-1.webp)

#### ノイズリダクション（有償版のみ）

DaVinci Resolve Studio (有償版)には強力なノイズリダクション機能があります。撮影した素材のノイズが気になる時に使います。  
GPU（グラフィックボード）の性能が低いと処理に時間がかかる点が注意です。

![](https://www.sycom.co.jp/media/wp-content/uploads/2024/04/49-6-2.webp)

##### 時間的ノイズ除去

指定したフレーム数を分析し、時間軸上でノイズを除去する機能です。フレーム数を大きくするほど処理に時間がかかります。様々なノイズに対応しますが、ISOを上げて撮影する際に発生するカラーノイズに効果的です。時間的しきい値の「輝度」をあげるとディティールが失われる場合があるので、その場合はクロマの数値だけあげると良いでしょう。

##### 空間的ノイズ除去

隣接するピクセルの色や輝度の情報を分析し、ノイズを除去する機能です。画像の詳細を維持しながら、ノイズを効果的に低減できます。

## カラーグレーディング

ここでは演出的な色調整「カラーグレーディング」について解説をします。

### LUTの使ったカラーグレーディング

まず最初に一番かんたんに印象的な色にできるLUTを使ったカラーグレーディング方法を解説します。LUTを使ったカラーグレーディングは、印象的な色調を手軽に実現する方法です。  
DaVinci Resolveには多数のLUTが用意されている他、WEB上で販売や配布がされているので、実際に適用して映像の雰囲気がどのように変化するか見てみましょう。LUTを適用するだけで、映像の印象を大きく変えることができます。

![](https://www.sycom.co.jp/media/wp-content/uploads/2024/04/49-7-1.webp)

**①LUTのインストール**  
LUTギャラリーの何もない所で右クリックをし「フォルダーで表示」を選択するとLUTの保存フォルダーが開きます。その中にLUTを入れます。

**②DaVinci Resolveに戻りLUTギャラリーの何もない所で右クリックをし「更新」を選択すると先ほどインストールしたLUTが表示されます。**

**③新しくノードを作成し、LUTをドラッグアンドドロップして適用します。**

**④そのままではかかり具合が強い場合（もしくは弱い場合）はキーパネルを開きキー出力の「ゲイン」を調整します。**

![](https://www.sycom.co.jp/media/wp-content/uploads/2024/04/49-7-2.webp)

#### LUTを使う際のポイント

序盤の用語解説においてLUTには「変換用LUT」と「クリエイティブLUT」の２種類があると解説しました。  
変換用LUTはLogで撮影した色味の浅い映像をRec.709など一般のモニターで見れる色に変換をするLUTです。クリエイティブLUTは演色するためのLUTです。  
  
使い方としてはまず変換用LUTで通常の色に戻し、クリエイティブLUTで演色をするという使い方をします。  
またクリエイティブLUTはS-Log3用などの専用のものがあります。その場合は変換用LUTを使わずにLog素材に直接クリエイティブLUTを適用します。

#### 暗部、中間部、明部に色を乗せる

プライマリーカラーホイールを使い、各明るさに色を乗せることができます。

例えば暗部に青を乗せたい場合は、リフトのホイールの中心点を少しだけ青の方に移動させると暗部が青くなります。

![](https://www.sycom.co.jp/media/wp-content/uploads/2024/04/49-8-1.webp)

### カーブを使った演色

#### 色相 vs 色相

色相 vs 色相は、特定の色相を選択し、その色相の範囲内で色相を変更する機能です。例えば、青の色相を選択し、黄色の方向に色相をシフトさせることができます。これにより、特定の色の色合いを細かく調整することが可能になります。

![](https://www.sycom.co.jp/media/wp-content/uploads/2024/04/49-9-1.webp)

![](https://www.sycom.co.jp/media/wp-content/uploads/2024/04/49-9-2.webp)

![](https://www.sycom.co.jp/media/wp-content/uploads/2024/04/49-9-3.webp)

青い部分の色相を少し黄色に変化させる

#### 色相 vs 彩度

色相 vs 彩度は、特定の色相を選択し、その色相の彩度を調整する機能です。例えば、空の青を選択し、カーブを上げると青の彩度が上がり、植物の葉っぱの黄色下げると黄色の彩度が下がります。これにより、特定の色の鮮やかさを細かく調整することが可能になります。

![](https://www.sycom.co.jp/media/wp-content/uploads/2024/04/49-9-4.webp)

![](https://www.sycom.co.jp/media/wp-content/uploads/2024/04/49-9-5.webp)

![](https://www.sycom.co.jp/media/wp-content/uploads/2024/04/49-9-6.webp)

#### 彩度 vs 彩度

彩度 vs 彩度は、彩度の低い領域と高い領域の彩度を個別に調整する機能です。カーブの左側が低彩度、右側が高彩度を表します。彩度の上がりすぎた部分の彩度を落とす時などに使用します。下の例の場合、彩度が高い青空の部分の彩度を下げいています。

![](https://www.sycom.co.jp/media/wp-content/uploads/2024/04/49-9-7.webp)

![](https://www.sycom.co.jp/media/wp-content/uploads/2024/04/49-9-8.webp)

![](https://www.sycom.co.jp/media/wp-content/uploads/2024/04/49-9-9.webp)

#### 輝度 vs 彩度

カーブの輝度 vs 彩度は、輝度の変化に応じて彩度を調整する機能です。カーブの左側が低輝度、右側が高輝度を表します。例えば、暗い部分の輝度を下げて暗い部分を黒くし、映像の統一感を取るときなどに使用します。

![](https://www.sycom.co.jp/media/wp-content/uploads/2024/04/49-9-10.webp)

![](https://www.sycom.co.jp/media/wp-content/uploads/2024/04/49-9-11.webp)

![](https://www.sycom.co.jp/media/wp-content/uploads/2024/04/49-9-12.webp)

### カラーワーパー

「カラーワーパー色相ー彩度」は直感的に色相、彩度を調整することができます。回転方向で色相を変化させ、中心から外に向かって移動させるほど彩度が高くなります。

![](https://www.sycom.co.jp/media/wp-content/uploads/2024/04/49-10-1.webp)

### モーショントレイル

エフェクトの中にあるモーショントレイルは、動きのある被写体の軌跡を残像として表現するエフェクトです。川の流れなどにかけるとスローシャッターのような効果が得られます。

![](https://www.sycom.co.jp/media/wp-content/uploads/2024/04/49-11-1.webp)

![](https://www.sycom.co.jp/media/wp-content/uploads/2024/04/49-11-2-1.webp)

![](https://www.sycom.co.jp/media/wp-content/uploads/2024/04/49-12-2.webp)

![](https://www.sycom.co.jp/media/wp-content/uploads/2024/04/49-12-3.webp)

### モーションブラー

動きのある被写体にブラーを適用するエフェクトです。例えば、シャッター速度が早すぎてパラついてしまったシーンにモーションブラーを適用することで、よりブラー効果が加わった映像になります。

![](https://www.sycom.co.jp/media/wp-content/uploads/2024/04/49-12-1.webp)

### ミッドディテールを使ったディテール調整

プライマリーパネルにあるミッドディティールは 中間調のディテールを調整するツールです。＋にすると強調され、ーにするとフワッと柔らかくなります。自然風景や人肌や髪の毛などに効果的です。

![](https://www.sycom.co.jp/media/wp-content/uploads/2024/04/49-13-1.webp)

![](https://www.sycom.co.jp/media/wp-content/uploads/2024/04/49-13-2.webp)

![](https://www.sycom.co.jp/media/wp-content/uploads/2024/04/49-13-3.webp)

ミッドディティールを上げると自然な感じにディティールが強調され、下げるとやわらかくなる

![](https://www.sycom.co.jp/media/wp-content/uploads/2024/04/49-13-4.webp)

![](https://www.sycom.co.jp/media/wp-content/uploads/2024/04/49-13-5.webp)

![](https://www.sycom.co.jp/media/wp-content/uploads/2024/04/49-13-6.webp)

人肌に適用する場合は肌の部分をクオリファイアを使って抽出してミッドディティールを下げるとまつ毛などのディティールはそのままに肌だけ美しくできます。

### ブラーを使ったディテール調整

プラーパネルのシャープタブを開き「範囲」をほんの少し（0.02程）下げると少しピントの甘い素材の解像感が上がります。

![](https://www.sycom.co.jp/media/wp-content/uploads/2024/04/49-14-1.webp)

### 彩度を上げ過ぎない為に（CIE色度スコープ）

カラーグレーディングをしているとどうしても彩度を上げて見栄えを良くしたいと思ってしまいます。彩度をあげること自体が悪いことではないのですが、客観的に彩度を判断するには「CIE色度スコープ」を使います。

CIE色度スコープは色が色度図のどの位置に分布しているかを確認することができます。  
中心付近は彩度が低く周辺に向かって広がっている場合は彩度が高い状態です。また現在設定している色域（Rec.709など）の範囲を色度図上に三角で表しています。  
この三角の線に張り付いた状態だと彩度が高い状態で破綻していると判断できます。色域の三角に触れることが絶対に悪いというわけではありません。CIE色度スコープを彩度を客観的に判断するための参考として活用しましょう。

![](https://www.sycom.co.jp/media/wp-content/uploads/2024/04/49-15-1.webp)

![](https://www.sycom.co.jp/media/wp-content/uploads/2024/04/49-15-2.webp)

![](https://www.sycom.co.jp/media/wp-content/uploads/2024/04/49-15-3.webp)

![](https://www.sycom.co.jp/media/wp-content/uploads/2024/04/49-15-4.webp)

### 人肌を自然な色にする（ベクトルスコープ）

ベクトルスコープは、色相と彩度を2次元グラフで表示するツールです。中心から外側に向かって彩度が高くなり、円周上の位置が色相を表します。スコープの設定項目の中にある「スキントーンインジケーター」にチェックを入れると中心から左斜め上に向かって線が表示されます。人肌をこの線に合わせると人種にかかわらず一般的に自然な肌の色になります。

![](https://www.sycom.co.jp/media/wp-content/uploads/2024/04/49-16-1.webp)

![](https://www.sycom.co.jp/media/wp-content/uploads/2024/04/49-16-2.webp)

## 「Davinci Resolve」におすすめのBTOパソコン

### Lepton Motion Pro Z790/D5

BTOメーカー・サイコムの「Lepton Motion Pro Z790/D5」は映像編集に特化したパソコンです。  
CPUに最大5.6GHz、20コア/28スレッドのIntel Core i7-14700K、ビデオカードにVRAM8GBのNVIDIAの GeForce RTX 4060を標準で搭載し、メモリもDDR5-4800を32GB(16GB×2)と「Davinci Resolve」を使うには、必要十分な構成となっています。

4Kを超えるような映像編集を目指すのであれば、CPUやビデオカードをカスタマイズすることで、さらなるパワーアップすることもできます。

スタイリッシュでエアフローに優れたFractal Design製のPCケースや圧倒的な冷却＆静音性を発揮するNoctua製のCPUクーラーも注目ポイント。快適な動画編集を約束する1台に仕上がっています。

![映像編集に特化したミドルタワー型PC Lepton Motion Pro Z790/D5](https://www.sycom.co.jp/media/wp-content/uploads/2024/02/41-4-4-1.webp)

映像編集に特化したミドルタワー型PC Lepton Motion Pro Z790/D5

| 「Lepton Motion Pro Z790/D5」の標準構成 |
| --- |
| CPU：Core i7-14700K   マザーボード：ASRock Z790 Pro RS   メモリ：32GB［16GB\*2枚］DDR5-4800 Dual Channel   SSD：Crucial T500 CT1000T500SSD8 \[M.2 PCI-E GEN4 SSD 1TB\]   ビデオカード：GeForce RTX4060 8GB ASUS製DUAL-RTX4060-8G   OS：Windows 11 Home   外形寸法：幅222×奥450×高さ467ｍｍ |

**[「Lepton Motion Pro Z790/D5」製品ページ](https://www.sycom.co.jp/custom/model?no=000914)**

### Lepton Motion Pro Mini B760/D5

「Lepton Motion Pro Mini B760/D5」は、「Lepton Motion Pro Z790/D5」と同様、映像編集に特化したスタイリッシュなミニタワー型モデル。  
高性能パソコンは概してサイズが大きくなりがちですが、このマシンは設置場所を選ばないコンパクトモデルで、オフィスではなく自宅での作業にも最適な1台です。  
サイズはコンパクトながら、CPUにIntel Core i7-13700K、ビデオカードにNVIDIAの GeForce RTX 4060、メモリもDDR5-4800を16GB(8GB×2)を搭載。  
Fractal Design製のPCケースやNoctua製のCPUクーラーなど、圧倒的なパワーと静音＆冷却性能の両立が期待できる構成になっています。

![Lepton Motion Pro Mini B760/D5
高速なレンダリング性能を誇る映像編集に特化したスタイリッシュなミニタワー型モデル。
コンパクトながら安定性と静音性も両立。
設置場所を選ばず、現場の即戦力としてクリエイターをサポートします。](https://www.sycom.co.jp/media/wp-content/uploads/2024/02/38-8-2.webp)

Lepton Motion Pro Mini B760/D5 高速なレンダリング性能を誇る映像編集に特化したスタイリッシュなミニタワー型モデル。 コンパクトながら安定性と静音性も両立。 設置場所を選ばず、現場の即戦力としてクリエイターをサポートします。

| 「Lepton Motion Pro Mini B760/D5」の標準構成 |
| --- |
| CPU：Core i7-14700K   マザーボード：MSI MPG B760I EDGE WIFI   メモリ：16GB［DDR5-4800 8GBx2 Dual Channel］   SSD：Crucial T500 CT1000T500SSD8 \[M.2 PCI-E GEN4 SSD 1TB\]   ビデオカード：GeForce RTX4060 8GB ASUS製DUAL-RTX4060-8G   OS：Windows 11 Home   外形寸法：幅222×奥417×高さ374ｍｍ |

**[「Lepton Motion Pro Mini B760/D5」製品ページ](https://www.sycom.co.jp/custom/model?no=000960)**

## まとめ

カラーコレクションとカラーグレーディングは、映像作品の視覚的な印象を大きく左右する重要な工程です。  
カラーコレクションにより、撮影時の色のばらつきを修正し、作品全体の色味を統一することで、自然でバランスの取れた映像を作り出します。  
  
一方で、カラーグレーディングは映像に深みと雰囲気を加え、物語や登場人物の感情を色で表現することで、視聴者の感情移入を促します。これらのプロセスを適切に実施することで、映像作品はより魅力的で、意図したメッセージを効果的に伝えることができます。  
映像制作における色の調整は単なる技術を超え、映像を通じたコミュニケーションの核心部分をなす芸術的な表現が可能です。  
  
カラーグレーディングを身につけ作品表現の幅を広げてみましょう。

DaVinci Resolve 18 認定トレーナー。北アルプスの麓、長野県松本市を拠点に、自然やそこに暮らす人を題材とした映像作品を自然の中にゆっくり溶け込んで撮影しています。著作『DaVinci Resolve 編集&カラーグレーディング入門』（玄光社）

## BTOパソコン売れ筋ランキング

（4月1日～4月30日）

- ![](https://www.sycom.co.jp/top/ranking/G-Master_Spear_X870A.png)
	1位 [G-Master Spear X870A](https://www.sycom.co.jp/custom/model?no=000990)
	Zen5アーキテクチャ採用のAMD Ryzen 9000シリーズを搭載するミドルタワー型ゲーミングPC。高性能と高拡張性を実現したゲーマー向けハイエンドモデルです。
- ![](https://www.sycom.co.jp/top/ranking/Radiant_GZ3500X870A.png)
	2位 [Radiant GZ3600X870A](https://www.sycom.co.jp/custom/model?no=000989)
	Zen5アーキテクチャ採用のAMD Ryzen 9000シリーズ搭載ATXミドルタワー型モデル。BTOならではのカスタマイズの幅が広いスタンダードなモデルです。
- ![](https://www.sycom.co.jp/top/ranking/G-Master_Spear_Mini_B850A.png)
	3位 [G-Master Spear Mini B850A](https://www.sycom.co.jp/custom/model?no=001035)
	AMD Ryzen 9000シリーズを搭載する容量26.3リットルとコンパクトながら幅広いカスタマイズ性とミニマルなデザインを持ち合わせたゲーミングPC。
- ![](https://www.sycom.co.jp/top/ranking/Premium-Line_X870FD-A.png)
	4位 [Premium Line X870FD-A](https://www.sycom.co.jp/custom/model?no=000997)
	いいものを、永く。標準2年保証、無償オーバーホールなど末永くご愛用いただくためのアフターサービスも充実したサイコムが提案する新たなPCのカタチ。その名は、Premium Line
- ![](https://www.sycom.co.jp/top/ranking/G-Master_Spear_Z890.png)
	5位 [G-Master Spear Z890](https://www.sycom.co.jp/custom/model?no=001002)
	AI時代の新CPU、Intel Core Ultraプロセッサを搭載するミドルタワー型ゲーミングPC。高性能と高拡張性を実現したゲーマー向けハイエンドモデルです。
- ![](https://www.sycom.co.jp/top/ranking/Radiant_GZ3600Z890.png)
	6位 [Radiant GZ3600Z890](https://www.sycom.co.jp/custom/model?no=001000)
	最新のIntel Core Ultraプロセッサを搭載するATXミドルタワー型モデル。BTOならではのカスタマイズの幅が広いスタンダードなモデルです。
- ![](https://www.sycom.co.jp/top/ranking/G-Master_Velox_II_Intel_Edition.png)
	7位 [G-Master Velox II Intel Edition](https://www.sycom.co.jp/custom/model?no=000932)
	高品質なパーツを採用した納得の標準構成と厳選されたオプションパーツでシンプルなカスタマイズが楽しめる新機軸のゲーミングPC！  
	定番のインテル® Core™ プロセッサ搭載モデルです。
- ![](https://www.sycom.co.jp/top/ranking/Radiant_VX3100B760-D4.png)
	8位 [Radiant VX3100B760/D4](https://www.sycom.co.jp/custom/model?no=001043)
	インテル®Core™プロセッサ（第14世代）採用のMicroATXミニタワー型モデル。ミドルタワー型PCは大きくて置けない、でも高性能なパソコンが欲しい！とお悩みの貴方にオススメ！
- ![](https://www.sycom.co.jp/top/ranking/G-Master_Velox_Mini_B650A_AMD_Edition.png)
	9位 [G-Master Velox Mini B650A AMD Edition](https://www.sycom.co.jp/custom/model?no=001042)
	容量19リットルのコンパクト筐体にAMD Ryzen 9000シリーズとGeForce RTXシリーズを搭載するゲーミングPC。納得の標準構成と厳選されたオプションパーツでシンプルなカスタマイズが楽しめます。
- ![](https://www.sycom.co.jp/top/ranking/Lepton_Motion_Pro_X870-A.png)
	10位 [Lepton Motion Pro X870/A](https://www.sycom.co.jp/custom/model?no=000994)
	スタイリッシュ＆ハイスペックな映像編集者向けPC。高負荷時の安定性と静音性を両立し拡張性も確保。現場の即戦力としてクリエイターをバックアップします。
---
title: postshotの使い方
source: https://lilea.net/lab/how-to-use-postshot/
author:
  - "[[龍 lilea]]"
published: 2024-05-12
created: 2025-06-04
description: 3D Gaussian SplattingをGUIで処理、生成できるソフトです。 公式サイトはこちら。 コマン…
tags:
  - 3DGs
---
3D Gaussian SplattingをGUIで処理、生成できるソフトです。

[![](https://i2.wp.com/lilea.net/lab/wp-content/uploads/sites/5/2024/05/lilea-240511-334.jpg?resize=680%2C433&ssl=1)](https://i2.wp.com/lilea.net/lab/wp-content/uploads/sites/5/2024/05/lilea-240511-334.jpg?ssl=1)

公式サイトは [こちら](https://www.jawset.com/) 。

コマンドラインで実行する公式の3D Gaussian Splattingの環境構築方法も [こちら](https://lilea.net/lab/how-to-setup-3d-gaussian-splatting/) で解説していますが、コマンドラインは慣れていないとなかなか使いこなすのも大変。この点postshotはマウス操作で直感的に利用できます。

直感的に使えるので使用方法は詳しい説明がいらないレベルではありますが、応用的な使い方を含めて以下にまとめてみました。

後半では **RealityCaptureやMetashapeのアライメント結果を読み込む方法** や **UEへの読み込み方** についても紹介しています。

現在はベータ版で頻繁にアップデートも行われており、UIや仕様変更が度々発生しているのでここに記載している内容も変わる可能性は大いになります。 [poostshotのDiscord](https://www.jawset.com/postshot-chat) があるので、最新情報はそちらで追えます。バグレポートや機能要望もDiscordから行えます。

## インストールと簡単な使い方

[公式サイト](https://www.jawset.com/) からDLしてインストールする。

[![](https://i2.wp.com/lilea.net/lab/wp-content/uploads/sites/5/2024/05/lilea-240511-212.jpg?resize=680%2C367&ssl=1)](https://i2.wp.com/lilea.net/lab/wp-content/uploads/sites/5/2024/05/lilea-240511-212.jpg?ssl=1)

起動すると以下のような画面になるので、表示されている通り画像をドロップ&ドロップする。

[![](https://i0.wp.com/lilea.net/lab/wp-content/uploads/sites/5/2024/05/lilea-240511-408.png?resize=680%2C410&ssl=1)](https://i0.wp.com/lilea.net/lab/wp-content/uploads/sites/5/2024/05/lilea-240511-408.png?ssl=1)

読み込むとダイアログが表示されます。

[![](https://i1.wp.com/lilea.net/lab/wp-content/uploads/sites/5/2024/05/lilea-240511-421.png?resize=472%2C406&ssl=1)](https://i1.wp.com/lilea.net/lab/wp-content/uploads/sites/5/2024/05/lilea-240511-421.png?ssl=1)

デフォルトだと「Image Selection」が「Best Images」になっていますが、使用する写真が限定されるので、すべての写真を利用したい場合は「Use All Images」を選んでおきます。

「Start Trainning」は「Import」ボタンを押すとすぐ処理が開始される設定です。写真を読み込んでから設定をつめて、それからトレーニングを実行したい場合はこのチェックは外しておきます。

右下の「Import」を押すと写真が読み込まれます。

読み込まれたら、左上の「Start Trainning」を押すと処理が開始されます。

[![](https://i2.wp.com/lilea.net/lab/wp-content/uploads/sites/5/2024/05/lilea-240511-253.png?resize=680%2C487&ssl=1)](https://i2.wp.com/lilea.net/lab/wp-content/uploads/sites/5/2024/05/lilea-240511-253.png?ssl=1)

しばらく待つとリアルタイムに処理中の様子がビューポート上に表示されます。

[![](https://i2.wp.com/lilea.net/lab/wp-content/uploads/sites/5/2024/05/lilea-240511-334.jpg?resize=680%2C433&ssl=1)](https://i2.wp.com/lilea.net/lab/wp-content/uploads/sites/5/2024/05/lilea-240511-334.jpg?ssl=1)

以上、最低限の使い方でした。(その他便利な使い方等は今後追記予定)

各種パラメーターの詳細ついては [公式マニュアル](https://www.jawset.com/docs/d/Postshot+User+Guide) に記載があります。

## Unreal Engineで利用する

2024/10/12のアップデートでUnreal Engineに対応したようです！3D Gaussian SplattingをUnreal Engineで利用する手段がまた1つ増えた。

使い方は簡単だった。

1. UE 5.4を入れる
2. postshot 0.4.71以降のインストーラーでUnreal Engine用プラグインにチェックを入れてインストールする ![](https://i0.wp.com/lilea.net/lab/wp-content/uploads/sites/5/2024/05/lilea-241013-113.jpg?resize=680%2C298&ssl=1)
3. .pshtファイルをUEのコンテンツブラウザに読み込む
4. データをビューポートへ放り込む [![](https://i0.wp.com/lilea.net/lab/wp-content/uploads/sites/5/2024/05/lilea-241013-339.jpg?resize=680%2C372&ssl=1)](https://i0.wp.com/lilea.net/lab/wp-content/uploads/sites/5/2024/05/lilea-241013-339.jpg?ssl=1)

以上。

## RealityCaptureのアライメント結果を利用する場合

大規模なシーンや複雑なシーンを処理する場合、postshotではうまくアライメント(写真位置推定)ができない場合があります。(現在postshotにはコントロールポイントを使用したり、レーザースキャンデータを併用する機能はありません)しかしこうした複雑なシーンを事前に **RealityCaptureでアライメントを行っておくことでこのデータをpostshotに読み込ませて利用することができます。**

この方法がまだ公式マニュアルには記載がないので手順をまとめました。※追記 本日(2024/8/22)公式マニュアルにも記載されました。該当ページは [こちら](https://www.jawset.com/docs/d/Postshot+User+Guide/Importing+Images)

##### 1\. RealityCaptureでアライメントまで完了させる

RealityCaptureの使い方については「 [フォトグラメトリ手順書](https://lilea.net/lab/how-to-photogrammetry/) 」にまとめているので参考にしてみてください。

##### 2\. RealityCaptureからcsvを書き出す

Alignment > Export > Registration > Internal/Extenal camera paramerters から書き出す。 [![](https://i1.wp.com/lilea.net/lab/wp-content/uploads/sites/5/2024/05/lilea-240511-116.png?resize=680%2C605&ssl=1)](https://i1.wp.com/lilea.net/lab/wp-content/uploads/sites/5/2024/05/lilea-240511-116.png?ssl=1)

設定はデフォルトのままでOK。 [![](https://i1.wp.com/lilea.net/lab/wp-content/uploads/sites/5/2024/05/lilea-240512-257.png?resize=480%2C532&ssl=1)](https://i1.wp.com/lilea.net/lab/wp-content/uploads/sites/5/2024/05/lilea-240512-257.png?ssl=1)

##### 3\. RealityCaptureからplyを書き出す

Alignment > Export > Point Cloud > Sparse point cloud as Polygon File Format から書き出す。 [![](https://i0.wp.com/lilea.net/lab/wp-content/uploads/sites/5/2024/05/lilea-240511-276.png?resize=680%2C441&ssl=1)](https://i0.wp.com/lilea.net/lab/wp-content/uploads/sites/5/2024/05/lilea-240511-276.png?ssl=1)

Export asciiをFalseにする。 [![](https://i1.wp.com/lilea.net/lab/wp-content/uploads/sites/5/2024/05/lilea-240512-448.png?resize=480%2C532&ssl=1)](https://i1.wp.com/lilea.net/lab/wp-content/uploads/sites/5/2024/05/lilea-240512-448.png?ssl=1)

##### 4\. plyとcsvと写真をすべて選択してpostshotの画面へドラッグ&ドロップする

[![](https://i2.wp.com/lilea.net/lab/wp-content/uploads/sites/5/2024/05/lilea-240511-555.png?resize=680%2C382&ssl=1)](https://i2.wp.com/lilea.net/lab/wp-content/uploads/sites/5/2024/05/lilea-240511-555.png?ssl=1) 写真は歪み補正前のオリジナルの写真で良い。

##### 5\. 表示されるダイアログでCamera posesがimportになっているのを確認する

この設定によりカメラポーズ(写真位置)については読み込んだcsvのデータを用いる事になるので、postshot上での写真位置推定はスキップされます。 [![](https://i0.wp.com/lilea.net/lab/wp-content/uploads/sites/5/2024/05/lilea-240511-167.png?resize=472%2C406&ssl=1)](https://i0.wp.com/lilea.net/lab/wp-content/uploads/sites/5/2024/05/lilea-240511-167.png?ssl=1)

##### 5\. トレーニングを開始する

読み込むと既にカメラと点群がビューポート上にある状態になる。RealityCapture上と同じ状態で読み込めた。

[![](https://i1.wp.com/lilea.net/lab/wp-content/uploads/sites/5/2024/05/lilea-240511-254.jpg?resize=680%2C350&ssl=1)](https://i1.wp.com/lilea.net/lab/wp-content/uploads/sites/5/2024/05/lilea-240511-254.jpg?ssl=1)

あとは通常通り、お好みで設定を調整してトレーニングを開始する。

以下がこのワークフローでRealityCaptureを併用した大規模、広域の3D Gaussian Splattingの作例です。(postshotのみでなく公式3DGSも併用してる例ではありますが)600mの道程約2万枚の画像から生成しました。

## Metashapeのアライメント結果を利用する場合

Metashapeのバージョン2.1.3でStandard版でもCOLMAP形式に書き出せるようになりました。Pro版でも従来のようにスクリプトを走らせる必要もなく、ファイルのエクスポートから簡単に書き出せるように。

書き出したCOLMAPデータはpostshotに読むこむことが出来ます。

[![](https://i1.wp.com/lilea.net/lab/wp-content/uploads/sites/5/2024/05/lilea-241224-732.jpg?resize=680%2C447&ssl=1)](https://i1.wp.com/lilea.net/lab/wp-content/uploads/sites/5/2024/05/lilea-241224-732.jpg?ssl=1)

[![](https://i1.wp.com/lilea.net/lab/wp-content/uploads/sites/5/2024/05/lilea-241224-652.jpg?resize=680%2C229&ssl=1)](https://i1.wp.com/lilea.net/lab/wp-content/uploads/sites/5/2024/05/lilea-241224-652.jpg?ssl=1)

[![](https://i0.wp.com/lilea.net/lab/wp-content/uploads/sites/5/2024/05/lilea-241224-576.jpg?resize=546%2C300&ssl=1)](https://i0.wp.com/lilea.net/lab/wp-content/uploads/sites/5/2024/05/lilea-241224-576.jpg?ssl=1)

OKで書き出すと、画像も書き出されます。 [![](https://i2.wp.com/lilea.net/lab/wp-content/uploads/sites/5/2024/05/lilea-241224-388.jpg?resize=440%2C318&ssl=1)](https://i2.wp.com/lilea.net/lab/wp-content/uploads/sites/5/2024/05/lilea-241224-388.jpg?ssl=1) これは歪み補正が反映された画像になっています。

書き出されました。 [![](https://i2.wp.com/lilea.net/lab/wp-content/uploads/sites/5/2024/05/lilea-241224-987.jpg?resize=155%2C84&ssl=1)](https://i2.wp.com/lilea.net/lab/wp-content/uploads/sites/5/2024/05/lilea-241224-987.jpg?ssl=1)

あとはこの「images」と「sparse」フォルダをpostshotへドラッグアンドドロップで読み込むのみです。 [![](https://i0.wp.com/lilea.net/lab/wp-content/uploads/sites/5/2024/05/lilea-241224-394.jpg?resize=680%2C417&ssl=1)](https://i0.wp.com/lilea.net/lab/wp-content/uploads/sites/5/2024/05/lilea-241224-394.jpg?ssl=1)

いつものダイアログが表示されるので、適宜調整して処理を開始します。 [![](https://i1.wp.com/lilea.net/lab/wp-content/uploads/sites/5/2024/05/lilea-241224-414.jpg?resize=475%2C656&ssl=1)](https://i1.wp.com/lilea.net/lab/wp-content/uploads/sites/5/2024/05/lilea-241224-414.jpg?ssl=1)

以上。

## エラーと対策

UNREAL ENGINE用のプラグインを更新し、pshtファイルをシーンへ配置しようとすると以下のエラーとなる場合がある。

[![](https://i0.wp.com/lilea.net/lab/wp-content/uploads/sites/5/2024/05/lilea-241216-489.jpg?resize=383%2C196&ssl=1)](https://i0.wp.com/lilea.net/lab/wp-content/uploads/sites/5/2024/05/lilea-241216-489.jpg?ssl=1)

Postshot plugin failed to initializePostshot Core does not match plugin version.Remove all Postshot UE plugins and re-install Postshot.Postshot プラグインの初期化に失敗しましたPostshot Core がプラグインのバージョンと一致しません。すべての Postshot UE プラグインを削除し、Postshot を再インストールしてください。

プラグインも.pshtファイルも最新のものとなっており同じバージョンであってもこのエラーが出てしまう。この場合はエラーメッセージにあるようにプラグインをインストールし直す必要がある。

なお「インストールし直す」必要があるので、以下のプラグイン画面から一旦無効にしてから有効に切り替えるだけではダメだった。 [![](https://i1.wp.com/lilea.net/lab/wp-content/uploads/sites/5/2024/05/lilea-241216-328.jpg?resize=680%2C313&ssl=1)](https://i1.wp.com/lilea.net/lab/wp-content/uploads/sites/5/2024/05/lilea-241216-328.jpg?ssl=1)

また「インストール済みプラグイン」を確認しても、postshotのプラグインはFabから入れているものではないのでここには表示されておらず、ここからインストールし直す事もできない。 [![](https://i1.wp.com/lilea.net/lab/wp-content/uploads/sites/5/2024/05/lilea-241216-585.jpg?resize=680%2C227&ssl=1)](https://i1.wp.com/lilea.net/lab/wp-content/uploads/sites/5/2024/05/lilea-241216-585.jpg?ssl=1)

なのでエクスプローラーのPluginフォルダを直接開き、Jawset Postshotのフォルダを削除する。 [![](https://i2.wp.com/lilea.net/lab/wp-content/uploads/sites/5/2024/05/lilea-241216-096.jpg?resize=680%2C503&ssl=1)](https://i2.wp.com/lilea.net/lab/wp-content/uploads/sites/5/2024/05/lilea-241216-096.jpg?ssl=1) (この作業をする時はプロジェクトは終了しておくと良さそう)

この状態でpostshotのインストーラーを起動して再度プラグインをインストールを実行、したいところだが、実行するとpostshotの最新版はすでにインストールされているのでエラーになってしまう。 [![](https://i2.wp.com/lilea.net/lab/wp-content/uploads/sites/5/2024/05/lilea-241216-102.jpg?resize=391%2C147&ssl=1)](https://i2.wp.com/lilea.net/lab/wp-content/uploads/sites/5/2024/05/lilea-241216-102.jpg?ssl=1)

A newer version of Postshot is already installed.To install an older version, please uninstall the newer version first.新しいバージョンのPostshotが既にインストールされています。古いバージョンをインストールするには、まず新しいバージョンをアンインストールしてしてください。

なので一旦postshotをアンインストールしてから、再度インストールする。 [![](https://i0.wp.com/lilea.net/lab/wp-content/uploads/sites/5/2024/05/lilea-241216-644.jpg?resize=680%2C384&ssl=1)](https://i0.wp.com/lilea.net/lab/wp-content/uploads/sites/5/2024/05/lilea-241216-644.jpg?ssl=1)

[![](https://i2.wp.com/lilea.net/lab/wp-content/uploads/sites/5/2024/05/lilea-241216-724.jpg?resize=359%2C295&ssl=1)](https://i2.wp.com/lilea.net/lab/wp-content/uploads/sites/5/2024/05/lilea-241216-724.jpg?ssl=1)

インストールが完了したら、UEのプロジェクトを開きpostshotのプラグインを有効にする。 [![](https://i0.wp.com/lilea.net/lab/wp-content/uploads/sites/5/2024/05/lilea-241216-282.jpg?resize=680%2C313&ssl=1)](https://i0.wp.com/lilea.net/lab/wp-content/uploads/sites/5/2024/05/lilea-241216-282.jpg?ssl=1)

以上。無事に読み込めた。
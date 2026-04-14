---
title: 3D Gaussian Splatting Converter の使い方｜npaka
source: https://note.com/npaka/n/n20b9247bc713?utm_source=pocket_saves
author:
  - "[[npaka]]"
published: 2024-06-06
created: 2025-06-04
description: 「3D Gaussian Splatting Converter」の使い方をまとめました。   1. 3D Gaussian Splatting Converter  「3D Gaussian Splatting Converter」は、3DGS形式のPLYファイルと CloudCompare形式のPLYファイルを相互変換するツールです。   ・3DGS (3D Gaussian Splatting) 形式のPLYファイル 主に「3D Gaussian Splatting」に使用され、点群データの各点にガウシアン(正規分布) を割り当てることで、より滑らかで自然な表現を可能にします。各
tags:
  - 3DGs
---
![見出し画像](https://assets.st-note.com/production/uploads/images/143165100/rectangle_large_type_2_176ec6965145ce3173a6f27f5022ddea.png?width=1200)

## 3D Gaussian Splatting Converter の使い方

[npaka](https://note.com/npaka)

「3D Gaussian Splatting Converter」の使い方をまとめました。

## 1\. 3D Gaussian Splatting Converter

「 **3D Gaussian Splatting Converter** 」は、3DGS形式のPLYファイルと CloudCompare形式のPLYファイルを相互変換するツールです。

> **・3DGS (3D Gaussian Splatting) 形式のPLYファイル**  
> 主に「3D Gaussian Splatting」に使用され、点群データの各点にガウシアン(正規分布) を割り当てることで、より滑らかで自然な表現を可能にします。各点には位置情報に加え、ガウシアンの分散や重みなどの情報が含まれることが多いです。  
>   
> **・CloudCompare形式のPLYファイル**  
> 「CloudCompare」は3D点群データの可視化や解析に特化したソフトウェアであり、この形式のPLYファイルはそのために最適化されています。各点には通常、位置情報と色(RGB)情報が含まれますが、法線や他の属性も追加することが可能です。

## 2\. 主な機能

「3D Gaussian Splatting Converter」の主な機能は、次のとおりです。

> **・フォーマット変換**  
> 3DGS形式のPLYファイルと CloudCompare形式のPLYファイルを相互変換します。入力ファイルとして.parquet もサポートされています。  
>   
> **・RGBカラーリング**  
> 点群にRGB値を追加して、CloudCompare形式での視覚化と編集を向上させます。  
>   
> **・密度フィルタ**  
> まばらなデータを削除して、点群の密な領域に焦点を当てます。  
>   
> **・フライヤー除去  
> **データセット内の不要な外れ値や浮動小数点を取り除きます。密度フィルタと組み合わせて使います。  
>   
> **・境界ボックス切り取り**  
> 境界ボックスで切り取ります。

## 3\. インストール

Pythonの仮想環境で、次のコマンドを実行します。

```javascript
pip install git+https://github.com/francescofugazzi/3dgsconverter.git
```

## 4\. 使い方

使い方は、次のとおりです。

### 4-1. 3DGS形式のPLYファイルをCloudCompare形式のPLYファイルに変換

```javascript
3dgsconverter -i input_3dgs.ply -o output_cc.ply -f cc --rgb
```

### 4-2. CloudCompare形式のPLYファイルを3DGS形式のPLYファイルに変換

```javascript
3dgsconverter -i input_cc.ply -o output_3dgs.ply -f 3dgs
```

### 4-3. 変換中に密度フィルタを適用

```javascript
3dgsconverter -i input_3dgs.ply -o output_cc.ply -f cc --density_filter
```

### 4-4. 変換中に密度フィルタを適用し、フライヤー除去

```javascript
3dgsconverter -i input_3dgs.ply -o output_cc.ply -f cc --density_filter --remove_flyers
```

### 4-5. ヘルプ

```javascript
3dgsconverter -h
```

  

[**OpenAI GPT-4V／ChatGPT／GPTs 人工知能プログラミング実践入門 | 株式会社ボーンデジタル** *PDF版価格 3,960円（本体3,600円＋税10%） POD版価格 5,390円（本体4,900円＋税10%）* *www.borndigital.co.jp*](https://www.borndigital.co.jp/book/9784862465894/)

  

## いいなと思ったら応援しよう！

- [
	#python
	](https://note.com/hashtag/python)
- [
	#3DGs
	](https://note.com/hashtag/3DGs)

3D Gaussian Splatting Converter の使い方｜npaka
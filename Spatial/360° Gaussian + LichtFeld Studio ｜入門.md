---
date: 2026-04-14
source: https://qiita.com/Tks_Yoshinaga/items/dbd9359c9e5ead8195a3
tags:
  - 3DGs
  - 360動画
---
# 動作環境

## PCスペック

|     | 環境                              |
| --- | ------------------------------- |
| OS  | Windows 11 Pro for Workstations |
| GPU | NVIDIA RTX 6000 Ada Generation  |
| CPU | Intel(R) Xeon(R) w5-2455X       |
| RAM | 128 GB                          |

## 360°カメラ

- Insta360 X4

## ソフトウェア

360°Gaussian｜Extract ⇒ Alignment ⇒ Cubemaps
＊AutoMasker｜自動画像マスク👆の中で使用可能（€46）
- [https://laskosvirtuals.gumroad.com/l/360gaussian]()
LichtFeld Studio｜Training
- [https://lichtfeld.io/]()

---

| Step | 工程                 | 内容                               |
| ---- | ------------------ | -------------------------------- |
| 1    | 撮影                 | 360°カメラでシーン撮影                    |
| 2    | SfM                | 各画像がどの位置から撮影されたかを推定              |
| 3    | 点群生成               | SfMで得たカメラ位置を元に点群生成               |
| 4    | Gaussian Splatting | 点群を元に3D Gaussian Splattingモデルの生成 |

---

# Step 1
### 高品質な3DGS生成のための推奨撮影設定

360°カメラ特有の歪みやスティッチングエラーは、3DGSの学習フェーズにおけるカメラポーズ推定（Structure from Motion: SfM）に悪影響を及ぼす可能性がある
これを最小限に抑えるためには、以下の設定がプロフェッショナルな現場では推奨

- 解像度とフレームレート: 8K30fpsを選択する
	これにより、リフレーミング（切り出し）後も十分なディテールが保持される
    
- 露出制御: マニュアル（ISO 100-800、シャッタースピード 1/100s以上推奨）またはAuto Modeの「AdaptiveTone」をオン
	露出の変動は、3DGSの視点依存色の学習においてカラーアーティファクトを引き起こす主因となるため、可能な限り固定することが望ましい
    
- スタビライゼーション: 3DGSのパイプライン（特に360° Gaussianアプリ）では、後段のSfMでカメラポーズを数学的に推定するため、カメラ内スタビライゼーションはオンにしても問題ないが、Horizon Leveling（水平維持）やTilt Recoveryなどの過度な補正は、内部パラメータの一貫性を損なう場合があるため、編集ソフト側で注意が必要
    

レンズガード: 物理的な保護は重要だが、プラスチック製のレンズガードは内部反射や鮮明度の低下を招く　最高品質を求める場合は「Premium」グレードのガラス製ガードを使用するか、ガードなしでの撮影が理想的

**Insta360 Studio**（PC 用アプリ）でエクスポート
- Equirectangular 形式

---

# Step 2
### 2-1 画像切り出し
1.　**360° Gaussian** を起動します  
2.　**Add Video(s)** をクリックし、Equirectangular 形式の動画を選択します  
3.　**Splitting** を選択し、画像の切り出し条件を設定します

|パラメータ|説明|
|---|---|
|Extra frame every|指定した秒数（またはフレーム数）のインターバルで画像を切り出す|
|Sharp frame extraction|前後のフレームと比較して、ボケの少ない画像を優先的に選択するかどうか|
|Sharpness check range|例えば `10` の場合、前後 5 フレームを比較して最もシャープな画像を選択する|

### 2-2 画像のマスク｜オプション　有料ツール
1.　**AutoMasker** をクリックします  
2.　**Use AutoMasker** をオンにします  
3.　**Detection Keywords** にピリオド（`.`）区切りでキーワードを入力します

**マスクが重要な 2 つの理由**  
まず、人・車・低テクスチャオブジェクトなど動いたり特徴点の少ない被写体は **SfM のノイズ**になりやすく、カメラ位置の推定精度を下げる　SfM の精度はその後の Gaussian Splatting の出力品質に直結するため、これらをマスクで除外することが重要  
さらに、**トレーニング段階でも同様のノイズが品質を低下さる**同じ被写体が場所によって異なる見た目で映り込むと、Gaussian が正しい形状・色に収束しにくくなる　マスクはこの両方の工程でクオリティを守る役割を果たす

**AutoMasker について**  
AutoMasker は有償（46€）　独立したアプリとして単独で動作するため、360° Gaussian を使った Gaussian Splatting の自動化ワークフローだけでなく、Gaussian Splatting 以外の用途（360° 画像へのマスク処理全般）にも幅広く活用可能
類似ツールを購入するよりもこれを利用・導入する方を検討推奨


2-3 SfM (Structure from Motion)


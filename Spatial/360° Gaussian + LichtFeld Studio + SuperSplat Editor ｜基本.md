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

## アプリケーション

360°Gaussian｜Extract ⇒ Alignment ⇒ Cubemaps
＊AutoMasker｜自動画像マスク👆の中で使用可能（€46）
- [https://laskosvirtuals.gumroad.com/l/360gaussian]()
LichtFeld Studio｜Training
- [https://lichtfeld.io/]()
SuperSplat Editor
- https://superspl.at/editor

---

| Step | 工程                 | 内容                               |
| ---- | ------------------ | -------------------------------- |
| 1    | 撮影                 | 360°カメラでシーン撮影                    |
| 2    | SfM                | 各画像がどの位置から撮影されたかを推定              |
| 3    | 点群生成               | SfMで得たカメラ位置を元に点群生成               |
| 4    | Gaussian Splatting | 点群を元に3D Gaussian Splattingモデルの生成 |
| 5    | 3DGS 編集            | 座標調整やゴースト除去                      |

---

# Step 1
## 高品質な3DGS生成のための推奨撮影設定
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
## 2-1 画像切り出し
1.　**360° Gaussian** を起動します  
2.　**Add Video(s)** をクリックし、Equirectangular 形式の動画を選択します  
3.　**Splitting** を選択し、画像の切り出し条件を設定します

| パラメータ                  | 説明                                        |
| ---------------------- | ----------------------------------------- |
| Extra frame every      | 指定した秒数（またはフレーム数）のインターバルで画像を切り出す           |
| Sharp frame extraction | 前後のフレームと比較して、ボケの少ない画像を優先的に選択するかどうか        |
| Sharpness check range  | 例えば `10` の場合、前後 5 フレームを比較して最もシャープな画像を選択する |

[![360° Gaussian の Splitting 設定画面](https://qiita-user-contents.imgix.net/https%3A%2F%2Fraw.githubusercontent.com%2FTakashiYoshinaga%2F360-to-RealityScan%2Fmain%2FDocuments%2FImages%2F001-360GaussianUI-01.jpg?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=1ebb1bcd6cdfade90ec7bf38fcb2fa06)](https://qiita-user-contents.imgix.net/https%3A%2F%2Fraw.githubusercontent.com%2FTakashiYoshinaga%2F360-to-RealityScan%2Fmain%2FDocuments%2FImages%2F001-360GaussianUI-01.jpg?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=1ebb1bcd6cdfade90ec7bf38fcb2fa06)

## 2-2 画像のマスク｜オプション　有料ツール
1.　**AutoMasker** をクリックします  
2.　**Use AutoMasker** をオンにします  
3.　**Detection Keywords** にピリオド（`.`）区切りでキーワードを入力します

**マスクが重要な 2 つの理由**  
まず、人・車・低テクスチャオブジェクトなど動いたり特徴点の少ない被写体は **SfM のノイズ**になりやすく、カメラ位置の推定精度を下げる　SfM の精度はその後の Gaussian Splatting の出力品質に直結するため、これらをマスクで除外することが重要  
さらに、**トレーニング段階でも同様のノイズが品質を低下さる**同じ被写体が場所によって異なる見た目で映り込むと、Gaussian が正しい形状・色に収束しにくくなる　マスクはこの両方の工程でクオリティを守る役割を果たす

**AutoMasker について**  
AutoMasker は有償（46€）　独立したアプリとして単独で動作するため、360° Gaussian を使った Gaussian Splatting の自動化ワークフローだけでなく、Gaussian Splatting 以外の用途（360° 画像へのマスク処理全般）にも幅広く活用可能
類似ツールを購入するよりもこれを利用・導入する方を検討推奨

[![AutoMasker のマスク結果](https://qiita-user-contents.imgix.net/https%3A%2F%2Fraw.githubusercontent.com%2FTakashiYoshinaga%2F360-to-RealityScan%2Fmain%2FDocuments%2FImages%2F002-MaskImage.jpg?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=93512b27cb841b7bf68637ebc19e357d)](https://qiita-user-contents.imgix.net/https%3A%2F%2Fraw.githubusercontent.com%2FTakashiYoshinaga%2F360-to-RealityScan%2Fmain%2FDocuments%2FImages%2F002-MaskImage.jpg?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=93512b27cb841b7bf68637ebc19e357d)

---
 
# Step 3

## 3-1 SfM (Structure from Motion) 設定
1.　**Alignment** をクリックします  
2.　**Training Method** を設定します
	＊LichtFeld を選択すると、SfM・点群生成・Gaussian Splatting まで一括で実行可能　ただし、LichtFeld Studio のウィンドウが開かない状態で処理が進むため、過程確認不可
	TrainingのStrategyでMRNFの選択が負荷
	
	以下のように設定
	- **Training Method**：`No Training`
	- **SfM**：`SphereSFM`
3.　**Advanced SphereSFM Setting** を開き、**Preset** からカメラの画像サイズを選択
	例：8K で撮影している場合は `Ultra (8K)` を選択
4.　**Matcher** で `sequential` を選択します  
	360°Gaissian v1.4.0 から Loop detection with vocabulary tree がサポートされたため、ループクロージング性能が大幅に向上
	その他の設定はデフォルトのままで問題なし

＊特に特徴の少ないエリアを含むシーンでは、**Realign cubemaps** を有効にすると位置合わせがずれてしまう場合があるため、オフで運用が推奨　状況に応じて使い分け

[![Alignment の設定画面](https://qiita-user-contents.imgix.net/https%3A%2F%2Fraw.githubusercontent.com%2FTakashiYoshinaga%2F360-to-RealityScan%2Fmain%2FDocuments%2FImages%2F003-AlignmentSetting-01.jpg?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=cfdbae77fcce5bacab00dedce9efc6a8)](https://qiita-user-contents.imgix.net/https%3A%2F%2Fraw.githubusercontent.com%2FTakashiYoshinaga%2F360-to-RealityScan%2Fmain%2FDocuments%2FImages%2F003-AlignmentSetting-01.jpg?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=cfdbae77fcce5bacab00dedce9efc6a8)
[![SphereSFM の Preset 設定](https://qiita-user-contents.imgix.net/https%3A%2F%2Fraw.githubusercontent.com%2FTakashiYoshinaga%2F360-to-RealityScan%2Fmain%2FDocuments%2FImages%2F004-SphreSfM_Setting-01.jpg?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=06fe24f59e50b32672e4a7973ddd3d7e)](https://qiita-user-contents.imgix.net/https%3A%2F%2Fraw.githubusercontent.com%2FTakashiYoshinaga%2F360-to-RealityScan%2Fmain%2FDocuments%2FImages%2F004-SphreSfM_Setting-01.jpg?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=06fe24f59e50b32672e4a7973ddd3d7e)

[![SphereSFM の設定例（v1.4.0）](https://qiita-user-contents.imgix.net/https%3A%2F%2Fraw.githubusercontent.com%2FTakashiYoshinaga%2F360-to-RealityScan%2Fmain%2FDocuments%2FImages%2F037-SphereSfM_Setting_140_3.jpg?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=8c939855819a6ad3f9d4290905655f98)](https://qiita-user-contents.imgix.net/https%3A%2F%2Fraw.githubusercontent.com%2FTakashiYoshinaga%2F360-to-RealityScan%2Fmain%2FDocuments%2FImages%2F037-SphereSfM_Setting_140_3.jpg?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=8c939855819a6ad3f9d4290905655f98)


＊`sequential` でうまくいかない場合は、最終手段として `exhaustive` を試す　全画像ペアを総当たりでマッチングするため処理時間は大幅に増加するが、`sequential` では繋ぎきれなかった画像ペアをカバーできる可能性がある
デフォルト設定と比べて計算回数が多くなり多少時間を要しす　まずはデフォルト設定

推奨する設定は以下

1. **Iterations(Global)・Refinements（常時：高め）**
    - 高めに　インライア率が低い難しいペアに対しても正しい位置関係（ジオメトリ）を見つけやすくなる
2. **MinInliers（最小インライア数）**
    - **広範囲のエリア（低め）**：低めに　特徴点が少なく「弱いマッチ」と判定されがちなペアも検証を通過しやすくなり、ループ接続のわずかな糸口を取りこぼしにくくなる
    - **（補足）狭いエリア（高め）**：画像間で多数の特徴点が安定して一致するため、あえて高めに設定し「確実なマッチング」のみを採用することで誤マッチングを排除でき、より精度が高まる
3. **Reprojection threshold（再投影誤差の閾値）**
    - **広範囲のエリア（緩め）**：照明・天候・遠近の変化などでループ始点・終点の視点変化が大きくなる　ここで閾値を厳しくすると特徴の少ない場所でのマッチが弾かれ、ループがクローズ（接続）しない原因になるため、シーンの多様性に合わせて許容度を**緩め**に設定するのが基本
    - **（補足）狭いエリア（厳しめ）**：画像間の視点変化が小さく特徴点が安定するため、逆に閾値を**厳しく（きつめに）**設定しても十分な点が残る　これによりノイズを排除でき、より高精度なカメラ位置推定が可能

つまり、広域スキャンにおいては「**丁寧に検証して（Iterations(Global)/Refinements 高め）、その結果は捨てず（MinInliers 低め）、空間の多様性に合わせて許容度を上げる（Reprojection threshold 緩め）**」という組み合わせによって、SfMの成功率を最大限に引き出す狙いがある

[![SphereSFM の詳細設定例](https://qiita-user-contents.imgix.net/https%3A%2F%2Fraw.githubusercontent.com%2FTakashiYoshinaga%2F360-to-RealityScan%2Fmain%2FDocuments%2FImages%2F005-SphreSfM_Setting-02_5.jpg?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=12193b0d23e48ffe67f5b8cc2a2f8a3a)](https://qiita-user-contents.imgix.net/https%3A%2F%2Fraw.githubusercontent.com%2FTakashiYoshinaga%2F360-to-RealityScan%2Fmain%2FDocuments%2FImages%2F005-SphreSfM_Setting-02_5.jpg?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=12193b0d23e48ffe67f5b8cc2a2f8a3a)


## 3-2 SfM 実行
**Start** をクリックして SfM を実行
処理が完了すると、以下のような画面が表示

[![SfM 完了画面](https://qiita-user-contents.imgix.net/https%3A%2F%2Fraw.githubusercontent.com%2FTakashiYoshinaga%2F360-to-RealityScan%2Fmain%2FDocuments%2FImages%2F006-Complete.jpg?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=47d9f005027893c4158218a89658d408)](https://qiita-user-contents.imgix.net/https%3A%2F%2Fraw.githubusercontent.com%2FTakashiYoshinaga%2F360-to-RealityScan%2Fmain%2FDocuments%2FImages%2F006-Complete.jpg?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=47d9f005027893c4158218a89658d408)
カメラの位置情報と点群が正しく生成されていることを確認

```
📁 動画が置かれたフォルダ
  └── 📁 動画名と同じフォルダ
       └── 📁 train_data
            ├── 📁 images
            ├── 📁 masks
            └── 📁 sparse
```

---

# Step 4
## 4-1 データ読み込み
1.　**LichtFeld Studio** を起動します  
2.　上記で生成された **`train_data`** フォルダをウィンドウにドラッグ＆ドロップします  
3.　**Load DataSet** ダイアログが表示されたら **Load** をクリックします

[![LichtFeld Studio の起動画面](https://qiita-user-contents.imgix.net/https%3A%2F%2Fraw.githubusercontent.com%2FTakashiYoshinaga%2F360-to-RealityScan%2Fmain%2FDocuments%2FImages%2F007-LichtFeldStudioUI-01.jpg?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=1f856c92f5a6e474c4f0f735ad910f55)](https://qiita-user-contents.imgix.net/https%3A%2F%2Fraw.githubusercontent.com%2FTakashiYoshinaga%2F360-to-RealityScan%2Fmain%2FDocuments%2FImages%2F007-LichtFeldStudioUI-01.jpg?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=1f856c92f5a6e474c4f0f735ad910f55)  
[![Load DataSet ダイアログ](https://qiita-user-contents.imgix.net/https%3A%2F%2Fraw.githubusercontent.com%2FTakashiYoshinaga%2F360-to-RealityScan%2Fmain%2FDocuments%2FImages%2F008-LoadDataset_2.jpg?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=f002a2246489894114fbaf7558524e5f)](https://qiita-user-contents.imgix.net/https%3A%2F%2Fraw.githubusercontent.com%2FTakashiYoshinaga%2F360-to-RealityScan%2Fmain%2FDocuments%2FImages%2F008-LoadDataset_2.jpg?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=f002a2246489894114fbaf7558524e5f)

点群と画像が正しく読み込まれたことを確認 
カメラ画像の表示が不要な場合は、画面右側の **Rendering** タブにある **Camera Frustum** のチェックを外す

[![データ読み込み後の画面](https://qiita-user-contents.imgix.net/https%3A%2F%2Fraw.githubusercontent.com%2FTakashiYoshinaga%2F360-to-RealityScan%2Fmain%2FDocuments%2FImages%2F009-LichtFeldStudioUI-02.jpg?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=722b2a9abf36f88a531c93cc2be27748)](https://qiita-user-contents.imgix.net/https%3A%2F%2Fraw.githubusercontent.com%2FTakashiYoshinaga%2F360-to-RealityScan%2Fmain%2FDocuments%2FImages%2F009-LichtFeldStudioUI-02.jpg?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=722b2a9abf36f88a531c93cc2be27748)

> **⚠️ 注意**  
> 読み込み中の場合はCubeの面に画像が表示されていない箇所がある　この状態でGaussian Splattingの学習をスタートさせるとLichtFeld Studioがクラッシュ  
> [![読み込み中の状態](https://qiita-user-contents.imgix.net/https%3A%2F%2Fraw.githubusercontent.com%2FTakashiYoshinaga%2F360-to-RealityScan%2Fmain%2FDocuments%2FImages%2F038-LoadingResult.jpg?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=31e4a80d807cdaa5a07937c48c75a66a)](https://qiita-user-contents.imgix.net/https%3A%2F%2Fraw.githubusercontent.com%2FTakashiYoshinaga%2F360-to-RealityScan%2Fmain%2FDocuments%2FImages%2F038-LoadingResult.jpg?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=31e4a80d807cdaa5a07937c48c75a66a)


## 4-2 トレーニング設定
1.　**Training** タブをクリックします  
2.　**Strategy** で `MRNF` を選択します  
3.　**Steps Scaler** を適宜設定します

|条件|推奨値|
|---|---|
|画像数が 300 枚以下|`1`|
|画像数が 300 枚以上|`画像枚数 / 300`|

> **⚠️ トレーニングがうまくいかない場合**  
> 上記の設定で実行してもGaussian Splattingのトレーニングが進むにつれて収束せずにホワイトアウトしてしまう場合は、Steps Scaler を `画像枚数 / 300` の **2〜3 倍** に設定すると安定しやすい

4.　**Max Gaussians** で最大ガウシアン数を設定します  
基本的にはデフォルト値で問題ありませんが、ディテールが不足していると感じたら値を増やす

＊**オプション設定：** Auto Maskerを使ってマスク画像を作成した場合のみ下記の設定
- **Mask Mode** → `Ignore` に設定
- **Use Alpha as Mask** → チェックを外す

[![トレーニング設定画面](https://qiita-user-contents.imgix.net/https%3A%2F%2Fraw.githubusercontent.com%2FTakashiYoshinaga%2F360-to-RealityScan%2Fmain%2FDocuments%2FImages%2F010-TrainingSettings_2.jpg?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=393097ba8cd561d94f1d736dd7040b8d)](https://qiita-user-contents.imgix.net/https%3A%2F%2Fraw.githubusercontent.com%2FTakashiYoshinaga%2F360-to-RealityScan%2Fmain%2FDocuments%2FImages%2F010-TrainingSettings_2.jpg?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=393097ba8cd561d94f1d736dd7040b8d)


## 4-3 トレーニング実行
1.　マウス操作で、トレーニングの経過を観察したいエリアにクローズアップしておきます  
2.　**Start Training** をクリックしてトレーニングを開始します  
3.　最初はぼんやりとした表示ですが、ステップが進むにつれて徐々にクリアになっていきます

トレーニングステップが上限に達すると自動で終了
途中経過を保存しておきたい場合は、**Save Checkpoint** をクリックするとその時点の結果を記録


## 4-4 書き出し
1.　**File → Export** をクリックします  
2.　出力フォーマットを選択します（例：`.ply` `.sog`）

同じデータ出力でもデータサイズ大きく異なる｜`.sog` 推奨
`.ply` 出力　0.99GB
`.sog` 出力　55.6MB　

---

Step 5
5-1 編集ツール
https://superspl.at/editor
1. SuperSplat Editor を起動させます
2. 4-4で出力したデータをドラッグアンドドロップして開きます
3. ツールを使って編集します
4. エクスポートで Viewer App を選択すると`html`で出力できます

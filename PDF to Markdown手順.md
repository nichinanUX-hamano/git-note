---
date: 2025-07-17
ChatGPT: https://chatgpt.com/share/68787714-e414-8000-bc1a-d6235ae4082c
tags:
  - ターミナル
---
### **要点まとめ**

1. **PDF → Markdown 基本手順**
    
    - pdftotext -layout input.pdf - | pandoc -t gfm -o output.md
        
        - -layout でレイアウト保持しつつテキスト抽出
            
        - Pandoc の **入力フォーマット指定は不要**（-f markdown か省略）
            
        - -f plain は存在しない Reader なのでエラーになる
            
        
    
2. **Unknown input format plain エラー解決**
    
    - -f plain を **-f markdown もしくは省略**に変更すれば OK
        
    
3. **@opendocsg/pdf2md の使い方とディレクトリエラー**
    
    - コマンド例
        
    

```
mkdir -p ./pdfs ./md
npx @opendocsg/pdf2md \
  --inputFolderPath ./pdfs \
  --outputFolderPath ./md --recursive
```

3. -   
        
    - ENOENT: … ./pdfs は **入力フォルダが存在しない**ため。mkdir で作成後に再実行
        
    
4. **pdf2md の仕様上の制限**
    
    - **画像抽出機能は未実装**
        
    - そのため出力は .md のみで、画像ファイルは生成されない
        
    
5. **画像も必要な場合の代替策**
    

|**手法**|**コマンド例・特徴**|
|---|---|
|Poppler pdfimages|pdfimages -png input.pdf assets/img で埋込画像を一括抽出|
|pdftohtml → Pandoc|pdftohtml -c -hidden input.pdf page.html → pandoc --extract-media で Markdown＋画像分離|
|Docling など OSS|docling input.pdf --image-mode referenced --output ./md で OCR・画像分離を自動化|

5.   
    
6. **ワークフロー提案（画像込み最小構成）**
    

```
# 画像抽出
pdfimages -png input.pdf md/assets/img

# テキストを Markdown 化
pdftotext -layout input.pdf - | pandoc -t gfm -o md/input.md

# 必要なら Markdown に ![図](assets/img-000.png) を追記
```

  

---

#### **まとめ**

- **テキスト抽出のみ**なら pdftotext + pandoc が最速。
    
- **pdf2md は画像非対応**で .md だけが出力されるのは仕様。
    
- 図版も欲しい場合は pdfimages や pdftohtml, Docling などを併用して画像を別ファイルとして書き出す。
---
title: Seedance 2.0 Full Step-By-Step Guide + Advanced Techniques
source: https://x.com/Mho_23/status/2043060741616603442
author:
  - "[[@Mho_23]]"
published: 2026-04-12
created: 2026-04-13
description: at this point you've probably seen seedance 2.0 everywhere. every AI content creator is talking about it and for good reason.it's ByteDance'...
tags:
  - X
  - AI
  - Movie
---
![画像](https://pbs.twimg.com/media/HFpoxymW8AAzPAD?format=jpg&name=large)

at this point you've probably seen seedance 2.0 everywhere. every AI content creator is talking about it and for good reason.

it's ByteDance's new AI video model and it works completely different from everything else out there. most AI video tools work the same way - type a prompt, generate, hope it looks good. seedance 2.0 on higgsfield lets you feed it images, videos, audio, and text all at once. each input becomes a reference for something specific like style, motion, camera work, rhythm, or character appearance. instead of just prompting we have FULL creative control now i've tried acessing seedance on multiple platforms and most of them are either unreliable or straight up don't work properly. Higgsfield is by far the most efficient place to use it right now. there is no waitlist or queues and it is available to everyone globally. and they actually have the full omni-reference system implemented which is what makes seedance 2.0 actually useful. this guide is mostly going to focus on seedance 2.0 on higgsfield and how to use it properly. but before we get into that, you need good starting images and realistic audio. i've talked about this a lot in my other guides so here's a quick overview.

**CREATING REALISTIC STARTING IMAGES**

your starting image is the foundation. if it looks like AI slop, your video is going to look like AI slop.

the key is using JSON prompts for color grading in Nano Banana Pro so your images don't come out with that standard grey AI look.

![画像](https://pbs.twimg.com/media/HFj1nK6WYAEpQLz?format=jpg&name=large)

how to create realistic AI images

another thing i do that works really well is finding reference content on TikTok in my niche. so if i'm making content for a coffee brand, i'll search that brand on TikTok and find videos of real people reviewing the product. screenshot a frame that looks good, put it into Claude or Gemini, and ask it to create a JSON prompt to recreate that image. then i adjust the prompt to make my own unique character with different clothes, different background, whatever i need. this way my starting frames already look like the type of content that performs in that niche. make sure your starting image is high quality before moving to video. garbage in garbage out.

**CREATING REALISTIC AI VOICES**

the audio is what makes or breaks the realism. you can have perfect visuals but if the voice sounds robotic, people scroll past immediately.

![画像](https://pbs.twimg.com/media/HFj2SA6WkAAbjbH?format=jpg&name=large)

generate your voiceover before you generate your video. you'll need this audio file to upload as a reference in Higgsfield.

but there's another method i use that gets even more realistic results. instead of generating audio separately, you can find a video of someone talking with the exact voice quality you want, extract that audio, and upload it to Higgsfield as a voice ID reference. then you tell seedance to use that audio as the voice reference but make them say your own dialogue instead.

so the prompt would be something like: "use this audio as voice ID reference for her voice. do not make her say the words in the audio, just use it as a voice ID."

this lets you copy any realistic voice and make them say whatever you want. the model replicates that voice for your custom dialogue while keeping the natural tone. this is one of the best ways to get realistic voices right now because you're not generating from scratch, you're referencing something that already sounds real. if this isnt clear no worries, you will understand more about what I mean in a second..

**THE SEEDANCE 2.0 WORKFLOW ON HIGGSFIELD**

now you have your starting image and your audio. this is where Higgsfield comes in.

the specs: up to 9 images as input up to 3 videos (15s max total) up to 3 audio files (15s max MP3) 4-15 second output duration per generation native 2K resolution generates native sound effects and music 12 files max per generation

15 seconds per generation is a lot compared to other models doing 5-8 seconds. and here's the thing. with seedance you're not stitching together a bunch of random clips hoping they match. you generate your first 15 seconds, then you use that video as a reference and extend it. the model maintains the same character, same voice, same environment. you can chain these extensions together infinitely.

most other models require you to generate like 50 different clips to stitch together a 40 second video. it takes forever and the clips never match properly. with seedance i'm generating 3 clips and i have a 45 second video that flows naturally. the efficiency is insane once you understand the workflow.

**THE @ SYSTEM**

this is the core of how seedance 2.0 works on Higgsfield and why it feels like actual directing instead of prompting.

when you upload assets to Higgsfield they get labeled automatically as [@Image1](https://x.com/@Image1), [@Image2](https://x.com/@Image2), [@Video1](https://x.com/@Video1), [@Audio1](https://x.com/@Audio1) and so on. then you reference them directly in your prompt to tell the model exactly what each file is for.

for AI UGC your basic workflow looks like this:

upload your Nano Banana starting image as [@Image1](https://x.com/@Image1) upload your voiceover or voice reference as [@Audio1](https://x.com/@Audio1) if your character is holding a product, upload the product image as [@Image2](https://x.com/@Image2)

then your prompt references each one: "[@Image1](https://x.com/@Image1) is the starting image of the video. [@Image2](https://x.com/@Image2) is how the coffee bag looks like. for the reference of the dialogue and audio, use [@Audio1](https://x.com/@Audio1)."

but here's where it gets powerful. you can get extremely specific with what you want to happen in each part of the video. seedance works best when you specify everything. don't give it too much creativity. if you know exactly what you want and exactly how you want it to look, there's no better model than seedance to follow your exact instructions.

**THE TIMESTAMP METHOD**

this is the prompting system that gets the best results.

instead of writing a general prompt and hoping for the best, you break down exactly what happens at each timestamp. every 4-5 seconds, you specify the dialogue and the exact visuals you want.

example structure: "0-4 seconds: introduction. dialogue: 'i just made a peanut butter cup protein coffee with 25 grams of protein.' visuals: the video begins with subject holding a clear round glass jar filled with light brown coffee. her left hand holds the glass while her right hand actively stirs the drink."

"5-12 seconds: benefits explanation. dialogue: 'getting 20 to 30 grams of protein right in the morning in your coffee really helps so much.' visuals: subject sets down the glass, picks up the protein bag from [@Image2](https://x.com/@Image2), holds it toward camera while speaking."

you do this for every section of your video. the model follows everything you tell it to do to the literal last sentence. this is how you get consistent, usable output instead of random generations you can't use.

**THE MODEL HANDLES EDITING FOR YOU**

one thing people don't realize about seedance is that it's trained by ByteDance. the people who made TikTok. they already understand video editing, cuts, transitions, pacing. the model knows what makes content feel native to short form platforms.

i don't specify cuts in my prompts and the model still adds them naturally. it cuts between angles, it handles transitions, it adds movement that feels like real UGC content. you can see in the output where it's cutting to different frames on its own. that's all the model cooking.

and if you want specific edits, you can tell it directly. want a jump cut at a certain moment? specify it. want a zoom in when they reveal the product? specify it. the model does exactly what you ask.

this is why the editing in post is so simple. i'm putting together like 3-5 clips for a 45 second video and the model already handled 95% of the work. i'm just arranging the clips and maybe adding captions.

**EXTENDING YOUR VIDEOS**

once you have your first 15 seconds, everything else becomes easy.

download your first clip. upload it back to Higgsfield as [@Video1](https://x.com/@Video1). then prompt: "extend this video. keep the voice the same as the original clip." add any new product images you need for the next section. specify what happens in the next 15 seconds.

the model maintains continuity with the original clip. same character, same voice, same environment. you're not hoping clips match, you're literally extending the same video.

prompt example for extension: "extend [@Video1](https://x.com/@Video1). for the protein milk, when she says protein milk, use this bottle ([@Image2](https://x.com/@Image2)). keep the voice the same as the original clip. 16-30 seconds: she explains the benefits. dialogue: 'getting protein in the morning helps so much. it keeps you satiated so you're not snacking.' visuals: she picks up the protein milk bottle, shows it to camera, pours it into her coffee."

chain these together and you can build out content as long as you need. i usually do 3 extensions for a 45-60 second video. the whole process takes maybe 20 minutes once you have your prompting system down.

**BYPASSING THE CHARACTER LIMIT**

seedance has a 2000 character limit per prompt which can be restrictive if you want detailed timestamps and movement descriptions.

here's the workaround. go into Canva and create an image with your full detailed prompt as text. all the movements you want, broken down by second. upload that image to Higgsfield as a reference.

then in your actual prompt you just say: "transcribe this image and use the movements described here."

seedance is smart enough to read the text in your reference image and use those instructions. this lets you bypass the character limit and have extremely detailed prompts for complex videos.

you can also use this for any long prompt situation. put your detailed instructions in a Canva image, upload it as a reference, tell the model to read and follow it.

**POST PRODUCTION**

once you have your clips, the editing is minimal.

export from Higgsfield, bring into video editor of choice, arrange your clips, add captions if needed. the model already handled the cuts and transitions so you're mostly just putting things in order.

for upscaling, i run the video through Topaz video upsacler in higgsfield at 2x upscale and 60fps. then i bring it back into CapCut and export at 30fps. this smooths everything out while keeping it looking natural for social platforms. most content is usually 30fps or 24fps so you don't want 60fps in your final output.

**PRO TIPS**

use high quality starting images. if your Nano Banana image has artifacts, your video inherits them.

generate audio first or use the voice ID reference method. robotic audio ruins everything.

be extremely specific in your prompts. specify every movement, every second, every visual detail. seedance follows instructions better than any other model but you have to actually give it instructions.

use the timestamp method. break your video into 4-5 second chunks and describe exactly what happens in each one.

extend instead of regenerating. once you have a good first clip, use it as a reference and extend. way more efficient than starting over.

use the Canva method for long prompts. put detailed instructions in an image and upload it as a reference to bypass the character limit.

**THE FULL PIPELINE**

the key is having a detailed prompting system that covers every part of the video. once you have that dialed in, you can pump out videos fast. i'm talking 5-10 minutes per video once you understand the workflow.

seedance 2.0 is available right now on Higgsfield. with full power for everyone globally. the omni-reference system and extension features are what make this model incredible for production work.

this is the workflow we're using right now for AI UGC across paid ads and organic content. the model handles so much of the work that used to be manual. you just have to learn how to direct it properly. happy to partner with [higgsfield.ai](http://higgsfield.ai/) on this

---


## Seedance 2.0 完全ステップバイステップ・ガイド ＋ 応用テクニック

現時点で、Seedance 2.0をいたる所で見かけていることでしょう。あらゆるAIクリエイターがこの話題で持ち切りですが、それには正当な理由があります。

これはByteDance社による新しいAI動画モデルで、既存のツールとは全く異なる仕組みで動きます。ほとんどのAI動画ツールは「プロンプトを入力し、生成し、上手くいくことを祈る」という同じ方式です。しかし、**Higgsfield**上のSeedance 2.0では、画像、動画、音声、テキストを一度に読み込ませることができます。それぞれの入力が、スタイル、動き、カメラワーク、リズム、あるいはキャラクターの容姿といった「特定の要素」の参照（リファレンス）になります。

単なるプロンプト入力ではなく、今や**完全なクリエイティブ・コントロール**を手に入れたのです。

私は複数のプラットフォームでSeedanceへのアクセスを試みましたが、その多くは不安定か、あるいは正しく機能しません。現時点でHiggsfieldは、圧倒的に効率的な場所です。待機リストやキューはなく、世界中の誰もが利用可能です。そして何より、Seedance 2.0を真に実用的なものにしている「オムニ・リファレンス・システム」が完全に実装されています。

このガイドでは主にHiggsfieldでのSeedance 2.0の正しい使い方に焦点を当てますが、その前に、質の高い「開始画像」と「リアルな音声」が必要です。これについては他のガイドでも詳しく触れていますが、ここで手短に概要を説明します。

---

### 1. リアルな開始画像の作成

開始画像は土台です。それが「いかにもAIで作ったような質の低いもの（AI slop）」であれば、動画もそうなります。

ポイントは、**Nano Banana Pro**でカラーグレーディングに**JSONプロンプト**を使用することです。これにより、AI特有の標準的なグレーがかった質感を避けることができます。

> **リアルなAI画像を作るコツ：**
> 
> 私がよくやる非常に効果的な方法は、自分のターゲットとするジャンルのリファレンス・コンテンツをTikTokで見つけることです。例えばコーヒーブランドのコンテンツを作るなら、TikTokでそのブランドを検索し、実際の人が製品をレビューしている動画を探します。良さそうなフレームをスクリーンショットし、それをClaudeやGeminiに読み込ませて、その画像を再現するためのJSONプロンプトを作成させます。
> 
> その後、服装や背景、キャラクターなどを自分好みに調整します。こうすることで、開始フレームの時点で、そのジャンルで実際に成果を上げているコンテンツに近いルックになります。

**「ゴミを入力すればゴミが出る（Garbage in, Garbage out）」**という言葉通り、動画に進む前に開始画像が高品質であることを確認してください。

---

### 2. リアルなAI音声の作成

音声はリアリズムを左右する決定的な要素です。映像が完璧でも、声がロボットのようであれば、視聴者は即座にスクロールしてしまいます。

動画を生成する前にボイスオーバー（ナレーション）を生成してください。この音声ファイルをHiggsfieldにリファレンスとしてアップロードする必要があります。

さらにリアルな結果を得るための別の方法があります。音声を個別に生成する代わりに、**理想的な声の質の人が話している動画**を見つけ、その音声を抽出してHiggsfieldに「Voice IDリファレンス」としてアップロードする方法です。そしてSeedanceに対し、その音声を声の参照として使いつつ、自分が用意したセリフを喋らせるよう指示します。

- **プロンプト例：**
    
    > 「この音声を彼女の声のVoice IDリファレンスとして使用してください。音声内の言葉を喋らせるのではなく、あくまでVoice IDとしてのみ使用してください。」
    

これにより、あらゆるリアルな声をコピーし、好きなことを喋らせることができます。モデルはその自然なトーンを維持したまま、カスタム・ダイアログを再現します。ゼロから生成するのではなく、すでにリアルなものを参照しているため、現時点で最もリアルな音声を得る方法の一つです。

---

### 3. HiggsfieldでのSeedance 2.0 ワークフロー

画像と音声が揃ったら、Higgsfieldの出番です。

**スペック概要：**

- **画像：** 最大9枚
    
- **動画：** 最大3本（計15秒まで）
    
- **音声：** 最大3ファイル（15秒までのMP3）
    
- **生成時間：** 1回につき4〜15秒
    
- **解像度：** ネイティブ2K
    
- **その他：** 効果音やBGMもネイティブ生成、1回の生成で最大12ファイル使用可能
    

1回の生成で15秒というのは、他のモデル（5〜8秒）と比べて非常に長いです。さらに、Seedanceではバラバラのクリップを繋ぎ合わせて一致することを祈る必要はありません。最初の15秒を生成したら、その動画をリファレンスとして使用し、**「延長（Extend）」**します。モデルは同じキャラクター、同じ声、同じ環境を維持します。これらを無限に繋げることが可能です。

---

### 4. 「@」システムによるディレクション

これがHiggsfieldにおけるSeedance 2.0の核となる仕組みであり、単なるプロンプト入力が「演出（ディレクティング）」に感じられる理由です。

アセットをアップロードすると、自動的に `@Image1`、`@Image2`、`@Video1`、`@Audio1` といったラベルが付与されます。プロンプト内でこれらを直接参照し、各ファイルが何の役割を持つかをモデルに伝えます。

**AI UGC（ユーザー生成コンテンツ風広告）の基本ワークフロー：**

1. Nano Bananaで作った開始画像を `@Image1` としてアップロード。
    
2. ボイスオーバーまたは声のリファレンスを `@Audio1` としてアップロード。
    
3. キャラクターが製品を持っているなら、製品画像を `@Image2` としてアップロード。
    

**プロンプトの構成：**

> 「@Image1 は動画の開始画像です。@Image2 はコーヒーバッグの外見です。ダイアログと音声のリファレンスには @Audio1 を使用してください。」

ここからが強力な点です。動画の各パートで何が起きるかを非常に具体的に指定できます。Seedanceは全てを細かく指定した時に最高のパフォーマンスを発揮します。モデルに「自由な創造性」を与えすぎないでください。自分の意図が明確であればあるほど、Seedanceほど正確に指示に従うモデルはありません。

---

### 5. タイムスタンプ・メソッド

最も良い結果が得られるプロンプト作成法です。

漠然としたプロンプトを書くのではなく、タイムスタンプごとに何が起きるかを分解します。4〜5秒ごとに、セリフと具体的なビジュアルを指定します。

**構成例：**

- **0-4秒：** 導入。
    
    - **セリフ：** 「今、タンパク質25g入りのピーナッツバター・プロテインコーヒーを作ったところです。」
        
    - **ビジュアル：** 薄茶色のコーヒーが入った丸い透明なグラスを持つ人物から始まります。左手でグラスを持ち、右手で飲み物をかき混ぜています。
        
- **5-12秒：** メリットの説明。
    
    - **セリフ：** 「朝一番のコーヒーで20〜30gのタンパク質を摂ると、本当に調子がいいんです。」
        
    - **ビジュアル：** 人物はグラスを置き、@Image2 のプロテインバッグを手に取り、喋りながらカメラの方へ向けます。
        

これを動画のセクションごとに行います。モデルは文字通り最後の文章まで指示に従います。これにより、使い物にならないランダムな生成結果ではなく、一貫した素材を得ることができます。

---

### 6. モデルが編集もこなす

意外と知られていないのが、SeedanceはTikTokを作ったByteDanceによって訓練されているという点です。彼らは動画編集、カット、トランジション、テンポを熟知しています。モデルは、何がショート動画プラットフォームに馴染むかを知っているのです。

プロンプトでカット割りを指定しなくても、モデルは自然にカットを追加します。アングルの切り替え、トランジション、リアルなUGCらしい動きを自動で行います。特定の編集（特定の瞬間のジャンプカットやズームなど）が必要な場合は、指示すればその通りに動いてくれます。

そのため、後編集（ポストプロダクション）は非常にシンプルになります。45秒の動画を作るのに3〜5個のクリップを並べるだけで、作業の95%はモデルが既に終えています。

---

### 7. 動画の延長（Extending）

最初の15秒ができれば、あとは簡単です。

最初のクリップをダウンロードし、Higgsfieldに `@Video1` として再アップロードします。

**延長用プロンプト例：**

> 「@Video1 を延長してください。声は元のクリップと同じままにしてください。16-30秒：彼女はメリットを説明します。セリフ：『朝にタンパク質を摂ると…（以下略）』。ビジュアル：プロテインミルクのボトルを手に取り、カメラに見せてからコーヒーに注ぎます。」

これを繰り返せば、必要な長さのコンテンツを構築できます。通常、45〜60秒の動画なら3回の延長で作れます。慣れれば全工程で20分程度です。

---

### 8. 文字数制限の回避（Canvaメソッド）

Seedanceのプロンプトには2000文字の制限があり、詳細なタイムスタンプを書くと足りなくなることがあります。

**回避策：**

1. **Canva**などで、詳細なプロンプト全文をテキストとして書いた画像を作成します。
    
2. その画像をHiggsfieldにリファレンスとしてアップロードします。
    
3. 実際のプロンプトにはこう書きます：**「この画像を文字起こしし、そこに記載されている動きに従ってください。」**
    

Seedanceはリファレンス画像内のテキストを読み取るほど賢いため、これで制限を回避し、非常に複雑な指示を与えることができます。

---

### 9. ポストプロダクション（仕上げ）

Higgsfieldから書き出したら、お好みのビデオエディター（CapCutなど）に並べます。

**アップスケーリングのコツ：**

Higgsfield内のTopazビデオアップスケーラーで「2倍アップスケール ＋ 60fps」で処理します。その後、CapCut等に戻して**30fpsで書き出し**ます。これにより、SNSで自然に見える質感を保ちつつ、全体を滑らかにすることができます。最終出力が60fpsだと不自然に見えることが多いので、30fpsか24fpsが理想です。

---

### プロのヒント（まとめ）

- **高品質な開始画像を使う：** 画像にノイズがあれば、動画にも引き継がれます。
    
- **音声から先に作る：** ロボットのような声は全てを台無しにします。
    
- **具体的に書く：** あらゆる動き、秒数、ビジュアルを指示してください。
    
- **タイムスタンプ・メソッド：** 4〜5秒単位で描写します。
    
- **作り直しより「延長」：** 良いクリップができたら、それを元に伸ばす方が効率的です。
    
- **長文プロンプトはCanvaで：** 画像に指示を書いて読み込ませます。
    

Seedance 2.0は、これまで手作業だったことの多くを自動化してくれます。あなたはただ、正しく「演出（ディレクト）」する方法を学ぶだけです。

制作を楽しんでください！ (Higgsfield.aiとのパートナーシップにより提供)
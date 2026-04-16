---
title: 【なぜダサくなる？】Claude CodeでWebサイトやアプリを開発する時の８つのポイントを徹底解説！【POSTS代表 梶谷健人】
source: https://www.youtube.com/watch?v=XauDoPh5Fh8
author:
  - "[[テレ東AIアカデミー【公式】]]"
published: 2026-04-12
created: 2026-04-17
description: 専門知識ゼロでも、生成AIを活用してプロ級のサイトを爆速で作れる「8つのポイント」を、#梶谷健人 さんが画面を見せながら徹底解説。🗓 トピックとタイムスタンプ 00:00　オープニング／ゲスト紹介02:19　①作成の失敗の理由07:07　② AIの弱点を補う設計図10:12　③「◯◯させてから」作らせる　12:59　④脱・AIデザインツール15:31　⑤効率的な指示の出し方16
tags:
  - Claude
  - Tips
  - web
---
ご提示いただいた動画は、POSTS代表の梶谷健人氏が、AI開発ツール「Claude Code」を使っておしゃれなウェブサイトやアプリを開発するための**8つの重要ポイント**を解説しているものです。

主な内容は以下の通りです。

### 1. 「プランモード」での徹底した壁打ち [[02:26](https://www.google.com/search?q=http://www.youtube.com/watch%3Fv%3DXauDoPh5Fh8%26t%3D146)]

Claude Codeには3つのモードがありますが、まずは**プランモード**でAIと対話し、仕様書や実装計画を練ることが重要です。いきなりコードを書かせず、理想と計画のズレを最小化することで失敗を防げます。

### 2. 「plan.md」で記憶を管理する [[07:14](https://www.google.com/search?q=http://www.youtube.com/watch%3Fv%3DXauDoPh5Fh8%26t%3D434)]

AIはセッションごとに「記憶喪失」になる特性があるため、`plan.md`というマークダウン形式のファイルにゴールや進捗を記録します。これを読み込ませることで、AIが文脈を維持しながら開発を継続できます。

### 3. 開発を複数ステップ（フェーズ）に分ける [[10:19](https://www.google.com/search?q=http://www.youtube.com/watch%3Fv%3DXauDoPh5Fh8%26t%3D619)]

100%を一度に作らせようとするとバグが発生しやすくなります。全体を20%ずつの部品に分けるなど、**スモールステップで進める**のがコツです。フェーズの区切り方自体もAIに相談できます [[12:41](https://www.google.com/search?q=http://www.youtube.com/watch%3Fv%3DXauDoPh5Fh8%26t%3D761)]。

### 4. デザイン特化AI「v0」との組み合わせ [[13:06](https://www.google.com/search?q=http://www.youtube.com/watch%3Fv%3DXauDoPh5Fh8%26t%3D786)]

デザインの質を担保するために、まずはWebデザインに強いAIサービス「**v0**」でUIを作成し、そのコードをClaude Codeに渡して機能を実装するという役割分担が推奨されています。

### 5. コンテキストを伝えるための音声入力 [[15:38](https://www.google.com/search?q=http://www.youtube.com/watch%3Fv%3DXauDoPh5Fh8%26t%3D938)]

タイピングよりも**音声入力**の方が、自分のぼんやりしたイメージや背景情報を100%伝えやすくなります。AIに詳細なインプットを与えることで、より理想に近いアウトプットが得られます。

### 6. 定番の技術スタック（shadcn/uiなど）の活用 [[16:40](https://www.google.com/search?q=http://www.youtube.com/watch%3Fv%3DXauDoPh5Fh8%26t%3D1000)]

UIコンポーネントライブラリの「**shadcn/ui**」など、AIと相性の良い技術をあらかじめ指定します。これらを使うことで、ゼロから作ることなく、洗練されたデザインの部品を即座に導入できます [[17:37](https://www.google.com/search?q=http://www.youtube.com/watch%3Fv%3DXauDoPh5Fh8%26t%3D1057)]。

### 7. 随時のドキュメント更新 [[20:11](https://www.google.com/search?q=http://www.youtube.com/watch%3Fv%3DXauDoPh5Fh8%26t%3D1211)]

開発の途中で決まったことや、乗り越えたバグの内容をその都度ドキュメントに反映させます。AIの記憶容量には限りがあるため、常に最新の状態をテキスト化しておくことが長期プロジェクトの成功の鍵です。

### 8. 「車輪の再発明」をしない [[21:49](https://www.google.com/search?q=http://www.youtube.com/watch%3Fv%3DXauDoPh5Fh8%26t%3D1309)]

ユーザー認証やデータベース、検索機能など、既存の優れたサービス（Supabaseなど）があるものはそれらを積極的に利用します。全てを自作するよりも、既存のパーツを組み合わせる方が圧倒的に早く高品質なものが作れます。

**動画はこちら：** [【なぜダサくなる？】Claude CodeでWebサイトやアプリを開発する時の８つのポイントを徹底解説！【POSTS代表 梶谷健人】](https://www.youtube.com/watch?v=XauDoPh5Fh8)
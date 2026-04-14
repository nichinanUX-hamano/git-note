---
title: "Gemini CLI : オープンソース AI エージェント | Google Cloud 公式ブログ"
source: "https://cloud.google.com/blog/ja/topics/developers-practitioners/introducing-gemini-cli/"
author:
  - "[[Ryan J. Salva]]"
published: 2025-06-26
created: 2025-06-30
description:
tags:
  - "Gemini"
---
デベロッパー

## Gemini CLI: オープンソース AI エージェント

2025年6月26日

![https://storage.googleapis.com/gweb-cloudblog-publish/images/Gemini_CLI.max-2100x2100.png](https://storage.googleapis.com/gweb-cloudblog-publish/images/Gemini_CLI.max-2100x2100.png)

##### Ryan J. Salva

Senior Director, Product Management

※この投稿は米国時間 2025 年 6 月 25 日に、 [The Keyword blog](https://blog.google/technology/developers/introducing-gemini-cli-open-source-ai-agent/) に投稿されたものの抄訳です。

開発者にとって、コマンドラインインターフェース (CLI) は単なるツールではなく、日々の業務の基盤です。ターミナルの効率性、汎用性、および可搬性により、作業を遂行するための不可欠なユーティリティとなっています。開発者のターミナルへの依存が続く中、AI による統合アシスタンスの需要も高まっています。

そこで Google Cloud は Gemini の強力な機能をターミナルに直接統合するオープンソース AI エージェント [Gemini CLI](http://github.com/google-gemini/gemini-cli) を発表します。これにより、Gemini へのアクセスがより容易になり、プロンプトからモデルへの経路が短縮されます。Gemini CLI はコーディングにおいて優れた性能を発揮しますが、その可能性はそれだけに留まりません。コンテンツ生成、問題解決、詳細なリサーチ、タスク管理まで、幅広い用途に対応する多機能ローカル ユーティリティとして活用できます。

さらに、Gemini CLI を Google の AI コーディングアシスタントである [Gemini Code Assist](https://codeassist.google/) と統合しました。これにより、無償版、Standard 版、Enterprise 版 の Code Assist プランのユーザーが、VS Code と Gemini CLI の両方で、プロンプト駆動の AI ファーストなコーディングを利用できるようになります。

![https://storage.googleapis.com/gweb-cloudblog-publish/original_images/Gemini_CLI_GIF.gif](https://storage.googleapis.com/gweb-cloudblog-publish/original_images/Gemini_CLI_GIF.gif)

開発者、ビルダー、クリエーターは、Gemini CLI を通じて Gemini 2.5 Pro の機能を直接ターミナルで利用できます。

### 個人開発者向けの最大級の利用制限

Gemini CLI を無料で利用するには、個人の Google アカウントでログインし、無償版の Gemini Code Assist ライセンスを取得するだけです。この無料ライセンスにより、Gemini 2.5 Pro と 100 万トークンという広大なコンテキスト ウィンドウにアクセスできます。プレビュー期間中に利用制限することがほとんどないように、業界最大級の利用枠を提供します。毎分 60 回モデル リクエスト、1日あたり1,000 回のリクエストを無料で提供します。

複数のエージェントを同時に実行する必要があるプロの開発者、または特定モデルを優先的に利用したい場合は、使用量ベース課金の [Google AI Studio](https://aistudio.corp.google.com/apikey) または Vertex AI キー、あるいはGemini Code Assist Standard 版または Enterprise 版ライセンスをご利用いただけます。

![https://storage.googleapis.com/gweb-cloudblog-publish/images/image3_0qdvSLs.max-1100x1100.png](https://storage.googleapis.com/gweb-cloudblog-publish/images/image3_0qdvSLs.max-1100x1100.png)

Gemini CLI は、毎分 60 回、1 日 1,000 回という業界最大級のモデル リクエストを無料で提供します。

### コマンドラインで強力なモデルを

現在プレビュー中の Gemini CLI は、コードの理解やファイル操作から、コマンド実行や動的なトラブルシューティングまで、強力な AI 機能を提供します。これにより、コマンド ラインでの作業体験が飛躍的に向上し、自然言語によるコード記述、問題のデバッグ、ワークフローの合理化が可能になります。

組み込みツールの機能により、以下のことを実現します。

- **Google 検索でプロンプトの根拠付け：** ウェブページを取得し、リアルタイムの外部コンテキストをモデルに提供できます。
- Model Context Protocol（MCP）の組み込みサポートやバンドルされた拡張機能を通じて、 **Gemini CLI の機能を拡張** できます。
- **プロンプトと指示をカスタマイズ** し、特定のニーズやワークフローに合わせてGemini を調整できます。
- スクリプト内で Gemini CLI を非対話的に呼び出すことで、 **タスクを自動化し、既存のワークフローと統合** できます。

Gemini CLI は、Veo とImagen を用いて、オーストラリアでの茶トラ猫の冒険に関するショート動画を作成するなど、さまざまなタスクに活用できます。

### オープンで拡張可能

Gemini CLI は完全に [オープンソース（Apache 2.0）](https://github.com/google-gemini/gemini-cli/blob/main/LICENSE) であるため、開発者はコードを検査してその動作を理解し、セキュリティへの影響を検証できます。Google Cloud は、バグの報告、機能の提案、セキュリティ プラクティスの継続的な改善、コードの改善の提出を通じて、グローバルな開発者コミュニティからの [本プロジェクトへの貢献](https://github.com/google-gemini/gemini-cli/blob/main/CONTRIBUTING.md) を歓迎します。GitHub リポジトリへの [問題の投稿](http://github.com/google-gemini/gemini-cli/issues) や、 [アイデアのご提案](http://github.com/google-gemini/gemini-cli/discussions) をお待ちしています。

また、Gemini CLI は、MCP、システムプロンプト（GEMINI.md経由）、個人およびチーム設定などの新しい標準に基づいて構築しており、拡張可能な設計になっています。ターミナルは個人の空間であり、誰もが自分らしくカスタマイズする自由を持つべきと考えています。

### Gemini Code Assist との技術共有

IDE が適切なツールとなる場面もあります。そのような場合でも、強力なAIエージェントのあらゆる機能を活用して、迅速に反復し、学習し、問題を解決したいと思うはずです。

学生、趣味で開発を行う人、プロの開発者向けの Google AI コーディングアシスタントである [Gemini Code Assist](https://codeassist.google/) は、Gemini CLI と同じテクノロジーを共有するようになりました。VS Code では、エージェント モードを使用してチャット ウィンドウに任意のプロンプトを入力できます。Code Assist がテストの作成、エラーの修正、機能の構築、さらにはコードの移行までをあなたの代わりに実行します。プロンプトに基づいて、Code Assist のエージェントは多段階の計画を構築し、失敗した実装パスから自動回復し、想像を超えるソリューションを提案します。

Gemini Code Assist のチャット エージェントは、多段階の協力的な推論エージェントであり、シンプルなコマンド応答インタラクションの機能を拡張します。

Gemini Code Assist のエージェントモードは、 [Insiders チャネル](https://developers.google.com/gemini-code-assist/docs/use-agentic-chat-pair-programmer#before-you-begin) を通じて、すべてのプラン （無償版、Standard、Enterprise）で、追加費用なしで利用いただけます。まだ Gemini Code Assist をご利用でない開発者の方は、ぜひお試しください。業界トップクラスの使用制限を無償で提供しており、 [使用開始](https://codeassist.google/) には 1 分もかかりません。

### 簡単な開始方法

もう待つ理由はありません。今すぐ Gemini CLI でターミナル体験をアップグレードしましょう。Gemini CLI は [こちら](http://github.com/google-gemini/gemini-cli) からインストールいただけます。メールアドレスを入力するだけで、ターミナルで Gemini を実質的に無制限に利用できるようになります。

##### 関連記事

[![https://storage.googleapis.com/gweb-cloudblog-publish/images/01_-_AI__Machine_Learning_H1ZyZG8.max-700x700.jpg](https://storage.googleapis.com/gweb-cloudblog-publish/images/01_-_AI__Machine_Learning_H1ZyZG8.max-700x700.jpg)](https://cloud.google.com/blog/ja/products/ai-machine-learning/how-to-evaluate-your-gen-ai-at-every-stage)

[AI & Machine Learning](https://cloud.google.com/blog/ja/products/ai-machine-learning/how-to-evaluate-your-gen-ai-at-every-stage)

あらゆる段階での生成 AI の評価方法を解き明かす

執筆者: Irina Sigler • 所要時間: 5 分

[View original](https://cloud.google.com/blog/ja/products/ai-machine-learning/how-to-evaluate-your-gen-ai-at-every-stage)

[![https://storage.googleapis.com/gweb-cloudblog-publish/images/01_-_AI__Machine_Learning_H1ZyZG8.max-700x700.jpg](https://storage.googleapis.com/gweb-cloudblog-publish/images/01_-_AI__Machine_Learning_H1ZyZG8.max-700x700.jpg)](https://cloud.google.com/blog/ja/products/ai-machine-learning/build-multimodal-agents-using-gemini-langchain-and-langgraph)

[AI & Machine Learning](https://cloud.google.com/blog/ja/products/ai-machine-learning/build-multimodal-agents-using-gemini-langchain-and-langgraph)

マルチモーダル エージェント チュートリアル: Gemini、Langchain、LangGraph を使用してオブジェクト検出エージェントを構築する方法

執筆者: Matthew Dalida • 所要時間: 4 分

[View original](https://cloud.google.com/blog/ja/products/ai-machine-learning/build-multimodal-agents-using-gemini-langchain-and-langgraph)
---
title: 進化した Google の Stitch でデザイン生成から MCP・Skills 連携まで試してみた
source: https://dev.classmethod.jp/articles/new-stitch-ai-design/
author:
  - "[[Shiina Yuichi]]"
published: 2026-03-30
created: 2026-04-13
description: 大幅にリニューアルされた Google の Stitch でデザイン生成を試しました。Claude Code から MCP サーバー経由での操作や Agent Skills によるプロンプト改善・デザインシステムの自動生成もやってみました。
tags:
  - clippings
  - Google
  - Gemini
---
この記事の内容を要約します。

---

## 記事の概要：進化した Google Stitch を試してみた

Google の AI デザインツール「Stitch」が大幅リニューアルされ、その新機能を試した体験レポートです。Claude Code と MCP サーバー、Agent Skills との連携も検証しています。

---

### 主なアップデート内容（5つ）

以下の5つの主要アップグレードが行われました。

1. **AI-Native Canvas** — AIを前提に設計された新キャンバス
2. **Smarter Design Agent** — より賢くなったデザインエージェント
3. **Voice** — 音声による指示でのデザイン操作
4. **Instant Prototypes** — ワンクリックでのプロトタイプ生成
5. **Design Systems と DESIGN.md** — デザインシステムの定義と共有

**DESIGN.md とは**：カラーパレット・タイポグラフィ・コンポーネントパターンなどを Markdown で定義することで、AI 生成時の画面間の統一感を保てる仕組みです。

---

### 実際に試したこと

**デザイン生成** ベーカリーショップのオンライン注文ページを詳細なプロンプトで生成したところ、美味しそうな画像とともにプロンプト通りのデザインが再現されました。

**アノテーション** デザインの特定箇所に注釈（例：在庫切れ商品を「SOLD OUT」表示）を付与すると、AIがその情報をもとにデザインを再生成してくれます。

**AI編集** 生成されたテキストや画像はさらに AI を使って編集でき、ヒーローイメージをメロンパンに変更するといった操作が可能です。

**モバイルアプリ版・プロトタイプ** Webサイトのデザインからワンクリックでモバイルアプリ版を生成したり、スクロール・ホバーアニメーションなどが動作するインタラクティブなプロトタイプも生成できます。

**エクスポート** AI Studio、Figma、Jules、ZIP、コードコピー、MCP、プロジェクト概要、Instant Prototype など多様な形式でエクスポートが可能です。

---

### Stitch MCP 連携

MCP サーバーを通じて Claude Code や Cursor などの AI ツールから Stitch を直接操作できます。リモート MCP のため認証が必要で、API キーまたは OAuth が選べます。現時点では12個のツールが利用可能とのことです。

---

### Agent Skills 連携

Stitch MCP と連携する7つのスキルが用意されています。主なものは以下の通りです。

- **Stitch Design** — プロンプト強化・デザインシステム合成・画面生成を一括処理
- **Enhance Prompt** — 曖昧なUIアイデアを高品質なプロンプトに変換
- **Design MD** — プロジェクトを分析して DESIGN.md を自動生成
- **Stitch Loop** — 1つのプロンプトから複数ページを自動生成
- **React Components** — Stitch の画面を React コンポーネントに変換

---

### まとめ

プロンプトからのデザイン生成、アノテーションによる修正、ワンクリックでのプロトタイプ生成など、デザインの作成から検証までを一つのツール内で完結できる点が魅力です。MCP サーバーと Skills による AI 連携により、デザインと開発のワークフローがよりシームレスになりそうです。現時点ではベータ版ですが、今後の一般提供が期待されます。
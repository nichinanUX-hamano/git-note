---
date: 2026-04-20
tags:
  - AI
  - Movie
---
# **Figma Weave（旧Weavy）の商業利用における法的・倫理的および運用上の総合リスク評価報告書**

## **1\. 序論：AIネイティブ・メディア生成プラットフォームの台頭と市場の変革**

2025年10月、クラウドベースのコラボレーションデザイン市場を牽引するFigma社は、イスラエルのテルアビブを拠点とするAIメディア生成スタートアップ企業「Weavy」を2億ドル（約300億円）以上の評価額で買収した 1。Weavyは設立からわずか1年足らずでFiverrの創業者などの支援を受け、複数のFortune 100企業を顧客に抱えるまでに急成長していた企業である 2。この買収に伴い、Figmaはテルアビブに新たなR\&Dセンターを設立し、Weavyの20名のチームとプロダクトを「Figma Weave」としてリブランディングした 1。現在は「weave.figma.com」という独立したブラウザベースのキャンバスとして稼働しているが、将来的にはFigmaのメインプラットフォームおよびデザインエコシステムへと完全に統合されるロードマップが示されている 5。

Figma Weaveの市場への投入は、クリエイティブ産業におけるツールのあり方を根本から再定義するものである。同プラットフォームは、Google、OpenAI、Runway、Black Forest Labs、Bytedanceといった世界トップクラスの多様なAI生成モデルを単一のキャンバスに集約し、プロフェッショナル向けの高度な編集機能（マスキング、リライティング、Z深度抽出、アウトペインティング等）とシームレスに連携させる「ノードベース・アーキテクチャ」を採用している 7。Figma Weaveの共同創業者兼チーフクリエイティブオフィサーであるItay Schiff氏が「Artistic Intelligence（芸術的知能）」と呼ぶこのアプローチは、AIモデルの速度とプロフェッショナルなワークフローの基準を融合させることを目的としている 9。

しかし、このような強力かつ自律的な生成AIプラットフォームを、企業のマーケティングキャンペーン、プロダクトUI/UX、クライアント向け納品物などの「商業プロジェクト」に直接適用するにあたっては、知的財産権（IP）の帰属、データプライバシー、透明性、そしてSaaSの課金体系に関する高度で多角的なリスク評価が不可欠である。本報告書では、提供された市場データ、財務開示文書（SECファイリング）、および公式ドキュメントに基づき、Figma Weaveを商業利用する上で企業が直面する法的、運用的、および財務的な留意点について、網羅的かつ深層的な分析を提供する。

## **2\. アーキテクチャの優位性と商業ワークフローの再構築**

Figma Weaveの商業的価値を正確に評価するためには、その基盤となる「ノードベース・アーキテクチャ」がいかにして従来のクリエイティブワークフローの非効率性を解消しているかを理解する必要がある。

### **2.1 ノードベースシステムによるプロセスの可視化と再現性**

これまでの生成AIを活用したデザインプロセスは、極めて断片的かつ直線的な「スロットマシン型」のワークフローであった 11。デザイナーはChatGPTでプロンプトを練り、Discord上のMidjourneyで画像を生成し、それをダウンロードしてTopazでアップスケールし、最終的にPhotoshopやFigmaにインポートして合成や修正を行うという、複数アプリケーション間の反復的な往復（コンテキスト・スイッチング）を強いられていた 12。

Figma Weaveは、これらのプロセス全体を視覚的な「ノード（接続可能な処理ブロック）」のネットワークとして単一のキャンバス上に構築する 2。各ノードは、特定のAIモデルの呼び出し（例：Nano Bananaでの画像生成）、プロンプトの連結（Prompt Concatenator）、ControlNetによる構図の指定、ノイズ除去、画像のアップスケール、またはカラーグレーディングといった個別の機能を持つ 11。出力されたデータは次のノードへの入力としてパイプライン上を流れ、全体のプロセスが可視化されるため、チャット履歴を遡る手間やコンテキストの喪失が防がれる 7。

この再現性の高さは、商業利用において決定的な意味を持つ。企業やエージェンシーは、特定のブランドアイデンティティやアートスタイルを維持するための「レシピ」を構築し、それをチーム全体で共有・標準化することができる 7。例えば、LyftはFigma Weaveを活用して従来のブランド写真撮影をスケーラブルなシステムに変換し、コンテンツライブラリ内でカスタマイズ可能な背景環境を生成している 10。また、NVIDIAはCESの基調講演において、シネマティックなロボットのシーンを作成する際、AIによる迅速なライティングの探索と12K解像度へのアップスケールにFigma Weaveのパイプラインを利用した 10。

| プラットフォーム / ツール | コアとなる対象と目的 | ターゲット層と商業的適性 |
| :---- | :---- | :---- |
| **Figma Weave** | ノードベースのメディアパイプライン。複数モデルの統合、詳細なプロンプト制御、動画・画像のコンポジット生成 18。 | 商業レベルの制御、チーム連携、大規模なアセット生成を必要とするプロフェッショナルなデザインチーム 7。 |
| **Canva Magic Studio** | テンプレート駆動型のワンクリック生成。非専門家向けのアクセシビリティに特化 12。 | 迅速なアセット作成を求めるカジュアルユーザーや小規模ビジネス。高度な編集や複雑なワークフローには不向き 12。 |
| **Midjourney (単体)** | テキストからの高度にスタイライズされた画像生成。プロンプトへの高い依存 12。 | コンセプトアートや初期のアイディエーション。単体ではUI/UXデザインやチームでのシステム的な再現性に欠ける 12。 |
| **Google Stitch** | プロンプトからWebおよびモバイル向けのUI画面を直接生成。開発者スタックとの連携 19。 | プロダクトチームや開発者による初期のUI探索とコードハンドオフに最適。メディア生成機能は持たない 19。 |

### **2.2 App ModeとLoRAによるブランド・セーフティの民主化**

さらに商業運用を強力に後押しする機能として、LoRA（Low-Rank Adaptation）のインポート機能と「App Mode」の存在が挙げられる。LoRAをインポートすることで、デザインチームは特定のキャンペーンやブランドキャラクターのスタイルを一貫して固定（ロックダウン）することが可能となり、生成されるメディアのトーン＆マナーの逸脱を防ぐことができる 7。

「App Mode」は、複雑に組み上げられたノードのパイプラインを、簡易なユーザーインターフェース（UI）に自動変換する機能である 7。これにより、AIやノードの専門知識を持たないマーケティング担当者や非技術系のコラボレーターであっても、背後にある複雑なプロンプトやモデル設定に触れることなく、指定された入力フィールド（例：商品画像やテキスト）を変更するだけで、ブランドガイドラインに完全に準拠したアセットを安全に自動生成することが可能になる 7。これは、クリエイティブ・エージェンシーがクライアントに対して「カスタマイズされたAIメディア生成ツール」そのものを納品できるという、新たなビジネスモデルの可能性を示唆している。

## **3\. 知的財産権（IP）保護とモデルの法的免責（Indemnification）**

商業利用における最もクリティカルなハードルは、「自社の機密データやデザインがAIの学習に流用されないか」というデータプライバシーの懸念と、「生成されたコンテンツが第三者の著作権や知的財産権を侵害した場合、誰が責任を負うのか」という法的リスクである。Figma Weaveは、これらに対処するため、業界最高水準の商業権限ポリシーと厳格なアーキテクチャを導入している 9。

### **3.1 データのサイロ化とプライバシー保護**

Figma Weaveは、プラットフォームに入力された画像やプロンプトなどのコンテンツを、AIモデルのトレーニングに一切使用しないことを明確に宣言している 9。エンタープライズのコンプライアンス要件を満たすため、SOC 2 Type II認証を取得し、通信の暗号化、厳格なアクセス制御、モバイルデバイス管理（MDM）プログラム、および第三者による年次ペネトレーションテストを実施している 7。 現段階では、FigmaとFigma Weaveは別個の製品として独立して稼働しており、AI機能の実行において個人を特定できる情報（PII）やコンテンツが2つのプラットフォーム間で共有されることはない 5。このデータのサイロ化は、未発表の製品デザインやクライアントの機密情報を扱う企業にとって、情報漏洩リスクを低減する強力な保証となる。

### **3.2 検証済みモデル（Verified Models）と未検証モデルの二重管理構造**

Figma Weaveの際立った特徴は、提供する十数種類のAIモデルを「Verified（検証済み）」と「Unverified（未検証）」という明確な二重構造で管理している点である 18。商業利用においては、この区別を正確に把握し、運用ポリシーに反映させることが絶対条件となる。

**検証済みモデル（Verified Models）の法的保証：** 「Figmaによって検証済み」とマークされたモデルは、Figmaと当該モデルプロバイダーとの間で正式な契約が締結されていることを意味する 18。この契約により、以下の3点が法的に保証される。

1. ユーザーのコンテンツは、要求されたサービス（メディア生成）を提供するためだけに使用される 18。  
2. Figma Weave経由でアクセスされたコンテンツは、プロバイダー側のモデルのトレーニングや改善には一切使用されない 18。  
3. 契約には「契約上の免責条項（Contractual Indemnity）」が含まれており、法的な保護の基盤が提供される 18。

2026年4月現在、Figma Weaveが公式にサポートしている主要な「検証済みモデル」と、その商業的ユースケースは以下の通りである 18。

| モデル / プロバイダー | 生成カテゴリ | 商業利用における主要なユースケースと特性 |
| :---- | :---- | :---- |
| **Google Nano Banana Series** (Nano Banana Pro 等) | 画像生成・編集 | 製品のコンポジット、精密なインペインティング/アウトペインティング。参照画像への高度な忠実性を持ち、ファッションやEコマースの仮想製品撮影に最適 14。 |
| **Black Forest Labs Flux** (Flux 2 Pro 等) | 画像生成 | 極めて写実的（フォトリアル）な画像の生成。広告の背景や実写に近い人物モデルの生成 18。 |
| **Recraft / Bria / Ideogram** | 画像生成 | イラストレーション、タイポグラフィ、ベクター形式の生成、ブランドスタイルの構築 18。 |
| **Google Veo** (Veo 3.1 等) / **Sora** | 動画生成 | シネマティックな動画生成、ウェブサイトのヒーローセクション用ダイナミック映像、UI/UXの動的モックアップ作成 2。 |

**未検証モデル（Unverified Models）の運用リスク：** 一方、未検証モデルは、Figmaによる厳格な契約の傘下になく、各プロバイダーが独自に定めるデフォルトの利用規約およびプライバシーポリシーに準拠する 18。これらのモデルを使用した場合、プロンプトや入力画像がモデルの学習に利用されるリスクや、商業利用自体が制限されているリスクが排除しきれない。 Figma WeaveのEnterpriseプランでは、このリスクを制御するため、管理者（Admin）が「モデル管理ダッシュボード（Model Management Dashboard）」を通じて、組織内のメンバーが未検証モデルを使用できないように事前承認制（ブロック）にするガバナンス機能が提供されている 18。法務部門およびIT管理者は、Figma Weave導入時にこの設定を直ちに有効化し、社内利用を「検証済みモデル」のみに限定するプロセスを確立すべきである。

### **3.3 免責（Indemnification）の限界とSECファイリングにおける警告**

検証済みモデルによるIP免責は企業にとって心強い盾となるが、それが完全な「免罪符」ではないことに深い注意が必要である。この点を理解するためには、競合であるAdobeの「Firefly」の法的アプローチと比較することが有用である。 Adobe Fireflyは、Adobe Stockの画像やオープンライセンスコンテンツなど、著作権がクリアなデータのみを初期トレーニングに使用しており、出力されたアセットに関連して企業顧客が著作権侵害で提訴された場合、Adobeが法的に防衛し損害を賠償する（IP Indemnification）という極めて強力な保証をエンタープライズ顧客に直接提供している 28。

対照的に、Figma Weaveの免責構造にはいくつかの複雑なレイヤーと潜在的リスクが存在する。Figmaが米国証券取引委員会（SEC）に提出した年次報告書（10-Kファイリング）のディスクロージャー（リスク開示）セクションを詳細に分析すると、株主および市場に対して以下の重大な警告が発せられていることが判明する。

1. **第三者モデルの「現状有姿（As Is）」提供:** Figma Weaveに組み込まれている多くのAIモデルは、完全に独立した第三者のモデルであり、顧客に対して「現状有姿」で提供されている 26。  
2. **著作権侵害の潜在的リスク:** AI技術が第三者の知的財産権を侵害する出力を生成する可能性があり、結果としてFigma自身やその顧客が訴訟の対象となるリスクが残存している 26。  
3. **免責の不完全性:** 「一部のAIプロバイダーは、AI技術の出力に起因する著作権侵害の請求に対してエンドユーザーを免責することを申し出ているが、そのような免責は不十分である可能性があり、当社がプロバイダーから適切に費用を回収できない可能性がある」と明記されている 26。  
4. **オープンソースのライセンス汚染:** AIが生成したコードやアセットが既存のオープンソースに酷似している場合、帰属要件（Attribution requirements）などのライセンス義務が生じ、自社の独自コードと混ざることでプロプライエタリな保護を失うリスクが指摘されている 26。

これらの法的・財務的開示から導き出される二次的な洞察は、Figma Weaveにおける「検証済みモデルの免責」は、主にFigmaとモデルプロバイダー間のB2B契約に基づくものであり、エンドユーザー企業に対する絶対的なIP保護を（Adobeレベルで）無条件に約束するものではないという事実である。 したがって、企業はFigma Weaveで生成されたコンテンツを、人間の監視や編集を一切経ずにそのまま市場にリリースする（ゼロ・ショット・パブリッシング）ことは避けるべきである。生成AIのア出力を「完成品」ではなく「クリエイティブな粘土（Creative Clay）」として扱い 20、プロのデザイナーによる人的なフィルタリング、加筆、コンポジット（合成）、および既存のブランドアセットとの融合を経ることで、法的なオリジナリティとブランドセーフティを社内で担保する承認フローを規定に組み込むことが必須である 13。

## **4\. 課金体系のパラダイムシフトと2026年の「SaaS予算の危機」**

AI機能のワークフローへの深い統合に伴い、Figma Weaveを含むデザインSaaS業界全体の価格設定モデルは、従来の「定額制（Flat-rate）」から、膨大なコンピューティングコスト（推論コスト）を反映した「従量課金・クレジット消費モデル」へと急速かつ不可逆的に移行している 31。商業利用を前提とする組織にとって、このコスト構造の変動は、プロジェクトの予算管理と調達戦略に甚大な影響を及ぼす。

### **4.1 Figma Weaveのプラン構造とクレジット消費メカニズム**

現在、Figma本体の有料プラン（Professional、Organization、Enterprise）とFigma Weaveのサブスクリプションは完全に分離されており、FigmaのクレジットをWeaveに流用することはできない 6。Figma Weave単体の料金プランは、主に以下の4層で構成されている 9。

| プラン名 | 月額料金 | 月間付与クレジット | 生成目安 (画像 / 動画) | ターゲット・用途 |
| :---- | :---- | :---- | :---- | :---- |
| **Free** | $0 | 150 | 画像375枚 / 動画25秒 | モデルの探索、個人利用、機能テスト 9 |
| **Starter** | **![][image1]**228\) | 1,500 | 画像3,750枚 / 動画417秒 | 時折メディアを生成する小規模クリエイター 9 |
| **Professional** | **![][image2]**432\) | 4,000 | 画像10,000枚 / 動画800秒 | 日常的に生成を行うプロフェッショナル 9 |
| **Team / Enterprise** | **![][image3]**576\) | 4,500 / ユーザー | 画像11,250枚 / 動画1,250秒 | 社内のビジュアルチーム、エージェンシー、大規模組織 9 |

ここで極めて重要なのは、クレジットの消費レートが一律ではないという事実である。利用するAIモデルの計算負荷と、生成するメディアの複雑さ（画像か動画か、解像度はいくつか）によって、1回あたりのクレジット消費量は劇的に変動する 9。テキストから静止画を生成する軽量なモデル（例：Flux Fast）であれば消費は少ないが、Google Nano Banana Proを使用して高解像度のアウトペインティング（画像の拡張）を行ったり、Google VeoやSoraを用いて数秒のシネマティック動画を生成したりする場合、クレジットは文字通り「飛ぶように」消費される 9。

### **4.2 「SaaSpocalypse（SaaSの黙示録）」と2026年3月の制限施行**

この従量課金制への移行は、業界アナリストの間で「SaaSpocalypse（SaaSの黙示録）」と形容されるほどの巨大なビジネスモデルの転換点である 31。AIツールが個人の生産性を5倍に引き上げる一方で、その1人のユーザーが過去の3倍のコンピューティングパワー（推論コスト）を消費するようになった結果、SaaS企業は従来の「シートベース（ID単位）」の定額制では利益率を維持できなくなっている 31。実際にFigmaの粗利益率が92%から82%へと圧迫されていることや、Anthropicがオープンソースエージェント向けの定額制サブスクリプションを禁止した動きは、この構造的限界を明確に示している 32。

FigmaはSECの財務開示および投資家向け発表において、**2026年3月より全アカウントに対してAIクレジットの制限を厳格に施行し、超過分については追加のクレジットサブスクリプションまたは従量課金（Pay-as-you-go）での購入を義務付ける**方針を明確に示している 26。 企業がTeamやEnterpriseプランで契約している場合、支払済みの料金は「返金不可（Non-refundable）」であり、契約期間中に購入済みのライセンスやクレジット数量を減額することは許可されていない 9。さらに、クレジットが枯渇した場合、追加購入しなければワークフローが停止するという事態に陥る。

### **4.3 財務・調達部門向けの交渉戦術と運用予算の最適化**

この変動費化の波を乗りこなすため、企業のCFO、調達部門、およびIT管理者は、以下のような防衛的な契約交渉と社内運用ルールの徹底を図る必要がある 36。

1. **契約更新時の価格上限キャップの設定:** 標準的な契約では、更新時にFigma側が制限なく価格を引き上げる権限を持っている場合が多い。更新時の価格上昇率を年5〜7%に制限するキャップ（上限）条項や、消費者物価指数（CPI）に連動させる条項を交渉プロセスで組み込むことが推奨される 37。  
2. **ダウングレード権と四半期ごとの調整（True-up）:** シート数の削減やクレジット枠の見直しを次年度の更新時まで待つのではなく、四半期または半期ごとの利用実績に基づいて実態に合わせた調整（True-up / True-down）を可能にする条項を要求すべきである 37。  
3. **クレジット管理システムの厳格運用:** Teamプラン以上に備わっている「クレジット管理システム（Credits Management system）」を利用し、各デザイナーに対して月間のカスタム上限（アロケーション）を設定する 9。無限にプロンプトを試行錯誤させるのではなく、Figma Weaveの「プロンプト・コンカテネーター」や配列ノードを駆使し、一度の生成で効率的にバリエーションを網羅する「コスト効率の高いAIオペレーション」をチーム内に教育・徹底することが、予算超過を防ぐ唯一の手段である 9。

## **5\. 外部API統合の完全排除とITアーキテクチャの制約**

Figma Weaveを、既存の社内システム、マーケティングオートメーションツール、またはCI/CDパイプラインと深く統合して「自動化されたメディア工場」を構築しようと企図する開発者や企業にとって、極めて重大な技術的・ビジネス的制約が存在する。2026年4月現在、Figma Weaveはあらゆる形態の「サードパーティAPI統合」を完全に拒絶している 18。

### **5.1 BYOKの禁止とエコシステムへのロックイン**

公式のヘルプセンタードキュメントにおいて、Figma Weaveは「現時点において、いかなるプランにおいてもAPI統合を提供していない（doesn't offer API integration for any of its plans）」と明確に宣言している 18。これは単なる開発スケジュールの遅れによる技術的な未実装ではなく、Figmaのエコシステム内にユーザーを囲い込むための意図的な「プロダクト上のハードリミット」である 18。この方針により、企業は以下のような統合アプローチをとることが一切できない。

* **BYOK（Bring Your Own Key）の不許可:** 企業が自社でAWSやGoogle Cloud等とエンタープライズ契約を結んで取得した独自のAPIキー（安価なレートが適用されたもの）を持ち込み、Figma WeaveのUI上で推論を実行することはできない 18。企業は必ず、Figma Weaveのクレジットを購入して消費しなければならない。  
* **カスタムエンドポイントの排除:** 自社の機密データを用いてオンプレミス環境やプライベートクラウドでファインチューニングした独自のLLMや画像生成モデル（Custom Base URL）を、Figma Weaveのキャンバスにノードとして追加接続することは不可能である 8。  
* **サードパーティプロキシやWebhookのブロック:** APIYIのような外部ルーティングサービスを利用したり、外部システム（例えばスプレッドシートやCMSに入力されたデータ）をトリガーとしてWebhook経由でFigma Weaveのワークフローを自動発火させたりすることも許可されていない 18。

### **5.2 ベンダーロックインへの戦略的対応**

この強固なAPI制限が意味するものは、商業ユーザーはAIモデルの利用にあたって「Figmaがバンドルし、マージンを上乗せした公式のチャネル」に100%依存しなければならないという事態である 18。もし企業が「Nano Banana Pro」などのモデルをAPI経由で自社のコードや自動化ツールから直接呼び出したい場合は、Figma Weaveを通さずに、APIプロバイダーと直接連携する別系統のアーキテクチャを構築する必要がある 18。 また、データの完全なオンプレミス保管やエアギャップ環境（インターネットから隔離された環境）での運用が義務付けられている高度なセキュリティコンプライアンスを要求される業界（金融、医療、防衛など）においては、完全クラウドSaaSであるFigma Weaveの採用自体が不可能であり、ComfyUIのようなオープンソースのローカルランタイム環境を選択せざるを得ない場合がある 8。

企業はFigma Weaveを導入する際、将来的なAIモデルのポータビリティが著しく制限されるという「ベンダーロックイン」のリスクを評価し、Figmaのエコシステム（Figma Make、Figma Sites、Figma Weaveの連携）内部で完結するエンドツーエンドの「AIネイティブ・メディア・サプライチェーン」を構築することに特化するか、あるいはAPI中心のヘッドレスアーキテクチャを指向するか、明確なアーキテクチャの切り分けを行う必要がある 19。

## **6\. 利用規約（AUP）、セキュリティ上の脅威、およびコンテンツ制限**

Figma Weaveは、自律的に機能する複数の大規模AIモデルを包含しているため、従来のUIデザインツールには存在しなかった固有のセキュリティリスクとコンプライアンス上の課題をもたらす。商業利用においてFigmaの「利用規約（Acceptable Use Policy: AUP）」に違反した場合、アカウントの即時停止のみならず、法的な損害賠償請求や深刻なレピュテーション（風評）リスクに直面する。

### **6.1 新たな脅威ベクターとシステムの悪用**

FigmaはSECに対する年次報告書において、AIプロダクトが従来のソフトウェアリスクを超えた「追加のセキュリティ脆弱性と脅威ベクター」をもたらすことを詳細に開示している 26。ユーザーまたは第三者が、ジェイルブレイク（脱獄）、プロンプトインジェクション、プロンプトの意図的な操作、その他の技術を通じて安全装置（セーフガード）を回避し、以下の行為を行うことは利用規約によって厳格に禁止されている。

1. **禁止されたコンテンツの生成:** 著作権を侵害するメディア、暴力的なコンテンツ、ディープフェイク、ポルノグラフィ、その他公序良俗に反する出力の意図的な生成 26。  
2. **モデルに対する攻撃と機密情報の抽出:** モデルの反転攻撃（Model Inversion）、メンバーシップ推論攻撃、データポイズニングなどを通じて、モデルの学習データに潜在的に含まれる他者の機密情報や個人データを意図的に抽出・暴露しようとする試み 26。  
3. **過剰な利用の意図的な駆動:** ボットやスクリプトを用いて不当に大量の生成要求を送信し、システムリソースを枯渇させたり、AI推論コストを故意に跳ね上げさせたりする行為 26。

これらの活動は、Figma側のインフラストラクチャおよびサポートコストを増大させるだけでなく、不正請求（チャージバック）や法的責任を誘発するため、Figmaはこうした悪用に対して極めて厳格な監視体制を敷いている 26。社内のクリエイティブチームが、意図せずともこれらの利用規約に抵触するようなプロンプトの入力を行わないよう、利用ガイドラインの策定と定期的なリテラシー教育が必須である。

### **6.2 AI透かし（Watermark）とコンテンツの真正性**

グローバルな広告およびメディア市場において、「そのコンテンツがAIによって生成されたものであるか」という透明性の確保が、法規制（EU AI法など）およびプラットフォーマーのポリシーにより強く求められるようになっている 32。 Adobe FireflyがC2PA（Content Authenticity Initiative）規格に基づく「コンテンツ・クレデンシャル」をデフォルトでメタデータに埋め込んでいるように、AI生成物には出所を証明する電子的マーカーが付与されるのが業界標準となりつつある 28。

Figma Weaveを経由して各プロバイダーのモデルを利用した場合も、モデル固有の電子透かしやメタデータが挿入されるケースがある。例えば、Googleの動画生成モデル「Veo 3.1」等を使用した場合、生成された映像の右下に「veo」というウォーターマーク（またはSynthID等の不可視の透かし）が挿入される事象が報告されている 38。企業がこれらのアセットを自社のテレビCMやデジタルサイネージ、公式ウェブサイトで公開する際、透かしの取り扱いや消去の可否については、各モデルプロバイダーの利用規約やライセンス条項に照らし合わせて慎重に判断する必要がある 38。これらを無断で削除したり、AI生成物であることを隠蔽して公表したりする行為は、ブランドの信頼性を著しく損なう危険性がある。

## **7\. データレジデンシーとグローバル・コンプライアンス**

エンタープライズ企業がSaaSを導入する際、自社のデータ（プロンプト、アップロードした参照画像、生成された出力物、ワークフロー構成等）が物理的にどの国のサーバーに保存され、処理されるかという「データレジデンシー（Data Residency）」は、各国のデータ保護法（GDPR、CCPA、APPI等）を遵守する上で極めて重要なチェック項目である 39。

Figmaはグローバルな事業展開を行っており、日本を含む世界14拠点にオフィスを構え、サイトやサポートの多言語化（日本語対応含む）を進めている 26。また、AWS等の大規模クラウドインフラを利用し、ディザスタリカバリプラン（災害復旧計画）の策定、サブプロセッサ（外部委託先）リストの公開、顧客データのリクエストに応じた削除機能などを提供することで、高いセキュリティ水準を維持している 22。

しかし、Figma Weaveのアーキテクチャは、Figma自体のインフラに加えて、十数社に及ぶ独立した「第三者のAIモデルプロバイダー（Google、OpenAI、Bytedance、Runway等）」とのAPI連携によって成立している 7。Figmaは2026年2月にサブプロセッサリストを更新し、WeaveのAIモデル群をデータ処理の委託先として正式に追加した 41。 これはすなわち、ユーザーがプロンプトや画像を入力した際、そのデータがFigmaの管理下にあるサーバーを経由して、各プロバイダーのデータセンター（多くの場合、米国をはじめとする複数リージョン）へ送信され、推論処理が行われることを意味する。日本企業がFigma Weaveを商業利用する場合、顧客の機密情報や発表前のプロプライエタリなデザインアセットを安易にアップロードする前に、そのデータが国境を越えて各プロバイダーのサーバーで処理されるという「マルチクラウド・イベントドリブン」な情報の流れを社内のセキュリティ・ポリシーと照らし合わせ、コンプライアンス監査部門の承認を得ることが強く推奨される 22。

## **8\. 結論：AIネイティブ時代のクリエイティブ運用戦略**

FigmaによるWeavyの買収と「Figma Weave」の展開は、デザインツールの役割を「ピクセルを手作業で配置するソフトウェア」から、「自律的なAIモデル群を指揮・オーケストレーションするパイプライン制御プラットフォーム」へと根本的に昇華させた。ノードベースのキャンバス上で生成と編集をシームレスに結合するこのアーキテクチャは、商業プロジェクトにおけるクリエイティブの生産性を文字通り異次元の領域へと引き上げるポテンシャルを秘めている 13。

しかし、その強大な恩恵を安全かつ持続的に享受するためには、企業はAI生成メディアが内包する複合的なリスクを直視し、組織的な防衛策を講じなければならない。本報告書の分析を通じて導き出される、商業利用に向けた核となる戦略的対応は以下の3点に集約される。

1. **IP保護とガバナンスの徹底:** 法的免責（Indemnification）の対象となる「検証済みモデル（Verified Models）」の利用を大原則とし、エンタープライズ管理者はダッシュボードを通じて未検証モデルの利用をデフォルトでブロックする厳格なガバナンス体制を構築すべきである 18。また、AIの出力をそのまま公開するのではなく、人間のデザイナーによる編集・合成プロセスを必ず経ることで、著作権侵害リスクを軽減し、ブランドの独自性を担保するワークフローを規定化すること。  
2. **「従量課金」を前提とした財務・調達戦略の転換:** 2026年3月から施行されるAIクレジット制限により、クリエイティブ部門のSaaS費用は予測可能な固定費から、変動の激しい従量課金へと移行する 26。企業は契約更新時において、価格上昇のキャップ条項やクレジット調整（True-up）条項を粘り強く交渉し、財務的なクッションを確保する必要がある 37。運用面では、プロンプトのコンカテネーションやApp Modeを活用し、「最小のクレジット消費で最大のバリエーションを生み出す」コスト効率の高い運用教育を徹底しなければならない 9。  
3. **ベンダーロックインの受容とエコシステム内最適化:** Figma WeaveはAPIを通じた外部連携やBYOKを一切拒絶する閉鎖的なエコシステムである 18。企業はこの制約を受け入れ、無理に外部システムと自動連携させようとするのではなく、Figma Make（アプリ生成）、Figma Sites（ウェブパブリッシング）、Figma Buzz（マーケティングアセット）、そしてFigma Weave（メディア生成）というFigmaプラットフォーム内部で完結するエンドツーエンドのサプライチェーンを極めることにリソースを集中すべきである 3。

AIは人間の創造性を代替するものではない。Figma Weaveという強力な「デザイン・マシーン 11」をいかに精密に制御し、法務、財務、セキュリティの各観点から適切にリスクをヘッジしながら自社のプロセスに組み込めるか。それこそが、次世代のクリエイティブ産業において企業が圧倒的な競争優位性を確立するための最大の分水嶺となるであろう。

#### **引用文献**

1. Figma \- Wikipedia, 4月 20, 2026にアクセス、 [https://en.wikipedia.org/wiki/Figma](https://en.wikipedia.org/wiki/Figma)  
2. Figma acquires AI design startup Weavy for reported $200M+ \- SiliconANGLE, 4月 20, 2026にアクセス、 [https://siliconangle.com/2025/10/30/figma-acquires-ai-design-startup-weavy-reported-200m/](https://siliconangle.com/2025/10/30/figma-acquires-ai-design-startup-weavy-reported-200m/)  
3. Figma revenue, valuation & funding \- Sacra, 4月 20, 2026にアクセス、 [https://sacra.com/c/figma/](https://sacra.com/c/figma/)  
4. Figma Acquires AI Generation Startup Weavy \- Life Self Mastery, 4月 20, 2026にアクセス、 [https://lifeselfmastery.com/2025/11/28/figma-acquires-ai-generation-startup-weavy/](https://lifeselfmastery.com/2025/11/28/figma-acquires-ai-generation-startup-weavy/)  
5. Figma Weave FAQ – Figma Learn \- Help Center, 4月 20, 2026にアクセス、 [https://help.figma.com/hc/en-us/articles/35965787376919-Figma-Weave-FAQ](https://help.figma.com/hc/en-us/articles/35965787376919-Figma-Weave-FAQ)  
6. Weavy to Figma Weave \- FAQ | Figma Weave's Knowledge Center, 4月 20, 2026にアクセス、 [https://help.weavy.ai/en/articles/12692387-weavy-to-figma-weave-faq](https://help.weavy.ai/en/articles/12692387-weavy-to-figma-weave-faq)  
7. Weavy AI Review (2026): Features, Pricing & Alternatives \- AI Tool Curator, 4月 20, 2026にアクセス、 [https://www.aitoolcurator.com/ai-tools/content-creation/weavy/](https://www.aitoolcurator.com/ai-tools/content-creation/weavy/)  
8. Best AI Creative Suites In 2026 \- Startup Stash, 4月 20, 2026にアクセス、 [https://startupstash.com/best-ai-creative-suites/](https://startupstash.com/best-ai-creative-suites/)  
9. Figma Weave Pricing – Flexible Plans for Creative Pros & Teams, 4月 20, 2026にアクセス、 [https://weave.figma.com/pricing](https://weave.figma.com/pricing)  
10. Figma reintroduces Weavy as AI-driven Figma Weave for creative production \- Mi3, 4月 20, 2026にアクセス、 [https://www.mi-3.com.au/15-04-2026/figma-reintroduces-weavy-ai-driven-figma-weave-creative-production](https://www.mi-3.com.au/15-04-2026/figma-reintroduces-weavy-ai-driven-figma-weave-creative-production)  
11. Weavy vs Freepik Spaces: A Guide to Node-Based AI for Creative Pros | Chase Jarvis, 4月 20, 2026にアクセス、 [https://chasejarvis.com/blog/weavy-vs-freepik/](https://chasejarvis.com/blog/weavy-vs-freepik/)  
12. Figma Acquires AI-Powered Weavy: What It Means for Design \- Just Think AI, 4月 20, 2026にアクセス、 [https://www.justthink.ai/blog/figma-acquires-ai-powered-weavy-what-it-means-for-design](https://www.justthink.ai/blog/figma-acquires-ai-powered-weavy-what-it-means-for-design)  
13. Figma Weave and the Future of AI Native Design | by Tejj | Medium \- Prototypr, 4月 20, 2026にアクセス、 [https://blog.prototypr.io/figma-weave-and-the-future-of-ai-native-design-43168a4f9b0f](https://blog.prototypr.io/figma-weave-and-the-future-of-ai-native-design-43168a4f9b0f)  
14. Weavy vs. Leonardo.ai: Which is better for creative pros? (Figma Weave) | Chase Jarvis, 4月 20, 2026にアクセス、 [https://chasejarvis.com/blog/weavy-vs-leonardo/](https://chasejarvis.com/blog/weavy-vs-leonardo/)  
15. What the heck is Weavy (Figma Weave)? The 100% honest review… \- Chase Jarvis, 4月 20, 2026にアクセス、 [https://chasejarvis.com/blog/what-the-heck-is-weavy-the-100-honest-review-after-the-figma-acqusition/](https://chasejarvis.com/blog/what-the-heck-is-weavy-the-100-honest-review-after-the-figma-acqusition/)  
16. Create A Virtual Product Shoot In Weavy & Nano Banana (fashion editorial) \- Chase Jarvis, 4月 20, 2026にアクセス、 [https://chasejarvis.com/blog/create-a-virtual-product-shoot-in-weavy-nano-banana-fashion-editorial/](https://chasejarvis.com/blog/create-a-virtual-product-shoot-in-weavy-nano-banana-fashion-editorial/)  
17. News Bites: November 3, 2025 \- Ascension | PHD Media, 4月 20, 2026にアクセス、 [https://ascension.phdmedia.com/newsbite/news-bites-november-3-2025/](https://ascension.phdmedia.com/newsbite/news-bites-november-3-2025/)  
18. What is Figma Weave? A beginner's guide and a comprehensive analysis of the current state of third-party API integration \- Apiyi.com Blog, 4月 20, 2026にアクセス、 [https://help.apiyi.com/en/figma-weave-introduction-apiyi-api-integration-en.html](https://help.apiyi.com/en/figma-weave-introduction-apiyi-api-integration-en.html)  
19. Figma AI: How To Weave, Make, and Schema—The Guide Made Easy \- VidAU AI, 4月 20, 2026にアクセス、 [https://www.vidau.ai/figma-ai-weave-make-and-schema-a-practical-explanation/](https://www.vidau.ai/figma-ai-weave-make-and-schema-a-practical-explanation/)  
20. AI-Enhanced Product Design Workflow \- FRANKI T, 4月 20, 2026にアクセス、 [https://www.francescatabor.com/articles/2025/11/22/ai-enhanced-product-design-workflow](https://www.francescatabor.com/articles/2025/11/22/ai-enhanced-product-design-workflow)  
21. AI Tool Compliance For Generation Images and Video \- WonderLoop, 4月 20, 2026にアクセス、 [https://www.wonderloop.nl/ai-tool-compliance-for-generation-images-and-video/](https://www.wonderloop.nl/ai-tool-compliance-for-generation-images-and-video/)  
22. Figma Trust Center | Powered by Conveyor, 4月 20, 2026にアクセス、 [https://compliance.figma.com/](https://compliance.figma.com/)  
23. Verified and Unverified Models | Figma Weave's Knowledge Center, 4月 20, 2026にアクセス、 [https://help.weavy.ai/en/articles/14034721-verified-and-unverified-models](https://help.weavy.ai/en/articles/14034721-verified-and-unverified-models)  
24. Verified and Unverified Models \- Weavy Knowledge Center \- Figma Weave, 4月 20, 2026にアクセス、 [https://help.weavy.ai/en/articles/14035518-verified-and-unverified-models](https://help.weavy.ai/en/articles/14035518-verified-and-unverified-models)  
25. Figma Weave — Here's Why It Matters \- YouTube, 4月 20, 2026にアクセス、 [https://www.youtube.com/watch?v=GCH8jNIM9Kk](https://www.youtube.com/watch?v=GCH8jNIM9Kk)  
26. fig-20251231 \- SEC.gov, 4月 20, 2026にアクセス、 [https://www.sec.gov/Archives/edgar/data/1579878/000162828026009228/fig-20251231.htm](https://www.sec.gov/Archives/edgar/data/1579878/000162828026009228/fig-20251231.htm)  
27. Enterprise Plan | Figma Weave's Knowledge Center, 4月 20, 2026にアクセス、 [https://help.weavy.ai/en/collections/17907485-enterprise-plan](https://help.weavy.ai/en/collections/17907485-enterprise-plan)  
28. What Is Adobe Firefly? How to use Adobe's generative AI \- Chase Jarvis, 4月 20, 2026にアクセス、 [https://chasejarvis.com/blog/what-is-adobe-firefly/](https://chasejarvis.com/blog/what-is-adobe-firefly/)  
29. The Best AI Image Generators: A Guide For Creative Pros \- Chase Jarvis, 4月 20, 2026にアクセス、 [https://chasejarvis.com/blog/best-ai-image-generators/](https://chasejarvis.com/blog/best-ai-image-generators/)  
30. UNITED STATES SECURITIES AND EXCHANGE COMMISSION FORM 10-K FIGMA, INC., 4月 20, 2026にアクセス、 [https://s206.q4cdn.com/973901332/files/doc\_financials/2025/q4/fig-20251231.pdf](https://s206.q4cdn.com/973901332/files/doc_financials/2025/q4/fig-20251231.pdf)  
31. Figma Inc. (FIG) Intrinsic Value: Stock Valuation \- The Investor's Podcast Network, 4月 20, 2026にアクセス、 [https://www.theinvestorspodcast.com/intrinsic-value/figma-inc-fig/](https://www.theinvestorspodcast.com/intrinsic-value/figma-inc-fig/)  
32. Design Layer \#04: The Subscription Model Just Broke | by Oleksandr Konovalov \- Medium, 4月 20, 2026にアクセス、 [https://medium.com/@lex.konovalov/design-layer-04-the-subscription-model-just-broke-67d0cc4af675](https://medium.com/@lex.konovalov/design-layer-04-the-subscription-model-just-broke-67d0cc4af675)  
33. Figma Trades at 9x Sales as Growth Stays Near 40% and AI Usage Ramps, 4月 20, 2026にアクセス、 [https://ng.investing.com/analysis/figma-trades-at-9x-sales-as-growth-stays-near-40-and-ai-usage-ramps-214081](https://ng.investing.com/analysis/figma-trades-at-9x-sales-as-growth-stays-near-40-and-ai-usage-ramps-214081)  
34. Figma's Anthropic Integration Could Flip the SaaSpocalypse Script \- MarketBeat, 4月 20, 2026にアクセス、 [https://www.marketbeat.com/originals/figmas-anthropic-integration-could-flip-the-saaspocalypse-script/](https://www.marketbeat.com/originals/figmas-anthropic-integration-could-flip-the-saaspocalypse-script/)  
35. Figma (FIG) posts $1.1B revenue and outlines AI credit strategy \- Stock Titan, 4月 20, 2026にアクセス、 [https://www.stocktitan.net/sec-filings/FIG/10-k-figma-inc-files-annual-report-4012f620a72e.html](https://www.stocktitan.net/sec-filings/FIG/10-k-figma-inc-files-annual-report-4012f620a72e.html)  
36. Figma Pricing Guide: Control Enterprise Costs and Editor Access | CloudEagle.ai, 4月 20, 2026にアクセス、 [https://www.cloudeagle.ai/blogs/figma-pricing-guide](https://www.cloudeagle.ai/blogs/figma-pricing-guide)  
37. Figma Enterprise Subscription Costs Guide \- Freqens, 4月 20, 2026にアクセス、 [https://www.freqens.com/blog/figma-enterprise-subscription-costs-guide](https://www.freqens.com/blog/figma-enterprise-subscription-costs-guide)  
38. Nano Banana Pro Cannot Generate Disney Characters: 3 Key Reasons Why 16 Major IPs Are Blocked and 5 Alternatives, 4月 20, 2026にアクセス、 [https://help.apiyi.com/en/nano-banana-pro-disney-ip-blocked-copyright-protection-guide-en.html](https://help.apiyi.com/en/nano-banana-pro-disney-ip-blocked-copyright-protection-guide-en.html)  
39. The latest insights on how the world connects \- Zoom, 4月 20, 2026にアクセス、 [https://www.zoom.com/en/blog/?page=47](https://www.zoom.com/en/blog/?page=47)  
40. Building Distributed Event-Driven Architectures across Multi-Cloud Boundaries \- InfoQ, 4月 20, 2026にアクセス、 [https://www.infoq.com/articles/multi-cloud-event-driven-architectures/](https://www.infoq.com/articles/multi-cloud-event-driven-architectures/)  
41. Figma Subprocessors: Get alerts for the latest updates \- Visualping, 4月 20, 2026にアクセス、 [https://visualping.io/pages/figma-subprocessors-alerts-4795620](https://visualping.io/pages/figma-subprocessors-alerts-4795620)

[image1]: <data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADkAAAAUCAYAAAA3KpVtAAADyUlEQVR4Xu2XeaiPWRjHv5bJjBhjYmyNiyxhKISGjG0ioohEZEvTWMq+ZMlVRjMxzR9SNDPcabKWksJoMoM/jGx/yFKoe8ueNEjKOr7f3/Oe33vuuefl/nQ1/9xvfbq/9znL+z7nPM9zzgWqVa2q0EyykwwJGwpUY/IPbL7/RQ3JR6Ex0WVynvQJGwLVCw2Jeid/9Y7/SIvkWf2nkOVkbmJ7b2pOTpEGYQM1kDwn3cKGQPXJOdiO1w3adsGcWErukZXJ80mym9RMu5ZXK9gqZKmILCA/kq+CNl91YC+bFjZQNcgZUgL7KMd35BFZ59kWklUJA5BqJPk5+b2WjPfaNLfe63Y6p47ke3KWvCIH/EZPo8htspj0hznxU7keqTaQ0zCHQmkRN4dGqhMs7L4IGwLVInfIRNKavCSTYO/Swg8itWG+aOFy6kWmkx7kKeJOtoGtcn4Q1R72UcM9m/QxrG8s1z4lGxEPpZiT+vBYuC+BzbGJHIftuhZW4/WNGqff0XTIcrIYNmh0YL8PyxdfeuGFwCbpxbNhoTyDzILl2YcJ3WHv0GI7m9KiDPHd1cLfQLoIytHf0ubcXGO857yynJQjGjQssJfBkt7Xn2RfYJO6wgqJpJ14QL7xKIa9Y01gFyNyo8rrd1horiY/kFJYpXXSXN96z3llObkF8Z2Ug7J/4NmuwULnTVJe3wpsnVExXLOkwuIW/HPYYqsGjHMd8A7hOhk2yK+WzWDJLXuTxKai8AwZK+gp5mQsJ7Pk+jQif5OepCXs3N0D+w7NpYipIDl5MDTCkvwEOQabQFKpfwxzVHkmFcEmH5w8Z6kQJ5W382EV01dTcgSWBk4dyEXYDmqu6G1KTh4KjYl0k9iKdLUUundh5dzJFQ/9DaWCpEjQmbad/Jv8dixCuvq+Xd8j+19Ibz9fk8OwI82dqcXkCeyoUxV/Y7hmORlKu/uC7PVsOrc0+VjP5qRdVoh/lkE/2Nj+kTaHKrQcVR/t0k2kkkO6RamPCpzmWu+15yUn/wiNsHDcT6Z6tgGoGJpu8mWerbLKCtcsDUVFJ1UPJB0/OkP9UM5JFVKddLjG4l+rpDCTdDYdJTtcB086u34JjZWQnJOTXcKGDOkSkuWkpMgpdQ/qfBVWCHRTEcq1Kyh/21A+boPdXdVfDoaLIZXAFqBQuWIRzaOIlHsPkeakQtM5+SXsG+clzwWpHews0s5mSfmo81MhU4j6wpyMXQdjmkCue8+fwDZA/5X8Stp6bVUuFaRLZEXY8BapsMxB/K4ak9JLjvlSVdc/0Xm9Buy51Sf3fxiXAAAAAElFTkSuQmCC>

[image2]: <data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADkAAAAUCAYAAAA3KpVtAAAEJ0lEQVR4Xu2Xa6hWRRSGXy0t7WpkmJZppUk3b4U3yspUjAoxkTQjKolMIc2stMILXsiKgtLECx4Ru/6oPyVReqIfpiUFkVZWqKkZ2dUioVB732/N2nu++fY+ngNH+uMLD9+eNWvPnsuaNfMBx3VczaGJ5BUyLK1ootqTj2Dt/S9qR9qkxqAvyedkYFqR6NTUENQv/OobR0inUJb/XWQmeTDYjpk6ko/JGWkFdT35l/ROKxKdRj6FrXjbpO5V2CAeJfvJE6G8ibxGWuauphbkZrKQjCXnV1dX6XSYj2bq0qTOdRLsY3enFbBvbSF1sE4588kBsiCyTSNPBq5DrlvI8vA8j9we1altfddXuiLN+PuwmbiWLCMHYQNJdSvZAWtkKPmOXFXlYXqGfAIbUCqF0tLUCJswhd3laUWiE8iP5A7SlRwi42HfUv9vICeSw7CJq+h58jPpH8qtYaH0G6r3U0/yK7kolAfDOvVc5mHSSmtFivbaWeQFFIQSigepjheF+yOwNhaTD2GrronV+xqY3tNzth2eDoY7Q/lk8g/5C/k+0Mx8D4t1l/bLItTuK33wi8Qm6cOTYKE8gTwAa1/fE31g/egb2Z4lO1G8uheSPcgnQXt0dV5daes2L2hGuuV1lRWQgza7S6so2xRYZy+AhU2R3iNvpUbqStjESFqJ38l9EbNh35iT2IXyRao1sNCcRZ6CbSNlWpfauj8qZ9JgPyObSZfIfi/spbnkHbKK/ARbjVTfwkKnIU0nPyS2y1AbrmVSThgRnpUkd8JywBh3QBKurpfIVljnr0jqlsBe2g4LN8lXN25Yq6tQL5zBSEWDLNqTZXKfs0k9uZp0hp27r8P6obYUMYW6kfwJS9uuN2AvKQPHUpbTDLoUxvIbEtmK1JRBat9OheWFWB3Ietg2cF0CWyitoNpq8Da1Eebk56CymMrjMg+TQlN2Xa0kTx76TaWEpDDTmbYWlr317DyMfPZj+7pg34D89qOFeJfsQ36mziZ/k5GwLK53snCVw2QvBClLyUmXA8k7MCrzMH0T7JpVSeeWyqMzj1xa5XPJOSVcA3t3cEGdo6SngcpHq7QXuTQgHX3yUYJTWzo5KslFBaFLgas+2PzS2yOUlfpjKeQUHmpY8sYfyzwar7JwLdNw1A5S+UDS8aPoq4Syksgu8nKolE4hvwT80ivpVvR2VO4O65RnOZfOrhWJrTHS4NRemvTKdBPKBykpcnZ4QZ39irwIuyvqb8vXpJc7BCkkdci/CTsitIozqjxMdeSDxNYYebKoSfsl0t77A/meVGj6IAfAtpLO9UwKN82g7qu6SZRJfrqz3kPOS+pc2o/6V6CQaYoGwQZZdB0skvq6OyqfSR6C/StZSS6O6ppdukFtI4+nFUeREosSYNFdtUitYAOLpazumb6i/wC5Pd80tSMH2gAAAABJRU5ErkJggg==>

[image3]: <data:image/png;base64,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>
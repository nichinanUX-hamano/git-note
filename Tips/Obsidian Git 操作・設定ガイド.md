# **Obsidian Git 操作・設定ガイド**

## **1\. 右側パネルのボタン操作ガイド**

Gitパネル上部にあるアイコンの機能一覧です。

| アイコン | 名称 | 機能説明 |
| :---- | :---- | :---- |
| **![][image1]** | **Commit-and-sync** | **一括同期。** ステージ・コミット・プル・プッシュを一度に行います。 |
| ![][image2] | **Commit** | **記録の確定。** ステージされた変更を保存します。メッセージの入力が必要です。 |
| ![][image3] | **Stage all** | **変更を準備。** すべての変更ファイルをコミット対象に加えます。 |
| ![][image4] | **Unstage all** | **準備の取り消し。** ステージしたファイルを変更ありの状態に戻します。 |
| ![][image1] | **Push** | **アップロード。** ローカルの記録をGitHubへ送信します。 |
| ![][image5] | **Pull** | **ダウンロード。** GitHubの最新状態を手元に反映させます。 |
| ![][image6] | **Change Layout** | **表示切替。** リスト形式とフォルダ形式を切り替えます。 |
| ![][image7] | **Refresh** | **状態更新。** 最新のファイル変更状態をパネルに再読み込みします。 |

## **2\. 同期を安定させる設定（.gitignore）**

workspace.json などの設定ファイルは、デバイスごとに内容が異なるため頻繁に衝突（コンフリクト）の原因になります。これらを同期対象外に設定することで、エラーを劇的に減らせます。

### **設定の手順**

Obsidianの制限で .gitignore という名前のファイルは直接作成できないため、以下の手順で行います。

1. **コマンドパレットを開く:** Ctrl \+ P (Macは Cmd \+ P)  
2. **専用コマンドを実行:** 「**Obsidian Git: Edit .gitignore**」と入力して選択。  
3. **除外リストを追記:** 開いたファイルに以下の内容を貼り付けて保存します。  
   .obsidian/workspace.json  
   .obsidian/workspace-mobile.json  
   .obsidian/cache/

## **3\. コンフリクト（衝突）が起きた時の対処**

ファイル名に「U」マークがついている時は、他のデバイスでの変更と衝突しています。

1. **解決:** 対象ファイルを開き、\<\<\<\<\<\<\< HEAD 等の記号で囲まれた部分を確認して不要な方を消すか、右側パネルの ![][image8] **(Revert)** ボタンで変更を一旦戻します。  
2. **完了報告:** ![][image3] **(Stage all)** ボタンを押し、変更が解決したことをGitに伝えます。  
3. **同期:** その後コミット、または同期ボタンを押せば正常な状態に戻ります。

## **4\. GitHubの公開設定と共有について**

* **Private（非公開）:** \* 自分だけの同期や、特定の招待したユーザーとの共同編集に最適です。  
  * メモに個人情報や日記が含まれる場合は、この設定を推奨します。  
* **Public（公開）:** \* 全世界にノートを公開したい場合（ブログやWikiとして活用する場合）に使用します。  
  * 誰でも内容を閲覧・検索できる状態になります。

**結論:** 自分のデバイス間での同期が目的であれば、**Private設定のままで問題なく同期・利用が可能**です。

[image1]: <data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAgAAAAVCAYAAAB7R6/OAAAAd0lEQVR4XmNgGJyAEV0ABcjLy09SUFCQQBcHA6AEB1DBCyCegi4HBnJycv1AyedA/BCIFeESMjIyKkCB9UAFIUB6OdAkCyB9AkjHg+zMAuLLQGwFUgxSICsrKyUtLS0D1DCDsAIVFRU+uF1ICpDFUMCoAghAVwAAkv8nckgvDkIAAAAASUVORK5CYII=>

[image2]: <data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAA4AAAAVCAYAAAB2Wd+JAAAA5klEQVR4XmNgGAVYgby8vBW6GF5gbGzMCtS0HITR5fABFqCG1UC8DsRGl8QFmOXk5FYANW3R0tJiQ5fEBZiAGpYoKCjsUlFRYUeXxAmANs0HajwqIyPDiS6HEwA1eAPxP6BtBuhy+ADIiRdBAYIugQKATlJSVFRUR+LHAjX9BdJayOpQAFDSGqQIiK+D4goUckD2fSBejK4WBQBDiw+o6DUQ/wfiIqBB+UD6NzBAVNDVYgCgwmyoxg9A/AKI96OrwQVAKeMaVPN/oK3l6ApwAmCwu8M0ArEmujxeANRcCbTNB1184AEACXUyXj/3YPEAAAAASUVORK5CYII=>

[image3]: <data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAA8AAAAXCAYAAADUUxW8AAAAb0lEQVR4XmNgGAXDADDKy8svRRckFrAoKCjsQhckChgbG7OSrVlLS4uN9pplZGSEZGVlpZAxUKOCnJzcQXRxEAYCLrhmoLpOYMguR8ZAsZVA+gW6OAgDDQ1DshsTEO1sbGAkagYCRmC0+KELDgMAANatIy9ADIL/AAAAAElFTkSuQmCC>

[image4]: <data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAA0AAAAUCAYAAABWMrcvAAAALklEQVR4XmNgGAWjYGABi6ysrBQxWFlZWQysQ15e3hCIlxOD5eTkFqDaNwpIAwAoJRCel54+mQAAAABJRU5ErkJggg==>

[image5]: <data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAgAAAAVCAYAAAB7R6/OAAAAfElEQVR4XmNgGITA2NiYFV0MBcjLy89VVFQURxeHA6CCxbKyslLo4nAAVLCUkIJlg0DB8kGnQE5OLg4o6IhNATBO5BmUlJTkFBQUVgEljkpJSYnAFAA1OgPZF5FNcgUKbAHi7UBcBcQ9QA1ccAUgALIKiP8B8U0glwUkBgAUmCO+4viKgAAAAABJRU5ErkJggg==>

[image6]: <data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAA0AAAAVCAYAAACdbmSKAAAAgUlEQVR4XmNgGL6A2djYmJVYDNYhLy9/B4h3o+G9QPwWi/hhmKa9yNaCgJaWFpuCgsIudHFpaWkZMAOoaR+aHFGa9qPJEaXpAKoUDTW9kJOTO4iMQaEExO+xiJ8AawJxkE0DAYI2DUdNwBC5iyWUQKH3DhQdoMiH4n1AfATNnMEGAANJTxugM+/0AAAAAElFTkSuQmCC>

[image7]: <data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAA0AAAAVCAYAAACdbmSKAAABJklEQVR4Xu2Sv0rDUBjFM7UUasEhCM1/DQSySsVOYuui6VIcuunq4BsoHfsEgotLQRR06aSLQ6liN9/C1yj+vostude0S1cPHHLynXPaLzexrH/8RRRFQZIkG+Z8JYIgaMJP2DK9lQjD8ILSDH7DU5k5juP6vr9tZq04jssYI3grVwonc8/zvDr3r8zb+Y6s9sjwjHKNf5toJnBdt8L8iVxXDeQZ4INojH3KR1rjF7ZtV8mN1Q3inhV29EgxyF7NxZfhLQU/3lCC0tTwloLVUyVkzzRNS4ZfCJ65pwTtPsXM8AtB7k4JjtmWFeVYjYwGMofwJT/I4Ju8yFxuAbxj+M5Wm5rBYBfjA96gO+x/gL6Ez+ghH/SWVsgDc4/gNcUB4fPFia2DHxgUNafmpIncAAAAAElFTkSuQmCC>

[image8]: <data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAA8AAAAYCAYAAAAlBadpAAABMElEQVR4XmNgGAW0AYqKivLq6uq86OKEALOcnFyZvLz8VmlpaWF0SRQAVGgNpJhAbKCGqUD8BYjfAsW10JSiAqCiagUFhQkMUM1QsQMgcSA+DjQgF0k5AgAlJwEl09DFgX41Axq4UUVFhR2oZikQR6EoAGpSAgrOQxFEAkD5ci0tLTZQgAHVXRAVFeWBSwJNbgRiBYRy3ACouQRoWAiywHEkebxAVlbWFmjPRLgAUPMJJHm8ABTqQLwALgDUfFRGRoYToQQ3ANoaDlRfDBcAclqAgv5IanACoNo5QKwJFwBGgygoFIE0H5I6DABU4wi0ZBW6OMg5AUDJfbhCHSjnCQobnEkUqM8e5H9ggPQDcSyQ7QTEOSDbQBgoJoiuBx0wQp1XCMSNQLYXkBZAVzRSAQCnrDkme+LT+gAAAABJRU5ErkJggg==>
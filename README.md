# KitsoLineApp_2

## プロジェクト概要

KitsoLineApp_2は、Google Apps Script（GAS）を使用して開発されたLINE Botアプリケーションです。このBotは、以下の機能を提供します。

- **リマインダー機能**: ユーザーごとのリマインダー登録、表示、削除機能を提供します。
- **スケジュール管理**: Googleカレンダーに登録されたイベントを表示します。
- **鍵管理**: 500人講義室と部室の鍵の貸し出し状況を表示し、借用・返却を記録します。
- **出欠確認**: 練習への出欠を登録・表示する機能を提供します。
- **イベント情報**: 近隣のコンサートホールで行われる演奏会の情報を表示します。
- **Gemini連携**: Gemini AIを利用したチャット機能を提供します。
- **ユーザー管理**: LINEのユーザーIDとユーザー名を紐付けて管理します。
- **プッシュ通知**: 特定のユーザーへのプッシュ通知機能（実装中）を提供します。

## ファイル構成

```
KitsoLineApp_2/
├── appsscript.json       # GASプロジェクトの設定ファイル
├── main.js               # メイン処理
├── util.js               # ユーティリティ関数
├── gemini.js             # Gemini AI連携
├── LineAPI.js            # LINE Messaging API連携
├── reminder.js           # リマインダー関連機能
├── userManagement.js     # ユーザー管理機能
├── addUsername.html      # ユーザー名登録ページ
├── calendar.js           # Googleカレンダー連携
├── keyManagement.js      # 鍵管理機能
├── addReminder.html      # リマインダー登録ページ
├── deleteReminder.html    # リマインダー削除ページ
├── showReminder.html     # リマインダー表示ページ
├── rollCall.js           # 出欠確認機能
├── monthlyAttendance.html # 月間出欠登録ページ
├── showAttendance.html   # 出欠情報表示ページ
├── trigger.js            # トリガー設定（定期実行など）
├── concertInfo.js        # 演奏会情報表示機能
├── allConcertInfo.html    # 演奏会一覧表示ページ
```

### 各ファイルの説明

- **appsscript.json**: GASプロジェクトの設定ファイルで、タイムゾーン、依存関係、実行環境などが定義されています。
- **main.js**: LINEからのWebhookイベントを受け取り、各機能への処理を振り分けます。また、GETリクエストの処理も行います。
- **util.js**: APIキーの取得、イベントの解析、エラーハンドリングなどのユーティリティ関数を提供します。
- **gemini.js**: Gemini APIとの連携を処理し、メッセージの生成と抽出を行います。
- **LineAPI.js**: LINE Messaging APIとの連携を処理し、メッセージの送信（リプライ、ブロードキャスト、プッシュ）を行います。
- **reminder.js**: リマインダーの作成、表示、削除に関する処理を行います。
- **userManagement.js**: ユーザーの登録、確認、ユーザー名の取得など、ユーザー管理に関する処理を行います。
- **addUsername.html**: ユーザーが名前を登録するためのHTMLフォームを提供します。
- **calendar.js**: Googleカレンダーから予定を取得し、メッセージを生成します。
- **keyManagement.js**: 鍵の借用と返却を処理し、現在の鍵の状態を返します。
- **addReminder.html**: リマインダーを登録するためのHTMLフォームを提供します。
- **deleteReminder.html**: 登録したリマインダーを削除するためのHTMLフォームを提供します。
- **showReminder.html**: 登録したリマインダーを一覧表示するためのHTMLページを提供します。
- **rollCall.js**: 出欠確認のメッセージ生成と出欠情報の登録を行います。
- **monthlyAttendance.html**: 月間出欠を登録するためのHTMLフォームを提供します。
- **showAttendance.html**: 月ごとの出欠状況を一覧表示するためのHTMLページを提供します。
- **trigger.js**: 定期実行される関数を定義し、週ごとのメッセージ送信などを実行します。
- **concertInfo.js**: Webサイトから演奏会情報を取得し、メッセージを生成します。
- **allConcertInfo.html**: 演奏会情報を一覧表示するためのHTMLページを提供します。

## 開発環境

- Google Apps Script (GAS)
- LINE Messaging API
- Gemini API

## 必要なAPIキー

以下のAPIキーをGoogle Drive内の指定フォルダにテキストファイルとして保存してください。

- `line_apikey.txt` : LINE Messaging APIのアクセストークン
- `gemini_apikey.txt` : Gemini APIの認証キー

## スプレッドシートの設定

以下のシート名を持つスプレッドシートが必要です。

- **UserID**: LINEユーザーIDとユーザー名を格納します。
- **Log**: 各種ログを記録します。
- **KeyLog**: 鍵の貸出・返却履歴を記録します。
- **Reminder**: リマインダー情報を格納します。
- **ErrorLog**: エラーログを記録します。
- **Attendance**: 出欠情報を格納します。
- **Concert**: コンサート情報を格納します。

## 使い方

1.  Google Apps Scriptプロジェクトを作成します。
2.  上記のファイル構成に従って、各ファイルの内容をコピー＆ペーストします。
3.  必要なAPIキーをGoogle Driveにテキストファイルとして保存します。
4.  スプレッドシートを作成し、上記のスプレッドシート設定をします。
5.  `appsscript.json` に従って、`webapp`の設定を行い、URLを発行します。
6.  LINE Botの設定を行い、Webhook URLに発行したURLをセットします。
7.  LINE Botを起動し、各機能を使用します。

## 今後の課題

- プッシュ通知機能の実装
- より詳細なエラーハンドリング
- UI/UXの改善
- ドキュメントの充実化
- 定期実行時のカレンダーイベントの考慮
- DBの構造の改善

## ライセンス

MIT License

詳細については[LICENSE](LICENSE)ファイルを参照してください。


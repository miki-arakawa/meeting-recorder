# Microsoft Store 配布ガイド

## 概要

Meeting RecorderはMicrosoft Storeで配布可能なアプリケーションとして設計されています。

## 主な機能

### 🔐 ユーザーごとのAPIキー設定

- **初回セットアップウィザード**: アプリ初回起動時に表示されます
- **設定画面**: いつでもAPIキーを変更可能
- **セキュアな保存**: electron-storeで暗号化されて保存
- **環境変数不要**: `.env`ファイルは不要です

### 📝 対応するAPIキー

1. **OpenAI API キー**（文字起こし用）
   - Whisper APIによる高精度な音声認識
   - 取得先: https://platform.openai.com/api-keys

2. **Anthropic API キー**（議事録生成用）
   - Claude AIによる議事録自動生成
   - 取得先: https://console.anthropic.com/settings/keys

## Microsoft Store 申請準備

### 1. アプリのビルド

```bash
# Windows向けにビルド
npm run build:win
```

### 2. アプリパッケージの作成

electron-builderの設定は`package.json`に含まれています：

```json
{
  "build": {
    "appId": "com.yourcompany.meetingrecorder",
    "productName": "Meeting Recorder",
    "win": {
      "target": ["nsis"],
      "icon": "assets/icon.ico"
    }
  }
}
```

### 3. Microsoft Partner Centerでの申請

1. **Partner Centerアカウント作成**
   - https://partner.microsoft.com/dashboard にアクセス
   - 開発者アカウントを作成（$19/年）

2. **新しいアプリの作成**
   - 「新しいアプリ」をクリック
   - アプリ名「Meeting Recorder」を予約

3. **パッケージのアップロード**
   - `release/`ディレクトリからビルドされたアプリをアップロード
   - アプリの説明、スクリーンショット、カテゴリを設定

4. **審査提出**
   - すべての情報を入力後、審査に提出

## ユーザー向け説明

### アプリの説明（Store用）

**短い説明:**
AI搭載の会議録音・議事録自動生成アプリ。Zoom/Teamsの音声を録音し、自動で文字起こしと議事録を作成します。

**詳細な説明:**

Meeting Recorderは、オンラインミーティングの音声を録音し、AIを使って自動的に議事録を生成するデスクトップアプリケーションです。

**主な機能：**
- 🎙️ Zoom、Teams、Google Meetなどの音声を録音
- 📝 OpenAI Whisperによる高精度な文字起こし
- 📋 Claude AIによる議事録の自動生成
- 💾 すべてのデータをローカルに安全に保存
- ✏️ 議事録の編集とエクスポート（Markdown/PDF/Word）

**使い方：**
1. アプリを起動し、APIキーを設定（初回のみ）
2. 録音したいミーティングの音声ソースを選択
3. 録音開始・停止ボタンで録音
4. 自動的に文字起こしと議事録を生成

**必要なもの：**
- OpenAI APIキー（文字起こし用）
- Anthropic APIキー（議事録生成用、オプション）

※APIキーは各サービスの公式サイトで取得できます（従量課金）

### スクリーンショット推奨

1. メイン画面（録音パネル）
2. 録音履歴一覧
3. 文字起こし結果の表示
4. 議事録の表示と編集
5. 設定画面（APIキー設定）

## セキュリティとプライバシー

### データの取り扱い

- **ローカル保存**: すべての録音データはユーザーのPCにローカル保存
- **外部送信**: 文字起こしと議事録生成時のみ、選択したAPIに送信
- **APIキー**: 暗号化してローカルに保存
- **プライバシー**: ユーザーデータを収集・送信しません

### セキュリティ機能

- Context Isolation有効
- Node Integration無効
- Content Security Policy実装
- APIキーの暗号化保存

## サポート情報

### ユーザーサポート

- **ドキュメント**: アプリ内のREADME.mdを参照
- **問い合わせ**: GitHubのIssuesページ
- **公式サイト**: https://github.com/your-repo/meeting-recorder

### よくある質問

**Q: APIキーの料金はいくらですか？**
A: OpenAI Whisper APIは音声1分あたり約$0.006、Claude APIは使用量に応じた従量課金です。

**Q: オフラインで使用できますか？**
A: 録音はオフラインで可能ですが、文字起こしと議事録生成にはインターネット接続が必要です。

**Q: データはどこに保存されますか？**
A: すべてのデータはユーザーのPCにローカル保存されます。

## カテゴリと対象ユーザー

- **カテゴリ**: 生産性、ビジネス
- **対象ユーザー**: 
  - リモートワーカー
  - プロジェクトマネージャー
  - 会議を頻繁に行うビジネスパーソン
  - 議事録作成を効率化したい方

## 年齢制限

- **推奨**: 13歳以上（一般ユーザー向け）

## システム要件

- Windows 10 以上（64-bit）
- メモリ: 4GB以上推奨
- ストレージ: 500MB以上の空き容量
- インターネット接続（AI機能使用時）

## 更新履歴

### バージョン 1.0.0（初回リリース）
- システム音声録音機能
- OpenAI Whisperによる文字起こし
- Claude AIによる議事録生成
- ローカルデータベース
- エクスポート機能（Markdown/PDF/Word）

## ライセンス

MIT License

---

**開発者**: Your Company Name  
**サポート**: support@yourcompany.com  
**ウェブサイト**: https://yourcompany.com

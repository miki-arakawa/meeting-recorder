# Meeting Recorder

AI搭載のミーティング録音・議事録自動生成デスクトップアプリケーション

Zoom、Microsoft Teams、Google Meetなどのオンラインミーティングの音声をリアルタイムで録音し、OpenAI WhisperとClaude AIを使用して自動で文字起こしと議事録を生成します。

## 主な機能

- 🎙️ **システム音声録音**: デスクトップアプリケーション（Zoom/Teams等）の音声をキャプチャ
- 📝 **自動文字起こし**: OpenAI Whisper APIによる高精度な音声認識
- 📋 **AI議事録生成**: Claude AIによる議事録の自動生成
- 💾 **ローカル保存**: すべてのデータをローカルに安全に保存
- ✏️ **議事録編集**: 生成された議事録を自由に編集可能
- 📄 **エクスポート**: Markdown/PDF/Word形式で出力
- 🔐 **セキュア**: APIキーは暗号化してローカルに保存

## クイックスタート

### Microsoft Store版をご利用の場合

1. アプリを起動すると、初回セットアップウィザードが表示されます
2. OpenAI APIキーまたはAnthropic APIキーを設定
3. 「始める」ボタンをクリック
4. 録音タブで音声ソースを選択して録音開始！

### 開発者向け

```bash
# 1. 依存関係をインストール
npm install

# 2. 開発モードで起動
npm run dev
```

**注意**: 開発版でも、アプリ起動後にUIからAPIキーを設定できます。`.env`ファイルは不要です。

## APIキーの取得

### OpenAI API キー（文字起こし用）
1. https://platform.openai.com/api-keys にアクセス
2. アカウントを作成またはログイン
3. "Create new secret key" をクリック
4. 生成されたキーをコピーしてアプリで設定

### Anthropic API キー（議事録生成用）
1. https://console.anthropic.com/settings/keys にアクセス
2. アカウントを作成またはログイン
3. "Create Key" をクリック
4. 生成されたキーをコピーしてアプリで設定

## 使用方法

### 1. APIキーの設定

初回起動時またはいつでも設定画面から：
- OpenAI APIキー（文字起こし用）
- Anthropic APIキー（議事録生成用）

**少なくとも1つのAPIキーを設定してください。**

### 2. 録音

1. 録音タブを開く
2. 音声ソース（Zoomウィンドウなど）を選択
3. 録音開始ボタンをクリック
4. ミーティング終了後、停止ボタンをクリック

### 3. 文字起こしと議事録生成

1. 履歴タブで録音を選択
2. 「文字起こしを開始」をクリック
3. 完了したら「議事録を生成」をクリック
4. 議事録を編集してエクスポート

## プロジェクト構造

```
meeting-recorder/
├── src/
│   ├── main/          # Electronメインプロセス
│   ├── renderer/      # Reactアプリ
│   └── shared/        # 共有型定義
├── package.json
└── README.md
```

## ドキュメント

- [README.md](README.md) - このファイル
- [QUICKSTART.md](QUICKSTART.md) - 最速で始めるガイド
- [SETUP.md](SETUP.md) - 詳細なセットアップ
- [CONTRIBUTING.md](CONTRIBUTING.md) - 貢献ガイド
- [PROJECT_OVERVIEW.md](PROJECT_OVERVIEW.md) - プロジェクト詳細
- [MICROSOFT_STORE.md](MICROSOFT_STORE.md) - Microsoft Store配布ガイド

## API使用料について

- **OpenAI Whisper API**: 音声1分あたり約$0.006
- **Anthropic Claude API**: 入力トークンあたり約$0.003/1K、出力トークンあたり約$0.015/1K

詳細は各サービスの公式サイトをご確認ください。

## セキュリティ

- ✅ APIキーは暗号化してローカルに保存
- ✅ すべての録音データはローカルに保存
- ✅ Context Isolation有効
- ✅ 外部への自動送信なし

## システム要件

- Windows 10以上、macOS 10.15以上、またはLinux
- メモリ: 4GB以上推奨
- インターネット接続（AI機能使用時）

## ビルド

```bash
# Windows
npm run build:win

# macOS
npm run build:mac

# Linux
npm run build:linux
```

## ライセンス

MIT License

## サポート

問題が発生した場合は、GitHubのIssuesページで報告してください。

---

Made with ❤️ by the Meeting Recorder Team

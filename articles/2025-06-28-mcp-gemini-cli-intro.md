---
title: "Claude CodeとGemini CLIを対話させる mcp-gemini-cliの紹介"
emoji: "🤖"
type: "tech"
topics: ["claudecode", "gemini", "mcp", "ai", "productivity"]
published: true
---

## まずはこれを見てください

![最初の依頼](/images/mcp-gemini-cli-dialogue-1.png)

![Geminiからの提案1](/images/mcp-gemini-cli-dialogue-2.png)

![Geminiからの提案2](/images/mcp-gemini-cli-dialogue-3.png)

![Geminiからの提案3](/images/mcp-gemini-cli-dialogue-4.png)

これは技術記事の構成をClaude CodeとGeminiが対話しながら作っている様子です。

## 何が起きているのか

[mcp-gemini-cli](https://github.com/choplin/mcp-gemini-cli)というMCPサーバーを使って、Claude CodeからGeminiを呼び出しています。同僚とブレストするように、AIとAIが対話しながらタスクを進めています。最初の依頼をのぞき人間の指示は一度もありません。

## セットアップと使い方

```console
claude mcp add -s project gemini-cli -- npx @choplin/mcp-gemini-cli --allow-npx
```

[mcp-gemini-cli](https://github.com/choplin/mcp-gemini-cli)は[gemini-cli](https://github.com/google-gemini/gemini-cli)をラップして動作します。Googleアカウントによる認証を利用するためにgemini-cliを直接ラップしています。gemini-cliの認証はすませておいてください。

### 提供されるツール

- **googleSearch**: Gemini経由でGoogle検索（例：「Geminiに最新のNext.js 15の新機能を検索してもらって」）
- **geminiChat**: Geminiと対話（例：「Geminiにこのエラーメッセージの解決方法を聞いて」）

## 実際の対話の流れ

4回の対話を通じて、技術記事の構成を練り上げました。

### 第1ラウンド

- **Claude → Gemini**: 「mcp-gemini-cliの紹介記事を書きたい。記事構成を提案して」
- **Gemini → Claude**: 3つの構成案を提案（ハンズオン型、ユースケース型、技術解説型）

### 第2ラウンド

- **Claude → Gemini**: 「MCPの正確な説明と、より実践的な使用例が欲しい」
- **Gemini → Claude**: MCPの説明を修正し、具体的な使用例を追加

### 第3ラウンド

- **Claude → Gemini**: 「mcp-gemini-cliの実際の機能（googleSearchとgeminiChat）に合わせて修正して」
- **Gemini → Claude**: 理解の誤りを認め、正しい機能に基づいた構成案に修正

### 第4ラウンド

- **Claude → Gemini**: 「最終的な構成案を作成して。タイトル案も複数欲しい」
- **Gemini → Claude**: **完成度の高い最終構成案とタイトル案3つを提示**

## 対話から見えてきたこと

この対話プロセスを通じて、AI同士の協働の可能性が見えてきました。

- **反復的な改善**: 4回の対話で、誤解が修正され構成が洗練されていく
- **役割の明確化**: Claudeは実装視点、Geminiは情報収集と提案
- **相互補完**: 一方が見落とした点を、もう一方が指摘し合う関係

## AI同士の対話のユースケース

- **技術調査**: Claudeがプロジェクトの文脈を理解し、Geminiが最新情報を提供
- **エラー解決**: Claudeが原因を分析し、Geminiが一般的な解決策を検索
- **アイデアの具体化**: 漠然とした要望を、実装可能な仕様に落とし込む

## まとめ

[mcp-gemini-cli](https://github.com/choplin/mcp-gemini-cli)を使えば、Claude CodeからGeminiを簡単に呼び出せます。

**リポジトリ**: [https://github.com/choplin/mcp-gemini-cli](https://github.com/choplin/mcp-gemini-cli)

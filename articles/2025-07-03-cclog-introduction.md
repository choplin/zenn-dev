---
title: "cclog - Claude Codeセッションビューア + 即時レジューム"
emoji: "📜"
type: "tech"
topics: ["claudecode", "cli", "fzf", "shell", "productivity"]
published: false
---

過去のClaude Codeセッションを瞬時に見つけて再開できるツール「[cclog](https://github.com/choplin/cclog)」を作りました。

## cclogとは

cclogは、Claude Codeのセッションログをfzfでインタラクティブに閲覧し、`claude --resume` によるセッション再開まで快適に行うシェルスクリプトツールです。

Claude Codeはセッションログを`~/.claude/projects/`配下にプロジェクトごとに保存しています。cclogはこのログファイルを解析して、使いやすい形で表示します。

![cclogの動作デモ](/images/2025-07-03-cclog-introduction/cclog-overview.gif)

## 主な機能

### 1. セッション一覧表示

```bash
$ cclog
```

現在のディレクトリのClaude Codeセッションを一覧表示。セッションID、開始時刻、最初のメッセージが確認できます。

![セッション一覧画面](/images/2025-07-03-cclog-introduction/cclog-session-list.png)

### 2. ログ詳細表示

fzfのプレビューウィンドウでセッション内容をリアルタイム表示。メッセージは色分けされ、セッション情報（ファイル名、メッセージ数、開始時刻、実行時間）も表示されます。

- **User**: シアン
- **Assistant**: 白
- **Tool**: グレー

![プレビューウィンドウでのログ詳細表示](/images/2025-07-03-cclog-introduction/cclog-detail.png)

### 3. セッション即時レジューム

`Ctrl-R`を押すだけで、選択したセッションを`claude -r`で即座に再開。中断した作業の継続がスムーズに行えます。

![セッションレジューム実行画面](/images/2025-07-03-cclog-introduction/cclog-resume.png)

## 必要な環境

- `fzf` - ファジーファインダー
- `python3` - JSON解析用
- `claude` - Claude Code CLI（再開機能を使う場合）

## インストール

### Sheldon

```toml
[plugins.cclog]
github = "choplin/cclog"
```

その他のプラグインマネージャー（Oh-My-Zsh、Zinit、Zplug等）やマニュアルインストール方法は[README](https://github.com/choplin/cclog)をご覧ください。

## 使い方

```bash
# セッション一覧を表示してインタラクティブに操作
$ cclog
```

キーバインド：

- **↑↓**: セッション選択
- **Enter**: セッションIDを返す
- **Ctrl-V**: ログ全体を表示
- **Ctrl-P**: ログファイルのパスを返す
- **Ctrl-R**: セッションを再開

## まとめ

cclogを使えば、Claude Codeのセッションログを効率的に管理・閲覧できます。過去の作業内容の確認や中断したセッションの再開など、Claude Codeをより快適に使うことができます。

ぜひ試してみてください！

GitHub: https://github.com/choplin/cclog

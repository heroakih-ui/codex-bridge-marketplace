# Claude Code → Codex Bridge

このPC向けに作成した個人用プラグインです。公式プラグインではありません。Claude CodeからローカルのCodex CLIを呼び出します。Codexデスクトップの既存チャットとの会話共有や双方向の自動同期は行いません。

## Claude Code内でインストール

次の2行を、Claude Codeの入力欄で順番に実行してください。

```text
/plugin marketplace add C:/Users/Admin/Desktop/codex-bridge-marketplace
/plugin install codex-bridge@local-codex-bridge
```

プラグインを有効にして新しいセッションを開き、次を実行してください。

```text
/codex-bridge:check
```

コマンドの検出、ログイン状態、実際の応答を確認します。Codexへの確認リクエストが1回発生します。

## 使い方

対象のプロジェクトをClaude Codeで開いて実行します。

```text
/codex-bridge:review 現在の変更に不具合がないか確認して
/codex-bridge:task ログイン画面の入力チェックを実装して
```

reviewは読み取り専用、taskは対象プロジェクト内への書き込みを許可します。Claude Codeが依頼を渡し、返ってきた結果や変更を確認します。実行するたびに必要な背景を渡すため、両者が自動で全会話を共有するわけではありません。

## 前提と環境

- Claude CodeとCodex CLIが同じ実行環境から利用できること。
- Codexでログインしていること。必要ならその環境で `codex login` を実行してください。
- WSLではこのフォルダーは `/mnt/c/Users/Admin/Desktop/codex-bridge-marketplace` です。登録時のパスを置き換え、CodexもWSL内で利用できることを確認してください。
- リモートやクラウドのClaude CodeにはローカルWindowsのフォルダーは見えません。フォルダーをその環境へコピーし、登録パスを変更する必要があります。
- ZIPを使う場合は展開して、展開したフォルダーをマーケットプレイスとして登録してください。

## 確認状況

作成時にJSON構文、構成ファイルと参照先、Codex CLIのexecオプション、Windows側のCodexログイン状態を確認しました。Claude Codeの実行コマンドはこのターミナルから見つからないため、Claude Codeによるプラグイン検証・インストールと、プラグイン経由の実際の応答は未確認です。

Claude Codeが動くターミナルで追加検証する場合:

```text
claude plugin validate C:/Users/Admin/Desktop/codex-bridge-marketplace
claude plugin validate C:/Users/Admin/Desktop/codex-bridge-marketplace/plugins/codex-bridge
```

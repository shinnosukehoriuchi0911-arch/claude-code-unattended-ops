# claude-code-unattended-ops

**Claude Code / Codex CLI を Windows で無人実行し、サブスクの週の利用枠を「自分の分を残したまま」使い切る運用キット**（PowerShell 5.1 ＋ タスクスケジューラ）。

> **状態：設計と目次だけ。スクリプトはまだこのリポジトリにありません。**
> 本にする前に「欲しい人がいるか」を確かめています。欲しければ **Star** を、要望があれば **Issue** をください。
> 設計の全文（何を入れ、何を入れないか）は Zenn の記事にあります：
> https://zenn.dev/shinai/articles/claude-code-unattended-ops-design

## 何が手に入る予定か

| ファイル | 役割 | 公開範囲（予定） |
|---|---|---|
| `autorun.ps1` | 毎時、使用率をトークン0で読み、ペース線より下の枠だけ AI を無人起動。早く終わったら続きから再起動 | 読む関数とペース線の判定は無料 |
| `autorun.config.json` | 調整値（先行%・5時間枠の上限・1回の分数・再起動回数） | 有料 |
| `publish-gate.ps1` | AI の代わりに `git push` する検査つきスクリプト（分岐なし／許可フォルダのみ／削除なし／秘密情報なし／1日1件／`-DryRun`） | 有料 |
| `permissions/claude-unattended.txt` | `claude -p` の `--allowedTools` / `--disallowedTools` の例と理由 | **無料** |
| `prompts/` | 無人 AI への指示（時間でなく成果の数で終わらせる）、複数 AI のリレー | 有料 |
| `templates/` | タスク板・進捗（5行以内）・人だけの作業 | タスク板は無料 |
| `skills/unattended-setup/SKILL.md` | Claude Code に導入させるスキル。ダミーファイルで deny が効くか必ず試す | 有料 |
| `CLAUDE.md.template` ＋ `checklists/token-saving.md` | 200行未満の CLAUDE.md の型、要約係サブエージェントの例 | 無料 |
| `docs/measurements.md` | 実測（日付・条件つき） | 有料 |

## 対象

- Windows 11 ＋ PowerShell 5.1 ＋ タスクスケジューラ
- Claude Code CLI（`claude -p`）、Codex CLI（`codex exec`）
- macOS / Linux は **未対応**（設計は同じ。スクリプトは作っていません）

## 注意

- サブスクのログインでの無人実行が Anthropic の利用規約上どう扱われるかは、一次情報で確認できていません。推奨構成は **Claude Console の API キー** で動かす形にする予定です。
- 無人実行は自己責任です。キットは「お金」「アカウント」「元に戻せない操作」を技術的に止める側に倒しますが、完全ではありません。

## 反応の見方（公開して7日）

- Star と Issue の数、Zenn 記事のいいねとコメントを見て、本を書くかどうかを決めます。
- 反応が少なければ本は書かず、無料にする予定だった `permissions/` と `CLAUDE.md.template` だけをここに置きます。

## License

公開するファイルは MIT License の予定です。

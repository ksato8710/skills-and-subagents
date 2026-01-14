# skills-and-subagents
skills と subagents の管理用リポジトリ。

## Skills

### review-codex

Codex CLI を使用してコード変更をレビューするスキル。

**使い方:**
```
/review-codex                    # uncommitted な変更をレビュー
/review-codex --base main        # main ブランチとの差分をレビュー
/review-codex --commit abc123    # 特定のコミットをレビュー
```

**インストール:**
```bash
claude config add skills /path/to/skills-and-subagents/skills/review-codex
```

## ディレクトリ構成

```
skills/
├── review-codex/
│   └── SKILL.md          # スキル定義
└── review-codex.skill    # パッケージ版
```

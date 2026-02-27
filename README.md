# Skills and Subagents

> Claude Code / Codex CLI 向けスキルとサブエージェントの管理リポジトリ

[![License: MIT](https://img.shields.io/badge/License-MIT-green?style=flat-square)](#license)

![Skills and Subagents Overview](screenshot.png)

---

## Why -- なぜこのリポジトリが必要か

Claude Code や Codex CLI のスキル定義は各プロジェクトに散在しがちで、再利用や品質管理が困難になります。このリポジトリは、スキルとサブエージェントを **一元管理・パッケージング・配布** するためのハブとして機能します。

標準化された `SKILL.md` フォーマットにより、スキルの目的・使い方・前提条件を明確に定義し、プロジェクト横断で再利用可能にします。

## Features

- **スキルパッケージング** -- 標準化された `.skill` パッケージ形式でスキルを配布
- **Codex CLI レビュー統合** -- `review-codex` スキルによる Codex CLI を活用したコードレビュー自動化
- **標準 SKILL.md フォーマット** -- 目的・使い方・前提条件を統一形式で定義
- **簡単インストール** -- `claude config add` コマンドで即座にスキルを追加可能

## Tech Stack

| 項目 | 技術 |
|------|------|
| スキル定義 | Markdown (SKILL.md) |
| パッケージ形式 | `.skill` ディレクトリ |
| 対応ツール | Claude Code, Codex CLI |
| 配布方式 | Git clone + `claude config add` |

## Getting Started

### Prerequisites

- **Claude Code** -- Anthropic の公式 CLI
- **Codex CLI** (任意) -- `review-codex` スキル使用時に必要

### Installation

```bash
# リポジトリをクローン
git clone https://github.com/ksato8710/skills-and-subagents.git
cd skills-and-subagents

# (任意) npm パッケージを利用するスキルがある場合
npm install

# スキルを Claude Code に登録
claude config add skills /path/to/skills-and-subagents/skills/review-codex

# 動作確認
claude # Claude Code を起動し /review-codex を実行
```

### Environment Variables

特別な環境変数は不要です。スキルは Claude Code / Codex CLI の既存設定に依存します。

## Architecture

```
skills-and-subagents/
├── skills/                          # スキル定義
│   └── review-codex.skill/         #   Codex CLI レビュースキル
│       └── SKILL.md                #     スキル定義ファイル
└── README.md                        # 本ファイル
```

### Key Files

| ファイル | 役割 |
|---------|------|
| `skills/review-codex.skill/SKILL.md` | Codex CLI レビュースキルの定義・使用方法・前提条件 |

## Commands

### review-codex スキル

| コマンド | 説明 |
|---------|------|
| `/review-codex` | 未コミットの変更をレビュー |
| `/review-codex --base main` | main ブランチからの差分をレビュー |
| `/review-codex --commit abc123` | 特定コミットの変更をレビュー |

### スキル管理

```bash
# スキルの登録
claude config add skills /path/to/skills-and-subagents/skills/review-codex

# 登録済みスキルの確認
claude config list skills

# スキルの削除
claude config remove skills review-codex
```

## スキル作成ガイド

新しいスキルを追加する場合は、以下の構造に従ってください:

```
skills/
└── your-skill-name.skill/
    └── SKILL.md       # 必須: スキル定義
```

`SKILL.md` には以下を含めてください:

1. **スキル名と概要** -- 一文で何をするスキルか
2. **前提条件** -- 必要なツールや環境
3. **使用方法** -- コマンド例と引数の説明
4. **出力** -- スキル実行後の結果

## Deploy

本リポジトリはサービスとしてのデプロイは不要です。各プロジェクトが `claude config add skills` でローカルパスを指定してスキルを参照します。

## Testing

スキルの動作検証は Claude Code セッションで実施:

1. `claude config add skills ./skills/review-codex` でスキルを登録
2. テスト用の変更を作成し `/review-codex` を実行
3. レビュー出力が期待通りであることを確認

## Related Projects

| プロジェクト | 関係 |
|-------------|------|
| [Product Hub](https://github.com/ksato8710/product-hub) | プロダクトエコシステム管理基盤・スキルカタログ管理 |
| [openclaw-config](https://github.com/ksato8710/openclaw-config) | OpenClaw エージェント設定 (86 スキル管理) |
| [codex-cli-config](https://github.com/ksato8710/codex-cli-config) | Codex CLI ホーム設定 |

## Changelog

| 日付 | 変更内容 |
|------|----------|
| 2026-02 | review-codex スキルのパッケージ化 (.skill 形式) |
| 2026-01 | 初期リポジトリ作成、SKILL.md フォーマット策定 |

## Roadmap

- [ ] スキルテンプレートジェネレーターの追加
- [ ] スキルバージョニング機能
- [ ] Product Hub スキルカタログとの自動同期 (`standards/skill-catalog/`)
- [ ] サブエージェント定義の追加
- [ ] スキル依存関係管理

## Contributing

新しいスキルの追加や既存スキルの改善を歓迎します。

1. `skills/` 配下に `.skill` ディレクトリを作成
2. `SKILL.md` を標準フォーマットで記述
3. Pull Request を作成

## License

MIT License

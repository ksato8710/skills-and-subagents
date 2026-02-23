---
name: review-codex
description: "Codex CLIを使用してコード変更をレビューする。実装したコード、未コミットの変更、特定のコミットをレビューしたい場合に使用。トリガー：codexでレビュー、コードレビュー、変更をレビュー、レビューして"
---

# Review Codex

Run `codex review` to analyze code changes and provide feedback.

## Usage

### Review Uncommitted Changes (Default)

```bash
codex review --uncommitted
```

Reviews all staged, unstaged, and untracked changes in the current directory.

### Review Against Base Branch

```bash
codex review --base main
```

Reviews changes compared to the specified base branch.

### Review Specific Commit

```bash
codex review --commit <SHA>
```

Reviews changes introduced by a specific commit.

### With Custom Instructions

```bash
codex review --uncommitted "Focus on security vulnerabilities"
```

Add a prompt to provide specific review instructions.

## Options

| Option | Description |
|--------|-------------|
| `--uncommitted` | Review staged, unstaged, and untracked changes |
| `--base <BRANCH>` | Review changes against the given base branch |
| `--commit <SHA>` | Review changes introduced by a specific commit |
| `--title <TITLE>` | Optional title to display in review summary |
| `-m, --model <MODEL>` | Specify model to use |

## Workflow

1. Determine what to review:
   - No args provided → use `--uncommitted` (most common)
   - PR context → use `--base <target-branch>`
   - Specific commit → use `--commit <sha>`

2. Run `codex review` with appropriate options

3. Present the review results to the user

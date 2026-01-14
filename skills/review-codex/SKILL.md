---
name: review-codex
description: Review code changes using Codex CLI. Use this skill when the user wants to review implemented code, uncommitted changes, or specific commits using the codex review command. Triggers on requests like "review my changes with codex", "codex review", or "review this commit".
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

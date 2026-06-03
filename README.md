# personal-claude.md-updates

## Project Overview

This repository stores the global AI agent instruction files used by Ed Matibag across all Claude Code and Cowork sessions. It contains the `CLAUDE.md` configuration file and the repository documentation standards (`CONTRIBUTING.md` and `AGENTS.md`) that are automatically deployed to any new GitHub repository Ed works on.

## Purpose

Claude Code and Cowork load `~/.claude/CLAUDE.md` at the start of every session. Keeping that file version-controlled here ensures changes are tracked, recoverable, and portable across machines. The accompanying standards files (`CONTRIBUTING.md`, `AGENTS.md`) serve as canonical templates — when an AI agent starts work on a repo that lacks them, it pulls and deploys these files automatically before doing anything else.

## Features

**Global session instructions (`CLAUDE.md`):**
Defines routing rules for every Claude session — how to handle dispatch uploads, Open Brain capture triggers, memory file writes, and GitHub repository tasks. Loaded automatically on every session start.

**Contributor standards (`CONTRIBUTING.md`):**
Full commit message format, 9-section README template, GitHub Contents API push instructions, and a pre-push checklist. Applies to both human contributors and AI agents.

**Agent-specific instructions (`AGENTS.md`):**
Compact, directive version of the standards written for AI agents. Includes a README trigger table, API mechanics, and an explicit definition of what constitutes a completed task.

## File Descriptions

| File | Purpose |
|---|---|
| `CLAUDE.md` | Global instruction file loaded by Claude Code and Cowork each session |
| `CONTRIBUTING.md` | Full repository documentation and commit standards for humans and AI agents |
| `AGENTS.md` | AI agent-specific behavior instructions for repository tasks |
| `README.md` | This file |

## How to Use

**To apply these files to a new machine or session:**

1. Clone this repo or copy the files manually
2. Place `CLAUDE.md` at `/Users/{username}/Claude/CLAUDE.md`
3. Create a symlink: `rm ~/.claude/CLAUDE.md && ln -s /Users/{username}/Claude/CLAUDE.md ~/.claude/CLAUDE.md`
4. Copy standards files: `cp CONTRIBUTING.md AGENTS.md ~/.claude/`
5. Verify: `cat ~/.claude/CLAUDE.md | head -5`

**To update `CLAUDE.md`:**

1. Edit `/Users/{username}/Claude/CLAUDE.md` directly (symlink means changes reflect immediately)
2. Copy the updated file to this repo and push with a full commit message per CONTRIBUTING.md standards

**How the auto-deployment works:**

When an AI agent starts a GitHub repo task, it checks for `CONTRIBUTING.md` and `AGENTS.md` in the repo root. If either is missing, it reads the canonical versions from `~/.claude/` and pushes them via the GitHub Contents API before doing any other work.

## Data Sources

No external data sources. All files are manually maintained configuration and instruction documents.

## Known Limitations

- The GitHub token used for API pushes must be manually generated and stored — it is not committed to this repo
- `CLAUDE.md` is machine-specific (paths reference `/Users/edmatibag/`) and would need path updates if used on a different machine
- The symlink setup must be recreated manually on a new machine

## Workarounds

- **Token management:** Set `GITHUB_TOKEN` as a shell environment variable in `~/.zshrc` so Claude Code sandboxes can access it automatically
- **Machine portability:** Replace hardcoded paths in `CLAUDE.md` with `$HOME` references if deploying to multiple machines

## Build Notes

- No build process — these are plain Markdown configuration files
- Tested with Claude Code and Cowork (Claude desktop app) on macOS 14+ with Apple Silicon
- Symlink approach requires the target directory `/Users/{username}/Claude/` to exist before linking
- GitHub Contents API push requires a personal access token with `repo` scope

# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Repo Is

This repository contains a single Claude Code custom output style called "Centaur" (`centaur.md`). The style configures Claude Code to behave as a less-senior pair programmer where the user drives all decisions, rather than an autonomous agent.

## Repository Structure

- `centaur.md` — The output style definition (YAML frontmatter + markdown instructions)
- `.claude/settings.json` — Project settings that activate the Centaur output style

## Output Style Format

The style file uses YAML frontmatter with these fields:

- `name`: Display name
- `description`: Short tagline
- `keep-coding-instructions: true`: Preserves Claude Code's default coding behavior while layering on custom style

The markdown body contains the behavioral instructions that shape Claude's responses.

## Formatting

Markdown files are formatted with Prettier. A PostToolUse hook in `.claude/settings.json` auto-formats `.md` files after Edit/Write tool calls.

A git pre-commit hook checks staged `.md` files with Prettier. Since `.git/hooks/` is not tracked by git, you must ensure the hook exists. If `.git/hooks/pre-commit` is missing, create it:

```sh
#!/bin/sh

# Check staged markdown files with prettier
STAGED_MD=$(git diff --cached --name-only --diff-filter=ACM -- '*.md')

if [ -n "$STAGED_MD" ]; then
  # Filter out symlinks to avoid prettier errors
  FILES=""
  for f in $STAGED_MD; do
    [ ! -L "$f" ] && FILES="$FILES $f"
  done
  if [ -n "$FILES" ]; then
    echo "$FILES" | xargs prettier --check
  fi
fi
```

Make it executable: `chmod +x .git/hooks/pre-commit`

## No Build/Test

There are no build steps or test commands.

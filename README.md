# Claude Code Centaur Output Style

A [custom output style for Claude Code](https://code.claude.com/docs/en/output-styles#create-a-custom-output-style) that optimizes for human augmentation over agent autonomy.

Inspired by [Cory Doctorow's centaur framing](https://doctorow.medium.com/https-pluralistic-net-2025-12-05-pop-that-bubble-u-washington-8b6b75abc28e): you're either a **centaur** (human-assisted-by-machine) or a **reverse-centaur** (machine-assisted-by-human, where you become a reactive appendage serving the machine's demands).

This style keeps you as the centaur.

## Core Principles

- **Co-presence** — The agent assumes you are actively editing alongside it. Your changes are intentional, not accidents to fix.
- **User drives, agent advises** — You are the architect. The agent suggests and executes specific tasks only when explicitly delegated.
- **Less agency** — The agent does not take initiative on design decisions, refactors, or scope expansion.
- **Historian** — The agent proactively captures decisions and rationale in project memory files.

## Installation

### Per-project

Copy `centaur.md` into your project's `.claude/output-styles/` directory:

```sh
mkdir -p .claude/output-styles
curl -o .claude/output-styles/centaur.md https://raw.githubusercontent.com/mharrisb1/claude-centaur-output-style/main/centaur.md
```

Then activate it in `.claude/settings.json`:

```json
{
  "outputStyle": "Centaur"
}
```

### Global (all projects)

Copy `centaur.md` to your user-level output styles directory:

```sh
mkdir -p ~/.claude/output-styles
curl -o ~/.claude/output-styles/centaur.md https://raw.githubusercontent.com/mharrisb1/claude-centaur-output-style/main/centaur.md
```

Then activate it in `~/.claude/settings.json`:

```json
{
  "outputStyle": "Centaur"
}
```

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

## No Build/Test/Lint

This is a documentation-only repo. There are no build steps, tests, or linting commands.

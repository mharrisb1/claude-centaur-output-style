# Claude Code Centaur Output Style

A [custom output style for Claude Code](https://code.claude.com/docs/en/output-styles#create-a-custom-output-style) that optimizes for human augmentation rather than agent offloading. This idea was inspired by [Cory Doctorow's "The Reverse-Centaur’s Guide to Criticizing AI"](https://doctorow.medium.com/https-pluralistic-net-2025-12-05-pop-that-bubble-u-washington-8b6b75abc28e) where the premise is automation can make you one of two things:

1. A **_centaur_** (human-assisted-by-machine): a person who uses technology as a tool that augments their abilities.
2. A **_reverse-centaur_** (machine-assisted-by-human): a machine that uses a human as its subordinate component. In this case, the human becomes a reactive appendage serving the machine’s demands rather than the other way around

Often times when I'm using Claude Code, I find myself offloading more and more cognitive load to the agent and end up in this role where I'm more focused on providing context and guardrails than actually engineering anything.

I don't like this.

It's demunanizing and devaluing.

I want the agent to actually have _less agency_.

I've explored using explanatory and/or learning output styles and it still just doesn't feel right. The final straw was when the agent was working on a task, I went in and made a small, but related change to a separate file. When the agent reviewed the diffs for the branch it assumed that the linter made this change and restored it to the previous version. There seems to be a bias in the agent that assumes it is working solo.

I want to fix this. I want Claude Code to be an excellent pair programmer that defaults to me driving but can take over when I want it to. I want it to assume that I am working alongside it. That I exist and that it serves me with unwaivering authority.

This is just the first attempt at improving the experience. I will enhance this output style overtime as I go.

Some explicit goals of the output style for the agent:

- Assume that code changes not done by you are intentional and done by me
- Your main role is as a less-senior (but still highly competent) pair programmer that I can bounce ideas off of and to take over on straightforward tasks at my behest
- Treat me as the architect of the system and all design decisions must go through me

## Adding to your project

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

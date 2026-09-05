# Coordinator Mode

A Claude Code skill that turns Claude into a structured **coordinator** for complex software tasks instead of a single-pass code executor. Work is decomposed into four phases — **Research → Synthesis → Implementation → Verification** — with a persistent task board tracking progress.

The coordinator never writes code until it has a synthesised spec with concrete file paths and line numbers.

## When to use it

Trigger phrases: `coordinate this`, `orchestrate`, `break this down`, `coordinator mode`, `4-stage pipeline`, `research then implement`.

Good fits:
- Large refactors and migrations
- Multi-module features
- Cross-layer changes (frontend + backend + tests)
- Anything where jumping straight to implementation would produce sloppy results

## How it works

The skill enforces an **asymmetric tool model**:

- **Coordinator** plans, decomposes, delegates, synthesises — does not edit source files or run state-changing commands.
- **Workers** execute scoped jobs, edit files within their scope, run tests, and return a structured `<task-notification>` block.

After each phase the coordinator publishes a progress summary to the user before moving on. Blocked or failed workers must be resolved, not skipped.

See [SKILL.md](SKILL.md) for the full protocol and [references/task-board-format.md](references/task-board-format.md) for the task board schema.

## Install

Clone into your Claude Code skills directory:

```bash
git clone https://github.com/breezyenm/coordinator-mode.git \
  ~/.claude/skills/coordinator-mode
```

Claude Code auto-discovers skills under `~/.claude/skills/`. Restart your session and the skill becomes available.

## Usage

Inside any Claude Code session:

```
coordinate this: migrate the auth layer from Passport to Lucia across the API and the web client
```

Claude will load the skill, set up the task board, and walk the four phases.

## Layout

```
coordinator-mode/
├── SKILL.md                          # Full protocol (loaded by Claude)
└── references/
    └── task-board-format.md          # Task board schema
```

## License

MIT

# dotagents

Agent-related configuration and instructions.

## Layout

```
pi/
├── AGENTS.md          # Persistent global agent instructions
├── settings.json      # pi UI/app settings (theme, changelog version)
├── models-store.json  # Model catalog (definitions, pricing, capabilities)
└── skills/            # Global agent skills (loaded on-demand)
claude-code/
├── CLAUDE.md          # Persistent global Claude Code instructions
├── settings.json      # Claude Code settings (theme, etc.)
└── skills/            # Global Claude Code skills (loaded on-demand)
```

## pi

These files live under `~/.pi/agent/` at runtime. To restore:

```sh
mkdir -p ~/.pi/agent
cp pi/AGENTS.md ~/.pi/agent/AGENTS.md
cp pi/settings.json ~/.pi/agent/settings.json
cp pi/models-store.json ~/.pi/agent/models-store.json
cp -r pi/skills ~/.pi/agent/skills
```

## claude-code

These files live under `~/.claude/` at runtime. To restore:

```sh
mkdir -p ~/.claude
cp claude-code/CLAUDE.md ~/.claude/CLAUDE.md
cp claude-code/settings.json ~/.claude/settings.json
cp -r claude-code/skills ~/.claude/skills
```

## Security

Secrets are **never** committed here. `~/.pi/agent/auth.json` (OAuth tokens)
is intentionally excluded via `.gitignore`. Session history (`sessions/`) and
local binaries (`bin/`) are also excluded.

For Claude Code, `~/.claude/.credentials.json` and `~/.claude.json` (OAuth
tokens, account state) are excluded, as are history, `projects/` (transcripts
and memory), sessions, caches, and plugins.

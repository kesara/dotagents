# dotagents

Agent-related configuration and instructions.

## Layout

```
pi/
├── AGENTS.md          # Persistent global agent instructions
├── settings.json      # pi UI/app settings (theme, changelog version)
└── models-store.json  # Model catalog (definitions, pricing, capabilities)
```

## pi

These files live under `~/.pi/agent/` at runtime. To restore:

```sh
mkdir -p ~/.pi/agent
cp pi/AGENTS.md ~/.pi/agent/AGENTS.md
cp pi/settings.json ~/.pi/agent/settings.json
cp pi/models-store.json ~/.pi/agent/models-store.json
```

## Security

Secrets are **never** committed here. `~/.pi/agent/auth.json` (OAuth tokens)
is intentionally excluded via `.gitignore`. Session history (`sessions/`) and
local binaries (`bin/`) are also excluded.

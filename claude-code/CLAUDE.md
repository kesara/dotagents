# Global Instructions

## Pushing

Never run `git push` (or otherwise push to a remote). Leave pushing to the
user. Committing locally is fine.

## Branching

Before creating a commit, check the current branch. If the project is on the
`main` branch, create a new branch first (do not commit directly to `main`),
unless the project explicitly opts into direct-to-main commits (e.g. via its
own project-level `AGENTS.md` / `CLAUDE.md`, as the `dotagents` repo does).

Name new branches using conventional-commit-style prefixes, for example:
`feat/`, `fix/`, `chore/`, `docs/`, `build/`, `refactor/`, `test/`.

## author-tools

Whenever the xml2rfc version is updated in the `author-tools` project
(`requirements.txt` / `constraints.txt`), remind the user to also update
https://github.com/rfc-editor-drafts/base-devcontainer

## dotagents sync

The `dotagents` repo mirrors `~/.claude/` config under `claude-code/`. It
tracks `CLAUDE.md`, `settings.json`, and `skills/`. Whenever any of these
files under `~/.claude/` is updated, copy the change into the dotagents repo
(`claude-code/`) and commit it there. Never commit secrets
(`.credentials.json`, `.claude.json`), session history, projects/memory,
caches, or plugins.

### Keep pi and Claude Code in step

The dotagents repo also mirrors the pi agent config under `pi/`. Any change to
persistent instructions/knowledge or skills MUST be applied to both:

| Kind         | Claude Code                          | pi                                 |
|--------------|--------------------------------------|------------------------------------|
| Instructions | `~/.claude/CLAUDE.md` → `claude-code/CLAUDE.md` | `~/.pi/agent/AGENTS.md` → `pi/AGENTS.md` |
| Skills       | `~/.claude/skills/` → `claude-code/skills/`     | `~/.pi/agent/skills/` → `pi/skills/`     |

Adapt tool-specific details (e.g. `PI_*` env vars, co-author lines for other
providers) rather than copying them verbatim. If the live `~/.pi/agent/`
directory is absent on this machine, update `pi/` in the repo only.

Store durable preferences and knowledge in these instruction files or skills,
not in Claude Code's per-project memory, so they reach both agents.

## Amending commits

When amending a commit (`git commit --amend`), always show the diff of the
pending changes first and let the user review it before running the amend.

## Git commits

Use the following author identity for commits:

- Author: `Kesara Rathnayake <kesara@fq.nz>`

Always append a co-author trailer, plus a `Model:` line with the actual
running model ID and reasoning effort. This replaces Claude Code's default
attribution line:

```
Co-Authored-By: Claude <noreply@anthropic.com>
Model: <model> (thinking: <reasoning level>)
```

Substitute the actual running model and reasoning level. Example:

```
Co-Authored-By: Claude <noreply@anthropic.com>
Model: claude-opus-5-5 (thinking: medium)
```

## Writing specifications

When writing or updating a technical specification, use the
`writing-specifications` skill.

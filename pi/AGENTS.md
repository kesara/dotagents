# Global Instructions

## Branching

Before creating a commit, check the current branch. If the project is on the
`main` branch, create a new branch first (do not commit directly to `main`),
unless the project explicitly opts into direct-to-main commits (e.g. via its
own project-level `AGENTS.md`, as the `dotagents` repo does).

Name new branches using conventional-commit-style prefixes, for example:
`feat/`, `fix/`, `chore/`, `docs/`, `build/`, `refactor/`, `test/`.

## author-tools

Whenever the xml2rfc version is updated in the `author-tools` project
(`requirements.txt` / `constraints.txt`), remind the user to also update
https://github.com/rfc-editor-drafts/base-devcontainer

## dotagents sync

The `dotagents` repo (`~/.pi/agent/` config mirrored under `pi/`) tracks
`AGENTS.md`, `settings.json`, and `models-store.json`. Whenever any of these
files under `~/.pi/agent/` is updated, copy the change into the dotagents repo
(`pi/`) and commit it there. Never commit secrets (`auth.json`), session
history, local binaries, or `TODO.md`.

## Amending commits

When amending a commit (`git commit --amend`), always show the diff of the
pending changes first and let the user review it before running the amend.

## Git commits

Use the following author identity for commits:

- Author: `Kesara Rathnayake <kesara@fq.nz>`

Always append a co-author trailer identifying the model that assisted, plus a
`Model:` line with the actual running model and reasoning level (from
`PI_MODEL` / `PI_REASONING_LEVEL`).

Choose the co-author line based on the provider (`PI_PROVIDER`):

- Anthropic (Claude):
  ```
  Co-Authored-By: Claude <noreply@anthropic.com>
  Model: <model> (thinking: <reasoning level>)
  ```
- Google (Gemini):
  ```
  Co-Authored-By: Gemini <gemini@gogle.cc>
  Model: <model> (thinking: <reasoning level>)
  ```

Substitute the actual running model and reasoning level. Example:

```
Co-Authored-By: Claude <noreply@anthropic.com>
Model: claude-opus-4-8 (thinking: medium)
```

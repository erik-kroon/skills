# Agent Workflow

This repository is the canonical source for repo-managed skills.

## Installed Skill Sync

The local installed checkout lives at:

```text
/Users/erik/agent-skills
```

`/Users/erik/.agents/skills` should symlink to:

```text
/Users/erik/agent-skills/skills
```

Repo-managed skills in `/Users/erik/.codex/skills` should be individual
symlinks to matching directories under:

```text
/Users/erik/agent-skills/skills
```

Keep these local-only Codex skills as normal directories, not repo entries:

- `agent-browser`
- `cloudflare-deploy`
- `gh-fix-ci`
- `screenshot`
- `yeet`

Do not add those five operational skills to this repository.

## After Pushing Main

When an agent pushes this repository to `origin/main` from any workspace or
isolated worktree, update the installed checkout before finishing:

```bash
git -C /Users/erik/agent-skills pull --ff-only origin main
```

This makes future sessions use the freshly pushed repo skills through the
existing symlinks.

If the pull cannot fast-forward, stop and report the divergence. Do not reset,
merge, or rebase `/Users/erik/agent-skills` without explicit user approval.

## Scope Rules

- Commit only repository files.
- Do not commit local symlinks, installed-skill directories, plugin cache, or
  machine-specific state.
- Keep public skill inventory files in sync when adding, removing, or renaming
  skills:
  - `README.md`
  - `SKILL_MATRIX.md`
  - `skills-inventory.md`
  - `skills-inventory.json`

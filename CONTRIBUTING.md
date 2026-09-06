# Contributing

This repository is a **publish target**, not an authoring workspace.

## Where to change skills

| Skill directory | Edit in | Ships on |
| --- | --- | --- |
| `khora-cli/` | [khoralabs/khora](https://github.com/khoralabs/khora) → `apps/cli/assets/skills/khora-cli/` | `release-khora-cli` workflow |
| `agent-review/` | [khoralabs/agent-review](https://github.com/khoralabs/agent-review) → `skills/agent-review/` | `release` workflow |
| `vellum-cli/` | [khoralabs/vellum](https://github.com/khoralabs/vellum) → `apps/cli/assets/skills/vellum-cli/` | `release-vellum-cli` workflow |

Open a PR against the source repo. On the next CLI release (with `dry_run` off), CI replaces the matching directory here wholesale and updates `skill-source.json`.

## Do not

- Hand-edit files under a published skill directory in this repo (they will be overwritten).
- Commit skill content here that does not exist in the source repo.
- Change `skill-source.json` by hand; the publisher owns that file.

## Operator setup

Each source repo needs a `SKILLS_REPO_TOKEN` repository secret: a fine-grained PAT with **Contents: Write** on `khoralabs/skills` only. Without it, the publish step no-ops with a warning so local and dry runs stay safe.

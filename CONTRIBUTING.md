# Contributing

This repository is a **publish target**, not an authoring workspace.

## Where to change skills

| Skill directory | Edit in | Ships on |
| --- | --- | --- |
| `skills/khora-cli/` | [khoralabs/khora](https://github.com/khoralabs/khora) → `apps/cli/assets/skills/khora-cli/` | `publish-khora-cli-skills` workflow (after `release-khora-cli`) |
| `skills/agent-review/` | [khoralabs/agent-review](https://github.com/khoralabs/agent-review) → `skills/agent-review/` | `publish-skills` workflow (after CLI `release`) |
| `skills/vellum-cli/` | [khoralabs/vellum](https://github.com/khoralabs/vellum) → `apps/cli/assets/skills/vellum-cli/` | `publish-vellum-cli-skills` workflow (after `release-vellum-cli`) |

Open a PR against the source repo. After that CLI is released, run the matching **publish-skills** workflow (separate from release) with the released semver. CI replaces the matching directory under `skills/` wholesale and updates `skill-source.json`.

Skills publish is intentionally **not** part of the release job so a missing PAT or publish failure cannot block npm / Homebrew.

## Do not

- Hand-edit files under a published skill directory in this repo (they will be overwritten).
- Commit skill content here that does not exist in the source repo.
- Change `skill-source.json` by hand; the publisher owns that file.

## Operator setup

Each source repo needs a `SKILLS_REPO_TOKEN` repository secret: a fine-grained PAT with **Contents: Write** on `khoralabs/skills` only. Required for the publish-skills workflows; unused by release workflows.

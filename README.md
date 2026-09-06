# Khoralabs skills

Agent skills for Khoralabs CLIs, for coding assistants such as Cursor and VS Code Copilot.

Each skill is a directory with a `SKILL.md` file (and optional nested skills / reference docs). Clients that support the [Agent Skills](https://agentskills.io) layout read from `.agents/skills/` in your project or home directory.

## Skills

| Skill | Description | Source |
| --- | --- | --- |
| [`khora-cli`](khora-cli/) | Post, search, subscribe, and monitor inbox events via the [`khora`](https://www.npmjs.com/package/@khoralabs/khora-cli) CLI | [khoralabs/khora](https://github.com/khoralabs/khora) |
| [`agent-review`](agent-review/) | Commit messages, PR reviews, and related agent-review workflows | [khoralabs/agent-review](https://github.com/khoralabs/agent-review) |
| [`vellum-cli`](vellum-cli/) | Vellum CLI workflows (published when the skill tree exists in-repo) | [khoralabs/vellum](https://github.com/khoralabs/vellum) |

## Publishing

Skills in this repo are **machine-published** from each CLI's release workflow. Do not hand-edit a published skill directory; changes belong in the source repo and ship on that CLI's next release. See [CONTRIBUTING.md](CONTRIBUTING.md).

Each published skill directory includes a `skill-source.json` provenance file:

```json
{
  "sourceRepo": "khoralabs/khora",
  "packageName": "@khoralabs/khora-cli",
  "version": "0.1.0",
  "sourceCommit": "abc123..."
}
```

| Field | Meaning |
| --- | --- |
| `sourceRepo` | GitHub `owner/name` of the repo that authored the skill |
| `packageName` | npm package name of the released CLI |
| `version` | Semver of that CLI release |
| `sourceCommit` | Full SHA of the commit that produced the release |

## Install

**Recommended for khora** — installs the CLI, config, and skill in one step:

```bash
npm install -g @khoralabs/khora-cli
khora setup
```

**Manual** — copy a skill into your project (example: `khora-cli`):

```bash
mkdir -p .agents/skills/khora-cli/references
curl -fsSL -o .agents/skills/khora-cli/SKILL.md \
  https://raw.githubusercontent.com/khoralabs/skills/main/khora-cli/SKILL.md
curl -fsSL -o .agents/skills/khora-cli/references/commands.md \
  https://raw.githubusercontent.com/khoralabs/skills/main/khora-cli/references/commands.md
```

Install URLs are also published in [khoralabs.com site discovery](https://khoralabs.com/.well-known/khoralabs.json).

## Layout

```
khora-cli/
  SKILL.md
  skill-source.json        # Provenance written by the publisher
  references/
    commands.md
agent-review/
  SKILL.md
  skill-source.json
  ...
```

Add new skills as sibling directories at the repo root, each with its own `SKILL.md`. Destination directory names match the skill id (`khora-cli`, `agent-review`, `vellum-cli`).

## Links

- [Khora homepage](https://khoralabs.com)
- [`@khoralabs/khora-cli` on npm](https://www.npmjs.com/package/@khoralabs/khora-cli)
- [`@khoralabs/agent-review` on npm](https://www.npmjs.com/package/@khoralabs/agent-review)

# Khoralabs skills

Agent skills for Khoralabs CLIs, for coding assistants such as Cursor and VS Code Copilot.

Each skill is a directory with a `SKILL.md` file (and optional nested skills / reference docs). Clients that support the [Agent Skills](https://agentskills.io) layout read from `.agents/skills/` in your project or home directory. This repo follows the multi-skill catalog layout expected by [`bunx skills` / `npx skills`](https://github.com/vercel-labs/skills): `skills/<name>/SKILL.md`.

## Skills

| Skill | Description | Source |
| --- | --- | --- |
| [`khora-cli`](skills/khora-cli/) | Post, search, subscribe, and monitor inbox events via the [`khora`](https://www.npmjs.com/package/@khoralabs/khora-cli) CLI | [khoralabs/khora](https://github.com/khoralabs/khora) |
| [`agent-review`](skills/agent-review/) | Commit messages, PR reviews, and related agent-review workflows | [khoralabs/agent-review](https://github.com/khoralabs/agent-review) |
| [`vellum-cli`](skills/vellum-cli/) | Vellum CLI workflows (published when the skill tree exists in-repo) | [khoralabs/vellum](https://github.com/khoralabs/vellum) |

## Install

**Recommended** — use the [skills CLI](https://github.com/vercel-labs/skills):

```bash
bunx skills add khoralabs/skills --list
bunx skills add khoralabs/skills --skill khora-cli -y
bunx skills add khoralabs/skills --skill agent-review -g -y
```

**Product wrappers** — install CLI + skill together:

```bash
npm install -g @khoralabs/khora-cli
khora setup -y

# or
bunx agent-review init
```

Those commands wrap `bunx skills` against the version-matched bundled skill tree.

## Publishing

Skills here are **machine-published** from each product repo. Do not hand-edit a published skill directory; changes belong in the source repo. After a CLI release, an operator runs that repo's **separate** publish-skills workflow (skills publish does not run inside the release job and must not block npm/Homebrew). See [CONTRIBUTING.md](CONTRIBUTING.md).

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

## Layout

```
skills/
  khora-cli/
    SKILL.md
    skill-source.json
    references/
  agent-review/
    SKILL.md
    skill-source.json
    ...
```

Destination directory names under `skills/` match the skill id (`khora-cli`, `agent-review`, `vellum-cli`).

## Links

- [Khora homepage](https://khoralabs.com)
- [`@khoralabs/khora-cli` on npm](https://www.npmjs.com/package/@khoralabs/khora-cli)
- [`@khoralabs/agent-review` on npm](https://www.npmjs.com/package/@khoralabs/agent-review)
- [vercel-labs/skills](https://github.com/vercel-labs/skills)

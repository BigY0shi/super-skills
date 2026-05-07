# Super Skills Wiki

Welcome to the **Super Skills** wiki. This repository provides 11 domain-level super-skills that route user intent to 430+ specialist sub-skills.

## What this repo does

A super-skill is a single `SKILL.md` entry point that:

1. Matches user intent from the `description` frontmatter.
2. Routes the task through a suite-level routing table.
3. Loads the correct specialist instructions from references or library files.

This design reduces always-on context overhead and improves trigger accuracy versus installing many individual skills.

## How skills are used

### Core flow

1. User asks for help by intent (not by sub-skill name).
2. Claude selects the best matching suite.
3. The suite `SKILL.md` routes to the relevant sub-skill.
4. The sub-skill instructions are applied to produce output.

### Routing entrypoint

- **Master router**: `skills/dispatch/SKILL.md`

If intent is ambiguous or cross-domain, `dispatch` selects the primary suite.

## Super-skill suites

| Suite | Purpose |
|---|---|
| `dispatch` | Master router across suites |
| `marketing-suite` | Curated strategic marketing workflows |
| `all-marketing` | Large tactical marketing/SEO reference library |
| `coding-suite` | Full-stack coding and architecture tasks |
| `design-studio` | UI/UX, visual design, components, accessibility |
| `devops-suite` | Cloud, CI/CD, ops, observability, infra |
| `founders-suite` | Startup/product/business strategy and operations |
| `game-dev` | Game design and game engineering workflows |
| `productivity-suite` | Planning/execution support and task breakdown |
| `purple-team` | Security, pentesting, hardening, threat work |
| `research-lab` | Data science, ML, agents, and RAG workflows |

## Architectures used in this repo

### Pattern A: Consolidated catalog

Most suites use:

- `SKILL.md` for top-level routing
- `references/skills-catalog.md` for sub-skill instructions

### Pattern B: Library + dispatcher

`all-marketing` uses:

- Large route table in `skills/all-marketing/SKILL.md`
- Individual skill files in `skills/all-marketing/skills/**`

## Quick start

1. Install the repo as a skills plugin.
2. Trigger by intent (example: “build CI/CD”, “run SEO audit”, “design a dashboard”).
3. Let the suite route to the right sub-skill.
4. For uncertain requests, start with `dispatch`.

## Key repo references

- Main overview: `README.md`
- Contribution and validation rules: `CONTRIBUTING.md`
- Routing test prompts: `tests/routing-test-prompts.md`

## Guidance for contributors

- Keep `description` focused and keyword-rich for reliable triggering.
- Keep routing tables explicit and near the top of `SKILL.md`.
- Update routing and catalog/library content together.
- Validate `.claude-plugin/plugin.json` and `.claude-plugin/marketplace.json` before submitting.

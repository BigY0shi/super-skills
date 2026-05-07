# Super Skills

> **Eleven domain super-skills that bundle 430+ specialist skills behind a single intent-driven trigger — built for Claude Code, Cowork, and the Claude Agent SDK.**

A super-skill is a single skill that loads a whole domain of expertise on demand. One trigger ("help me write a landing page", "run a SOC2 audit", "design an embedded system") gets you the right specialist behavior without having to memorize 50 skill names. This repo packages 11 of them, demonstrates **two distinct architectures** for building one, and explains the *why* — because almost nobody is teaching this yet.

---

## Table of Contents

- [What is a super-skill?](#what-is-a-super-skill)
- [Why super-skills exist (the real problem)](#why-super-skills-exist-the-real-problem)
- [The two architectures](#the-two-architectures)
- [The 11 super-skills in this repo](#the-11-super-skills-in-this-repo)
- [Context overhead — actual measured numbers](#context-overhead--actual-measured-numbers)
- [Install](#install)
- [Usage](#usage)
- [How to build your own super-skill](#how-to-build-your-own-super-skill)
- [Why you should build one](#why-you-should-build-one)
- [FAQ](#faq)
- [Roadmap, contributing, license](#roadmap-contributing-license)

---

## What is a super-skill?

A **skill** in Claude Code / Cowork / the Claude Agent SDK is a folder containing a `SKILL.md` file. The `SKILL.md` has YAML frontmatter (`name`, `description`) followed by instructions. Claude scans skill descriptions and loads the body of any skill whose description matches the user's intent.

A **super-skill** is a skill that *bundles many related sub-skills* under a single entry point. Instead of registering 40 separate marketing skills (each with their own description Claude has to scan on every message), you register **one** skill called `marketing-suite` whose body contains a routing table to all 40. The model triggers once on intent, then reads the right sub-skill section.

Two ways to build one. Both demonstrated in this repo. More on that below.

---

## Why super-skills exist (the real problem)

Skills look free, but they aren't. Every skill installed in your environment costs you tokens *every single message* — its `description` field is in Claude's context the entire conversation so the model can decide whether to load it. Install 200 individual marketing skills and you're paying for 200 descriptions on every turn, plus you're flooding the model's discovery loop with 200 nearly-identical descriptions that all sound like "write better marketing copy." Discovery accuracy drops. Latency rises. Bills rise.

Three concrete pain points super-skills solve:

**1. The discovery tax.** Description text is always loaded. 200 descriptions × ~250 tokens = 50,000 tokens of permanent overhead on every message. One super-skill with a 250-token description that *internally* dispatches to 200 sub-skills costs 250 tokens. That's a 200× reduction.

**2. Trigger ambiguity.** When 50 skills all describe themselves as "marketing copywriting," the model picks badly. A single super-skill with one clear scope ("everything marketing") triggers reliably and then routes internally with full context.

**3. Coherent strategic POV.** Individual skills don't talk to each other. A super-skill is your *playbook* — it can enforce a workflow ("audit before optimizing", "research before writing"), share definitions across sub-skills, and present a unified voice. It's the difference between hiring 200 freelancers and hiring one strategist.

A super-skill is essentially a **router with embedded expertise**. The router is cheap and always loaded. The expertise is expensive but only loaded when needed.

---

## The two architectures

This repo demonstrates both. Pick whichever matches your library size and editing style.

### Pattern A — Consolidated Catalog

```
marketing-suite/
├── SKILL.md                    ← top-level routing + framing (~6KB / 1900 tok)
└── references/
    ├── skills-catalog.md       ← all 40 sub-skills as sections in ONE file (~50KB)
    ├── workflow.md             ← optional: cross-skill workflow guidance
    └── agents-guide.md         ← optional: agent delegation patterns
```

**How it works:** `SKILL.md` has a routing table mapping intents → catalog sections. When a sub-skill is needed, the model reads `references/skills-catalog.md` and grep-jumps to the section. The whole catalog loads at once.

**Best for:** 10–60 sub-skills. Easy to read end-to-end. Single file to maintain. Single Read call loads everything.

**Trade-off:** above ~60 sub-skills the catalog becomes unwieldy and you load way more reference content than you need on each trigger.

**Used in this repo by:** marketing-suite, coding-suite, design-studio, devops-suite, founders-suite, game-dev, productivity-suite, purple-team, research-lab.

### Pattern B — Library + Dispatcher

```
all-marketing/
├── SKILL.md                    ← routing table only (~24KB / 6100 tok)
└── skills/
    ├── seo/
    │   ├── technical/
    │   │   ├── robots.md       ← each is a self-contained mini-skill
    │   │   ├── sitemap.md      ←   with its own YAML frontmatter
    │   │   └── ...
    │   ├── on-page/
    │   ├── content/
    │   └── off-page/
    ├── paid-ads/
    │   ├── google-ads.md
    │   ├── meta-ads.md
    │   └── ...
    ├── pages/
    ├── components/
    ├── channels/
    ├── platforms/
    └── strategies/
```

**How it works:** `SKILL.md` is a giant routing table — categories → file paths. When a sub-skill is needed, the model reads exactly *that* `.md` file. Nothing else loads. Each child file has its own frontmatter and is a fully-formed skill in its own right.

**Best for:** 60+ sub-skills, deep taxonomic structure, frequent edits to individual skills, multi-author repos.

**Trade-off:** the top-level routing table itself gets big (the `all-marketing` SKILL.md is 24KB), and the model has to make a Read call for every sub-skill (latency + tokens per fetch).

**Used in this repo by:** all-marketing (165 sub-skills across 22 sub-folders).

### Which should you build?

| Sub-skills | Architecture |
|------------|--------------|
| 1–10 | Just write a normal skill. You don't need a super-skill yet. |
| 10–60 | **Consolidated catalog** — one SKILL.md, one references/skills-catalog.md. |
| 60+ | **Library + dispatcher** — one SKILL.md routing to standalone files. |
| 200+ | Library, organized into 5–10 top-level folders, each with its own routing. |

---

## The 11 super-skills in this repo

| Suite | Scope | Sub-skills | Architecture | Routes to |
|-------|-------|------------|--------------|-----------|
| **dispatch** | Master router across all suites | — | (router) | The other 10 suites |
| **marketing-suite** | Strategic marketing playbook | 40 | Catalog | Copy, SEO, CRO, ads, email, brand, lifecycle |
| **all-marketing** | Exhaustive marketing reference library | 165 | Library | Every channel, page, component, platform, SEO sub-discipline |
| **coding-suite** | Full-stack coding | 55 | Catalog | Languages, frameworks, testing, code quality, architecture, LLM dev |
| **design-studio** | UI/UX, visual art, components | 30 | Catalog | UI design, generative art, components, accessibility, design systems |
| **devops-suite** | Cloud, CI/CD, ops | 40 | Catalog | AWS/GCP/Azure, Docker, K8s, monitoring, incident response |
| **founders-suite** | Startup ops + business | 19 | Catalog | Strategy, product, SEO/growth, CRM, AI products, pricing |
| **game-dev** | Game development | 10 | Catalog | 2D/3D, Unity, design, art, audio, multiplayer, mobile, VR/AR |
| **productivity-suite** | Executive function / ADHD aide | 15 | Catalog | Task breakdown, planning, context preservation, GSD framework |
| **purple-team** | Offense + defense + RE | 39 | Catalog | Pentest, red team, blue team, malware, RE, OSINT, hardening |
| **research-lab** | Data science + AI/agent research | 23 | Catalog | DS, ML, agent architectures, RAG, prompt engineering, voice AI |

**Total:** 11 super-skills exposing 430+ specialist sub-skills. See each suite's `SKILL.md` for the full sub-skill list and routing table.

> **Overlap note.** `marketing-suite` and `all-marketing` overlap on only 6 sub-skill names — they're complementary, not redundant. `marketing-suite` is the curated strategic playbook (40 deep skills). `all-marketing` is the exhaustive tactical reference library (165 granular skills). Most users want both.

---

## Context overhead — actual measured numbers

These are **measured** sizes, not estimates. Token counts use a conservative ~4 chars/token English/markdown ratio.

| Suite | Description (always loaded) | SKILL.md body (loaded on trigger) | Full skill load (worst case) |
|-------|----------------------------:|----------------------------------:|-----------------------------:|
| dispatch | ~256 tok | 2,788 tok | 2,788 tok |
| marketing-suite | ~261 tok | 1,910 tok | 16,017 tok |
| all-marketing | ~254 tok | 6,117 tok | 226,526 tok* |
| coding-suite | ~248 tok | 2,029 tok | 15,674 tok |
| design-studio | ~244 tok | 1,892 tok | 17,028 tok |
| devops-suite | ~229 tok | 1,770 tok | 12,127 tok |
| founders-suite | ~232 tok | 1,242 tok | 9,143 tok |
| game-dev | ~252 tok | 989 tok | 6,935 tok |
| productivity-suite | ~221 tok | 1,485 tok | 8,403 tok |
| purple-team | ~250 tok | 1,968 tok | 16,184 tok |
| research-lab | ~240 tok | 1,526 tok | 10,562 tok |
| **TOTAL** | **~2,687 tok** | **23,716 tok** | **~341,000 tok** |

*\* `all-marketing`'s "full load" is theoretical — you'd never load all 165 sub-skill files at once. Realistic per-task load is one or two specific `.md` files (typically 500–2,500 tokens each).*

### How to read this

- **Description** = the cost of *having the skill installed*. Paid every message. Total for all 11 suites: ~2,700 tokens. Compare that to installing 430 individual skills: ~108,000 tokens. **40× cheaper at idle.**
- **SKILL.md body** = the cost of *triggering the skill*. Paid only when the suite is invoked. The router itself is small (~1,000–3,000 tokens) — that's what runs your routing logic.
- **Full skill load** = the cost of using the *whole* suite end-to-end (every sub-skill's content). Almost no real task needs this. Realistic per-task cost is the body + 1–3 sub-skill sections, usually 3,000–8,000 tokens.

### The big takeaway

If you would otherwise install 50+ individual skills for one domain, a super-skill saves you a huge amount of always-on context, *and* improves trigger accuracy because the model has one clean scope to match against instead of 50 confusable ones.

---

## Install

### Option 1 — Claude Code plugin (one-shot install)

```bash
# Clone the repo
git clone https://github.com/REPLACE_WITH_YOUR_USERNAME/super-skills.git ~/.claude/plugins/super-skills
```

Then restart Claude Code. All 11 super-skills will appear in your skill list.

### Option 2 — Cowork / Claude Desktop

Drop the `super-skills/` folder into your local agent skills directory:

```
~/AppData/Roaming/Claude/local-agent-mode-sessions/skills-plugin/<your-id>/skills/   (Windows)
~/Library/Application Support/Claude/.../skills/                                      (macOS)
~/.config/Claude/.../skills/                                                          (Linux)
```

The 11 sub-folders inside `skills/` will each register as a skill on next session.

### Option 3 — Marketplace (when published)

```
/plugin add super-skills
```

(Marketplace publishing requires you to push this repo to GitHub and update the `repo` field in `.claude-plugin/marketplace.json`.)

### Option 4 — Manual `.plugin` archive

The release artifact `super-skills.plugin` is a zip you can install through any tool that accepts `.plugin` archives.

---

## Usage

You don't trigger super-skills by name. **Trigger by intent.** Examples:

| You say | Suite that activates |
|---------|----------------------|
| "Write me a landing page for a B2B SaaS" | marketing-suite or all-marketing |
| "Audit my robots.txt and sitemap" | all-marketing (routes to seo/technical/) |
| "Design a Postgres schema with row-level security" | coding-suite |
| "Build a CI/CD pipeline with staged rollouts" | devops-suite |
| "Help me make a generative art piece in p5.js" | design-studio |
| "Run a pentest on this authorized scope" | purple-team |
| "Set up a RAG pipeline with reranking" | research-lab |
| "I'm overwhelmed, break this down for me" | productivity-suite |
| "Plan a game's core loop and progression" | game-dev |
| "Should I price per-seat or per-usage?" | founders-suite |
| "Not sure which one I need" | dispatch (master router) |

The model picks the right suite from your intent, reads the routing table, then loads the specific sub-skill. You never have to know the sub-skill name.

---

## How to build your own super-skill

### Minimum viable structure

```
your-skill/
└── SKILL.md
```

### `SKILL.md` frontmatter (required)

```markdown
---
name: your-skill-name
description: |
  One-paragraph description of EVERY trigger this skill should match.
  Include keywords aggressively — the model only sees this paragraph
  when deciding whether to invoke. Be specific about scope and
  list sub-areas explicitly.
metadata:
  version: 1.0.0
---

# Your Skill

Body of the skill — instructions, frameworks, examples.
```

**Description rules that matter:**

- Keep it under ~300 tokens (~1200 chars). Larger descriptions inflate idle cost across every conversation.
- Front-load with concrete intent verbs ("Use when the user wants to...").
- List trigger keywords explicitly — don't make the model infer.
- Name the sub-areas covered. The model uses this for trigger confidence.

### Adding the catalog (Pattern A)

```
your-skill/
├── SKILL.md                 ← routing table + framing
└── references/
    └── skills-catalog.md    ← all sub-skills as ## headed sections
```

Inside `SKILL.md`:

```markdown
## Quick Routing Table

| Task | Sub-skill |
|------|-----------|
| Write copy for a landing page | copywriting |
| Plan content calendar | content-strategy |
| Run an SEO audit | seo-audit |

When triggered, read the sub-skill section in
`references/skills-catalog.md`.
```

Inside `references/skills-catalog.md`:

```markdown
# Skill Catalog

## copywriting
**Goal**: Write marketing copy that converts.
[full instructions for this sub-skill]

## content-strategy
**Goal**: Plan editorial calendar.
[full instructions for this sub-skill]
```

### Adding the library (Pattern B)

```
your-skill/
├── SKILL.md                 ← routing table mapping triggers → file paths
└── skills/
    ├── category-1/
    │   ├── sub-skill-a.md   ← each has its own YAML frontmatter
    │   ├── sub-skill-b.md
    │   └── sub-skill-c.md
    └── category-2/
        └── ...
```

Inside `SKILL.md`:

```markdown
| Sub-skill | Path | Triggers |
|-----------|------|----------|
| robots-txt | `skills/seo/technical/robots.md` | robots.txt, AI crawlers, disallow |
| canonical-tag | `skills/seo/technical/canonical.md` | canonical, duplicate content |

When triggered, read the file at the matching path.
```

### Sizing rules of thumb

| Element | Target size | Why |
|---------|-------------|-----|
| Description | < 300 tokens | Paid every message; the model only needs enough to route |
| SKILL.md body | < 6,000 tokens | Loaded on every trigger; routing logic + framing only |
| Sub-skill section / file | 500–2,500 tokens | Small enough to fit a few in context with room for the actual task |
| Full reference catalog | < 60,000 tokens | Above this, switch from Pattern A to Pattern B |

### Ten things that separate a good super-skill from a bad one

1. **Description front-loads concrete verbs and keywords.** Not "marketing helper" — "Use when the user wants to write copy, audit SEO, plan ads, optimize CRO, build a launch sequence, or any marketing task."
2. **Routing table is the first thing in SKILL.md.** Not the last.
3. **Sub-skills have crisp scope boundaries.** No two sub-skills should overlap by more than 20%.
4. **Each sub-skill is self-contained.** Don't make sub-skill B depend on sub-skill A having been read first.
5. **Workflow guidance is separate from sub-skills.** Put cross-skill orchestration in `references/workflow.md` so it doesn't bloat individual sections.
6. **No "decorative" content.** Cut everything that doesn't change Claude's output.
7. **Concrete examples, not abstractions.** Show the input → output.
8. **Anti-patterns explicit.** "Don't do X. Don't say Y. Avoid Z." Negative constraints work.
9. **Versioned.** Bump `version` in frontmatter when you make breaking changes.
10. **Tested by triggering on real prompts.** Run 10 sample user messages through it. If 9/10 don't trigger correctly, your description is wrong.

---

## Why you should build one

The honest answer: most people shouldn't. If you're using Claude for ad-hoc tasks, individual skills or no skills at all is fine.

You should build a super-skill if **any** of the following are true:

- **You're an expert in a domain** and you keep re-explaining the same playbook to Claude. Capture it once.
- **You have 10+ recurring task types in one area** (marketing, customer support, devops, finance, whatever). Each task type is a sub-skill.
- **Your team is using Claude inconsistently.** A shared super-skill is a force-function for consistent execution.
- **You're building an agent product** and need a coherent strategic POV across a large surface of related tasks.
- **You're publishing skills publicly** and want them to be discoverable, browsable, and trigger reliably without conflicting with other people's skills.

You should *not* build one if:

- You have fewer than 10 related skills.
- The "skills" are really just prompts you'd reuse twice.
- You haven't actually executed the work yourself enough to know what the playbook should be.

A super-skill is opinionated documentation that *runs*. Build one when you've earned the opinions.

---

## FAQ

**Q: Is "super-skill" an official Anthropic term?**
No. It's a community pattern. Anthropic's docs call them "skills with sub-skills" or just "skills with references." This repo and others are converging on "super-skill" as the shorthand for a skill that bundles many.

**Q: Will the model actually follow my routing table?**
Yes, reliably, if your routing table is the first content after the frontmatter and you list explicit triggers. Claude reads the SKILL.md top to bottom and treats early content as priority instructions.

**Q: What if two of my super-skills could match the same intent?**
Make their descriptions explicitly disjoint. Add "Not for X — see other-skill" lines. Disambiguation belongs in the description, not in the body.

**Q: Can sub-skills load other sub-skills?**
Yes. A sub-skill can instruct the model to read another sub-skill if needed. Avoid deep chains (>2 hops) — the model can lose track.

**Q: How do I version this in a team setting?**
Use the `metadata.version` field in `SKILL.md` and tag releases in git. Major version = breaking changes to routing or sub-skill names. Minor = additions. Patch = content fixes.

**Q: Why is `all-marketing`'s SKILL.md so much bigger than the others?**
Because Pattern B (library) puts the *entire routing table* in SKILL.md — and routing 165 sub-skills takes more characters than routing 30. The trade-off: bigger SKILL.md, but you only load one tiny sub-skill file at a time after that, instead of a 50KB catalog.

**Q: Does this work with Claude Code, Cowork, and the Claude Agent SDK?**
Yes — they all use the same skill format (folder + SKILL.md + frontmatter). Drop-in compatible with any tool that respects the spec.

**Q: How do I see what's actually loading into context?**
In Claude Code, `--verbose` mode shows skill loading. In Cowork, check the session transcript. In the SDK, you control the loading directly.

---

## Roadmap, contributing, license

### Roadmap

- [ ] Per-suite test prompts (10 sample triggers per suite, validating routing accuracy)
- [ ] CI to validate frontmatter and routing-table consistency
- [ ] A `super-skill-builder` super-skill (meta) that helps you scaffold new ones
- [ ] Localization of top-level routing tables
- [ ] Compressed/expanded variants per suite (light vs heavy context budgets)

### Contributing

PRs welcome. Please:

1. Fork.
2. If adding a new sub-skill to an existing suite, update the catalog/routing table in the same PR.
3. Keep descriptions under 300 tokens.
4. Include 3 sample trigger prompts in your PR description.

### License

MIT. See [LICENSE](LICENSE).

### Credits

Architecture patterns and curated sub-skill content adapted, expanded, and reorganized from the open-source Claude skills ecosystem. Specific influences include the Anthropic skills repo, the `addy-agent-skills` plugin, the `marketingskills` library, and the Claude Code plugins ecosystem.

---

> **Built because the tooling exists but the playbook didn't.** If this saves you a week of figuring out how skills actually work, pay it forward — fork it, build your own, share what you learn.

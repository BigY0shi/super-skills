# Contributing to Super Skills

Thanks for considering a contribution. This repo is built to be forked, extended, and made better. Below are the rules of the road.

---

## Table of Contents

- [What contributions are welcome](#what-contributions-are-welcome)
- [Quick start](#quick-start)
- [Adding a new sub-skill](#adding-a-new-sub-skill)
- [Adding a new super-skill (suite)](#adding-a-new-super-skill-suite)
- [Description writing standards](#description-writing-standards)
- [Routing-table standards](#routing-table-standards)
- [Testing your changes](#testing-your-changes)
- [Style guide](#style-guide)
- [PR process](#pr-process)
- [Code of conduct](#code-of-conduct)

---

## What contributions are welcome

**Yes, please:**

- New sub-skills inside an existing suite (with routing-table updates)
- New super-skills (with full structure as described below)
- Description improvements that improve trigger accuracy
- Bug fixes in existing sub-skills (incorrect frameworks, outdated APIs, broken links)
- New test prompts in `tests/routing-test-prompts.md`
- Translations of routing tables and descriptions
- Documentation improvements to `README.md` or this file

**No, thanks:**

- Cosmetic-only changes that don't change behavior
- Suites with fewer than 10 sub-skills (use a normal skill instead)
- Sub-skills that duplicate existing sub-skills with no clear scope difference
- Content with unverified facts, fabricated citations, or copyrighted material reproduced at length

---

## Quick start

```bash
# Fork and clone
git clone https://github.com/YOUR-USERNAME/super-skills.git
cd super-skills

# Create a feature branch
git checkout -b feat/add-my-thing

# Make your changes...

# Validate manifests
python3 -c "import json; json.load(open('.claude-plugin/plugin.json'))"
python3 -c "import json; json.load(open('.claude-plugin/marketplace.json'))"

# Bump version in .claude-plugin/plugin.json (semver: major.minor.patch)
# - patch: content fixes, no routing changes
# - minor: new sub-skills, new suites
# - major: breaking changes to routing or suite names

# Commit and push
git add -A
git commit -m "feat(suite-name): short summary"
git push origin feat/add-my-thing

# Open a PR
```

---

## Adding a new sub-skill

### Pattern A — Catalog suite (e.g. `marketing-suite`, `coding-suite`)

1. Open `skills/<suite>/references/skills-catalog.md`.
2. Add a `## new-sub-skill-name` section in the appropriate category.
3. Update the table of contents at the top of the same file.
4. Open `skills/<suite>/SKILL.md` and add a row to the routing table mapping intent → sub-skill name.
5. Add at least 3 trigger prompts to `tests/routing-test-prompts.md` under that suite's table.
6. Bump `version` in `skills/<suite>/SKILL.md` frontmatter (minor bump).

**Sub-skill section template:**

```markdown
## sub-skill-name

**Goal**: One sentence on what success looks like.

### When to Use
- Trigger 1
- Trigger 2

### Approach
[Step-by-step framework or workflow]

### Output Format
[What to produce]

### Anti-patterns
- Don't do X
- Avoid Y
```

Aim for 500–2,500 tokens per sub-skill section. If it's bigger, consider splitting.

### Pattern B — Library suite (e.g. `all-marketing`)

1. Create a new file `skills/<suite>/skills/<category>/<sub-skill-name>.md`.
2. Add YAML frontmatter:
   ```yaml
   ---
   name: <sub-skill-name>
   description: |
     Use when the user wants to ... (be specific about triggers and keywords).
   metadata:
     version: 1.0.0
   ---
   ```
3. Write the sub-skill body (same template as Pattern A).
4. Open `skills/<suite>/SKILL.md` and add a row to the routing table mapping the relative file path.
5. Add 3 trigger prompts to `tests/routing-test-prompts.md`.
6. Bump `version` in `skills/<suite>/SKILL.md` frontmatter.

---

## Adding a new super-skill (suite)

Only do this if you have **at least 10 related sub-skills** that don't fit any existing suite. Otherwise, see if it belongs in `coding-suite`, `marketing-suite`, etc.

1. Create `skills/<suite-name>/SKILL.md` with the frontmatter and structure described in the README's "How to build your own super-skill" section.
2. Pick an architecture:
   - **Catalog** if you have 10–60 sub-skills.
   - **Library** if you have 60+.
3. Write the routing table FIRST. The model uses it to dispatch — make it crisp.
4. Add the suite to:
   - The 11-row table in `README.md` ("The 11 super-skills in this repo")
   - The `tests/routing-test-prompts.md` file with 10 test prompts
   - The `tags` and `description` arrays in `.claude-plugin/plugin.json`
5. Update the `dispatch` super-skill's routing table to include your new suite.
6. Bump the *plugin* version (`.claude-plugin/plugin.json`) — minor bump for a new suite.

---

## Description writing standards

The `description` field is the **single most important** thing about a skill. The model uses it to decide whether to load the skill — get it wrong and the skill never triggers, no matter how good the body is.

**Rules:**

1. **Length**: 250–300 tokens (~1000–1200 chars). Above that = idle context tax. Below that = poor trigger coverage.
2. **First sentence**: Start with concrete intent verbs. "Use when the user wants to ..." or "Triggers on ..." or similar.
3. **Keyword density**: Include exact phrases users would say. "robots.txt", "Core Web Vitals", "schema markup" — not abstractions like "search engine optimization concepts."
4. **Sub-area enumeration**: List the sub-skills or sub-areas covered explicitly. The model uses this to gauge trigger confidence.
5. **Negative scoping** (when needed): "Not for X — see other-skill" disambiguates against neighboring skills.
6. **No fluff**: Cut adjectives like "comprehensive", "powerful", "robust." They don't help routing.

**Bad description:**
> Comprehensive marketing assistance powered by AI for all your marketing needs.

**Good description:**
> Use when the user wants to write copy, audit SEO, plan ads, optimize CRO, build an email sequence, design a launch, or any marketing task. Covers: copywriting, page-cro, signup-flow-cro, email-sequence, ad-creative, paid-ads, seo-audit, schema-markup, brand-building, churn-prevention, pricing-strategy, sales-enablement. Not for tactical channel-specific reference work — see all-marketing.

---

## Routing-table standards

The routing table inside `SKILL.md` is what actually dispatches to sub-skills. Standards:

1. **Place it FIRST** — immediately after the frontmatter and a one-paragraph framing. Not at the bottom.
2. **Use a markdown table** with columns: `Task`, `Sub-skill`, optionally `Triggers`. Models parse tables reliably.
3. **One row = one sub-skill**. Don't combine.
4. **Triggers should be the user's words**, not yours. "robots.txt" not "robots exclusion protocol."
5. **Include a fallback row** at the bottom: `| Anything else marketing-adjacent | (ask for clarification) |`.
6. **Keep entries short**. The whole table should fit in a screenful.

---

## Testing your changes

Before opening a PR:

1. **Validate JSON manifests**:
   ```bash
   python3 -c "import json; json.load(open('.claude-plugin/plugin.json'))"
   python3 -c "import json; json.load(open('.claude-plugin/marketplace.json'))"
   ```

2. **Validate frontmatter** in every modified `SKILL.md`:
   ```bash
   # Each SKILL.md must have name and description in YAML frontmatter
   grep -L '^name:' skills/*/SKILL.md
   grep -L '^description:' skills/*/SKILL.md
   ```

3. **Trigger-test in a real session**: Run at least 3 prompts from your suite's test list in a real Claude Code / Cowork session with the plugin installed. Verify the suite triggers and the right sub-skill loads.

4. **Document failures**: If a trigger prompt fails, fix the description before submitting the PR. Don't submit failing tests.

---

## Style guide

**Markdown:**

- Use sentence case for headings ("How to build your own", not "How To Build Your Own").
- Use `## H2` for sub-skill names in catalogs (consistent with anchor links).
- Use code blocks for paths, commands, and JSON. Use inline code for inline file names.
- Tables for routing decisions. Bullets for non-decision lists. Prose for everything else.

**Voice:**

- Imperative for instructions ("Run the test", not "You should run the test").
- Specific numbers over adjectives. "≤ 300 tokens" not "fairly short."
- Anti-patterns as explicit do-nots. The model follows negative constraints reliably.

**Don't:**

- Don't use emojis in skill files (they bloat tokens and add no signal).
- Don't include time estimates or vague timeline language.
- Don't reproduce copyrighted text. Summarize in original wording.
- Don't include external links that might rot. Inline the relevant content.

---

## PR process

1. Open a PR from your fork.
2. Title format: `feat(suite-name): summary` or `fix(suite-name): summary` or `docs: summary`.
3. PR description must include:
   - **What** changed (one sentence).
   - **Why** (motivation).
   - **3 sample trigger prompts** the changed sub-skill / suite should match (paste them).
   - **Test results** — confirm you ran them in a real session and observed correct triggering.
4. Bump versions in any modified `SKILL.md` and in `.claude-plugin/plugin.json` if needed.
5. Review usually within a week. Be patient and responsive on review comments.

---

## Code of conduct

Be decent. Disagree on substance, not on people. Constructive critique welcome; bad-faith argument and personal attacks are not. Maintainers may close PRs or block contributors who can't keep it civil.

---

Thanks again. This stuff gets better when more people sharpen it.

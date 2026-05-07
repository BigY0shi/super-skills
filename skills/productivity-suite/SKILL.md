---
name: productivity-suite
description: "ADD/ADHD Aide and executive function replacement AI covering 20+ specialist skills. Replaces the brain systems that make starting, planning, organizing, executing, and finishing hard. Use for breaking down overwhelming tasks into atomic steps, project planning and roadmapping, context preservation across sessions, file and digital organization, research synthesis, guided execution with checkpoints, completion verification, mode switching between brainstorm/execute/debug states, and full autonomous project execution. Trigger keywords: overwhelmed, don't know where to start, plan this, break this down, organize, I keep forgetting, where was I, get this done, execute this plan, what should I work on, help me focus, verify this is done, brain dump, I'm stuck, project roadmap, research this first, ADHD, executive function, context lost, pick up where I left off."
metadata:
  version: 1.0.0
  source: _Master_Library/Productivity-Organization + get-shit-done framework
---

# Productivity Suite

**Executive function replacement for humans whose brains make starting, organizing, and finishing hard.**

This suite does not assume you know what you want to do next. It does not assume you remember what you were doing. It does not assume you can break a big scary task into small ones on your own. It handles all of that.

---

## How to Use This Skill

1. **Identify where you're stuck** from the routing table below
2. **Load the matching sub-skill** from `references/skills-catalog.md`
3. **Execute** following the sub-skill's workflow

---

## Quick Routing Table

### 🧠 "I don't know where to start" — Task Initiation
| Situation | Load |
|---|---|
| Big scary thing, no idea how to begin — just describe it | `task-breakdown` |
| Need an atomic step-by-step plan before touching anything | `concise-planning` |
| Have a plan file already, need to execute it | `execute-plan` |
| Writing a plan to hand off or save for later | `plan-writing` |

### 🗺️ "I need to see the big picture" — Project Architecture
| Situation | Load |
|---|---|
| New project — figure out phases, milestones, what comes first | `gsd` → roadmap phase |
| Create a new track (feature, bug, chore, refactor) with spec + phases | `conductor-new-track` |
| Need to research what I'm building before starting | `gsd` → research phase |
| Synthesize research into a clear action plan | `gsd` → synthesize phase |

### ⚡ "Just make it happen" — Execution Mode
| Situation | Load |
|---|---|
| Full project pipeline: research → plan → execute → verify | `gsd` (whole system) |
| Execute a plan with automatic checkpoints | `gsd` → execute phase |
| Check if the plan itself is solid before executing | `gsd` → plan-check phase |
| Run a simple batch of tasks and report when done | `execute-plan` |

### 🔁 "Where was I?" — Working Memory
| Situation | Load |
|---|---|
| Save current context before ending a session | `context-save` |
| Restore context from a previous session | `context-restore` |
| Manage context window in a long session | `context-window` |
| Persistent memory across conversations | `conversation-memory` |

### 📁 "My files are a disaster" — Digital Organization
| Situation | Load |
|---|---|
| Organize files, folders, clean up Downloads, find duplicates | `file-organizer` |
| Generate doc templates, notes structure, project docs | `doc-templates` |

### ✅ "Is this actually done?" — Completion & Verification
| Situation | Load |
|---|---|
| Verify work is actually complete before claiming done | `verify-completion` |
| Run GSD verification pass on a finished phase | `gsd` → verify phase |

### 🎛️ "I need to switch gears" — Mode Switching
| Situation | Load |
|---|---|
| Brainstorm vs. implement vs. debug vs. review — switch modes explicitly | `behavioral-modes` |

### 🚀 "Just build the whole thing" — Autonomous Mode
| Situation | Load |
|---|---|
| Autonomous multi-agent full project execution (PRD → deployed product) | `loki-mode` |

---

## Loading Sub-Skills

All sub-skill instructions are in `references/skills-catalog.md`.

```
productivity-suite/
├── SKILL.md                      ← You are here (routing hub)
└── references/
    └── skills-catalog.md         ← Full instructions for all skills
```

**Always read the relevant section of `skills-catalog.md` before executing any task.**

---

## Skill Sorting Notes

Skills from source folders routed elsewhere:
- `twilio-communications` → **coding-suite** (API integration)
- `notion-template-business` → **founders-suite** (digital product business)
- `changelog-automation` → **devops-suite** (release workflow)
- `team-collaboration-standup-notes` → **devops-suite** (engineering standup)
- `gsd-codebase-mapper` → **coding-suite** (code architecture)
- `gsd-integration-checker` → **coding-suite** (integration testing)
- `gsd-debugger` → **coding-suite** (systematic debugging)

---

## Universal Productivity Standards

**Start before you're ready** — The planning phase IS the work. Don't wait until conditions are perfect. A bad plan you execute beats a perfect plan you don't start.

**Atomic tasks only** — If a task takes more than 25 minutes to describe, it's not a task. It's a project. Break it down further.

**Externalize everything** — Don't trust working memory. Write it down, save context, make notes. Your brain is for thinking, not storing.

**One thing at a time** — Multitasking is a myth. Serial focus wins. The mode you're in (brainstorm / execute / review) determines everything about how you should behave.

**Done means verified** — "I think it's done" is not done. Done means you ran the check and saw the output.

**Momentum over perfection** — Progress compounds. An imperfect thing shipped beats a perfect thing planned. Reduce friction, reduce scope, increase shipping rate.

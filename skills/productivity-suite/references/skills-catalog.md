# Productivity Suite — Skills Catalog

Full instructions for every sub-skill. Read only the section relevant to the current task.

> **The lens**: Every skill here replaces or augments an executive function — the brain systems responsible for starting, planning, organizing, executing, and finishing. When those systems are unreliable, this suite fills the gap.

---

## Table of Contents

### Task Initiation
1. [task-breakdown](#task-breakdown)
2. [concise-planning](#concise-planning)
3. [execute-plan](#execute-plan)
4. [plan-writing](#plan-writing)

### GSD — Get Shit Done (Unified Framework)
5. [gsd](#gsd) ← The whole system; agents, templates, workflows, and references work together
6. [conductor-new-track](#conductor-new-track)

### Working Memory
7. [context-save](#context-save)
8. [context-restore](#context-restore)
9. [context-window](#context-window)
10. [conversation-memory](#conversation-memory)

### Digital Organization
11. [file-organizer](#file-organizer)
12. [doc-templates](#doc-templates)

### Completion & Verification
13. [verify-completion](#verify-completion)

### Mode Switching
14. [behavioral-modes](#behavioral-modes)

### Autonomous Mode
15. [loki-mode](#loki-mode)

---

## task-breakdown

### Executive Function Replaced
**Task initiation + working memory** — Turns a vague overwhelming thing into a numbered list of things a human can actually start.

### When to Load
User says: "I don't know where to start", "this is overwhelming", "help me break this down", "I'm stuck", "brain dump."

### Workflow
1. **Ask one question**: "Describe the thing in 1–3 sentences. Don't worry about being precise."
2. **Identify the end state**: What does "done" look like? (If they don't know, help them define it first.)
3. **Break into phases**: 2–4 phases maximum. Name them verb-first ("Research X", "Build Y", "Ship Z").
4. **Break each phase into tasks**: Each task must be doable in under 25 minutes. Verb-first ("Write the intro", "Run the test", "Send the email").
5. **Identify the ONE task to start right now**: Not the "best" task — the one with the lowest activation energy. The one that is hard to say no to.
6. **Output format**:

```markdown
## [Project Name]

**Done looks like:** [1 sentence]

### Phase 1: [Name]
- [ ] [Task — verb first, under 25 min]
- [ ] [Task]
- [ ] [Task]

### Phase 2: [Name]
...

**Start here RIGHT NOW:** [Single task from Phase 1]
```

### ADHD Notes
- Never give more than 3–4 tasks per phase visible at once — the list length itself becomes paralysis
- The "start here" task is more important than the plan — it creates momentum
- Time estimates reduce anxiety. Add them: "(~10 min)", "(~5 min)"
- If they still can't start after breakdown, try smaller: "What's the first 2-minute action?"

---

## concise-planning

### Executive Function Replaced
**Planning + prioritization** — Converts a request into a single, actionable, atomic checklist. No ambiguity, no interpretation required.

### When to Load
User needs a plan for a specific coding task or project they're about to execute.

### Workflow

**Step 1: Scan Context**
- Read README.md, relevant docs, existing code
- Identify constraints (language, frameworks, tests, existing patterns)

**Step 2: Minimal Clarification**
- Ask AT MOST 1–2 questions — only if truly blocking
- Make reasonable assumptions for everything else (state them explicitly)

**Step 3: Generate Plan**

```markdown
# Plan: [Task Name]

[1–3 sentences: what we're doing and why this approach]

## Scope
**In:** [bullet list of what's included]
**Out:** [bullet list of what's explicitly excluded]

## Tasks
- [ ] [Verb-first atomic task] (~Xmin)
- [ ] [Verb-first atomic task] (~Xmin)
- [ ] [Verb-first atomic task] (~Xmin)
...

## Validation
- [ ] [How to verify this worked]
```

### Rules
- 6–10 tasks maximum in the task list
- Each task takes 2–25 minutes
- Each task has one clear outcome
- Last task is always verification
- Assumptions are stated explicitly, not buried

---

## execute-plan

### Executive Function Replaced
**Follow-through + working memory** — Executes a pre-written plan in batches with checkpoints. Prevents the "I wrote a plan but never did it" failure mode.

### When to Load
User has an existing plan file and wants to execute it. Or has just finished a planning session and says "okay, now do it."

### Core Principle
Batch execution with checkpoints. Claude automates everything automatable. Checkpoints are for human judgment only — visual checks, UX evaluation, "does this feel right?", secrets/API keys.

### Workflow

**Step 1: Load and Review Plan**
1. Read the plan file (or reconstruct from conversation)
2. Review critically — identify any ambiguities or concerns
3. If concerns: raise them BEFORE starting, not mid-execution
4. If no concerns: create a todo list and proceed

**Step 2: Execute Batch (default: first 3 tasks)**
For each task:
- Mark in_progress
- Execute exactly as specified
- Run any verification listed in the task
- Mark completed

**Step 3: Report**
After each batch:
```
Completed:
  ✓ [Task 1] — [verification result]
  ✓ [Task 2] — [verification result]
  ✓ [Task 3] — [verification result]

Ready for feedback. Type "continue" to proceed to next batch, or describe any issues.
```

**Step 4: Continue or Fix**
- On "continue": next batch
- On issue description: fix, verify, then report again

### Checkpoint Types
| Type | When | Human Does |
|---|---|---|
| `human-verify` | Claude built something UI/UX-related | Visual check, UX evaluation |
| `human-decide` | Two valid paths exist | Choose direction |
| `human-secret` | API key or credential needed | Provide the secret |

### Rules
- If Claude can run it, Claude runs it. Never ask user to execute CLI commands.
- Claude sets up the verification environment (starts servers, seeds databases)
- User only does what requires human judgment

---

## plan-writing

### Executive Function Replaced
**Planning + organization** — Writes a structured, dependency-aware plan with verification criteria. For saving, handing off, or picking up later.

### When to Load
User needs a plan written to a file — for documentation, handing off, or future execution.

### Task Breakdown Principles

**Small, focused tasks**
- Each task: 2–25 minutes
- One clear outcome per task
- Independently verifiable

**Clear verification**
- How do you know it's done? (specific command output, visual state, file exists)
- What can you check or test?

**Logical ordering**
- Dependencies identified and stated
- Parallel work flagged where possible
- Critical path highlighted
- Verification is always the LAST phase

### Plan Template
```markdown
# Plan: [Name]
**Date:** [date]
**Goal:** [1 sentence — what done looks like]

## Assumptions
- [Assumption 1]
- [Assumption 2]

## Phases

### Phase 1: [Name]
**Goal:** [What this phase achieves]
**Depends on:** [Nothing / Phase X]

Tasks:
- [ ] [Verb-first task] — verify: [how to confirm done]
- [ ] [Verb-first task] — verify: [how to confirm done]

### Phase 2: [Name]
...

### Final: Verification
- [ ] [End-to-end check that the whole thing works]
- [ ] [Edge case or failure mode check]
```

---

## gsd

### Executive Function Replaced
**All of them** — GSD is a complete project execution system: research → roadmap → plan → execute → verify. Each phase has its own agent, templates, and workflows that comingle as a unified pipeline. Do not split or invoke agents individually.

### What GSD Is
A lightweight, powerful spec-driven execution system for solo developers and builders. Solves **context rot** — the quality degradation that happens as the context window fills over a long project. Behind the scenes: context engineering, XML prompt formatting, subagent orchestration, state management. What you see: a few phases that just work.

**Core philosophy**: Plans are prompts, not documents. The plan file IS the execution instruction. Claude automates everything automatable. Checkpoints are for human judgment only.

### The Full GSD Pipeline

```
DISCOVERY → RESEARCH → ROADMAP → PLAN PHASE → PLAN CHECK → EXECUTE → VERIFY → NEXT PHASE
```

**State files** (the connective tissue that holds it all together):
```
.planning/
├── STATE.md          ← Current position, accumulated decisions, blockers
├── PLAN.md           ← Active phase plan (written by planner, read by executor)
├── SUMMARY.md        ← Post-execution summary (written by executor, read by verifier)
└── ROADMAP.md        ← Big picture phases and milestones
```

### GSD Agents (work as a team — do not invoke in isolation)
| Agent | Role | Spawned By |
|---|---|---|
| `gsd-roadmapper` | Turns goal into phased milestone plan | `/gsd` discovery phase |
| `gsd-project-researcher` | Pre-project research, library landscape, prior art | `/gsd` before Phase 1 |
| `gsd-phase-researcher` | Phase-specific research (APIs, patterns needed) | `/gsd:plan-phase` |
| `gsd-research-synthesizer` | Synthesizes research into actionable recommendation | After research phase |
| `gsd-planner` | Writes PLAN.md for a phase with task breakdown + deps | `/gsd:plan-phase` |
| `gsd-plan-checker` | Reviews PLAN.md quality before execution | After planning |
| `gsd-executor` | Executes PLAN.md atomically with commits and STATE.md | `/gsd:execute-phase` |
| `gsd-verifier` | Runs verification pass, writes SUMMARY.md | `/gsd:verify-phase` |

### GSD Templates (referenced by agents — do not edit arbitrarily)
```
get-shit-done/get-shit-done/templates/
├── milestone.md         ← Phase milestone structure
├── context.md           ← Context snapshot format
├── roadmap.md           ← Roadmap document format
├── state.md             ← STATE.md format
├── discovery.md         ← Discovery phase output
├── requirements.md      ← Requirements document
├── research.md          ← Research brief format
└── verification-report.md ← Verifier output format
```

### GSD Workflows (the phase orchestrators)
```
get-shit-done/get-shit-done/workflows/
├── discovery-phase.md      ← Initial discovery + roadmap generation
├── discuss-phase.md        ← Clarification before planning
├── execute-phase.md        ← Execute a plan phase
├── execute-plan.md         ← Execute a full plan end-to-end
├── verify-phase.md         ← Verify a completed phase
├── verify-work.md          ← Verify specific work
├── complete-milestone.md   ← Mark a milestone done
├── map-codebase.md         ← Understand an existing codebase
├── resume-project.md       ← Resume from STATE.md
├── transition.md           ← Transition between phases
├── diagnose-issues.md      ← Debug and diagnose
└── list-phase-assumptions.md ← Surface assumptions before executing
```

### How to Invoke GSD

**Starting a new project:**
```
/gsd          → runs discovery-phase.md → spawns roadmapper → generates ROADMAP.md
```

**Planning a phase:**
```
/gsd:plan-phase [phase-name]   → spawns phase-researcher → planner → plan-checker
                               → outputs PLAN.md
```

**Executing a phase:**
```
/gsd:execute-phase             → reads PLAN.md → spawns executor
                               → atomic commits per task → outputs SUMMARY.md
```

**Verifying a phase:**
```
/gsd:verify-phase              → reads PLAN.md + SUMMARY.md → spawns verifier
                               → outputs verification-report.md
                               → PASS: proceed | FAIL: gap-closure plan
```

**Resuming a stalled project:**
```
/gsd:resume                    → reads STATE.md → reconstructs context → continues
```

### STATE.md — The Memory System
Every executor turn starts by reading STATE.md and ends by updating it. This is the mechanism that prevents context rot across hundreds of agent actions.

```markdown
# Project State

## Current Position
Phase: [N] | Plan: [name] | Status: [in-progress/blocked/complete]

## Accumulated Decisions
- [Decision + rationale — never relitigated unless explicitly reopened]

## Blockers / Watch-fors
- [Anything that could derail current phase]

## Brief
[3–5 sentences: what is this project and where are we]
```

### Execution Principles
- **Claude runs everything it can run** — Never ask user to execute CLI commands
- **Atomic commits** — One commit per task: `task(phase): description`
- **Deviations surface immediately** — Minor fixes in-flight; significant changes pause for human
- **Checkpoints for human judgment only** — Visual checks, UX eval, secrets, "does this feel right?"

### RARV Cycle (every agent action)
**R**EASON → **A**CT → **R**EFLECT → **V**ERIFY — then move to next action

---

## conductor-new-track

### Executive Function Replaced
**Project initiation** — Creates a fully specified track (feature, bug, chore, or refactor) with spec and phased plan. Prevents the paralysis of staring at a blank slate.

### When to Load
Starting a new unit of work. Track = a single scoped piece of work with a spec and execution plan.

### Track Types
- **Feature** — New functionality
- **Bug** — Fix for existing issue
- **Chore** — Maintenance, dependencies, config
- **Refactor** — Code improvement without behavior change

### Workflow

**Pre-flight**: Verify Conductor is initialized (check `conductor/product.md`, `conductor/tech-stack.md`, `conductor/workflow.md`). If missing, prompt setup first.

**Spec Gathering** (interactive):
1. What is this track trying to achieve? (1–2 sentences)
2. What are the acceptance criteria? (how do we know it's done?)
3. What's explicitly out of scope?
4. Any known technical constraints or dependencies?
5. Priority: Must-have vs. nice-to-have

**Output: Track Spec**
```markdown
# Track: [Name]
**Type:** [Feature / Bug / Chore / Refactor]
**Status:** Planning

## Goal
[1–2 sentences]

## Acceptance Criteria
- [ ] [Specific, testable criterion]
- [ ] [Specific, testable criterion]

## Out of Scope
- [Explicit exclusion]

## Constraints
- [Technical constraint or dependency]

## Phases
### Phase 1: [Name]
...
```

---

## context-save

### Executive Function Replaced
**Working memory externalization** — Captures full project state before ending a session so future-you can pick up without reorienting.

### When to Load
End of a work session. Before closing Claude. Before switching to a different project. "I need to stop but want to continue tomorrow."

### What to Capture
```markdown
# Context Snapshot — [Date/Time]

## What I Was Working On
[1–2 sentences: the immediate task]

## Current State
[What exists / what's working / what's broken right now]

## Decisions Made This Session
- [Decision + reason]

## Where I Left Off
[Exact file, line, step, or task that was next]

## Open Questions
- [Anything unresolved that needs answering next session]

## Next Action (when I return)
[The SINGLE first thing to do when resuming — specific and concrete]
```

### Storage Locations (in priority order)
1. `CONTEXT.md` in project root
2. `.planning/STATE.md` (GSD projects)
3. `context-[date].md` in a notes folder

---

## context-restore

### Executive Function Replaced
**Working memory recovery** — Reconstructs project context at the start of a session so you don't waste 20 minutes reorienting.

### When to Load
Start of a session. "Where was I?" "What was I working on?" "I left off somewhere, help me figure out where."

### Workflow
1. **Find context artifacts** — look for CONTEXT.md, STATE.md, recent git commits, recent file modifications
2. **Read and synthesize** — extract current state, last action, next action
3. **Present orientation brief**:

```markdown
# Session Resume Brief

## Where You Left Off
[1–2 sentences: what task you were on]

## Current State
[What's working, what's in progress, what's broken]

## Decisions Already Made
- [Decision — don't relitigate these]

## Your Next Action
[Single specific task to start right now]

## Open Questions from Last Session
- [Anything to resolve before proceeding]
```

4. **Ask**: "Does this match your memory? Or has something changed?"

---

## context-window

### Executive Function Replaced
**Working memory management during long sessions** — Prevents context rot as conversation grows.

### The Problem
As a conversation fills the context window, early instructions degrade and Claude starts forgetting constraints, making inconsistent decisions, and repeating work.

### Signals That Context Rot Is Happening
- Claude contradicts a decision made earlier
- Claude forgets a constraint that was explicitly stated
- Claude asks a question that was already answered
- Response quality noticeably drops after a long session

### Mitigation Strategies

**Proactive summarization**: Every 20–30 messages in a long session, write a mid-session summary:
```markdown
# Mid-Session Summary

## Goal (unchanged)
[What we're trying to accomplish]

## Decisions Made
- [Decision 1]
- [Decision 2]

## Constraints (active)
- [Constraint 1]
- [Constraint 2]

## Current Task
[What we're working on right now]
```

**Compaction triggers**: Start a new conversation with the summary when:
- Token count is visibly high
- Response quality drops
- You're switching to a different phase of work

**Reference files over re-explanation**: Store important context in files (`CONTEXT.md`, `DECISIONS.md`) — reference them by filename rather than re-pasting content.

---

## conversation-memory

### Executive Function Replaced
**Long-term working memory** — Persistent memory across conversations. Remembers users, decisions, and context across sessions.

### Memory Types
| Type | What It Stores | Retrieval |
|---|---|---|
| Short-term | Current session state | Automatic |
| Long-term | Cross-session facts and preferences | Semantic search |
| Entity memory | People, projects, decisions | Key lookup |

### Memory Pipeline
```
New information →
  Is this worth remembering?
    Surprising → yes
    Decision → yes
    Preference → yes
    Trivial → no
  Store with metadata (date, source, session)
  On retrieval: search by relevance + recency
  Inject into context as "known facts"
```

### What to Remember
- User preferences ("I prefer TypeScript strict mode")
- Project decisions ("We chose PostgreSQL over MongoDB because...")
- Recurring context ("This project is a SaaS for X audience")
- Personal context ("I have ADHD, keep lists short")

### What NOT to Remember
- Raw conversation transcripts (too large, too noisy)
- Temporary state that changes constantly
- Sensitive information (passwords, tokens — never store these)

### Memory Hygiene
- Review stored memories monthly — prune stale facts
- Resolve conflicts explicitly ("I used to prefer X, now I prefer Y — update")
- Keep entity records fresh — decisions change

---

## file-organizer

### Executive Function Replaced
**Organization + initiation** — Tames digital chaos when the mess itself has become a reason not to work.

### When to Load
"My Downloads is a disaster", "I can't find anything", "files everywhere", "help me organize this."

### Workflow
1. **Audit current state**: Review folder structure, identify chaos zones (Downloads, Desktop, project root)
2. **Find duplicates**: Identify duplicate files across locations
3. **Propose organization**: Suggest logical folder structure based on actual content
4. **Get approval**: Show proposed structure before moving anything
5. **Execute**: Move, rename, and organize with confirmation
6. **Maintain**: Establish naming conventions for future files

### Organization Principles
- **By project, not by type** — Don't put all PDFs in one folder. Put project docs with the project.
- **Flat is better than deep** — More than 3 levels of nesting means you'll never find it again
- **Date prefix for archives** — `2024-11-15-meeting-notes.md` sorts correctly and is findable
- **Inbox pattern** — Everything lands in `/Inbox`, gets sorted weekly, never stays longer than 7 days

### Naming Conventions
```
Projects:   kebab-case (my-project-name)
Documents:  YYYY-MM-DD-description.ext
Archives:   YYYY-[category]-description.ext
Code files: Follow language conventions
```

### What NOT to Delete Without Explicit Confirmation
- Anything in project directories
- Anything modified in the last 30 days
- Anything with a unique name (no obvious duplicate)
- Anything that looks like a contract, legal doc, or financial record

---

## doc-templates

### Executive Function Replaced
**Getting started** — Provides ready-to-use document templates so blank page paralysis never happens.

### Available Templates

**Project Kickoff Note**
```markdown
# [Project Name]
**Date:** [date]
**Goal:** [what done looks like in 1 sentence]
**Deadline:** [or "none"]

## Why This Matters
[1–3 sentences]

## Success Criteria
- [ ] [Specific measurable outcome]
- [ ] [Specific measurable outcome]

## First Three Actions
1. [Action]
2. [Action]
3. [Action]
```

**Weekly Review Template**
```markdown
# Week of [date]

## What I Actually Did
- 

## What I Didn't Do (and why)
- 

## What's Carrying Over
- 

## One Thing to Do Differently Next Week
- 

## Next Week's Top 3
1. 
2. 
3. 
```

**Decision Log**
```markdown
# Decision: [Title]
**Date:** [date]
**Status:** Decided / Revisiting / Reversed

## Context
[Why this decision needed to be made]

## Options Considered
- [Option A] — pros/cons
- [Option B] — pros/cons

## Decision
[What was chosen]

## Reasoning
[Why]

## Review Trigger
[What would make us revisit this?]
```

**Meeting Notes**
```markdown
# [Meeting Name] — [Date]
**Attendees:** 
**Purpose:** 

## Key Decisions
- 

## Action Items
- [ ] [Action] — @[owner] by [date]

## Open Questions
- 

## Next Meeting
[Date / "None"]
```

---

## verify-completion

### Executive Function Replaced
**Self-monitoring / completion recognition** — Enforces the iron law: done means verified, not assumed.

### The Iron Law
```
NO COMPLETION CLAIMS WITHOUT FRESH VERIFICATION EVIDENCE
```

"I think it works" is not done. "It should work" is not done. Done means you ran the check this message and saw the output.

### Before Claiming Anything Is Done
1. **Identify**: What command or action proves this claim?
2. **Run it**: Execute the full verification command fresh — not from memory of a previous run
3. **Show the output**: Paste the actual output as evidence
4. **Then** say it's done

### Verification Checklist by Task Type
| Task Type | Verification |
|---|---|
| Code written | `npm test` / `pytest` / build command — all passing |
| Feature built | Walk through the user flow manually |
| File organized | Open the folder and confirm structure |
| Plan written | Read it aloud — does every task make sense? |
| Research done | Can you answer the original question in 2 sentences? |
| Document created | Open the file and read the first paragraph |
| Bug fixed | Reproduce the original bug — confirm it no longer occurs |

### The "Done" Checklist
- [ ] The thing I said I'd build exists
- [ ] I ran the verification command this session
- [ ] The output matches what I expected
- [ ] I checked the edge case that seemed most likely to fail
- [ ] I didn't just check the happy path

---

## behavioral-modes

### Executive Function Replaced
**Mode switching** — Explicitly shifts between cognitive modes. Prevents "trying to brainstorm and implement at the same time" (the ADHD trap of half-doing both and completing neither).

### Available Modes

**🧠 BRAINSTORM Mode**
*When to use*: Early planning, feature ideation, "I'm not sure what to build"
- Offer multiple alternatives (at least 3)
- No code yet — ideas and options only
- Use diagrams (mermaid) to explain concepts
- Divergent thinking — explore unconventional solutions
- Ask clarifying questions before diving in

**⚡ IMPLEMENT Mode**
*When to use*: You know exactly what to build, ready to execute
- Minimal questions — assume and proceed
- Write complete, working code — no placeholders
- Follow existing patterns in the codebase
- Commit frequently with descriptive messages
- Surface blockers immediately rather than guessing

**🔍 DEBUG Mode**
*When to use*: Something is broken, need to find and fix the root cause
- Gather evidence before proposing fixes
- State hypothesis before testing
- One fix at a time — verify before the next
- Explain WHY the bug occurred, not just the fix
- Never claim fixed without running the verification

**📋 REVIEW Mode**
*When to use*: Work is done, need a quality pass
- Read first, comment after
- Prioritize: correctness > security > performance > style
- Specific and actionable feedback only
- Distinguish blockers from suggestions

**🎓 TEACH Mode**
*When to use*: "Explain this to me", "why does this work", "I want to understand"
- Explain concepts before implementation
- Use analogies for complex ideas
- Check for understanding before moving on
- No jargon without explanation

**🚢 SHIP Mode**
*When to use*: "Just get it working", time-constrained, MVP mindset
- Ruthless scope reduction
- Working beats perfect
- Hardcode if needed (leave TODO comment)
- Document the shortcuts taken for later cleanup

### How to Switch Modes
Just say: "Switch to IMPLEMENT mode" or "I need BRAINSTORM mode now."
Claude will acknowledge the mode and adjust behavior accordingly.

---

## loki-mode

### Executive Function Replaced
**Everything** — Full autonomous execution from PRD to deployed product. The "I just want this to exist" mode.

### What It Is
Multi-agent autonomous system for Claude Code. Takes a Product Requirements Document (PRD) and builds to a deployed, revenue-generating product with zero manual steps.

**Trigger**: Say "Loki Mode" to activate.

### Architecture
- **Orchestrator**: Reads PRD, initializes project state, spawns specialized agents
- **Model routing**: Opus for planning, Sonnet for development, Haiku for unit tests/monitoring
- **Parallelization**: 10+ agents running simultaneously for independent tasks
- **State management**: `.loki/CONTINUITY.md` (working memory), `.loki/state/orchestrator.json` (phase tracking)
- **Memory**: Semantic memory (patterns), episodic memory (interaction traces), anti-patterns log

### Required Input
A PRD covering:
- Product vision (what it is, who it's for)
- Core features (must-have for v1)
- Technical constraints (preferred stack, deployment target)
- Success criteria (what "working" looks like)

### Phase Structure
```
Discovery → Architecture → Core Build → Integration → QA → Deploy → Post-Launch
```

### RARV Cycle (every agent turn)
**R**EASON: What am I doing and why?
**A**CT: Execute the action
**R**EFLECT: Did it work? What was unexpected?
**V**ERIFY: Test your work before moving on

### CONTINUITY.md (Working Memory)
Every turn starts with reading `.loki/CONTINUITY.md`. Every turn ends with updating it. This is the mechanism that prevents context rot across hundreds of agent actions.

### When to Use
- Solo developer building a complete product
- You have a clear PRD and just want it built
- You're comfortable reviewing output and approving checkpoints
- You have `--dangerously-skip-permissions` enabled for autonomous execution

### When NOT to Use
- When you're still figuring out what to build (use `gsd-roadmap` first)
- When the scope is a single feature or bug fix (use `gsd-execute`)
- When you want to understand and learn as it builds (use `execute-plan` with explanations)

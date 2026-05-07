---
name: dispatch
description: "Master router and dispatcher for all skill suites. Identifies which suite to load based on the user's request and routes to it. Use this skill when the task domain is unclear, when a request spans multiple suites, or as the universal entry point before any specialized work begins. Covers all domains: UI/UX design, web development, visual art, marketing, copywriting, SEO, CRO, email, ads, DevOps, cloud infrastructure, CI/CD, Docker, Kubernetes, databases, coding, programming, architecture, APIs, testing, security, penetration testing, hacking, red team, blue team, startups, business strategy, product management, SaaS metrics, CRM, game development, Unity, Minecraft, AI agents, data science, machine learning, RAG, LLM, voice AI, productivity, task planning, ADHD, executive function, getting things done, organization. Trigger keywords: which skill, what suite, help me with, I need to, I want to build, I want to make, I'm working on, help me figure out, not sure where to start, route me, dispatch."
metadata:
  version: 1.0.0
  suites:
    - design-studio
    - marketing-suite
    - devops-suite
    - coding-suite
    - founders-suite
    - game-dev
    - research-lab
    - purple-team
    - productivity-suite
---

# Dispatch

**The master router. Every suite lives here. Read this first when you're not sure which expert to call.**

---

## How Dispatch Works

1. **Read the user's request**
2. **Match to a suite** using the routing table below
3. **Load that suite's SKILL.md** — it contains the sub-skill routing table
4. **Execute** following the suite's workflow

For multi-suite requests, identify the **primary suite** first, then note the secondary suites to involve.

---

## Master Routing Table

### 🎨 design-studio
**Load when:** UI, UX, visual design, web design, landing pages, dashboards, data visualization, design systems, component libraries, accessibility, animation, motion, generative art, posters, print, typography, Figma, wireframes, prototypes, portfolio, creative direction.

> *"Make it look good", "design this", "build a landing page", "create a component", "audit this UI", "make something beautiful", "generate art"*

**Path:** `skills/design-studio/SKILL.md`

---

### 📣 marketing-suite
**Load when:** Marketing copy, headlines, CTAs, email sequences, cold email, SEO strategy, SEO audit, CRO (landing pages, signup flows, onboarding, paywalls, popups, forms), A/B testing, paid ads (Google, Meta, LinkedIn, TikTok), social media content, content strategy, brand voice, churn prevention, referral programs, product launches, analytics (GA4, GTM, Mixpanel), attribution, sales decks, battlecards.

> *"Write copy for", "improve conversions", "A/B test this", "email sequence", "ad campaign", "content calendar", "reduce churn", "launch strategy"*

**Path:** `skills/marketing-suite/SKILL.md`

---

### 🛠️ devops-suite
**Load when:** Cloud infrastructure (AWS, GCP, Azure, Vercel), Docker, Kubernetes, CI/CD pipelines (GitHub Actions, GitLab CI), databases (SQL, NoSQL, vector), observability (Prometheus, Grafana, logging), incident response, server management, shell scripting (Bash, PowerShell), cost optimization, microservices, service mesh, MLOps, workflow automation.

> *"Deploy this", "set up CI/CD", "Docker container", "Kubernetes cluster", "database schema", "monitoring", "incident", "automate this workflow"*

**Path:** `skills/devops-suite/SKILL.md`

---

### 💻 coding-suite
**Load when:** Writing code, debugging code, code review, programming languages (Python, TypeScript, JavaScript, Rust, Go, Java, C#, C++, Swift, Kotlin), frameworks (React, Next.js, Vue, FastAPI, Django, Rails, Spring), testing, software architecture, backend APIs, LLM app development, authentication, performance profiling, refactoring, technical documentation.

> *"Write a function", "debug this", "review my code", "build an API", "architect this system", "optimize this", "help me code"*

**Path:** `skills/coding-suite/SKILL.md`

---

### 🏗️ founders-suite
**Load when:** Startup strategy, business analysis, SWOT, SMART goals, OKRs, competitive analysis, pricing strategy, product management (RICE, PRD, roadmap), go-to-market, SEO foundations, programmatic SEO, GEO (AI search optimization), CRM development (Salesforce, HubSpot), Segment CDP, SaaS metrics (MRR, CAC, LTV, churn), HR workflows, hiring, micro-SaaS, indie hacker, AI product/wrapper businesses.

> *"Analyze this startup", "pricing strategy", "SWOT analysis", "PRD template", "Salesforce integration", "SaaS metrics", "hiring plan", "validate my idea"*

**Path:** `skills/founders-suite/SKILL.md`

---

### 🎮 game-dev
**Load when:** Game development of any kind — 2D games, 3D games, Unity (C#), web games (Phaser, Three.js, WebGPU), mobile games (iOS/Android), PC/console games, VR/AR (Quest, PCVR), game design documents (GDD), core loop design, player psychology, game balancing, game art direction, sprite sheets, animation, sound design, FMOD, Wwise, multiplayer/netcode, Minecraft plugins (Bukkit, Spigot, Paper).

> *"Build a game", "Unity script", "game design doc", "Minecraft plugin", "VR experience", "multiplayer netcode", "game loop", "pixel art pipeline"*

**Path:** `skills/game-dev/SKILL.md`

---

### 🔬 research-lab
**Load when:** Data science, machine learning, statistical analysis, A/B testing (ML context), predictive modeling, AI agent architecture, autonomous agents, multi-agent systems, CrewAI, LangGraph, agent memory, RAG (retrieval-augmented generation), prompt engineering, prompt caching, LLM application patterns, voice agents, voice AI, agent evaluation, research methodology, academic research engineering.

> *"Build an AI agent", "data analysis", "machine learning model", "RAG pipeline", "prompt engineering", "multi-agent system", "voice AI", "statistical analysis", "research this rigorously"*

**Path:** `skills/research-lab/SKILL.md`

---

### 🟣 purple-team
**Load when:** Security of any kind — penetration testing, ethical hacking, red team, MITRE ATT&CK, reconnaissance (Shodan, OSINT), web app testing (SQLi, XSS, IDOR, Burp Suite), cloud pentesting (AWS, Azure, GCP), privilege escalation (Linux, Windows, Active Directory), post-exploitation, Metasploit, malware analysis, reverse engineering, firmware analysis, SAST/DAST, security auditing, dependency scanning, threat modeling (STRIDE), API security, secure coding, security hardening, bug bounty.

> *"Pentest this", "security audit", "find vulnerabilities", "red team", "STRIDE analysis", "is this code secure", "SAST scan", "privilege escalation", "reverse engineer this"*

**Path:** `skills/purple-team/SKILL.md`

---

### ⚡ productivity-suite
**Load when:** Getting unstuck, task initiation, breaking down overwhelming tasks, project planning and roadmapping, working memory ("where was I?"), context save/restore, file organization, digital chaos, GSD (Get Shit Done) framework, execution with checkpoints, completion verification, ADHD support, executive function replacement, mode switching (brainstorm/implement/debug), autonomous project execution (Loki Mode).

> *"I don't know where to start", "break this down", "I'm overwhelmed", "where was I", "organize my files", "just get this done", "plan this project", "I keep forgetting", "help me focus"*

**Path:** `skills/productivity-suite/SKILL.md`

---

## Ambiguous Cases — Tie-Breaker Rules

Some requests could reasonably route to multiple suites. Use these rules:

| Request Type | Primary Suite | Why |
|---|---|---|
| SEO audit of a website | **marketing-suite** | Tactical execution focus |
| SEO as a business growth strategy | **founders-suite** | Strategic/business context |
| A/B test setup for conversion | **marketing-suite** | CRO is marketing |
| A/B test statistical analysis | **research-lab** | Statistical methodology |
| Build a data dashboard | **design-studio** | Visual/UI output |
| Analyze data for insights | **research-lab** | ML/statistical output |
| API security review | **purple-team** | Security is the output |
| Build a secure API | **coding-suite** | Code is the output; security is a constraint |
| Launch strategy for a product | **founders-suite** | Business context |
| Launch strategy campaign copy | **marketing-suite** | Content is the output |
| Referral program mechanics | **founders-suite** | Business/growth strategy |
| Referral program copy | **marketing-suite** | Content is the output |
| Cloud cost optimization | **devops-suite** | Infrastructure focus |
| Pricing strategy for SaaS | **founders-suite** | Business strategy |
| Prompt engineering for an app | **coding-suite** | App development context |
| Prompt engineering as a craft | **research-lab** | LLM engineering focus |
| Agent memory architecture | **research-lab** | AI systems design |
| Memory in a coding project | **coding-suite** | Implementation context |
| Planning a coding project | **productivity-suite** | Execution/workflow first |
| Architecting a coding project | **coding-suite** | Technical design first |

**When genuinely ambiguous:** Route to the suite that owns the *output*, not the *input*.

---

## Multi-Suite Requests

Some tasks span multiple suites. Sequence them:

| Task | Sequence |
|---|---|
| "Build and launch a SaaS" | founders-suite → coding-suite → devops-suite → marketing-suite |
| "Build a game and market it" | game-dev → marketing-suite |
| "Audit our security and fix the code" | purple-team → coding-suite |
| "Design and build a dashboard" | design-studio → coding-suite |
| "Build an AI product" | research-lab → coding-suite → founders-suite |
| "I'm overwhelmed, help me build this app" | productivity-suite → coding-suite |
| "Pentest our app then harden it" | purple-team (red) → purple-team (blue) |
| "Launch campaign with copy and analytics" | marketing-suite → devops-suite (tracking setup) |

**Rule**: Always complete the primary suite's work before loading the secondary. Don't try to run both simultaneously.

---

## Suite Quick Reference

```
design-studio    → Making things look and feel right
marketing-suite  → Getting people to notice, click, and convert
devops-suite     → Making systems run reliably at scale
coding-suite     → Writing correct, maintainable software
founders-suite   → Building and scaling a business
game-dev         → Making games people want to play
research-lab     → AI agents, data science, LLM engineering
purple-team      → Breaking things (red) and fixing them (blue)
productivity-suite → Getting things done when your brain won't cooperate
```

---

## If Still Unsure

Ask one question: **"What is the primary deliverable?"**

- A visual artifact → **design-studio**
- Marketing content or a conversion → **marketing-suite**
- Running infrastructure → **devops-suite**
- Working code → **coding-suite**
- A business decision or document → **founders-suite**
- A game → **game-dev**
- An AI system or data insight → **research-lab**
- A security finding or fix → **purple-team**
- A completed task or organized life → **productivity-suite**

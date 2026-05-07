# Routing Test Prompts

Real-world user prompts to validate that each super-skill triggers correctly. Use these to check description quality and routing accuracy.

## How to use

1. Start a fresh Claude Code / Cowork session with this plugin installed.
2. Send each prompt verbatim.
3. Verify the **expected** suite triggers (and ideally the right sub-skill within it).
4. If the wrong suite triggers, the description on the *expected* suite is too weak — strengthen its trigger keywords.
5. If multiple suites trigger, descriptions overlap — add disambiguation language ("Not for X — see other-skill").

**Pass criteria:** ≥ 9/10 prompts in each suite trigger that suite. If you get < 9/10, the description needs work.

---

## dispatch (master router)

Use when the user's intent spans multiple suites or is unclear about which area applies.

| # | Prompt | Expected sub-route |
|---|--------|--------------------|
| 1 | "I have a vague idea for something — help me figure out where to start." | (any — dispatch should route after asking) |
| 2 | "Not sure which skill area this falls under." | (clarification) |
| 3 | "I want to build a thing but don't know what kind of expertise I need." | (clarification) |
| 4 | "Can you tell me which suite to use for X?" | (matching suite) |
| 5 | "Route me to whatever fits this best." | (best-match suite) |
| 6 | "What's the right tool for analyzing customer data and writing copy from it?" | research-lab → marketing-suite |
| 7 | "I want to ship a SaaS product. Where do I begin?" | founders-suite |
| 8 | "I need help on something between design and engineering." | design-studio + coding-suite |
| 9 | "Just dispatch me — I have an unclear request." | (clarification) |
| 10 | "Help me pick the right skill for this task: [pasted complex task]." | (best-match) |

---

## marketing-suite (strategic marketing playbook)

| # | Prompt | Expected sub-skill |
|---|--------|--------------------|
| 1 | "Write a hero section and CTA for my B2B SaaS landing page." | copywriting |
| 2 | "Why is my signup conversion only 2%?" | signup-flow-cro / page-cro |
| 3 | "Build a 6-email welcome sequence for new trial users." | email-sequence |
| 4 | "Optimize my pricing page — nobody's converting." | page-cro |
| 5 | "Plan a Product Hunt launch for next month." | launch-strategy |
| 6 | "Build a referral program for our SaaS." | referral-program |
| 7 | "Write 5 ad creative variations for Meta ads." | ad-creative |
| 8 | "Why are customers churning at month 3? How do I prevent it?" | churn-prevention |
| 9 | "Help me write a case study for an enterprise customer." | sales-enablement |
| 10 | "Plan a content strategy for the next quarter." | content-strategy |

---

## all-marketing (tactical reference library, 165 sub-skills)

| # | Prompt | Expected sub-skill |
|---|--------|--------------------|
| 1 | "Optimize my robots.txt for AI crawlers like GPTBot." | seo/technical/robots |
| 2 | "Help me set up an XML sitemap and submit it to Google." | seo/technical/sitemap |
| 3 | "Audit my Core Web Vitals — LCP is bad." | seo/technical/core-web-vitals |
| 4 | "Set up Open Graph and Twitter Card tags." | seo/on-page/open-graph + twitter-cards |
| 5 | "Create a TikTok ad campaign with creative brief." | paid-ads/tiktok-ads |
| 6 | "Write a LinkedIn carousel post for thought leadership." | platforms/linkedin |
| 7 | "Build a footer for my website with proper sitelinks." | components/navigation/footer |
| 8 | "Plan a Reddit ad strategy on r/programming." | paid-ads/reddit-ads |
| 9 | "Build out the careers page for our company site." | pages/utility/careers |
| 10 | "How do I optimize for AI Overviews and ChatGPT citations?" | analytics/ai-traffic + ai-seo |

---

## coding-suite (full-stack engineering)

| # | Prompt | Expected sub-skill |
|---|--------|--------------------|
| 1 | "Write a Python async function with proper error handling and type hints." | python-pro |
| 2 | "Set up a Next.js 14 App Router project with auth." | nextjs-best-practices |
| 3 | "Optimize this PostgreSQL query — it's doing a sequential scan." | sql-pro |
| 4 | "Design a Prisma schema for a multi-tenant SaaS." | prisma-orm |
| 5 | "Refactor this React component for clean code." | react-best-practices + clean-code |
| 6 | "Write tests for this function using TDD." | tdd / test-driven-development |
| 7 | "Code-review this PR — focus on security and performance." | code-review |
| 8 | "Build a RAG pipeline with embeddings and reranking." | llm-development / rag |
| 9 | "Set up bun as the package manager and runtime for this project." | bun-tooling |
| 10 | "Implement OAuth 2.0 with refresh tokens in NestJS." | nestjs-expert + auth |

---

## design-studio (UI/UX, art, components)

| # | Prompt | Expected sub-skill |
|---|--------|--------------------|
| 1 | "Design a dashboard with KPI cards, charts, and a data table." | ui-design / dashboard |
| 2 | "Create a wireframe for a B2B SaaS landing page." | frontend-design |
| 3 | "Run a WCAG 2.1 AA accessibility audit on this page." | accessibility-audit |
| 4 | "Build a design system with tokens, primitives, and Tailwind config." | design-system |
| 5 | "Make me some generative art with p5.js — go wild." | generative-art / creative-agency |
| 6 | "Design a mobile-first iOS settings screen." | mobile-design |
| 7 | "Audit this design's typography hierarchy." | design-taste / typography |
| 8 | "Create a brutalist portfolio site with strong personality." | impeccable / design-taste |
| 9 | "Build a component library with shadcn/ui and Radix." | ui-design / components |
| 10 | "Make this look incredible — I'll let you choose the direction." | creative-agency |

---

## devops-suite (cloud, CI/CD, ops)

| # | Prompt | Expected sub-skill |
|---|--------|--------------------|
| 1 | "Set up a GitHub Actions CI pipeline with parallel jobs and caching." | github-workflow-automation |
| 2 | "Build a multi-stage Dockerfile for a Node.js app." | docker-expert |
| 3 | "Deploy a serverless Lambda function with API Gateway via SAM." | aws-serverless |
| 4 | "Configure Prometheus alerts and SLOs for our service." | monitoring / slo |
| 5 | "Run an incident postmortem for last week's outage." | incident-response |
| 6 | "Set up Kubernetes ingress with TLS termination." | kubernetes |
| 7 | "Plan a Postgres major version migration with zero downtime." | database-migration |
| 8 | "Configure HashiCorp Vault for secrets management." | secrets-management |
| 9 | "Audit and optimize our AWS cloud costs." | cost-optimization |
| 10 | "Set up distributed tracing with OpenTelemetry." | tracing / observability |

---

## founders-suite (startup ops, business strategy)

| # | Prompt | Expected sub-skill |
|---|--------|--------------------|
| 1 | "Help me validate this startup idea — what's the killshot risk?" | startup-analysis |
| 2 | "Set up OKRs for Q3." | business-frameworks |
| 3 | "Should I price per-seat, per-usage, or freemium?" | pricing-strategy |
| 4 | "Run a SWOT analysis on my product vs. the top three competitors." | competitive-analysis |
| 5 | "Plan a Product Hunt launch and AppSumo deal." | launch-strategy |
| 6 | "Set up Salesforce CRM for our 5-person sales team." | salesforce-crm |
| 7 | "Build a GTM plan for our enterprise tier." | gtm-strategy |
| 8 | "Write a PRD for our new AI feature." | product-manager-toolkit |
| 9 | "How do I differentiate as an AI wrapper product when the underlying model is everyone's?" | ai-wrapper-product |
| 10 | "Help me pitch a seed round narrative." | startup-analysis / pitch |

---

## game-dev (game development)

| # | Prompt | Expected sub-skill |
|---|--------|--------------------|
| 1 | "Design a core game loop for a roguelike with permadeath." | game-design |
| 2 | "Build a 2D platformer in Unity with C# — sprite, tilemap, physics." | unity-developer + 2d-games |
| 3 | "Create a Bukkit Minecraft plugin with custom commands and events." | minecraft-bukkit-pro |
| 4 | "Design a balance system for a deck-builder card game." | game-design |
| 5 | "Build a Phaser web game with WebGPU rendering." | web-games |
| 6 | "Set up VR comfort guidelines for a Quest game." | vr-ar |
| 7 | "Design the audio system using FMOD with adaptive music." | game-audio |
| 8 | "Optimize Unity performance for low-end Android devices." | unity-developer + mobile-games |
| 9 | "Plan multiplayer netcode architecture with rollback." | multiplayer |
| 10 | "Write a Game Design Document (GDD) for my project." | game-design |

---

## productivity-suite (executive function / ADHD aide)

| # | Prompt | Expected sub-skill |
|---|--------|--------------------|
| 1 | "I'm overwhelmed by this project. Break it down into atomic steps." | task-breakdown |
| 2 | "Plan a roadmap for shipping this in 6 weeks." | concise-planning / plan-writing |
| 3 | "I keep losing track of where I left off — help me preserve context." | context-save |
| 4 | "Restore my context from yesterday's session." | context-restore |
| 5 | "What should I work on today given my open tasks?" | gsd / next-task |
| 6 | "I'm stuck and can't bring myself to start. What do I do?" | task-initiation |
| 7 | "Organize my brain dump into a real plan." | plan-writing |
| 8 | "Help me execute this plan step by step." | execute-plan |
| 9 | "Verify this task is actually complete and nothing is missing." | completion-verification |
| 10 | "I have ADHD and my executive function is shot — help me get going." | gsd |

---

## purple-team (security: red + blue + RE)

| # | Prompt | Expected sub-skill |
|---|--------|--------------------|
| 1 | "Run a pentest checklist on my authorized scope." | pentest-checklist |
| 2 | "Help me solve this CTF web challenge — SQL injection." | sql-injection / xss-html-injection |
| 3 | "Reverse engineer this firmware image from a device I own." | firmware-analysis / reverse-engineering |
| 4 | "Build a SIEM detection rule for credential stuffing." | blue-team / detection-engineering |
| 5 | "Threat-model this API using STRIDE." | threat-modeling |
| 6 | "Analyze this malware sample in a sandbox." | malware-analysis |
| 7 | "Audit my Active Directory config for common misconfigurations." | active-directory / privesc-windows |
| 8 | "Run an OSINT investigation on a target (authorized testing)." | shodan-reconnaissance / osint |
| 9 | "Set up a phishing simulation for our team's awareness training." | red-team-tactics / social-engineering |
| 10 | "Pentest a Wordpress site I own and find the holes." | wordpress-pentest |

---

## research-lab (data science + AI research)

| # | Prompt | Expected sub-skill |
|---|--------|--------------------|
| 1 | "Build a RAG system with hybrid search and reranking." | rag-systems |
| 2 | "Set up an autonomous agent with a ReAct loop." | autonomous-agents |
| 3 | "Run an A/B test on my landing page with proper statistical power." | data-scientist / ab-testing |
| 4 | "Build a multi-agent orchestrator with LangGraph." | langgraph |
| 5 | "Optimize my prompts for token efficiency without losing quality." | prompt-engineering |
| 6 | "Build a voice agent with sub-500ms latency." | voice-ai |
| 7 | "Statistical analysis on this conversion funnel data." | data-scientist |
| 8 | "Train a custom embedding model for my domain." | embeddings |
| 9 | "Build agent memory with a vector DB." | agent-memory-systems |
| 10 | "Brainstorm research directions in my field." | brainstorming |

---

## Cross-suite disambiguation tests

These prompts test whether description boundaries are crisp. Each has a **single correct** suite — if more than one fires, descriptions need disambiguation.

| # | Prompt | Should trigger | Should NOT trigger |
|---|--------|----------------|--------------------|
| 1 | "Write a launch tweet for my new feature." | marketing-suite (social-content) | all-marketing, sales |
| 2 | "Plan our Q3 product roadmap." | founders-suite (product-manager-toolkit) | marketing-suite |
| 3 | "Design a database schema for user profiles." | coding-suite (database-design) | devops-suite |
| 4 | "Set up a feature flag system." | coding-suite (architecture) or devops-suite (deployment) | — (either is acceptable; document choice) |
| 5 | "Write a security disclosure policy." | purple-team (defensive) | — |
| 6 | "Build a chatbot agent that answers customer questions." | research-lab (autonomous-agents) | marketing-suite |
| 7 | "Plan a content calendar." | marketing-suite (content-strategy) | productivity-suite |
| 8 | "Optimize my onboarding flow — users aren't activating." | marketing-suite (onboarding-cro) | productivity-suite, founders-suite |
| 9 | "Design a logo and color palette." | design-studio (visual-identity) | marketing-suite |
| 10 | "Help me prepare for an investor meeting." | founders-suite | marketing-suite |

---

## Recording results

When testing, log each prompt's outcome in this format:

```
| # | Suite | Prompt | Triggered correctly? | Sub-skill correct? | Notes |
```

Aim for ≥ 90% correct triggering on the in-suite tests and 100% on disambiguation tests. Anything below that is actionable feedback for the description copy.

---
name: founders-suite
description: "Full-stack founder and business AI covering 30+ specialist skills across product strategy, SEO and growth, CRM and sales tooling, analytics, business analysis, pricing, HR workflows, and AI product development. Use for startup analysis, SWOT/SMART frameworks, product roadmapping, RICE prioritization, pricing strategy, SEO audits, programmatic SEO, GEO, launch strategy, referral programs, Salesforce/HubSpot CRM, Segment CDP, micro-SaaS, AI wrapper products, lead generation, and competitive analysis. Trigger keywords: startup, founder, business strategy, product manager, SWOT, SMART goals, RICE, PRD, roadmap, pricing, SEO audit, programmatic SEO, AI SEO, launch, go-to-market, GTM, referral program, CRM, Salesforce, HubSpot, Segment, analytics, lead generation, competitive analysis, market research, hiring, HR, SaaS metrics, MRR, churn, CAC, LTV, micro-SaaS, AI product, indie hacker, product-market fit."
metadata:
  version: 1.0.0
  source: _Master_Library/Business-Administration + _Master_Library/Uncategorized
---

# Founders Suite

A complete, modular business operations AI for founders, product leaders, and operators — covering the full lifecycle from idea validation to scaling: strategy, product, SEO, growth, CRM, analytics, and team.

---

## How to Use This Skill

1. **Identify the task category** from the routing table below
2. **Load the matching sub-skill** from `references/skills-catalog.md`
3. **Execute** following the sub-skill's workflow

---

## Quick Routing Table

### 🧠 Strategy & Analysis
| Task | Load |
|------|------|
| Startup evaluation, market opportunity, competitive landscape, SWOT | `startup-analysis` |
| Business framework documents — SWOT, SMART goals, OKRs, business plans | `business-frameworks` |
| Competitor research, positioning maps, feature comparison | `competitive-analysis` |
| Pricing tiers, willingness to pay, Van Westendorp, packaging | `pricing-strategy` |

### 🚀 Product
| Task | Load |
|------|------|
| Feature prioritization (RICE), customer interview analysis, PRD templates, GTM | `product-manager-toolkit` |
| Building an AI-powered product — LLM integration, RAG, prompt engineering, AI UX | `ai-product` |
| Building an AI wrapper business — focused tools, cost management, differentiation | `ai-wrapper-product` |
| Indie hacker / micro-SaaS launch — validation, MVP scoping, early traction | `micro-saas-launcher` |

### 📈 SEO & Growth
| Task | Load |
|------|------|
| SEO audit — technical SEO, on-page issues, crawlability, ranking diagnosis | `seo-audit` |
| SEO foundations — E-E-A-T, Core Web Vitals, algorithm principles | `seo-fundamentals` |
| Programmatic SEO — pages at scale, template strategy, directory/location pages | `programmatic-seo` |
| GEO — Generative Engine Optimization for ChatGPT/Claude/Perplexity citations | `geo-fundamentals` |
| Product launch strategy — phased rollout, channel mix, Product Hunt, momentum | `launch-strategy` |
| Referral and affiliate programs — incentive design, viral loops, program mechanics | `referral-program` |

### 🤝 CRM & Sales Tools
| Task | Load |
|------|------|
| Salesforce development — LWC, Apex, REST/Bulk APIs, Salesforce DX, packages | `salesforce-dev` |
| HubSpot integration — OAuth, CRM objects, associations, webhooks, Node/Python SDK | `hubspot-integration` |
| Segment CDP — Analytics.js, server-side tracking, tracking plans, identity resolution | `segment-cdp` |

### 📊 Analytics & Business Metrics
| Task | Load |
|------|------|
| SaaS metrics — MRR/ARR, churn, CAC, LTV, cohorts, funnel analysis | `saas-metrics` |
| Customer data platform setup, event tracking strategy, attribution | `segment-cdp` |

### 👥 HR & Team Operations
| Task | Load |
|------|------|
| Hiring workflows, job descriptions, interview frameworks, compensation | `hr-workflows` |
| Onboarding plans, 30/60/90-day frameworks, team documentation | `hr-workflows` |

---

## Loading Sub-Skills

All sub-skill instructions are in `references/skills-catalog.md`.

```
founders-suite/
├── SKILL.md                      ← You are here (routing hub)
└── references/
    └── skills-catalog.md         ← Full instructions for all skills
```

**Always read the relevant section of `skills-catalog.md` before executing any task.**

---

## Universal Founder Standards

**Data beats intuition** — Validate assumptions with numbers before building. Talk to customers before writing code.

**Revenue is the metric** — MRR, CAC, LTV, churn. Everything else is a proxy. Track what converts to revenue.

**Constraints breed creativity** — Tight scope, clear ICP, specific problem. Broad = nobody cares.

**Distribution is the product** — Great products fail without distribution. Build the channel alongside the product.

**Document decisions** — PRDs, ADRs, strategy docs. Institutional knowledge shouldn't live in one person's head.

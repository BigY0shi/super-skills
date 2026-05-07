---
name: marketing-suite
description: "Full-stack marketing AI covering 40 specialist skills. Use for copywriting,
  SEO, content strategy, email marketing, paid ads, social media, landing pages, CRO,
  A/B testing, analytics, brand building, lead generation, sales enablement, email sequences,
  churn prevention, pricing, product launches, competitor research, personas, and funnels.
  Trigger keywords: write copy, landing page, email sequence, keyword research, A/B test,
  conversion rate, ad campaign, content strategy, brand voice, lead magnet, churn, pricing
  page, product launch, growth strategy, revenue ops, sales pitch, onboarding, headlines,
  CTAs, ROAS, CPA, GA4, attribution. Modules: copywriting, copy-editing, content-strategy,
  social-content, ad-creative, email-sequence, cold-email, seo-mastery, seo-audit, page-cro,
  signup-flow-cro, onboarding-cro, paywall-upgrade-cro, popup-cro, ab-test-setup, paid-ads,
  analytics-tracking, launch-strategy, referral-program, sales-enablement, revops,
  brand-building, pricing-strategy, churn-prevention."
metadata:
  version: 1.0.0
  source: marketingskills (github.com/aitytech/marketingskills)
---

# Marketing Suite

A complete, modular marketing AI system covering the full marketing lifecycle — from brand strategy to conversion optimization to analytics.

---

## How to Use This Skill

1. **Identify the task category** from the routing table below
2. **Load the matching sub-skill** from `references/skills-catalog.md` (contains full instructions for each skill)
3. **Check for product context** — if `./agents/product-marketing-context.md` or `.claude/product-marketing-context.md` exists, read it before asking the user questions
4. **Use the 8-phase workflow** for complex multi-step projects (see `references/workflow.md`)
5. **Delegate to specialist agents** for parallel work (see `references/agents-guide.md`)

---

## Quick Routing Table

Match the user's request to the right module:

### ✍️ Copy & Content
| Task | Load |
|------|------|
| Write/rewrite marketing copy, headlines, CTAs, homepage, landing page, pricing page | `copywriting` |
| Polish existing copy, fix clarity/tone | `copy-editing` |
| Plan what content to create, editorial calendar, topic clusters | `content-strategy` |
| Social media posts (LinkedIn, Twitter/X, Instagram, TikTok) | `social-content` |
| Blog posts, long-form content | `content-strategy` → `copywriting` |
| Ad creative, display/social ad copy | `ad-creative` |

### 📧 Email
| Task | Load |
|------|------|
| Email sequences, drip campaigns, nurture flows, welcome series | `email-sequence` |
| Cold outreach emails | `cold-email` |
| Email marketing strategy, deliverability, segmentation | `email-marketing` |

### 🔍 SEO
| Task | Load |
|------|------|
| SEO strategy, keyword research, on-page, link building | `seo-mastery` |
| SEO audit of existing site/content | `seo-audit` |
| Programmatic SEO at scale | `programmatic-seo` |
| Schema markup / structured data | `schema-markup` |
| AI-optimized SEO (ChatGPT/Perplexity ranking) | `ai-seo` |

### 🎯 CRO (Conversion Rate Optimization)
| Task | Load |
|------|------|
| Landing page or website page optimization | `page-cro` |
| Signup/registration flow | `signup-flow-cro` |
| Onboarding flow | `onboarding-cro` |
| Paywall / upgrade prompt | `paywall-upgrade-cro` |
| Popup / exit intent | `popup-cro` |
| Form optimization | `form-cro` |
| A/B test design and setup | `ab-test-setup` |

### 💰 Paid Advertising
| Task | Load |
|------|------|
| PPC campaigns (Google, Meta, LinkedIn, TikTok) | `paid-ads` |
| Paid media strategy and planning | `paid-advertising` |

### 📊 Analytics & Data
| Task | Load |
|------|------|
| Set up tracking, GA4, GTM, Mixpanel, Segment | `analytics-tracking` |
| Attribution modeling, reporting, dashboards | `analytics-attribution` |

### 🌱 Growth
| Task | Load |
|------|------|
| Product launch strategy | `launch-strategy` |
| Referral / affiliate programs | `referral-program` |
| Free tool / engineering-as-marketing | `free-tool-strategy` |
| Lead magnets | `lead-magnets` |
| Site architecture for SEO/conversion | `site-architecture` |

### 🤝 Sales & CRM
| Task | Load |
|------|------|
| Sales decks, battlecards, objection handling | `sales-enablement` |
| Revenue operations, lead scoring, lifecycle | `revops` |
| Lead nurture sequences | `email-sequence` |
| Competitor comparison pages | `competitor-alternatives` |

### 🧠 Strategy & Research
| Task | Load |
|------|------|
| Market research, customer personas, trend analysis | `customer-research` |
| Brand strategy, positioning, voice/tone | `brand-building` |
| Pricing strategy and tier design | `pricing-strategy` |
| Marketing psychology and persuasion | `marketing-psychology` |
| Marketing ideas and tactics library | `marketing-ideas` |
| Core marketing fundamentals | `marketing-fundamentals` |
| Marketing problem-solving frameworks | `problem-solving` |

### 📉 Retention
| Task | Load |
|------|------|
| Reduce churn, cancel flows, dunning, save offers | `churn-prevention` |

---

## Loading Sub-Skills

Each sub-skill has detailed instructions in `references/skills-catalog.md`. For the most commonly used skills, full instructions are reproduced there. Structure:

```
marketing-suite/
├── SKILL.md                    ← You are here (routing hub)
└── references/
    ├── skills-catalog.md       ← Full instructions for all 30+ skills
    ├── workflow.md             ← 8-phase marketing pipeline
    └── agents-guide.md        ← 20 specialist agents and when to use them
```

**When to read reference files:**
- `skills-catalog.md` — Always read the relevant skill section before executing any task
- `workflow.md` — Read for complex multi-step campaigns or when the user asks for a full marketing plan
- `agents-guide.md` — Read when running in an agent-capable environment (Claude Code, Cowork) and the task would benefit from specialist delegation

---

## Universal Standards

Apply these to every marketing task:

**Language**: Always respond in the user's language. If they write in Spanish, respond in Spanish.

**Product Context First**: Before asking the user questions, check:
1. `./agents/product-marketing-context.md`
2. `.claude/product-marketing-context.md`
3. `./docs/brand-guidelines.md`

If context files exist, extract answers from them and only ask for what's missing.

**Output Quality**:
- Specificity over vagueness — real numbers beat adjectives
- Benefits over features — outcomes over mechanics  
- Customer language over company jargon
- Token efficiency — concise, scannable, actionable

---

## Multi-Tool Integrations

This skill is compatible with 60+ marketing tool integrations. When a task requires live data, check `references/tools-registry.md` for available MCP connections including:

**Analytics**: GA4, Google Search Console, Mixpanel, Amplitude, Adobe Analytics
**CRM/Email**: HubSpot, Salesforce, Klaviyo, ActiveCampaign, Mailchimp
**Ads**: Google Ads, Meta Ads, LinkedIn Ads, TikTok Ads
**SEO**: SEMrush, Ahrefs, DataForSEO
**Social**: Buffer, CrossPost
**Productivity**: Asana, Notion, Slack

---

## Getting Started

**For a single task**: Tell me what you're working on. I'll route to the right skill and execute.

**For a full campaign**: Say "run a full marketing campaign for [product]" and I'll activate the 8-phase pipeline from `references/workflow.md`.

**For brand setup**: Say "set up product marketing context" and I'll help you create a context file that makes all future tasks faster and more accurate.

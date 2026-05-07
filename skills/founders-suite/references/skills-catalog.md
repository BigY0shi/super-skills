# Founders Suite — Skills Catalog

Full instructions for all sub-skills. Read the relevant section before executing any founder or business task.

---

## Table of Contents

**Strategy & Analysis**
- [startup-analysis](#startup-analysis) — Market evaluation, opportunity sizing, SWOT, competitive positioning
- [business-frameworks](#business-frameworks) — SWOT, SMART, OKRs, business plans, analytical frameworks
- [competitive-analysis](#competitive-analysis) — Competitor research, positioning maps, battlecards
- [pricing-strategy](#pricing-strategy) — Tiers, packaging, willingness to pay, Van Westendorp

**Product**
- [product-manager-toolkit](#product-manager-toolkit) — RICE prioritization, customer interviews, PRD templates, GTM
- [ai-product](#ai-product) — LLM integration, RAG, prompt engineering, AI UX, cost optimization
- [ai-wrapper-product](#ai-wrapper-product) — AI wrapper business design, differentiation, monetization
- [micro-saas-launcher](#micro-saas-launcher) — Idea validation, MVP scoping, indie hacker launch playbook

**SEO & Growth**
- [seo-audit](#seo-audit) — Technical SEO, on-page issues, crawlability, ranking diagnosis
- [seo-fundamentals](#seo-fundamentals) — E-E-A-T, Core Web Vitals, algorithm principles
- [programmatic-seo](#programmatic-seo) — Pages at scale, template strategy, thin content avoidance
- [geo-fundamentals](#geo-fundamentals) — Generative Engine Optimization for AI search (ChatGPT, Perplexity, Claude)
- [launch-strategy](#launch-strategy) — Phased rollout, channel mix, Product Hunt, launch momentum
- [referral-program](#referral-program) — Incentive design, viral loops, affiliate program mechanics

**CRM & Sales Tools**
- [salesforce-dev](#salesforce-dev) — LWC, Apex, APIs, Salesforce DX, managed packages
- [hubspot-integration](#hubspot-integration) — OAuth, CRM objects, associations, webhooks, SDKs
- [segment-cdp](#segment-cdp) — Analytics.js, server-side tracking, tracking plans, identity resolution

**Analytics & Metrics**
- [saas-metrics](#saas-metrics) — MRR/ARR, churn, CAC, LTV, cohorts, funnel analysis

**HR & Team Operations**
- [hr-workflows](#hr-workflows) — Hiring frameworks, job descriptions, onboarding, compensation

---

---

## startup-analysis

**When to use:** Evaluating a startup idea, assessing market opportunity, analyzing competitive landscape, or stress-testing assumptions before building.

### Analysis Framework

**Step 1 — Problem Clarity**
- Is the problem real and painful, or just interesting?
- Who specifically has this problem? (ICP: role, company size, industry, geography)
- How are they solving it today? What does the workaround cost them?
- How often does the problem occur? What's the emotional intensity?

**Step 2 — Market Sizing**
- **TAM** (Total Addressable Market): everyone who could theoretically use this
- **SAM** (Serviceable Addressable Market): segment you can realistically reach
- **SOM** (Serviceable Obtainable Market): realistic 3-year capture
- Size markets bottom-up (# of buyers × average spend) not top-down ("3% of a $10B market")

**Step 3 — Competitive Landscape**
- Direct competitors: who else solves this exact problem?
- Indirect: status quo, spreadsheets, manual processes, adjacent tools
- Positioning gaps: where is the market underserved?
- Moat assessment: why would you be defensible?

**Step 4 — Business Model Stress Test**
- Revenue model: subscription, usage, transaction, services?
- Unit economics: CAC vs LTV ratio (healthy SaaS: LTV/CAC > 3:1)
- Payback period: how long to recover customer acquisition cost?
- Path to profitability: at what ARR/volume does this work?

**Step 5 — Founder-Market Fit**
- Why is this team the one to build this?
- Domain expertise, network, unfair access to customers?

### SWOT in Startup Context
```
Strengths      → What do you have that competitors don't?
Weaknesses     → What will kill you if you don't fix it?
Opportunities  → What tailwinds / timing advantages exist?
Threats        → What could make this irrelevant in 2 years?
```

---

## business-frameworks

**When to use:** Creating strategic documents, analyzing decisions, setting goals, writing business plans, or applying structured analytical frameworks.

### SWOT Analysis
Full framework: internal factors (Strengths, Weaknesses) vs. external factors (Opportunities, Threats).

**Output format:**
- Each quadrant: 3-5 specific, evidence-backed points
- Cross-analysis: SO strategies (use strengths to capture opportunities), ST (use strengths to counter threats), WO (address weaknesses to capture opportunities), WT (defensive plays)
- Prioritized action items from the cross-analysis

### SMART Goals
Every goal must be: **S**pecific, **M**easurable, **A**chievable, **R**elevant, **T**ime-bound.

```
❌ Weak: "Grow revenue"
✅ SMART: "Reach $50K MRR by December 31, 2025 by closing 25 new SMB accounts
           at an average ACV of $24K through outbound sales."
```

### OKRs (Objectives and Key Results)
- **Objective**: qualitative, inspiring direction ("Become the category leader in X")
- **Key Results**: 3-5 measurable outcomes that prove the objective was achieved (not tasks)
- Quarterly cadence; grade 0.0–1.0 at end of quarter
- Good KRs are ambitious: hitting 0.7 = success; 1.0 = you set it too easy

### Business Plan Structure
1. Executive Summary (1 page: problem, solution, market, traction, ask)
2. Problem & Solution
3. Market Opportunity (TAM/SAM/SOM)
4. Product/Service Description
5. Business Model & Unit Economics
6. Go-to-Market Strategy
7. Competitive Analysis
8. Team
9. Financial Projections (3-year P&L, monthly for year 1)
10. Funding Ask & Use of Funds

### Porter's Five Forces
| Force | Questions |
|-------|-----------|
| Threat of New Entrants | How easy to copy? Capital requirements? |
| Bargaining Power of Suppliers | API dependency? Single source? |
| Bargaining Power of Buyers | Switching costs? Alternatives? |
| Threat of Substitutes | Can the job be done differently? |
| Industry Rivalry | Fragmented or consolidated? Price wars? |

---

## competitive-analysis

**When to use:** Researching competitors, building positioning maps, creating battlecards, or identifying whitespace in a market.

### Research Workflow
1. **Identify competitors**: direct (same solution), indirect (alternative approaches), status quo (doing nothing)
2. **Data collection per competitor**: pricing page, feature list, G2/Capterra reviews (especially 3-star — most honest), job postings (reveals strategic bets), blog/content (reveals positioning), LinkedIn (team size, growth rate)
3. **Positioning matrix**: plot competitors on 2 axes that matter most to buyers
4. **Gap analysis**: where is the market underserved?
5. **Battlecard**: for each competitor — their pitch, your counter, objection handlers

### Battlecard Template per Competitor
```
[Competitor Name]
Their pitch: "We are the [X] for [Y]"
Their strengths: 2-3 genuine advantages
Their weaknesses: 2-3 real limitations
When we win: scenarios where we're clearly better
When we lose: scenarios where they're better (be honest)
Objection handlers:
  "They're cheaper" → ...
  "They have more features" → ...
  "We already use them" → ...
```

---

## pricing-strategy

**When to use:** Designing pricing tiers, changing prices, deciding on freemium vs. free trial, or analyzing willingness to pay.

### Before Starting — Gather Context
1. Product type and GTM motion (self-serve vs. sales-led)
2. Target market segment (SMB, mid-market, enterprise)
3. Primary value metric — what does the customer get more of when they pay more?
4. Current pricing (if any) and conversion/churn data
5. Competitor pricing landscape

### Value Metric Selection (Most Important Pricing Decision)
The value metric should: scale with customer value, be easy to understand, and be hard to game.

| Company | Value Metric |
|---------|-------------|
| Slack | Active users (seats) |
| Twilio | API calls / messages |
| Stripe | % of revenue processed |
| Loom | Videos recorded |
| Figma | Editor seats |

### Tier Architecture
- **3 tiers** is the standard: Starter (hook), Growth (target), Enterprise (custom)
- Each tier should have a clear buyer persona
- Middle tier should be 70%+ of revenue — design it first
- Freemium: works when time-to-value is fast and viral coefficient > 0

### Van Westendorp Price Sensitivity Meter
Four questions to find acceptable price range:
1. At what price is it too cheap to trust? (quality concern)
2. At what price is it a bargain? (great deal)
3. At what price is it getting expensive? (worth evaluating alternatives)
4. At what price is it too expensive? (won't buy)

Acceptable range: between "too cheap" and "too expensive"
Optimal price point: intersection of "bargain" and "too expensive" curves

### SaaS Pricing Heuristics
- Land-and-expand: price low to get in, charge more as usage grows
- Annual discount: 15-20% off monthly for annual commitment
- Price increases: raise prices before you run out of money; existing customers grandfathered for 12 months
- Don't compete on price unless you have structural cost advantage

---

---

## product-manager-toolkit

**When to use:** Prioritizing features, running product discovery, writing PRDs, synthesizing customer research, or planning a go-to-market.

### RICE Prioritization
Score each feature: **(Reach × Impact × Confidence) / Effort**

| Factor | Measure |
|--------|---------|
| **Reach** | Users affected per quarter |
| **Impact** | 0.25 (minimal) → 3 (massive) on key metric |
| **Confidence** | % (100% = data-backed, 50% = gut feel) |
| **Effort** | Person-months to build |

Higher RICE score = higher priority. Run quarterly; recalibrate as you learn.

### Customer Interview Analysis
- Record and transcribe (with permission)
- Tag by: problem mentioned, current solution, pain intensity, desired outcome
- Cluster themes across 5+ interviews before drawing conclusions
- Watch for: words customers use repeatedly (use in copy), workarounds they've built (strong pain signal), budget they mention (willingness to pay signal)

### PRD Template
```
# [Feature Name] PRD

## Problem Statement
What user problem are we solving? Evidence?

## Success Metrics
How will we know this worked? (specific, measurable)

## User Stories
As a [persona], I want to [action] so that [outcome]

## Scope
In scope: ...
Out of scope (explicitly): ...

## Design/UX Notes
Link to mockups, key interaction flows

## Technical Notes
Dependencies, constraints, edge cases

## Launch Plan
- Beta: [date], [criteria]
- GA: [date]
- Comms: [email/in-app/blog]
```

### Discovery Frameworks
- **JTBD (Jobs to Be Done)**: "When [situation], I want to [motivation], so I can [outcome]"
- **Problem/Solution fit check**: can you describe the problem in the customer's words before pitching the solution?
- **Opportunity Scoring**: importance × satisfaction gap (Ulwick's ODI framework)

---

## ai-product

**When to use:** Building an LLM-powered product feature — RAG systems, AI chat interfaces, structured output pipelines, or any production LLM integration.

### Core Principle
Demos are easy. Production is hard. Prompts are code — version them, test them, measure them.

### Architecture Decisions
- **When to use RAG vs. fine-tuning**: RAG for dynamic/proprietary data (most cases); fine-tuning for specific output format or tone that prompting can't achieve
- **Structured output**: use function calling / JSON mode + schema validation (Zod, Pydantic) — never parse free text
- **Streaming**: always stream to reduce perceived latency; interrupt handling for long responses
- **Fallbacks**: every LLM call should have: timeout, retry (for rate limits), fallback model, graceful degradation

### Prompt Engineering for Products
```python
# Version prompts in code
PROMPTS = {
    "v1.2": {
        "system": "...",
        "user_template": "...",
    }
}

# Test prompts as CI
def test_prompt_regression(prompt_version):
    results = run_eval_suite(PROMPTS[prompt_version], TEST_CASES)
    assert results.accuracy > 0.92
```

### Cost Optimization
- Cache repeated prompts (same input = same output): 40-80% cost reduction on common queries
- Summarize conversation history instead of sending full context
- Use smaller models for classification/routing, larger for generation
- Token counting before sending: warn users before hitting context limits

### AI UX Principles
- Show confidence indicators — never present LLM output as ground truth
- Provide feedback mechanisms (thumbs up/down) — this is your eval data
- Graceful error states: "I'm not sure about this" > hallucinated confident answer
- Streaming + skeleton states > blank loading screens

### Production Checklist
- [ ] Output validation (schema check, toxicity filter, hallucination detection)
- [ ] Rate limiting per user
- [ ] Cost monitoring and budget alerts
- [ ] Prompt version tracking
- [ ] Eval suite with at least 50 test cases
- [ ] Fallback when LLM is unavailable

---

## ai-wrapper-product

**When to use:** Designing or building a product that wraps an AI API (OpenAI, Anthropic, etc.) into a focused, paid tool.

### The Wrapper Trap — And How to Avoid It
"AI wrapper" gets a bad rap because most are just "ChatGPT but for X." The good ones solve a specific, painful problem where AI is the enabling technology — not the product.

### Differentiation Strategies
1. **Domain-specific context**: train on proprietary data, embed domain knowledge in system prompts
2. **Workflow integration**: connect to tools your user already lives in (Notion, Slack, their CRM)
3. **Output format**: deliver the specific artifact they need (contract, code, design brief) not just text
4. **Speed**: pre-built templates + guided UX → 10 minutes of work in 30 seconds
5. **Trust/verification**: add human review, source citation, fact-checking layer

### Business Model
- Usage-based: works for variable-volume users; difficult to forecast
- Seat-based subscription: predictable; good for team products
- Credits/tokens: creates urgency; appropriate if output is clearly valuable
- Rule of thumb: your margin = (price to user) - (API cost) - (infra) - (support)

### Prompts as Product IP
Your prompts are your moat. Treat them as trade secrets:
- Version in code with semantic versioning
- Never expose raw system prompt to users
- A/B test like copy — small wording changes = large quality differences

---

## micro-saas-launcher

**When to use:** Launching a small, focused SaaS product — indie hacker or solo founder style. Idea to paying customers in weeks, not months.

### The Indie Hacker Validation Protocol
**Before writing a single line of code:**
1. Find 10 people who match your ICP
2. Describe the problem (not the solution) and ask if they have it
3. If yes: "How are you solving it?" and "What would you pay to solve it better?"
4. Pre-sell: "I'm building this. Would you pay $X/month? Here's my Stripe link."
5. If 3+ people pay: build. If not: pivot the idea, not the effort.

### Solo Founder Tech Stack (optimize for speed, not scale)
- **Frontend**: Next.js (full-stack in one repo)
- **Database**: Neon or Supabase (serverless Postgres, free tier)
- **Auth**: Clerk or Supabase Auth
- **Payments**: Stripe (subscriptions + one-time)
- **Email**: Resend + React Email
- **Hosting**: Vercel (zero-config deploys)
- **Analytics**: Plausible (privacy-friendly, simple)

### MVP Scoping Rules
- One core job-to-be-done, done exceptionally well
- 3-week build target for MVP — if it's longer, cut features
- No admin dashboard until you have 10 paying customers
- No mobile app until web is profitable

### Launch Channels (week 1)
1. Your network: personal email + LinkedIn post
2. Reddit: relevant subreddits where your ICP hangs out (no spam, add value first)
3. Product Hunt: coordinate upvotes, post Tuesday-Thursday 12:01am PT
4. Hacker News: "Show HN" post when you have something polished
5. Indie Hackers: post your story in progress

### SaaS Metrics to Track from Day 1
| Metric | Target |
|--------|--------|
| MRR growth | 10-20% MoM in early stage |
| Churn rate | < 5% monthly |
| Trial → Paid conversion | > 15% |
| Payback period | < 12 months |

---

---

## seo-audit

**When to use:** Diagnosing why a site isn't ranking, identifying technical SEO issues, auditing on-page optimization, or checking crawlability and indexation.

### Audit Priority Order
1. **Crawlability & Indexation** — Can Google find and index the site?
   - Check `robots.txt` — is anything important blocked?
   - Verify `sitemap.xml` exists and is submitted to Search Console
   - Check for `noindex` tags on pages that should rank
   - Crawl budget issues on large sites

2. **Technical Foundations**
   - Core Web Vitals (LCP < 2.5s, INP < 200ms, CLS < 0.1)
   - Mobile responsiveness
   - HTTPS — no mixed content
   - Canonical tags — no duplicate content issues
   - Site speed: measure with PageSpeed Insights and GTmetrix

3. **On-Page Optimization**
   - Title tags: unique, < 60 chars, primary keyword near front
   - Meta descriptions: unique, compelling, < 160 chars
   - H1: one per page, contains primary keyword
   - Internal linking: pages should be linked from relevant content
   - Image alt text: descriptive, not keyword-stuffed

4. **Content Quality**
   - E-E-A-T signals: author credentials, original research, citations
   - Thin content: pages with < 300 words that provide no unique value
   - Keyword cannibalization: multiple pages targeting same keyword
   - Content freshness: stale content on time-sensitive topics

5. **Authority**
   - Backlink profile: spam links, toxic domains
   - Missing opportunities: unlinked brand mentions

### Quick Wins Checklist
- [ ] Title tags are unique and keyword-rich
- [ ] Core Web Vitals pass (use Search Console → Core Web Vitals report)
- [ ] No broken internal links
- [ ] Sitemap submitted and all important pages indexed
- [ ] No duplicate content (use canonical tags or 301 redirects)

---

## seo-fundamentals

**When to use:** Understanding SEO principles, explaining how Google ranks content, or grounding SEO work in foundational concepts.

### E-E-A-T Framework (Google's quality signal)
| Principle | What it means | How to signal it |
|-----------|---------------|-----------------|
| **Experience** | First-hand knowledge | Case studies, personal examples, original data |
| **Expertise** | Deep domain knowledge | Author credentials, detailed content, cited sources |
| **Authoritativeness** | Industry recognition | Backlinks, mentions, industry awards |
| **Trustworthiness** | Accuracy and transparency | HTTPS, clear authorship, factual accuracy |

### Core Web Vitals
| Metric | Good | What it Measures |
|--------|------|-----------------|
| LCP (Largest Contentful Paint) | < 2.5s | Loading speed of main content |
| INP (Interaction to Next Paint) | < 200ms | Responsiveness to user input |
| CLS (Cumulative Layout Shift) | < 0.1 | Visual stability (no jumping content) |

### The Long Game
SEO is compounding — early investment pays off for years. Prioritize:
1. Content that answers questions your ICP is actually searching
2. Technical hygiene so Google can crawl everything
3. Internal linking to pass authority to important pages
4. Earning backlinks through genuinely useful resources

---

## programmatic-seo

**When to use:** Building SEO-optimized pages at scale — directory pages, location pages, comparison pages, integration pages, or any template-driven approach.

### Core Principle: Every Page Must Earn Its Existence
Google penalizes thin programmatic content. Each page needs unique value:
- Unique data (not just template variables swapped)
- Useful information specific to that page's topic
- Meaningful differentiation from other pages in the set

### Page Type Playbook
| Type | Example | Data Source |
|------|---------|-------------|
| Location pages | "[Service] in [City]" | Location data + local content |
| Comparison | "[A] vs [B]" | Feature data + pricing |
| Integration | "[Tool] + [Tool]" | API docs + use cases |
| Directory | "Best [Category] tools" | Curated database |
| Data-driven | "[Metric] for [Industry]" | Proprietary data |

### Implementation Checklist
- [ ] Each page has at least 300 words of unique content
- [ ] Dynamic meta titles and descriptions per page
- [ ] Canonical tags on paginated sets
- [ ] Internal links connecting related pages
- [ ] A robots.txt that allows crawling
- [ ] No duplicate H1 tags
- [ ] Schema markup (LocalBusiness, Product, FAQPage as appropriate)

---

## geo-fundamentals

**When to use:** Optimizing content to be cited in AI-generated answers (ChatGPT, Claude, Perplexity, Gemini), also called AI SEO or Generative Engine Optimization.

### How GEO Differs from Traditional SEO
- Traditional SEO: rank in a link list
- GEO: be cited or referenced within an AI-generated answer
- Trust signal shift: AI models favor content that sounds authoritative, cites sources, and is structured for scanning

### GEO Optimization Tactics
1. **Structured, factual content**: AI models extract clean facts. Use tables, numbered lists, clear definitions.
2. **Cite sources**: include links to authoritative primary sources — models trust content that references external data
3. **Answer the question directly**: start with the answer, then elaborate (inverted pyramid)
4. **Schema markup**: FAQ schema, HowTo schema increase extraction likelihood
5. **Brand mentions**: get mentioned on Wikipedia, Reddit, industry publications — models train on these
6. **Define your category**: create content that establishes your brand as the definition of a category

### Monitoring
- Track AI search referral traffic (currently limited; improving)
- Search your brand name in ChatGPT/Perplexity monthly
- Monitor for brand misrepresentation in AI answers

---

## launch-strategy

**When to use:** Planning a product launch, feature release, or go-to-market campaign from early access through full release.

### Core Philosophy
The best companies launch repeatedly — every feature, update, and milestone is a launch opportunity. Build a launch machine, not a launch event.

### The ORB Framework
Every launch should drive traffic back to **Owned** channels:
- **Owned**: email list, in-app notifications, blog, social following
- **Rented**: Product Hunt, Hacker News, Reddit, press (you don't control these)
- **Borrowed**: partnerships, influencers, integrations, co-marketing

### Phased Launch Playbook
**Phase 1 — Beta (4-6 weeks pre-launch)**
- Recruit 20-50 power users from your network
- Gather feedback, fix critical issues
- Build social proof: testimonials, case studies, usage stats

**Phase 2 — Early Access (2 weeks pre-launch)**
- Open waitlist, build anticipation
- Content: behind-the-scenes, launch countdown
- Brief press/influencers with embargo

**Phase 3 — Launch Day**
- Product Hunt submission (post at 12:01am PT Tuesday-Thursday)
- Email blast to full list
- Social push (founders post personally — outperforms brand accounts)
- Engage every comment and reply within the first 4 hours

**Phase 4 — Post-Launch Momentum (weeks 2-4)**
- "Made with [Product]" content from users
- Retrospective blog post ("what we learned building X")
- Follow-up to all press that didn't cover the launch

---

## referral-program

**When to use:** Designing or optimizing a customer referral program, affiliate program, or word-of-mouth growth strategy.

### When Referral Works
Referral programs succeed when: NPS > 50, product is genuinely shareable, and there's a clear incentive that feels valuable (not just a discount).

### Program Types
| Type | Best For | Example Incentive |
|------|----------|------------------|
| **Customer referral** | B2C, PLG products | Account credits, free months |
| **Affiliate** | B2B, higher ACV | Cash commission (15-30% MRR) |
| **Ambassador** | Community-driven | Status, early access, swag |

### Incentive Design Rules
- Two-sided reward (both referrer and referee) consistently outperforms one-sided
- Recurring incentive (% of their bill each month) > one-time reward for high-churn products
- Cash > credits for affiliates (they can't use your credits for coffee)
- Minimum LTV threshold before paying out — prevent fraud and churned referrals

### Program Mechanics
1. Unique referral link per user (track source)
2. Landing page that mentions the program (increase organic word-of-mouth)
3. Automated reward fulfillment (don't do this manually past 50 users)
4. Fraud prevention: minimum paid tenure before reward pays out
5. Dashboard for referrers to see their earnings/credits

---

---

## salesforce-dev

**When to use:** Building Salesforce platform features — Lightning Web Components, Apex triggers, custom APIs, managed packages, or Salesforce DX workflows.

### Core Coverage
- **LWC (Lightning Web Components)**: `@wire` for reactive data, `@api` for parent-child props, `@track` for reactive private props
- **Apex**: bulkified triggers (handle 200+ records), trigger handler pattern, queueable for async processing, `@future` for callouts from triggers
- **APIs**: REST API (record CRUD), Bulk API (mass operations), Streaming API (real-time events)
- **Salesforce DX**: scratch orgs for dev, source control with SFDX project structure, 2nd generation packages (2GP)
- **Connected Apps**: OAuth flows for external integrations

### Bulkified Apex Rule
Every Apex trigger must handle 200+ records per transaction. Never put SOQL queries or DML inside loops.

```apex
// ❌ SOQL in loop
trigger AccountTrigger on Account (before update) {
    for(Account acc : Trigger.new) {
        List<Contact> contacts = [SELECT Id FROM Contact WHERE AccountId = :acc.Id];
    }
}

// ✅ Bulk query outside loop
trigger AccountTrigger on Account (before update) {
    Set<Id> accountIds = Trigger.newMap.keySet();
    Map<Id, List<Contact>> contactsByAccount = new Map<Id, List<Contact>>();
    for(Contact c : [SELECT Id, AccountId FROM Contact WHERE AccountId IN :accountIds]) {
        if(!contactsByAccount.containsKey(c.AccountId)) contactsByAccount.put(c.AccountId, new List<Contact>());
        contactsByAccount.get(c.AccountId).add(c);
    }
}
```

---

## hubspot-integration

**When to use:** Integrating with HubSpot CRM — contact/deal management, OAuth apps, webhook handling, or syncing external data.

### Core Coverage
- **Auth**: OAuth 2.0 for public apps (3-legged), Private App tokens for single-account use
- **CRM Objects**: Contacts, Companies, Deals, Tickets — CRUD via REST API
- **Associations**: link objects (contact ↔ deal, company ↔ contact) with association types
- **Webhooks**: subscribe to object property changes, deal stage transitions, contact creation
- **Batch operations**: batch create/update up to 100 records per call

### SDK Usage (Node.js)
```javascript
const hubspot = require('@hubspot/api-client');
const client = new hubspot.Client({ accessToken: process.env.HUBSPOT_TOKEN });

// Create contact
const contact = await client.crm.contacts.basicApi.create({
  properties: { email: 'user@example.com', firstname: 'Jane' }
});

// Search contacts
const results = await client.crm.contacts.searchApi.doSearch({
  filterGroups: [{ filters: [{ propertyName: 'email', operator: 'EQ', value: 'user@example.com' }] }]
});
```

---

## segment-cdp

**When to use:** Implementing Segment for customer data tracking, setting up tracking plans, routing data to analytics destinations, or resolving user identity.

### Core Calls
```javascript
// Identify a user
analytics.identify('user-123', { email: 'user@example.com', plan: 'pro' });

// Track an event
analytics.track('Subscription Started', { plan: 'pro', mrr: 99, trial_days: 14 });

// Page view
analytics.page('Pricing', { url: window.location.href });

// Group (account-level)
analytics.group('account-456', { name: 'Acme Corp', employees: 50 });
```

### Tracking Plan Discipline
- Every event has a spec: name, properties, when it fires, who triggers it
- Use `Protocols` to enforce schema — reject events that don't match spec
- Event naming: `Object Action` format → `Subscription Started`, `Report Downloaded`, `Payment Failed`

### Identity Resolution
- Anonymous ID persists across sessions until `identify()` is called
- Server-side `identify` on signup to merge anonymous session with user ID
- `alias()` call to merge anonymous and identified user in some destinations

---

---

## saas-metrics

**When to use:** Measuring SaaS business health, setting growth targets, understanding unit economics, or preparing metrics for investors.

### The Core SaaS Dashboard

**Revenue Metrics**
| Metric | Formula | Healthy Target |
|--------|---------|---------------|
| MRR | Sum of all monthly recurring revenue | — |
| ARR | MRR × 12 | — |
| MRR Growth | (This month MRR - Last month MRR) / Last month MRR | 10-20% early stage |
| Net Revenue Retention | (Starting MRR + expansion - contraction - churn) / Starting MRR | > 100% |

**Customer Metrics**
| Metric | Formula | Healthy Target |
|--------|---------|---------------|
| Churn Rate | Churned customers / Starting customers | < 2% monthly SMB, < 0.5% enterprise |
| CAC | Sales + Marketing spend / New customers | — |
| LTV | ARPU / Churn rate | LTV/CAC > 3:1 |
| Payback Period | CAC / (ARPU × Gross Margin) | < 12 months |

**Funnel Metrics**
| Metric | Healthy Benchmark |
|--------|------------------|
| Trial → Paid conversion | > 15-25% |
| Lead → Trial | > 5-10% |
| Visitor → Lead | > 2-5% |

### The Rule of 40
For evaluating SaaS health: Revenue Growth Rate + Profit Margin ≥ 40%.
Early stage companies can sacrifice margin for growth; mature companies need balance.

### Cohort Analysis
Track monthly cohorts of new customers. Measure: what % are still paying at month 1, 3, 6, 12? Flattening retention curve = product-market fit signal.

---

## hr-workflows

**When to use:** Hiring, writing job descriptions, structuring interviews, building onboarding plans, or managing compensation.

### Job Description Template
```
[Title] at [Company]

About us (3-4 sentences, honest, no corporate speak)

What you'll do (bullet list, outcomes not tasks)
- Not "attend standups" — "ship X new features per quarter"
- Not "collaborate with team" — "own the ML pipeline end-to-end"

What you'll need (required vs. nice-to-have, be honest about each)

Compensation (publish the range — candidates skip opaque JDs)

How we work (remote/hybrid, timezone, team size, stack)
```

### Interview Framework (Structured Interviews)
- Same questions, same order for every candidate (reduces bias)
- Behavioral questions: "Tell me about a time when..." (past behavior predicts future)
- Work sample: small paid test or portfolio review for final-stage candidates
- Scorecard: defined criteria rated before debriefing as a group

### 30/60/90 Day Onboarding Framework
- **Day 1-30**: Learn — understand the product, team, codebase, customers. No major independent decisions.
- **Day 31-60**: Contribute — own small, scoped projects. First real deliverables.
- **Day 61-90**: Lead — take ownership of a domain. Propose improvements. Demonstrate judgment.

### Compensation Principles
- Publish ranges in JDs (top candidates won't apply to opaque ranges)
- Benchmark to market data (Levels.fyi, Radford, Carta Compensation)
- Equity: document vesting schedule, cliff, exercise window clearly in offer
- Pay for the role, not the person's negotiating ability

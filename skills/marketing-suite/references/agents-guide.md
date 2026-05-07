# Marketing Suite — Specialist Agents Guide

Use these agents when running in Claude Code or Cowork (environments with subagent support). In Claude.ai, use these as role descriptions to adopt before executing tasks.

---

## How to Use Agents

**In Claude Code / Cowork**: Delegate tasks to specialist agents in parallel for complex campaigns.

**In Claude.ai**: Adopt the agent's persona/expertise before tackling the relevant task. Example: "Acting as a conversion copywriter..." then apply the copywriter instructions.

---

## Agent Directory

### copywriter
**Expertise**: High-converting marketing copy — landing pages, emails, social, ads
**Use when**: Any writing task where the goal is to persuade or convert
**Activate for**: Homepage, landing page, email sequences, ad copy, social posts

### seo-specialist  
**Expertise**: Organic search strategy, keyword research, on-page optimization, link building
**Use when**: Ranking content, auditing existing pages, building content strategy
**Activate for**: Keyword research, meta tags, content briefs, technical SEO guidance

### conversion-optimizer
**Expertise**: CRO — turning traffic into leads and customers
**Use when**: Improving conversion rates on any page or flow
**Activate for**: Landing page audits, signup flow review, paywall optimization, A/B test design

### email-wizard
**Expertise**: Email sequences, deliverability, automation architecture
**Use when**: Building any email system — welcome, nurture, re-engagement, lifecycle
**Activate for**: Sequence strategy, individual email writing, deliverability troubleshooting

### researcher
**Expertise**: Market research, competitive intelligence, audience analysis
**Use when**: Need to understand market context before executing
**Activate for**: Competitor analysis, customer personas, trend research, keyword discovery

### brand-voice-guardian
**Expertise**: Brand consistency, voice and tone, messaging architecture
**Use when**: Creating content that must align with brand guidelines
**Activate for**: Brand audits, voice/tone documentation, cross-asset consistency review

### brainstormer
**Expertise**: Creative ideation, campaign concepts, growth ideas
**Use when**: Stuck on direction, need fresh angles, exploring possibilities
**Activate for**: Campaign concept ideation, growth hacking ideas, content angle brainstorming

### persona-builder
**Expertise**: Building detailed ICPs and buyer personas from research
**Use when**: Need to define or refine who you're marketing to
**Activate for**: ICP documentation, persona creation, audience segmentation

### lead-qualifier
**Expertise**: Lead scoring, qualification criteria, sales handoff
**Use when**: Defining what makes a good lead and how to attract more of them
**Activate for**: Scoring model design, MQL/SQL criteria, audience targeting strategy

### attraction-specialist
**Expertise**: Top-of-funnel traffic acquisition across all channels
**Use when**: Need to grow awareness and drive new traffic
**Activate for**: Channel strategy, SEO planning, content promotion, PR/media outreach

### continuity-specialist
**Expertise**: Retention, lifecycle marketing, reducing churn
**Use when**: Keeping existing customers engaged and paying
**Activate for**: Retention email design, churn analysis, lifecycle trigger mapping

### upsell-maximizer
**Expertise**: Revenue expansion — upsells, cross-sells, plan upgrades
**Use when**: Growing revenue from existing customer base
**Activate for**: Paywall design, upgrade email sequences, pricing page optimization

### sales-enabler
**Expertise**: Sales collateral — decks, battlecards, scripts, one-pagers
**Use when**: Helping sales close more deals
**Activate for**: Pitch deck creation, objection handling, competitive battlecards

### planner
**Expertise**: Campaign planning, project management, resource coordination
**Use when**: Coordinating complex multi-asset, multi-channel campaigns
**Activate for**: Campaign calendars, launch checklists, quarterly plans

### project-manager
**Expertise**: Task breakdown, timelines, execution tracking
**Use when**: Turning strategy into actionable tasks with owners and deadlines
**Activate for**: Project planning, kickoff documents, status reports

### solopreneur
**Expertise**: High-leverage, low-resource marketing for small teams
**Use when**: Limited resources require maximum ROI on marketing efforts
**Activate for**: Prioritization decisions, lean channel strategy, bootstrap marketing

### startup-founder
**Expertise**: Early-stage growth, founder-led marketing, product-market fit messaging
**Use when**: Pre-product-market-fit or early growth stage
**Activate for**: Early-stage positioning, founder story, community-led growth

### docs-manager
**Expertise**: Marketing documentation, knowledge management
**Use when**: Creating/maintaining brand guidelines, playbooks, SOPs
**Activate for**: Brand book creation, process documentation, onboarding guides

### mcp-manager
**Expertise**: Coordinating marketing tool integrations via MCP servers
**Use when**: Connecting data between marketing tools
**Activate for**: HubSpot workflows, GA4 queries, Slack/Asana task creation

### command-helper
**Expertise**: Guiding users through available commands and capabilities
**Use when**: User isn't sure what's possible or how to ask
**Activate for**: Onboarding new users, capability discovery, help documentation

---

## Multi-Agent Workflows

### Full Campaign (4 agents in parallel)
1. **researcher** → Market and competitor analysis
2. **persona-builder** → ICP documentation
3. **attraction-specialist** → Channel strategy
4. **brainstormer** → Campaign concepts

Then sequentially:
5. **copywriter** → All copy assets
6. **conversion-optimizer** → CRO review
7. **planner** → Launch calendar

### Content Sprint (3 agents)
1. **researcher** → Keyword and topic research
2. **copywriter** → Draft all content
3. **brand-voice-guardian** → Consistency review

### Email Program Build (3 agents)
1. **persona-builder** → Segment definitions
2. **email-wizard** → Sequence architecture
3. **copywriter** → All email copy

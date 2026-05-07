---
name: all-marketing
description: "Full-spectrum marketing and SEO skill library with 160+ specialist skills. Use for any marketing task — SEO (technical, on-page, content, off-page, local, programmatic, entity), content creation, paid ads (Google, Meta, LinkedIn, TikTok, YouTube, Reddit, CTV, display, native), web pages (landing, pricing, homepage, blog, docs, features, FAQ, legal, utility), web components (hero, nav, CTA, testimonials, popups, breadcrumb), channels (email, affiliate, influencer, referral, PR, community), platforms (Reddit, LinkedIn, TikTok, YouTube, X, Medium, GitHub), strategies (GTM, cold start, product launch, branding, PMF, retention, growth funnel, pricing, localization, GEO), and analytics (GA4, Search Console, rank tracking). Use whenever user mentions robots.txt, sitemap, canonical, Core Web Vitals, schema markup, keyword research, link building, copywriting, landing page, cold start, Product Hunt, SEO audit, content strategy, social media, or any marketing/SEO topic."
---

# Marketing & SEO Skills Library

A library of 160+ specialist skills covering every domain of digital marketing. Each skill is a focused SKILL.md with frameworks, workflows, and production-ready guidance.

## How to Use

1. **Identify the right skill(s)** — match the user's request to one or more skills in the routing table below. When in doubt, check the "Key triggers" column.
2. **Read the sub-skill** — use the Read tool on the path `skills/<skill-path>.md` (relative to this file's directory).
3. **Apply it** — follow the sub-skill's instructions to complete the task.
4. **Chain skills** — for multi-step work, read related skills in dependency order (e.g., technical SEO → on-page → content).

**Project context**: Always check whether `project-context.md` exists in `.claude/` or `.cursor/` before running any skill. Sub-skills read it automatically for tailored output. Prompt the user to fill one in if they haven't already.

**Skip intro**: If the user says "skip intro" or "just do it," go straight to the actionable output — skip preamble.

---

## Routing Table

### SEO — Technical

| Skill | Path | Key triggers |
|-------|------|--------------|
| robots-txt | `skills/seo/technical/robots.md` | robots.txt, AI crawlers, Googlebot, crawl rules, disallow |
| xml-sitemap | `skills/seo/technical/sitemap.md` | sitemap.xml, XML sitemap, sitemap index, sitemap submission |
| canonical-tag | `skills/seo/technical/canonical.md` | canonical, duplicate content, canonical URL, self-referencing |
| indexing | `skills/seo/technical/indexing.md` | indexing issues, noindex, de-index, Search Console coverage |
| indexnow | `skills/seo/technical/indexnow.md` | IndexNow, Bing indexing, faster indexing, real-time crawl |
| site-crawlability | `skills/seo/technical/crawlability.md` | crawlability, redirect chains, broken links, orphan pages, pagination |
| core-web-vitals | `skills/seo/technical/core-web-vitals.md` | Core Web Vitals, LCP, INP, CLS, page speed, PageSpeed Insights |
| mobile-friendly | `skills/seo/technical/mobile-friendly.md` | mobile-first indexing, mobile usability, viewport, touch targets |
| rendering-strategies | `skills/seo/technical/rendering-strategies.md` | SSR, SSG, CSR, ISR, server-side rendering, JavaScript SEO |

### SEO — On-Page

| Skill | Path | Key triggers |
|-------|------|--------------|
| title-tag | `skills/seo/on-page/title.md` | title tag, page title, `<title>`, SERP title, title optimization |
| meta-description | `skills/seo/on-page/description.md` | meta description, SERP snippet, click-through rate, description tag |
| featured-snippet | `skills/seo/on-page/featured-snippet.md` | featured snippet, position zero, answer box, rich snippet |
| serp-features | `skills/seo/on-page/serp-features.md` | SERP features, People Also Ask, knowledge panel, rich results |
| page-metadata | `skills/seo/on-page/metadata.md` | hreflang, meta robots, charset, viewport meta, page metadata |
| open-graph | `skills/seo/on-page/open-graph.md` | Open Graph, OG tags, og:title, og:image, social sharing preview |
| twitter-cards | `skills/seo/on-page/twitter-cards.md` | Twitter Card, X card, summary card, large image card |
| schema-markup | `skills/seo/on-page/schema.md` | schema markup, structured data, JSON-LD, Schema.org, rich results |
| internal-links | `skills/seo/on-page/internal-links.md` | internal links, link equity, anchor text, silo structure |
| url-structure | `skills/seo/on-page/url-structure.md` | URL structure, URL slug, URL hierarchy, permalink, URL optimization |
| heading-structure | `skills/seo/on-page/heading.md` | headings, H1, H2, H3, heading hierarchy, heading optimization |
| image-optimization | `skills/seo/on-page/image-optimization.md` | image SEO, alt text, WebP, image compression, LCP image, lazy loading |
| video-optimization | `skills/seo/on-page/video-optimization.md` | video SEO, VideoObject schema, video sitemap, video thumbnail |

### SEO — Content, Off-Page, Tactics

| Skill | Path | Key triggers |
|-------|------|--------------|
| keyword-research | `skills/seo/content/keyword-research.md` | keyword research, search intent, keyword difficulty, keyword volume |
| content-strategy | `skills/seo/content/content-strategy.md` | content strategy, content clusters, pillar pages, topic clusters |
| content-optimization | `skills/seo/content/content-optimization.md` | content optimization, word count, keyword density, content gaps |
| eeat-signals | `skills/seo/content/eeat-signals.md` | E-E-A-T, author bio, trust signals, YMYL, expertise, authority |
| competitor-research | `skills/seo/content/competitor-research.md` | competitor research, competitor SEO, content gap, SERP competitor |
| link-building | `skills/seo/off-page/link-building.md` | link building, backlink acquisition, outreach, guest posting, HARO |
| backlink-analysis | `skills/seo/off-page/backlink-analysis.md` | backlink audit, toxic links, disavow, backlink profile, Ahrefs |
| local-seo | `skills/seo/local.md` | local SEO, Google Business Profile, NAP, local citations, GMB |
| entity-seo | `skills/seo/entity-seo.md` | entity SEO, Knowledge Graph, Knowledge Panel, Organization schema |
| parasite-seo | `skills/seo/parasite-seo.md` | parasite SEO, Medium SEO, Reddit SEO, Grokipedia, high-authority platforms |
| programmatic-seo | `skills/seo/programmatic-seo.md` | programmatic SEO, template pages, data-driven pages, pages at scale |
| seo-strategy | `skills/strategies/seo.md` | SEO strategy, SEO plan, SEO roadmap, where to start SEO, SEO workflow |

### Content

| Skill | Path | Key triggers |
|-------|------|--------------|
| copywriting | `skills/content/copywriting.md` | copywriting, headlines, CTAs, ad copy, AIDA, PAS, landing page copy |
| video-marketing | `skills/content/video.md` | video script, video marketing, short-form video, YouTube script, hooks |
| visual-content | `skills/content/visual-content.md` | visual content, infographics, social images, image planning, repurposing |
| translation | `skills/content/translation.md` | translation, localization content, glossary, human vs machine translation |

### Paid Ads

| Skill | Path | Key triggers |
|-------|------|--------------|
| google-ads | `skills/paid-ads/google-ads.md` | Google Ads, Search ads, PPC, Quality Score, Performance Max, Google CPC |
| meta-ads | `skills/paid-ads/meta-ads.md` | Meta ads, Facebook ads, Instagram ads, lookalike audience, Facebook pixel |
| linkedin-ads | `skills/paid-ads/linkedin-ads.md` | LinkedIn ads, B2B ads, Lead Gen Forms, LinkedIn sponsored content |
| reddit-ads | `skills/paid-ads/reddit-ads.md` | Reddit ads, subreddit targeting, Promoted Posts, Reddit advertising |
| tiktok-ads | `skills/paid-ads/tiktok-ads.md` | TikTok ads, Spark Ads, TikTok creative, video ads younger audience |
| youtube-ads | `skills/paid-ads/youtube-ads.md` | YouTube ads, TrueView, Bumper ads, video ad campaign |
| app-ads | `skills/paid-ads/app-ads.md` | app install ads, Google App Campaigns, Apple Search Ads, CPI, UAC |
| ctv-ads | `skills/paid-ads/ctv-ads.md` | CTV, OTT, streaming TV ads, Hulu, Roku, connected TV advertising |
| display-ads | `skills/paid-ads/display-ads.md` | display ads, banner ads, programmatic display, ad network, CPM |
| native-ads | `skills/paid-ads/native-ads.md` | native ads, Taboola, Outbrain, content recommendation, sponsored content |
| directory-listing-ads | `skills/paid-ads/directory-listing-ads.md` | G2 ads, Capterra ads, Taaft sponsored, directory paid placement |
| paid-ads-strategy | `skills/strategies/paid-ads.md` | paid ads strategy, channel selection, ad budget, when to use ads, ROAS |

### Pages — Brand

| Skill | Path | Key triggers |
|-------|------|--------------|
| home-page | `skills/pages/brand/home.md` | homepage, home page, website homepage, homepage design |
| about-page | `skills/pages/brand/about.md` | about page, about us, company story, team page |
| contact-page | `skills/pages/brand/contact.md` | contact page, contact form, get in touch page |

### Pages — Content

| Skill | Path | Key triggers |
|-------|------|--------------|
| blog-page | `skills/pages/content/blog.md` | blog page, blog index, blog listing, article list page |
| article-page | `skills/pages/content/article.md` | blog post, article page, editorial content, post template |
| faq-page | `skills/pages/content/faq.md` | FAQ page, frequently asked questions, FAQ section |
| docs-page | `skills/pages/content/docs.md` | documentation page, docs, product docs, help center |
| features-page | `skills/pages/content/features.md` | features page, product features, feature list, feature comparison |
| glossary-page | `skills/pages/content/glossary.md` | glossary, glossary page, terms dictionary, definitions page |
| resources-page | `skills/pages/content/resources.md` | resources page, resource hub, content library, resource center |
| tools-page | `skills/pages/content/tools.md` | tools page, free tools, tool directory, calculator page |
| template-page | `skills/pages/content/template-page.md` | template page, page template, programmatic page template |
| api-page | `skills/pages/content/api.md` | API page, API docs page, API reference page, developer page |

### Pages — Marketing

| Skill | Path | Key triggers |
|-------|------|--------------|
| landing-page | `skills/pages/marketing/landing-page.md` | landing page, PPC landing page, conversion page, lead capture page |
| pricing-page | `skills/pages/marketing/pricing.md` | pricing page, pricing table, pricing tiers, plans page |
| alternatives-page | `skills/pages/marketing/alternatives.md` | alternatives page, competitor alternative, vs page, best alternative to |
| use-cases-page | `skills/pages/marketing/use-cases.md` | use cases page, use case, how it's used, use case examples |
| solutions-page | `skills/pages/marketing/solutions.md` | solutions page, solution for X, solutions by role/industry |
| integrations-page | `skills/pages/marketing/integrations.md` | integrations page, integration directory, connects with |
| customer-stories | `skills/pages/marketing/customer-stories.md` | customer stories, case studies, testimonial page, success stories |
| products-page | `skills/pages/marketing/products.md` | products page, product catalog, product listing, product directory |
| services-page | `skills/pages/marketing/services.md` | services page, our services, service offering, service detail |
| affiliate-program-page | `skills/pages/marketing/affiliate-program.md` | affiliate program page, become an affiliate, partner program page |
| migration-page | `skills/pages/marketing/migration.md` | migration page, switch from X, migrate from competitor |
| category-pages | `skills/pages/marketing/category-pages.md` | category page, category landing, taxonomy page, hub page |
| contest-page | `skills/pages/marketing/contest.md` | contest page, giveaway page, sweepstakes, competition page |
| download-page | `skills/pages/marketing/download.md` | download page, app download, get the app, download CTA |
| media-kit-page | `skills/pages/marketing/media-kit.md` | media kit, press kit, brand assets page, media resources |
| press-coverage-page | `skills/pages/marketing/press-coverage.md` | press page, press coverage, as seen in, media mentions |
| showcase-page | `skills/pages/marketing/showcase.md` | showcase page, gallery, customer showcase, examples gallery |
| startups-page | `skills/pages/marketing/startups.md` | startups page, for startups, startup program, startup offer |

### Pages — Legal

| Skill | Path | Key triggers |
|-------|------|--------------|
| privacy-policy | `skills/pages/legal/privacy.md` | privacy policy, data privacy, GDPR, CCPA, privacy notice |
| terms-of-service | `skills/pages/legal/terms.md` | terms of service, ToS, terms and conditions, user agreement |
| cookie-policy | `skills/pages/legal/cookie-policy.md` | cookie policy, cookie consent, cookie notice, GDPR cookies |
| refund-policy | `skills/pages/legal/refund.md` | refund policy, return policy, money back guarantee |
| shipping-policy | `skills/pages/legal/shipping.md` | shipping policy, delivery policy, shipping rates |
| legal-page | `skills/pages/legal/legal.md` | legal page, legal notices, disclaimer, legal hub |

### Pages — Utility

| Skill | Path | Key triggers |
|-------|------|--------------|
| 404-page | `skills/pages/utility/404.md` | 404 page, error page, not found page, broken link page |
| careers-page | `skills/pages/utility/careers.md` | careers page, jobs page, we're hiring, open positions |
| changelog-page | `skills/pages/utility/changelog.md` | changelog, release notes, what's new, version history |
| status-page | `skills/pages/utility/status.md` | status page, system status, uptime page, incident page |
| signup-login-page | `skills/pages/utility/signup-login.md` | signup page, login page, register page, auth page |
| feedback-page | `skills/pages/utility/feedback.md` | feedback page, feature request, send feedback, user feedback |
| disclosure-page | `skills/pages/utility/disclosure.md` | disclosure page, affiliate disclosure, sponsored content disclosure |

### Components — Branding

| Skill | Path | Key triggers |
|-------|------|--------------|
| hero-section | `skills/components/branding/hero.md` | hero section, hero banner, above the fold, hero headline |
| logo | `skills/components/branding/logo.md` | logo, logomark, wordmark, logo design, brand logo |
| favicon | `skills/components/branding/favicon.md` | favicon, site icon, tab icon, browser icon, apple touch icon |
| brand-visual | `skills/components/branding/brand-visual.md` | brand visual, visual identity, brand style guide, color palette, typography |

### Components — Conversion

| Skill | Path | Key triggers |
|-------|------|--------------|
| cta | `skills/components/conversion/cta.md` | CTA, call to action, button copy, CTA button, conversion button |
| testimonials | `skills/components/conversion/testimonials.md` | testimonials, reviews section, social proof, customer quotes |
| trust-badges | `skills/components/conversion/trust-badges.md` | trust badges, trust signals, security badges, certifications |
| newsletter-signup | `skills/components/conversion/newsletter-signup.md` | newsletter signup, email capture, subscribe form, email opt-in |
| popup | `skills/components/conversion/popup.md` | popup, modal, exit-intent popup, overlay, lightbox |

### Components — Navigation

| Skill | Path | Key triggers |
|-------|------|--------------|
| navigation-menu | `skills/components/navigation/navigation-menu.md` | navigation menu, nav bar, main menu, header navigation |
| footer | `skills/components/navigation/footer.md` | footer, site footer, footer links, footer design |
| breadcrumb | `skills/components/navigation/breadcrumb.md` | breadcrumb, breadcrumb trail, breadcrumb schema, breadcrumb navigation |
| sidebar | `skills/components/navigation/sidebar.md` | sidebar, sidebar navigation, side nav, sticky sidebar |
| toc | `skills/components/navigation/toc.md` | table of contents, TOC, page navigation, jump links, anchor links |

### Components — Layout & Utility

| Skill | Path | Key triggers |
|-------|------|--------------|
| card | `skills/components/layout/card.md` | card component, content card, feature card, pricing card |
| carousel | `skills/components/layout/carousel.md` | carousel, image slider, content slider, slideshow |
| grid | `skills/components/layout/grid.md` | grid layout, content grid, CSS grid, photo grid |
| list | `skills/components/layout/list.md` | list component, feature list, icon list, checklist component |
| masonry | `skills/components/layout/masonry.md` | masonry layout, Pinterest layout, masonry grid |
| tab-accordion | `skills/components/content/tab-accordion.md` | tabs, accordion, tab component, expandable section |
| social-share | `skills/components/utility/social-share.md` | social share, share buttons, share widget, share links |
| top-banner | `skills/components/utility/top-banner.md` | top banner, announcement bar, sticky banner, notification bar |
| url-slug | `skills/components/utility/url-slug.md` | URL slug, slug generator, URL-friendly string |

### Marketing Channels

| Skill | Path | Key triggers |
|-------|------|--------------|
| email-marketing | `skills/channels/email-marketing.md` | email marketing, email campaign, newsletter, drip campaign, email list |
| affiliate | `skills/channels/affiliate.md` | affiliate marketing, affiliate program, affiliate channel, commission |
| influencer | `skills/channels/influencer.md` | influencer marketing, influencer outreach, creator partnership |
| referral | `skills/channels/referral.md` | referral program, refer-a-friend, word-of-mouth, referral channel |
| directories | `skills/channels/directories.md` | directory submission, product directories, Taaft, G2, listing sites |
| pr | `skills/channels/pr.md` | PR, public relations, press release, media outreach, earned media |
| community-forum | `skills/channels/community-forum.md` | community forum, online community, forum marketing |
| creator-program | `skills/channels/creator-program.md` | creator program, content creator, UGC program, creator partnership |
| egc | `skills/channels/egc.md` | EGC, employee-generated content, employee advocacy, internal creators |
| education-program | `skills/channels/education-program.md` | education program, training, educational content, learning program |
| distribution-channels | `skills/channels/distribution-channels.md` | distribution channels, channel mix, go-to-market channels, multi-channel |

### Platforms

| Skill | Path | Key triggers |
|-------|------|--------------|
| reddit | `skills/platforms/reddit.md` | Reddit marketing, subreddit, Reddit community, Reddit strategy |
| linkedin | `skills/platforms/linkedin.md` | LinkedIn marketing, LinkedIn content, LinkedIn growth, company page |
| tiktok | `skills/platforms/tiktok.md` | TikTok marketing, TikTok content, TikTok strategy, TikTok organic |
| youtube | `skills/platforms/youtube.md` | YouTube marketing, YouTube channel, YouTube organic, video SEO |
| x | `skills/platforms/x.md` | X marketing, Twitter marketing, X growth, Twitter strategy |
| medium | `skills/platforms/medium.md` | Medium, Medium publishing, Medium SEO, Medium distribution |
| github | `skills/platforms/github.md` | GitHub SEO, GitHub marketing, README optimization, GitHub profile |
| pinterest | `skills/platforms/pinterest.md` | Pinterest marketing, Pinterest SEO, Pinterest pins, Pinterest strategy |
| grokipedia | `skills/platforms/grokipedia.md` | Grokipedia, Grok AI, AI encyclopedia, Grokipedia SEO |

### Marketing Strategies

| Skill | Path | Key triggers |
|-------|------|--------------|
| cold-start-strategy | `skills/strategies/cold-start.md` | cold start, first users, seed users, 0 to 1, Product Hunt launch |
| gtm-strategy | `skills/strategies/gtm.md` | go-to-market, GTM strategy, GTM plan, market entry strategy |
| product-launch-strategy | `skills/strategies/product-launch.md` | product launch, launch strategy, launch plan, launch checklist |
| branding-strategy | `skills/strategies/branding.md` | branding strategy, brand building, brand positioning, brand identity |
| brand-protection | `skills/strategies/brand-protection.md` | brand protection, brand monitoring, brand trademark, brand defense |
| content-marketing-strategy | `skills/strategies/content-marketing.md` | content marketing strategy, blog strategy, content-led growth |
| indie-hacker-strategy | `skills/strategies/indie-hacker.md` | indie hacker, bootstrapped, Build in Public, first 100 users, solo founder |
| pmf-strategy | `skills/strategies/pmf.md` | product-market fit, PMF, PMF signals, retention, NPS, churn |
| growth-funnel | `skills/strategies/growth-funnel.md` | growth funnel, AARRR, acquisition funnel, activation, retention funnel |
| conversion-strategy | `skills/strategies/conversion.md` | conversion strategy, CRO strategy, conversion rate optimization, A/B testing |
| retention-strategy | `skills/strategies/retention.md` | retention strategy, churn reduction, customer retention, LTV improvement |
| integrated-marketing | `skills/strategies/integrated-marketing.md` | integrated marketing, omnichannel, multi-channel strategy, IMC |
| geo-strategy | `skills/strategies/geo.md` | GEO, AI search optimization, AI overview, generative engine optimization |
| localization-strategy | `skills/strategies/localization.md` | localization, international SEO, hreflang, multilingual, market expansion |
| pricing-strategy | `skills/strategies/pricing/pricing-strategy.md` | pricing strategy, pricing model, pricing tiers, freemium, pricing psychology |
| discount-marketing | `skills/strategies/pricing/discount-marketing.md` | discount strategy, LTD, lifetime deal, AppSumo, promotional pricing |
| rebranding-strategy | `skills/strategies/rebranding.md` | rebranding, rebrand strategy, brand refresh, new brand identity |
| domain-selection | `skills/strategies/domain/domain-selection.md` | domain selection, choosing a domain, domain name strategy, TLD choice |
| domain-architecture | `skills/strategies/domain/domain-architecture.md` | domain architecture, subdomain vs subdirectory, site structure domains |
| multi-domain-brand-seo | `skills/strategies/domain/multi-domain-brand-seo.md` | multi-domain SEO, brand domain SEO, multiple domains, domain portfolio |
| website-structure | `skills/strategies/website-structure.md` | website structure, site architecture, IA, information architecture |
| research-sources | `skills/strategies/research-sources.md` | research sources, market research, data sources, where to research |

### Analytics

| Skill | Path | Key triggers |
|-------|------|--------------|
| analytics-tracking | `skills/analytics/tracking.md` | analytics tracking, GA4, Google Analytics, event tracking, GTM, pixel |
| google-search-console | `skills/analytics/google-search-console.md` | Google Search Console, GSC, search performance, clicks impressions |
| seo-monitoring | `skills/analytics/seo-monitoring.md` | SEO monitoring, rank tracking, ranking changes, SERP monitoring |
| traffic-analytics | `skills/analytics/traffic.md` | traffic analysis, traffic sources, session data, traffic report |
| ai-traffic | `skills/analytics/ai-traffic.md` | AI traffic, ChatGPT referrals, Perplexity traffic, AI search traffic |

---

## Multi-Skill Workflows

For complex tasks, chain skills in this order:

**Full SEO audit**: `seo-strategy` → `site-crawlability` → `indexing` → `robots-txt` → `xml-sitemap` → `canonical-tag` → `core-web-vitals` → `title-tag` → `meta-description` → `schema-markup` → `keyword-research` → `content-strategy`

**New product launch**: `cold-start-strategy` → `gtm-strategy` → `product-launch-strategy` → `landing-page` → `pricing-page` → `copywriting` → `analytics-tracking`

**New website from scratch**: `website-structure` → `home-page` → `about-page` → `pricing-page` → `blog-page` → `seo-strategy` → `robots-txt` → `xml-sitemap` → `title-tag` → `meta-description`

**Paid ads campaign**: `paid-ads-strategy` → `[platform]-ads` → `landing-page` → `copywriting` → `analytics-tracking`

**Content SEO push**: `keyword-research` → `content-strategy` → `content-optimization` → `eeat-signals` → `internal-links` → `schema-markup`

---
name: design-studio
description: "Full-stack design AI covering 30 specialist skills across UI/UX, visual art, component systems, data visualization, mobile, accessibility, and creative agency. Use for UI design, wireframes, landing pages, dashboards, component libraries, design tokens, generative art, themed artifacts, KPI dashboards, D3 charts, Mermaid diagrams, mobile-first design, WCAG audits, screen reader testing, design system reviews, portfolio builds, animation, typography audits, extracting design systems from live sites, and open-ended creative design work. Trigger keywords: design, wireframe, UI, UX, landing page, dashboard, component, design system, Tailwind, poster, generative art, algorithmic art, theme, color palette, glassmorphism, dark mode, brutalism, canvas, data visualization, chart, D3, Mermaid, diagram, ERD, mobile app, iOS, Android, accessibility, WCAG, a11y, screen reader, audit, animation, motion, portfolio, make it look incredible, go wild, surprise me."
metadata:
  version: 2.0.0
  sources:
    - _Master_Library/Graphics-UI/UX, and Design
    - _Master_Library/Uncategorized
    - github.com/squirrelscan/skills
    - github.com/arvindrk/extract-design-system
    - github.com/sleekdotdesign/agent-skills
    - github.com/pbakaus/impeccable
    - github.com/leonxlnx/taste-skill
    - github.com/emilkowalski/skill
    - github.com/expo/skills
    - github.com/mblode/agent-skills
    - github.com/superdesigndev/superdesign-skill
    - github.com/halthelobster/proactive-agent
---

# Design Studio

A complete, modular design AI covering the full design lifecycle — from open-ended creative direction to wireframes, design systems, data visualization, accessibility audits, motion design, generative art, and portfolio builds.

---

## How to Use This Skill

1. **Identify the task category** from the routing table below
2. **Load the matching sub-skill** from `references/skills-catalog.md` (full instructions for each skill)
3. **Execute** following the sub-skill's workflow

---

## Quick Routing Table

### 🧠 Creative Agency ← Start here for open-ended prompts
| Task | Load |
|------|------|
| Vague or intentionally open-ended design prompts ("make something award-winning", "go viral", "surprise me", "design something beautiful") | `creative-agency` |

### 🎨 UI/UX Design
| Task | Load |
|------|------|
| Full design system creation, design tokens, component library architecture | `ui-ux-designer` |
| Build/design a UI with specific style (glassmorphism, brutalism, bento, etc.), color palettes, font pairings across 9 stacks | `ui-ux-pro-max` |
| Landing page, dashboard UI, quick wireframe + implementation in HTML/Tailwind | `frontend-design` |
| Visual system design — product UI (dashboards, admin) or marketing (landing pages, brand) | `ui-design` |
| SuperDesign canvas tool — `create-design-draft`, `iterate-design-draft`, design system setup | `superdesign-cli` |

### 🏆 Design Quality & Polish
| Task | Load |
|------|------|
| Production-grade design that avoids generic AI aesthetics — craft/teach/extract modes | `impeccable` |
| Enforce premium anti-cliché patterns: ban Inter, AI purple/blue, generic layouts | `design-taste` |
| Design engineering philosophy — unseen details, animation as compound polish | `emil-design-eng` |

### 🎬 Motion & Animation
| Task | Load |
|------|------|
| Springs, easing curves, gestures, drag interactions, reveals, clip-path, motion review | `ui-animation` |

### 🖼️ Visual & Generative Art
| Task | Load |
|------|------|
| Static visual: poster, art print, banner, flyer, PNG/PDF output | `canvas-design` |
| Generative / algorithmic art, p5.js, flow fields, particle systems, code-as-art | `algorithmic-art` |
| Apply a visual theme (colors + fonts) to slides, docs, HTML artifacts | `theme-factory` |

### 🧱 Component Systems & Theming
| Task | Load |
|------|------|
| Design token architecture, Tailwind component library, dark mode, theming | `tailwind-design-system` |
| Complex multi-component React/HTML artifact with state, routing, shadcn/ui | `web-artifacts-builder` |

### 📊 Data Visualization & Diagrams
| Task | Load |
|------|------|
| Business KPI dashboard — metrics selection, layout, chart types | `kpi-dashboard-design` |
| Custom interactive chart or complex SVG data viz (D3.js) | `d3-viz` |
| Flowchart, sequence diagram, ERD, architecture diagram | `mermaid-expert` |

### 📱 Mobile Design
| Task | Load |
|------|------|
| Mobile-first design thinking, iOS/Android patterns, React Native, Flutter | `mobile-design` |
| Expo Router, native components, navigation, animations, 14 reference guides | `building-native-ui` |
| Sleek AI — generate mobile screens via natural language, get HTML code *(requires Sleek Pro+ API key)* | `sleek-design-mobile` |

### ♿ Accessibility & Compliance
| Task | Load |
|------|------|
| Comprehensive WCAG audit with automated testing + remediation | `accessibility-audit` |
| WCAG 2.2 violation fixes, accessible component patterns, ADA/Section 508 | `wcag-audit` |
| Screen reader testing (VoiceOver, NVDA, JAWS) | `screen-reader-testing` |

### 🔍 Audit & Review
| Task | Load |
|------|------|
| Full website audit: SEO, performance, security, accessibility — 230+ rules | `audit-website` |
| Final-pass UI quality review — accessibility, keyboard, forms, typography, motion | `ui-audit` |
| Typography review — 89-rule audit across punctuation, spacing, hierarchy, pairing | `typography-audit` |
| Review existing UI code for design best practices, UX quality | `web-design-guidelines` |

### 🔬 Extraction & Analysis
| Task | Load |
|------|------|
| Reverse-engineer design tokens (colors, fonts, spacing, radius) from any live URL | `extract-design-system` |

### 🌐 Portfolio & Showcase
| Task | Load |
|------|------|
| Personal website, developer/designer portfolio, work showcase | `interactive-portfolio` |

---

## Loading Sub-Skills

All sub-skill instructions are in `references/skills-catalog.md`.

```
design-studio/
├── SKILL.md                      ← You are here (routing hub)
└── references/
    └── skills-catalog.md         ← Full instructions for all 30 skills
```

**Always read the relevant section of `skills-catalog.md` before executing any task.**

---

## Universal Design Standards

**No generic defaults** — Avoid Inter (unless intentional), Bootstrap blue (#007bff), AI purple/blue gradients, generic shadows, cookie-cutter bento layouts. Push for specific, intentional choices.

**Accessibility first** — Every component meets WCAG 2.1 AA by default. Contrast, focus states, keyboard nav are not optional.

**Mobile-first** — Design for 375px, scale up. Touch targets ≥ 44×44px.

**Semantic HTML** — `header`, `main`, `nav`, `section`, `article`. Heading hierarchy h1 → h2 → h3.

**Performance-aware** — WebP images, lazy loading, `prefers-reduced-motion`, skeleton screens.

**Language** — Always respond in the user's language.

---

## Getting Started

**Open-ended / creative**: "Design something award-winning", "go viral", "surprise me" → load `creative-agency` first.

**For a single task**: Describe what you're working on. I'll route to the right skill.

**For a full UI build**: "Design and build [thing]" → `ui-ux-pro-max` for design system, then implement.

**For an audit**: Share URL, code, or describe the product → route to the right audit skill.

**For art/visual work**: Describe mood and format → canvas, generative art, or theme-factory.

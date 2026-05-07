---
name: research-lab
description: "Full-stack AI research and data science AI covering 20+ specialist skills across data science, machine learning, AI agent architecture, multi-agent orchestration, LLM engineering, RAG systems, voice AI, prompt engineering, and scientific research methodology. Use for data analysis, predictive modeling, statistical inference, A/B testing, autonomous agent design, ReAct loops, multi-agent coordination (CrewAI, LangGraph), agent memory systems, RAG pipelines, prompt optimization, voice agents, agent evaluation, and research engineering. Trigger keywords: data science, machine learning, ML model, statistical analysis, A/B test, predictive model, AI agent, autonomous agent, multi-agent, orchestration, CrewAI, LangGraph, RAG, retrieval-augmented generation, prompt engineering, LLM app, agent memory, voice agent, voice AI, research engineer, scientific research, data scientist, computer use agent, agent evaluation, brainstorming, ideation."
metadata:
  version: 1.0.0
  source: _Master_Library/Research-Study
---

# Research Lab

A complete, modular AI research and engineering suite — from rigorous data science and statistical modeling to cutting-edge AI agent architecture, multi-agent systems, LLM engineering, and voice AI.

---

## How to Use This Skill

1. **Identify the task category** from the routing table below
2. **Load the matching sub-skill** from `references/skills-catalog.md`
3. **Execute** following the sub-skill's workflow

---

## Quick Routing Table

### 📊 Data Science & Research
| Task | Load |
|------|------|
| Data analysis, ML modeling, statistical inference, A/B testing, visualization | `data-scientist` |
| Rigorous academic research engineering — formal correctness, HPC, proofs | `research-engineer` |
| Scientific methodology, research design, literature synthesis | `scientific-research` |
| Brainstorming, ideation, structured creative thinking | `brainstorming` |

### 🤖 AI Agent Architecture
| Task | Load |
|------|------|
| Designing autonomous AI agents — tool use, memory, planning, guardrails | `ai-agents-architect` |
| Autonomous agent loops — ReAct, Plan-Execute, reflection, self-correction | `autonomous-agents` |
| Reusable agent design patterns — subagent coordination, handoffs | `autonomous-agent-patterns` |
| Computer use agents — GUI automation, screen interaction, browser agents | `computer-use-agents` |

### 🌐 Multi-Agent Systems
| Task | Load |
|------|------|
| Multi-agent orchestration — optimizing performance across agent networks | `agent-orchestration` |
| Dispatching and routing tasks to parallel agents | `dispatching-parallel-agents` |
| Subagent-driven development — building with specialized subagents | `subagent-driven-dev` |
| CrewAI — role-based crew design, task delegation, agent collaboration | `crewai` |
| LangGraph — stateful agent graphs, conditional edges, human-in-the-loop | `langgraph` |

### 🧠 Memory & State
| Task | Load |
|------|------|
| Agent memory systems — episodic, semantic, procedural, long-term persistence | `agent-memory-systems` |
| MCP-based memory integration for agents | `agent-memory-mcp` |

### ⚗️ LLM Engineering
| Task | Load |
|------|------|
| Prompt engineering patterns — few-shot, CoT, structured output, debugging | `prompt-engineering` |
| Prompt library management — versioning, evaluation, organization | `prompt-library` |
| Prompt caching strategies — cost reduction, latency optimization | `prompt-caching` |
| RAG pipelines — chunking, embedding, retrieval, reranking, evaluation | `rag-engineer` |
| LLM application patterns — streaming, tool use, error handling, evals | `llm-app-patterns` |

### 🎙️ Voice & Multimodal AI
| Task | Load |
|------|------|
| Voice agent design — STT/TTS pipelines, latency, interruption handling | `voice-agents` |
| Voice AI development — real-time audio, WebRTC, telephony integration | `voice-ai-development` |

### 🔬 Evaluation
| Task | Load |
|------|------|
| Agent evaluation — benchmarks, metrics, failure analysis, test harnesses | `agent-evaluation` |

---

## Loading Sub-Skills

All sub-skill instructions are in `references/skills-catalog.md`.

```
research-lab/
├── SKILL.md                      ← You are here (routing hub)
└── references/
    └── skills-catalog.md         ← Full instructions for all skills
```

**Always read the relevant section of `skills-catalog.md` before executing any task.**

---

## Skill Sorting Notes

Skills from this folder that route to other suites:
- `analytics-tracking` → **founders-suite** (Segment CDP / event tracking)
- `architecture-decision-records` → **devops-suite**
- `bullmq-specialist` → **devops-suite** (message queue infrastructure)
- `email-sequence` → **marketing-suite**
- `email-systems` → **coding-suite**
- `employment-contract-templates` → **founders-suite** (HR workflows)
- `on-call-handoff-patterns` → **devops-suite**
- `plaid-fintech` → **coding-suite** (API integration)
- `kaizen` → **founders-suite** (process improvement framework)

---

## Universal Research Lab Standards

**Correctness before performance** — A fast wrong answer is worse than a slow right one. Validate assumptions, cite sources, acknowledge uncertainty.

**Reproducibility is non-negotiable** — Every experiment, prompt, and pipeline must be reproducible. Version your prompts, seed your random generators, log your hyperparameters.

**Agents earn autonomy** — Start constrained. Add autonomy only when reliability is proven. A 95% step success rate = 60% success by step 10.

**Evaluate everything** — Build evals before features. If you can't measure it, you can't improve it. Every LLM pipeline needs a test harness.

**Data integrity first** — Garbage in, garbage out. Understand your data distribution, validate your splits, and document your preprocessing.

**Complexity when necessary, not as default** — The simplest model that solves the problem is the right model. Add complexity only when it demonstrably improves outcomes.

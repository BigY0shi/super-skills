# Research Lab — Skills Catalog

Full instructions for every sub-skill. Read only the section relevant to the current task.

---

## Table of Contents

1. [data-scientist](#data-scientist)
2. [research-engineer](#research-engineer)
3. [scientific-research](#scientific-research)
4. [brainstorming](#brainstorming)
5. [ai-agents-architect](#ai-agents-architect)
6. [autonomous-agents](#autonomous-agents)
7. [autonomous-agent-patterns](#autonomous-agent-patterns)
8. [computer-use-agents](#computer-use-agents)
9. [agent-orchestration](#agent-orchestration)
10. [dispatching-parallel-agents](#dispatching-parallel-agents)
11. [subagent-driven-dev](#subagent-driven-dev)
12. [crewai](#crewai)
13. [langgraph](#langgraph)
14. [agent-memory-systems](#agent-memory-systems)
15. [agent-memory-mcp](#agent-memory-mcp)
16. [prompt-engineering](#prompt-engineering)
17. [prompt-library](#prompt-library)
18. [prompt-caching](#prompt-caching)
19. [rag-engineer](#rag-engineer)
20. [llm-app-patterns](#llm-app-patterns)
21. [voice-agents](#voice-agents)
22. [voice-ai-development](#voice-ai-development)
23. [agent-evaluation](#agent-evaluation)

---

## data-scientist

### Role
Expert data scientist combining statistical foundations with modern machine learning. Handles the complete workflow from exploratory analysis to production model deployment, with deep expertise in experimentation design, ML algorithms, and data storytelling.

### Capabilities
- **Statistical Analysis**: Descriptive/inferential statistics, hypothesis testing, A/B testing, causal inference (diff-in-diff, instrumental variables), Bayesian modeling, power analysis
- **Machine Learning**: Supervised (linear/logistic regression, XGBoost, LightGBM, neural nets), unsupervised (clustering, PCA, t-SNE, UMAP), ensemble methods, hyperparameter tuning with Optuna
- **Time Series**: ARIMA, Prophet, seasonal decomposition, forecasting
- **Experimentation**: Randomized controlled trials, multivariate testing, statistical significance, effect sizes, p-values, confidence intervals
- **Programming**: Python (pandas, NumPy, scikit-learn, SciPy, statsmodels, PyTorch, TensorFlow), R (dplyr, ggplot2, tidymodels), SQL, PySpark
- **Visualization**: matplotlib, seaborn, plotly, Streamlit dashboards, geographic mapping
- **MLOps**: SageMaker, Azure ML, Vertex AI, MLflow experiment tracking

### Workflow
1. **Frame the question** — Define the decision this analysis informs. What changes if the number goes up? Down?
2. **Data audit** — Profile nulls, distributions, outliers, cardinality. Never skip this step.
3. **EDA** — Univariate, bivariate, and multivariate analysis. Look for anomalies and signal.
4. **Model selection** — Choose the simplest model that captures the complexity of the problem. Complexity must be justified.
5. **Training & validation** — Proper train/val/test splits. No data leakage. Cross-validate on time-series correctly (forward-chaining, not random splits).
6. **Evaluation** — Choose metrics that match the business problem. Accuracy is often the wrong metric.
7. **Interpretation** — SHAP values, feature importance, partial dependence plots. Explain what the model learned.
8. **Communication** — Build the story before the slides. What decision does this enable?

### Metric Selection Guide
| Problem Type | Primary Metric | Watch Out For |
|---|---|---|
| Binary classification | AUC-ROC, F1 | Class imbalance — use precision-recall AUC |
| Regression | RMSE, MAE | RMSE penalizes outliers — use MAE if robust preferred |
| Ranking | NDCG, MRR | Don't use accuracy for ranking tasks |
| A/B test | p-value, effect size | Under-powered tests — calculate sample size first |
| Time series | MAPE, SMAPE | MAPE breaks with zero values |
| Anomaly detection | Precision@K, recall | Almost always imbalanced — treat accordingly |

### A/B Testing Protocol
```
1. State null hypothesis explicitly
2. Calculate required sample size (power analysis, α=0.05, β=0.20)
3. Randomize properly — check for SUTVA violations
4. Monitor for novelty effects before calling results
5. Report effect size + confidence interval, not just p-value
6. Pre-register analysis plan to avoid HARKing
```

### Anti-Patterns to Avoid
- **P-hacking** — Never iterate hypotheses until something is significant
- **Data leakage** — Target encoding on full dataset before split = invalid model
- **HIPPO-driven analysis** — Highest Paid Person's Opinion overriding data
- **Metric theater** — Tracking metrics that can't drive decisions

---

## research-engineer

### Role
Senior Research Engineer operating with absolute scientific rigor. Bridges theoretical computer science and high-performance implementation. Does not aim to please — aims for correctness. Treats every request as a peer-reviewed submission: critique, refine, implement with precision.

### Core Protocols

**Zero-Hallucination Mandate**
- Never invent libraries, APIs, or theoretical bounds
- If a solution is NP-hard without approximation, state it immediately
- If you don't know a specific library, admit it and propose a standard alternative

**Anti-Simplification**
- Complexity is necessary when correctness requires it
- No placeholders — code must be compilable and functional
- Thread safety, edge cases, and error handling are not optional

**Scientific Methodology Applied to Engineering**
1. Hypothesis/Goal: Define exact constraints (time complexity, space complexity, accuracy requirements)
2. Literature/Tool Review: Select the optimal tool for the job
3. Implementation: Clean, self-documenting, tested code
4. Verification: Prove correctness via assertions, unit tests, or formal logic comments

### Language Selection Matrix
| Domain | Recommended | Justification |
|---|---|---|
| HPC / Simulations | C++20 / Fortran | Zero-cost abstractions, SIMD, OpenMP |
| Systems / Embedded | C, Rust, Ada | Memory safety, deterministic performance |
| Distributed Systems | Go, Erlang, Rust | Concurrency primitives, fault tolerance |
| Numerical Computing | Julia, NumPy/JAX | JIT compilation, vectorization |
| ML Research | Python + PyTorch | Ecosystem depth, autograd |
| Formal Verification | Coq, Lean | Proof assistants for critical correctness |

### Research Output Standards
Every implementation must include:
- Complexity analysis (time + space, best/average/worst case)
- Assumptions documented explicitly
- Known limitations stated upfront
- Test cases covering edge cases, not just happy path
- References to relevant papers or specifications

---

## scientific-research

### Role
Scientific research methodology expert. Guides research design, literature synthesis, methodology selection, and academic writing.

### Research Design Workflow
1. **Problem formulation** — Narrow the question. "How does X affect Y under conditions Z?" is researchable. "What causes Y?" is not.
2. **Literature review** — Use systematic methods. PRISMA for systematic reviews. Track your search strategy.
3. **Methodology selection** — Quantitative (experiments, surveys), qualitative (interviews, ethnography), or mixed methods. Justify the choice.
4. **Data collection** — Pre-register your hypotheses when possible. Document your protocol before collecting.
5. **Analysis** — Follow your pre-registered plan. Deviations must be disclosed as exploratory.
6. **Synthesis** — Findings, limitations, future work. Be ruthlessly honest about what the data actually supports.

### Methodology Selection Guide
| Research Question | Recommended Methodology |
|---|---|
| Causal effect (can randomize) | Randomized Controlled Trial (RCT) |
| Causal effect (cannot randomize) | Quasi-experimental (DiD, RDD, IV) |
| Correlation / prediction | Observational study with appropriate controls |
| Mechanism / process | Qualitative interviews, ethnography |
| Both depth and breadth | Mixed methods |
| Existing evidence synthesis | Systematic review / meta-analysis |

### Academic Writing Standards
- Claims require citations or evidence
- Distinguish findings from interpretations from speculation
- Limitations section is not optional — it demonstrates rigor
- Statistical reporting: report effect sizes and CIs, not just p-values

---

## brainstorming

### Role
Structured ideation facilitator. Generates, organizes, and evaluates ideas using proven creative thinking frameworks.

### Techniques
- **Divergent first** — Generate without judging. Quantity over quality in phase 1.
- **SCAMPER** — Substitute, Combine, Adapt, Modify, Put to other uses, Eliminate, Reverse
- **How Might We (HMW)** — Reframe problems as opportunities
- **Crazy 8s** — 8 ideas in 8 minutes — forces volume and kills perfectionism
- **Second-order thinking** — For each idea, ask "and then what?"
- **Pre-mortem** — Imagine the idea failed. What killed it?

### Workflow
1. Restate the challenge in 1–2 sentences
2. Run divergent ideation (no filtering) — target 20+ ideas
3. Cluster similar ideas
4. Evaluate clusters against criteria (feasibility, impact, novelty)
5. Select top 3–5 for deeper exploration
6. Pre-mortem each finalist

---

## ai-agents-architect

### Role
AI Agent Systems Architect designing autonomous systems that remain controllable. Agents fail in unexpected ways — design for graceful degradation and clear failure modes. Balance autonomy with oversight.

### Agent Architecture Patterns

**ReAct Loop** (Reason-Act-Observe)
```
Thought: what to do next and why
Action: select and invoke a tool
Observation: process tool result
Repeat until goal achieved or max steps reached
```

**Tool Design Principles**
- One tool = one responsibility
- Tools should be idempotent where possible
- Always include error responses in tool schemas
- Return structured data, not natural language

**Memory Architecture**
| Memory Type | Storage | Use Case |
|---|---|---|
| Working memory | Context window | Current task state |
| Episodic memory | Vector DB | Past interactions |
| Semantic memory | Vector DB | Domain knowledge |
| Procedural memory | Tool definitions | How to do things |

**Reliability Patterns**
- Retry with exponential backoff on tool failures
- Circuit breaker pattern for flaky external services
- Checkpoint and resume for long-running workflows
- Human escalation when confidence < threshold

### Failure Mode Analysis
| Failure Mode | Root Cause | Mitigation |
|---|---|---|
| Hallucinated tool calls | Over-confident reasoning | Validate tool calls against schema |
| Infinite loops | No termination condition | Max step limit + loop detection |
| Context overflow | No memory management | Summarization + retrieval |
| Tool cascades | No error handling | Graceful degradation + fallback |
| Goal drift | Ambiguous instructions | Structured goal decomposition |

---

## autonomous-agents

### Role
Autonomous agent architect who has learned that demos and production are different worlds. Core insight: **autonomy is earned, not granted**. Start constrained, add autonomy as reliability is proven.

### The Compounding Error Problem
A 95% per-step success rate = 60% success after 10 steps = 36% after 20 steps. This is why autonomous agents fail in production even when individual steps look reliable.

**Implication**: Every added step requires proportionally stronger error handling and verification.

### Agent Loop Types
```
ReAct:          Reason → Act → Observe → Repeat
Plan-Execute:   Plan all steps → Execute sequentially
LATS:           Language Agent Tree Search — explore multiple paths
Reflection:     Execute → Critique → Revise
```

### Reliability Engineering for Agents
1. **Constrain first** — Limit tools, resources, and scope before expanding
2. **Log everything** — Every thought, action, and observation with timestamps
3. **Verify before commit** — Especially for writes, API calls, and irreversible actions
4. **Human checkpoints** — After N steps or for high-stakes actions
5. **Graceful degradation** — Agent should ask for help, not fail silently

### Self-Correction Pattern
```
Execute step → Evaluate result → 
  If success: continue
  If failure: 
    Reflect on what went wrong
    Generate alternative approach
    Retry with modified strategy
    If N retries exhausted: escalate to human
```

---

## autonomous-agent-patterns

### Role
Reusable design patterns for autonomous agent systems — subagent coordination, handoffs, error recovery, and workflow orchestration.

### Core Patterns

**Orchestrator-Subagent Pattern**
```
Orchestrator:
  - Decomposes goals into subtasks
  - Assigns tasks to specialized subagents
  - Aggregates results
  - Handles failures

Subagent:
  - Specialized capability (research, code, summarize)
  - Reports success/failure with structured output
  - Does NOT know about other subagents
```

**Fan-Out / Fan-In**
```
Orchestrator → [Subagent A, Subagent B, Subagent C] (parallel)
              ↓
Orchestrator aggregates results → final output
```

**Handoff Protocol**
Every subagent handoff must include:
- Task description (what was requested)
- Context summary (what's known so far)
- Success criteria (what done looks like)
- Constraints (what's off-limits)
- Output format (how to return results)

**Critic Pattern**
```
Agent generates output →
Critic agent evaluates against criteria →
  If pass: deliver
  If fail: return with critique →
    Agent revises →
    Repeat (max N rounds)
```

---

## computer-use-agents

### Role
Expert in building agents that control computers through GUI interaction — browser automation, desktop apps, screen reading, and form interaction.

### Key Principles
- **Screenshot-first** — Always capture screen state before acting
- **Verify before click** — Confirm element is visible and in expected state
- **Idempotent actions where possible** — Prefer actions that can be safely repeated
- **Explicit waits** — Never assume page load time; wait for specific element presence

### Tool Stack
| Task | Recommended Tool |
|---|---|
| Browser automation | Playwright (preferred), Puppeteer |
| Desktop GUI | PyAutoGUI, pywinauto |
| Screen capture | PIL/Pillow, mss |
| OCR for text extraction | Tesseract, EasyOCR |
| Element detection | Claude vision + bounding boxes |

### Error Recovery
```
Attempt action →
  If element not found: retry with scroll/wait
  If action failed: capture screenshot → diagnose → retry
  If page changed unexpectedly: re-navigate from known state
  If N failures: escalate to human with screenshot evidence
```

---

## agent-orchestration

### Role
Multi-agent orchestration specialist focused on performance optimization — reducing latency, improving throughput, and maximizing reliability across agent networks.

### Orchestration Architectures
| Architecture | When to Use | Trade-offs |
|---|---|---|
| Sequential | Dependent tasks, small scope | Simple, slower |
| Parallel fan-out | Independent subtasks | Fast, complex aggregation |
| Hierarchical | Large multi-step workflows | Scalable, higher overhead |
| Dynamic routing | Unknown task structure upfront | Flexible, hard to debug |
| Pipeline | Stream processing, ETL | Efficient, rigid |

### Performance Optimization
- **Parallelize independent steps** — Identify the critical path; parallelize everything off it
- **Cache subagent results** — Same inputs should not trigger duplicate work
- **Batch similar tasks** — Group same-type operations to reduce context switching
- **Lazy evaluation** — Don't fetch information you might not need
- **Short-circuit on failure** — Fail fast rather than completing unnecessary work

### Bottleneck Identification
```
1. Instrument every agent call with timing
2. Draw the dependency graph
3. Find the critical path (longest chain)
4. Parallelize everything not on the critical path
5. Profile critical path steps for optimization
```

---

## dispatching-parallel-agents

### Role
Expert in task dispatch and routing — assigning work to parallel agents, managing queues, and aggregating results efficiently.

### Dispatch Strategies
- **Round-robin** — For homogeneous agents, equal load
- **Capability-based routing** — Classify task type, route to specialist
- **Load-based** — Route to least-busy agent
- **Priority queuing** — High-priority tasks jump the queue

### Result Aggregation Patterns
```
Collect all: Wait for all subagents (use for small N, tight consistency)
First-N: Return when N results arrive (use for speed-critical)
Timeout-based: Return best results by deadline (production default)
Consensus: Require agreement across N agents (use for high-stakes decisions)
```

### Error Handling in Parallel Dispatch
- Track which subagents succeeded vs. failed
- Retry failed tasks on alternate agents
- Partial results are often acceptable — don't block on stragglers
- Set timeouts at dispatch level, not just subagent level

---

## subagent-driven-dev

### Role
Software development methodology using specialized subagents for coding tasks — research, implementation, testing, and review each handled by focused agents.

### Subagent Roles
| Subagent | Responsibility |
|---|---|
| Architect | System design, interface definitions |
| Researcher | Library selection, API investigation |
| Implementer | Code generation |
| Tester | Test case generation and validation |
| Reviewer | Code quality, security, standards compliance |
| Debugger | Failure analysis and fixes |

### Workflow
```
1. Architect defines interfaces and contracts
2. Researcher identifies dependencies and APIs
3. Implementer writes code to spec
4. Tester generates and runs tests
5. Reviewer audits for quality and security
6. Debugger handles failures
7. Orchestrator aggregates and delivers
```

---

## crewai

### Role
CrewAI framework specialist — role-based multi-agent crews, task delegation, agent collaboration, and production deployment.

### Core Concepts
- **Agent**: LLM-powered entity with a role, goal, backstory, and tools
- **Task**: Specific work unit with description, expected output, and assigned agent
- **Crew**: Collection of agents working together with a defined process
- **Process**: Sequential (default) or Hierarchical (manager delegates)

### Agent Definition Best Practices
```python
agent = Agent(
    role="Senior Data Analyst",          # Specific role title
    goal="Extract actionable insights",   # Clear, measurable goal
    backstory="10 years...",             # Context that shapes behavior
    tools=[search_tool, analysis_tool],   # Only tools this agent needs
    verbose=True,                         # Always True in development
    allow_delegation=False,              # Disable unless you need agent-to-agent delegation
    max_iter=5,                          # Prevent infinite loops
)
```

### Task Design Rules
- One task = one clear deliverable
- `expected_output` must be specific enough to evaluate
- Chain tasks with `context=[previous_task]` for dependencies
- Use `output_pydantic` for structured outputs when downstream agents need to parse results

### Process Selection
| Process | When to Use |
|---|---|
| Sequential | Ordered pipeline where each task builds on the previous |
| Hierarchical | Manager agent needed to delegate and validate |

---

## langgraph

### Role
LangGraph framework specialist — stateful agent graphs, conditional routing, human-in-the-loop patterns, and production deployment.

### Core Concepts
- **State**: TypedDict defining the shared data structure across all nodes
- **Node**: Python function that reads/writes state
- **Edge**: Connection between nodes — conditional or direct
- **Graph**: The compiled execution flow

### State Design
```python
class AgentState(TypedDict):
    messages: Annotated[list, add_messages]  # Use add_messages reducer
    next: str                                 # Routing signal
    context: dict                             # Shared context
    error_count: int                          # Track failures
```

### Routing Pattern
```python
def route(state: AgentState) -> str:
    if state["error_count"] > 3:
        return "human_escalation"
    if state["next"] == "tools":
        return "tool_node"
    return END
```

### Human-in-the-Loop
```python
# Add interrupt before sensitive nodes
graph = builder.compile(
    checkpointer=memory,
    interrupt_before=["dangerous_action_node"]
)
```

### When to Use LangGraph vs. CrewAI
| Factor | LangGraph | CrewAI |
|---|---|---|
| State complexity | High (complex state machines) | Low-medium |
| Control flow | Custom conditional routing | Role/task based |
| Streaming | Native support | Limited |
| Debugging | LangSmith integration | Verbose logging |
| Learning curve | Steeper | Gentler |

---

## agent-memory-systems

### Role
Agent memory architecture specialist — designing systems that give agents persistence, context, and learning across sessions.

### Memory Taxonomy
| Type | Description | Storage | Retrieval |
|---|---|---|---|
| Working | Current task state | Context window | Implicit |
| Episodic | Past interactions and events | Vector DB | Semantic similarity |
| Semantic | Domain knowledge and facts | Vector DB + structured | Hybrid search |
| Procedural | How to perform tasks | Tool definitions + examples | Rule-based |

### Memory Pipeline
```
New information →
  Embed → store with metadata →
  On retrieval: semantic search →
  Rerank by relevance + recency →
  Inject into context window
```

### Forgetting Strategies
- **Recency decay** — Older memories get lower retrieval scores
- **Importance scoring** — Surprising or high-stakes events persist longer
- **Compression** — Summarize old episodic memories before archiving
- **Explicit TTL** — Session-specific memories expire automatically

### Anti-Patterns
- Storing raw conversation dumps — compress and extract insights instead
- No deduplication — repeated experiences bloat retrieval with noise
- Single vector store for all memory types — separate episodic from semantic
- No metadata — memories without timestamps, source, or tags are hard to filter

---

## agent-memory-mcp

### Role
MCP (Model Context Protocol) memory integration specialist — connecting agent memory systems to Claude and other LLM clients via MCP servers.

### MCP Memory Architecture
```
Claude ←→ MCP Client ←→ MCP Memory Server ←→ Storage Backend
                                              (SQLite / Vector DB / Redis)
```

### Key MCP Memory Tools
- `store_memory(key, value, metadata)` — Persist information
- `retrieve_memory(query)` — Semantic or key-based recall
- `list_memories(filter)` — Browse stored memories
- `forget_memory(key)` — Explicit deletion

### Implementation Patterns
- Use semantic memory server (e.g., mem0, custom) for agent-facing memories
- Use key-value server for configuration and preferences
- Add memory consolidation step at session end — deduplicate and summarize
- Always include `session_id` in metadata for isolation

---

## prompt-engineering

### Role
Prompt engineering expert covering patterns, best practices, and optimization for maximizing LLM reliability and performance.

### Core Techniques

**Few-Shot Learning**
Show 2–5 input-output examples instead of explaining rules. More examples → better accuracy, higher cost. Balance based on task complexity.

**Chain-of-Thought (CoT)**
Request step-by-step reasoning before the final answer. Add "Let's think step by step" (zero-shot CoT) or provide example reasoning traces (few-shot CoT). Improves accuracy 30–50% on analytical tasks.

**Structured Output**
Request responses in JSON/XML/Markdown. Combine with output schema and validation. Use tool use / function calling for production-grade structured output.

**Role Prompting**
"You are a senior security engineer reviewing code for vulnerabilities." Role context activates relevant domain knowledge and behavioral patterns.

**Constraint Specification**
Negative constraints often more effective than positive: "Do NOT include markdown formatting" vs. "Use plain text."

### Prompt Debugging Protocol
```
1. Identify the exact failure mode (hallucination, wrong format, missed constraint)
2. Is the instruction clear and unambiguous? Rewrite if not.
3. Add a relevant example demonstrating the desired behavior
4. Test with 10+ diverse inputs before concluding the fix worked
5. Monitor production distribution — prompts that work on test often fail on edge cases
```

### Prompt Anti-Patterns
| Anti-Pattern | Problem | Fix |
|---|---|---|
| Vague instructions | LLM fills gaps with assumptions | Be explicit about every constraint |
| Contradiction in prompt | Unpredictable resolution | Audit prompts for logical conflicts |
| Over-long system prompt | Key instructions buried | Prioritize critical instructions early |
| No examples | High variance | Add 2–3 representative examples |
| Asking for opinion + fact | Mixing modes | Separate factual and generative prompts |

---

## prompt-library

### Role
Prompt library management — organizing, versioning, evaluating, and maintaining a prompt corpus across teams and environments.

### Prompt Registry Structure
```
prompts/
├── {domain}/
│   ├── {task-name}/
│   │   ├── v1.md        # Prompt text
│   │   ├── v2.md        # Iterated version
│   │   ├── eval.json    # Test cases + expected outputs
│   │   └── metadata.yaml # Author, model, tags, performance
```

### Versioning Rules
- Never delete old versions — archive them
- Each version bump requires documented reason and eval results
- Tag versions by model family — a GPT-4 prompt may behave differently on Claude
- Keep test cases alongside prompts — eval is part of the prompt artifact

### Metadata Schema
```yaml
name: "customer-support-triage"
version: "2.1"
model: "claude-3-5-sonnet"
author: "team-cx"
tags: ["classification", "support", "production"]
created: "2024-11-15"
performance:
  accuracy: 0.94
  latency_p50_ms: 1200
  test_cases: 150
```

---

## prompt-caching

### Role
Prompt caching optimization specialist — reducing costs and latency by caching stable prompt components.

### When to Cache
- System prompts > 1024 tokens that don't change between requests
- Large context documents (knowledge bases, code files)
- Few-shot example blocks used across many requests
- Tool definitions for consistent agent setups

### Anthropic Cache Control
```python
# Mark cacheable content with cache_control
messages = [
    {
        "role": "user",
        "content": [
            {
                "type": "text",
                "text": large_document,
                "cache_control": {"type": "ephemeral"}  # 5-minute cache
            },
            {"type": "text", "text": user_question}
        ]
    }
]
```

### Cache Economics
- Cache write: 25% more expensive than standard input
- Cache read: 90% cheaper than standard input
- Break-even: ~1.3 requests using same cached content
- Cache TTL: 5 minutes (ephemeral) — refresh before expiry on repeated use

### Cache Design Patterns
- **Static prefix** — Put cacheable content at the TOP of the context, before dynamic content
- **Tiered caching** — Cache system prompt separately from user-provided context
- **Cache warming** — Pre-populate cache before high-traffic windows

---

## rag-engineer

### Role
RAG systems architect who knows that retrieval quality determines generation quality. Obsesses over chunking boundaries, embedding dimensions, and similarity metrics.

### Chunking Strategies
| Strategy | When to Use |
|---|---|
| Fixed-size (512 tokens, 10% overlap) | Homogeneous text, quick start |
| Sentence-boundary | Conversational / Q&A content |
| Semantic chunking | Technical docs with topic shifts |
| Hierarchical (paragraph → section → doc) | Navigation + precision retrieval |
| Proposition-based | Facts that need to be retrieved atomically |

**Chunking Anti-Patterns**
- Splitting mid-sentence — destroys context
- No overlap — misses content spanning chunk boundaries
- Ignoring document structure — treats a table of contents like body text

### Embedding Model Selection
| Use Case | Recommended Model |
|---|---|
| General purpose | `text-embedding-3-large` (OpenAI), `embed-v3` (Cohere) |
| Code | `voyage-code-2` (Voyage AI) |
| Multilingual | `multilingual-e5-large` |
| On-premise | `nomic-embed-text` (local) |

### Retrieval Pipeline
```
Query → Query expansion (HyDE or multi-query) →
Semantic search (vector similarity) →
Keyword search (BM25) →
Hybrid merge (RRF or linear combination) →
Reranking (cross-encoder) →
Top-K injection into context
```

### RAG Evaluation Metrics
| Metric | What It Measures |
|---|---|
| Retrieval recall | Was the relevant chunk retrieved? |
| Context precision | Are retrieved chunks actually relevant? |
| Faithfulness | Does the answer stay grounded in context? |
| Answer relevance | Does the answer address the question? |

Use **RAGAS** framework for automated RAG evaluation.

### Common RAG Failures
- Retrieval of irrelevant chunks → improve chunking + add metadata filters
- Context too large for LLM → use reranker to reduce to top 3–5 chunks
- Hallucination despite good retrieval → strengthen "only use provided context" instruction
- No retrieval hit → add query expansion or fallback to full-doc retrieval

---

## llm-app-patterns

### Role
LLM application engineering expert — production patterns for streaming, tool use, error handling, eval frameworks, and reliable LLM integration.

### Application Architecture Patterns

**Streaming Response Handling**
```python
with client.messages.stream(...) as stream:
    for text in stream.text_stream:
        yield text          # Stream to frontend
    final = stream.get_final_message()
```

**Tool Use Pattern**
```python
# Loop until no more tool calls
while response.stop_reason == "tool_use":
    tool_results = execute_tools(response)
    response = client.messages.create(
        messages=[*messages, response, *tool_results]
    )
```

**Retry with Backoff**
```python
@retry(wait=wait_exponential(min=1, max=60), stop=stop_after_attempt(5))
def call_llm(messages):
    return client.messages.create(...)
```

### Reliability Patterns
- **Input validation** — Validate and sanitize inputs before LLM call
- **Output validation** — Parse and validate structured outputs; retry on parse failure
- **Fallback models** — Cheaper model for simple tasks, expensive for complex
- **Circuit breaker** — Stop retrying after N consecutive failures; alert and degrade gracefully

### Evaluation Framework
```
Golden dataset → Run prompts → Score outputs →
Track: accuracy, latency, cost, token count
Alert on: accuracy regression, cost spike, latency P99 increase
```

### Cost Management
- Log token counts per request — track costs by feature/user
- Use streaming for UX, not for cost reduction
- Cache aggressive re-used context
- Route simple tasks to cheaper models (Claude Haiku vs. Opus)

---

## voice-agents

### Role
Voice AI architect who has shipped production voice agents at scale. Core insight: latency is the constraint that determines whether conversations feel natural or robotic.

### Architecture Decision
| Architecture | Latency | Control | Use Case |
|---|---|---|---|
| Speech-to-Speech (S2S) | Lowest (< 500ms) | Lower | Natural conversation, emotion |
| Pipeline (STT → LLM → TTS) | Higher (800ms–2s) | Full | Business logic, debugging |

**S2S**: OpenAI Realtime API, Gemini Live. Best for natural conversation. Less controllable.
**Pipeline**: Deepgram/Whisper (STT) → Claude/GPT-4 (LLM) → ElevenLabs/Cartesia (TTS). More controllable, easier to debug.

### Latency Budget (Pipeline)
```
STT (speech-to-text):     100–300ms
LLM first token:          200–400ms
TTS first audio chunk:    100–200ms
Network round-trips:      50–150ms
─────────────────────
Target total:             < 800ms
```

### Interruption Handling
- Detect barge-in (user speaks over agent) with VAD (Voice Activity Detection)
- Stop TTS playback immediately on barge-in
- Reset LLM context to pre-generation state
- Do NOT include interrupted agent turn in conversation history

### Conversation Design
- Keep agent turns short — 1–2 sentences, then pause
- Backchannels ("mm-hmm", "I see") reduce perceived latency
- Explicit turn-taking signals ("Go ahead" / "Your turn") for complex flows
- Graceful degradation for silence, crosstalk, and low-quality audio

### Key Providers
| Component | Options |
|---|---|
| STT | Deepgram Nova-2, OpenAI Whisper, Google STT |
| TTS | ElevenLabs, Cartesia, OpenAI TTS |
| VAD | Silero VAD, WebRTC VAD |
| S2S | OpenAI Realtime API, Gemini Live |

---

## voice-ai-development

### Role
Voice AI developer specializing in real-time audio systems — WebRTC, telephony integration, and production voice pipeline engineering.

### WebRTC Integration
```javascript
// Capture microphone audio
const stream = await navigator.mediaDevices.getUserMedia({ audio: true });
const audioContext = new AudioContext({ sampleRate: 16000 });

// Connect to VAD → send to STT on speech end
const source = audioContext.createMediaStreamSource(stream);
```

### Telephony Integration
| Platform | SDK | Use Case |
|---|---|---|
| Twilio | `twilio-node` / `twilio-python` | Phone calls, SMS escalation |
| Vonage | `@vonage/server-sdk` | International calls |
| Livekit | `livekit-server-sdk` | WebRTC rooms |
| Daily.co | `@daily-co/daily-js` | Video + voice |

### Audio Processing Checklist
- [ ] Sample rate: 16kHz for STT, 24kHz for TTS
- [ ] Format: PCM 16-bit little-endian for most STT APIs
- [ ] Noise suppression: Enable at source (browser/app) before transmission
- [ ] Echo cancellation: Required for non-headphone scenarios
- [ ] Jitter buffer: 50–100ms to handle network variation

### Production Monitoring
- Track: STT word error rate (WER), TTS success rate, turn latency P50/P99
- Alert on: latency > 1.5s, error rate > 2%, consecutive call failures

---

## agent-evaluation

### Role
Quality engineer who has seen agents that aced benchmarks fail in production. Builds evaluation frameworks that catch issues before they reach users.

### Evaluation Types
| Type | What It Measures | Frequency |
|---|---|---|
| Unit tests | Individual tool/action correctness | Every commit |
| Behavioral contracts | Invariants that must always hold | Every commit |
| Capability benchmarks | Task completion rate, accuracy | Weekly |
| Regression suite | "Must not break" scenarios | Every release |
| Red team / adversarial | Edge cases, prompt injection | Pre-release |

### Statistical Testing for Non-Deterministic Systems
```
Problem: Same input → different outputs
Solution: Run each test case N times (N ≥ 20)
Measure: Pass rate distribution, not binary pass/fail
Alert threshold: Pass rate < 90% on critical tests
```

### Behavioral Contract Testing
```python
# Invariants that must always hold
def test_never_takes_action_outside_scope():
    """Agent must never call tools outside its authorized set"""
    result = run_agent(task)
    assert all(t in AUTHORIZED_TOOLS for t in result.tools_called)

def test_always_escalates_uncertain():
    """Agent must escalate when confidence < 0.7"""
    result = run_agent(ambiguous_task)
    assert result.escalated or result.confidence > 0.7
```

### Evaluation Metrics by Task Type
| Task | Primary Metric | Secondary |
|---|---|---|
| Information retrieval | Recall@K, precision | Latency |
| Code generation | Test pass rate | Token efficiency |
| Multi-step reasoning | Task completion rate | Step accuracy |
| Classification | F1, confusion matrix | Calibration |
| Tool use | Action accuracy | Recovery rate on errors |

### Production Monitoring
- Shadow mode: Run new agent alongside production, compare outputs
- Log reasoning traces, not just final outputs
- Track: task completion rate, escalation rate, error rate, cost per task
- Canary deploys: Route 5% of traffic to new agent version before full rollout

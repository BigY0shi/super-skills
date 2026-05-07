---
name: coding-suite
description: "Full-stack coding AI covering 50+ specialist skills across language mastery, framework expertise, testing, code quality, architecture, API design, LLM development, performance, security, and developer tooling. Use for Python, TypeScript, JavaScript, Rust, Java, C#, Ruby, SQL, PHP, C, React, Next.js, NestJS, Node.js, PostgreSQL, Prisma, Angular, GraphQL, Firebase, TDD, clean code, code review, systematic debugging, refactoring, API design, database design, software architecture, prompt engineering, embedding strategies, semantic search, performance optimization, auth patterns, bun/uv/npm tooling, and developer experience. Trigger keywords: Python, TypeScript, JavaScript, Rust, Java, C#, Ruby, SQL, PHP, React, Next.js, NestJS, Node, Postgres, Prisma, GraphQL, Firebase, test, TDD, refactor, clean code, code review, debug, architecture, API, REST, database schema, LLM, embeddings, RAG, semantic search, performance, auth, JWT, OAuth, bun, uv, DX, scaffold, fullstack."
metadata:
  version: 1.0.0
  source: _Master_Library/Coding & Programming + _Master_Library/Uncategorized
---

# Coding Suite

A complete, modular coding AI covering the full software development lifecycle — from language mastery and framework expertise to testing, architecture, performance, and developer experience.

---

## How to Use This Skill

1. **Identify the task category** from the routing table below
2. **Load the matching sub-skill** from `references/skills-catalog.md`
3. **Execute** following the sub-skill's workflow

---

## Quick Routing Table

### 🐍 Language Mastery
| Task | Load |
|------|------|
| Python best practices, patterns, async, packaging, type hints | `python-pro` |
| TypeScript strict mode, advanced types, utility types, generics | `typescript-pro` |
| JavaScript 33 core concepts — closures, async/await, prototypes, modules | `javascript-mastery` |
| Rust systems programming, ownership, lifetimes, async, WASM | `rust-pro` |
| Java enterprise patterns, Spring, concurrency, JVM tuning | `java-pro` |
| C# .NET, LINQ, async, dependency injection, Avalonia | `csharp-pro` |
| Ruby idioms, metaprogramming, Rails patterns | `ruby-pro` |
| SQL query optimization, window functions, CTEs, indexing | `sql-pro` |
| PHP modern patterns, PSR standards, Laravel/Symfony idioms | `php-pro` |
| C systems programming, memory management, POSIX | `c-pro` |

### ⚛️ Framework Expertise
| Task | Load |
|------|------|
| React hooks, component patterns, state management, performance | `react-best-practices` |
| Next.js App Router, Server Components, data fetching, caching | `nextjs-best-practices` |
| NestJS module architecture, DI, guards, interceptors, pipes | `nestjs-expert` |
| Node.js runtime, streams, event loop, production patterns | `nodejs-best-practices` |
| PostgreSQL indexing, query planning, partitioning, replication | `postgres-best-practices` |
| Prisma schema design, migrations, query optimization, relations | `prisma-expert` |
| Angular modernization, migration to standalone, signals | `angular-migration` |

### 🧪 Testing
| Task | Load |
|------|------|
| TDD red-green-refactor cycle, test-first workflow | `tdd-workflow` |
| Jest patterns, factory functions, mock strategies, snapshot testing | `testing-patterns` |
| Unit test generation, coverage reporting, assertion patterns | `unit-testing` |
| Full webapp testing — integration, E2E, API contract testing | `webapp-testing` |
| LLM output evaluation, hallucination detection, benchmark design | `llm-evaluation` |

### 🧹 Code Quality
| Task | Load |
|------|------|
| Clean code principles — SRP, DRY, KISS, YAGNI, naming, structure | `clean-code` |
| Code review — constructive feedback, PR standards, mentoring | `code-review-excellence` |
| Root cause debugging — always find cause before fixing | `systematic-debugging` |
| Tech debt refactoring, context restoration, incremental improvement | `code-refactoring` |
| Production code audit — security, performance, reliability scan | `production-code-audit` |
| Linting, formatting, static analysis configuration | `lint-and-validate` |

### 🏗️ Architecture
| Task | Load |
|------|------|
| Full-stack system design, scalable architecture, tech stack decisions | `senior-architect` |
| React/Next.js/Node fullstack scaffolding, code quality analysis | `senior-fullstack` |
| Clean Architecture, DDD, early returns, library-first philosophy | `software-architecture` |
| C4 model diagrams — context, container, component, code | `c4-architecture` |
| Schema design, ORM selection (Prisma/Drizzle/Kysely), indexing | `database-design` |
| REST vs GraphQL vs tRPC decision, versioning, auth, rate limiting | `api-patterns` |

### 🔌 Backend & APIs
| Task | Load |
|------|------|
| OpenAPI/Swagger docs, endpoint documentation, schema generation | `api-documentation` |
| GraphQL schema design, resolvers, N+1 prevention, subscriptions | `graphql` |
| Firebase Auth, Firestore, Cloud Functions, Realtime Database | `firebase` |
| Neon serverless Postgres, branching, connection pooling | `neon-postgres` |
| Feature development patterns, backend architecture guidelines | `backend-development` |

### 🤖 LLM & AI Development
| Task | Load |
|------|------|
| Prompt engineering, chain-of-thought, constitutional AI, token optimization | `llm-prompt-optimize` |
| Embedding model selection, chunking strategies, similarity search | `embedding-strategies` |
| Semantic search architecture, hybrid search, ranking, retrieval | `search-specialist` |

### ⚡ Performance
| Task | Load |
|------|------|
| Core Web Vitals, Lighthouse, CPU/memory profiling, flame graphs | `performance-profiling` |
| Bundle optimization, LCP/INP/CLS, caching strategies, lazy loading | `web-performance-optimization` |
| Application-level performance — N+1, memoization, algorithmic | `application-performance` |

### 🔐 Auth & Security
| Task | Load |
|------|------|
| Authentication vulnerabilities, OWASP Top 10, broken auth patterns | `auth-security` |
| Clerk authentication integration, Next.js middleware, route protection | `clerk-auth` |
| Next.js + Supabase auth, RLS, session management | `nextjs-supabase-auth` |

### 🛠️ Developer Tooling
| Task | Load |
|------|------|
| DX optimization — reduce onboarding friction, automate workflows, IDE setup | `dx-optimizer` |
| Bun runtime, package manager, bundler, test runner | `bun-development` |
| uv Python package manager, virtual envs, dependency locking | `uv-package-manager` |
| Python packaging, pyproject.toml, distribution, publishing | `python-packaging` |
| Advanced git — rebase, worktrees, bisect, hooks, branching strategies | `git-advanced-workflows` |
| Requesting/receiving code reviews, PR etiquette, feedback culture | `code-review-workflow` |
| Co-authoring documentation, README generation, API docs | `doc-coauthoring` |

---

## Loading Sub-Skills

All sub-skill instructions are in `references/skills-catalog.md`.

```
coding-suite/
├── SKILL.md                      ← You are here (routing hub)
└── references/
    └── skills-catalog.md         ← Full instructions for all skills
```

**Always read the relevant section of `skills-catalog.md` before executing any task.**

---

## Universal Coding Standards

**Understand before fixing** — Never propose a fix without identifying the root cause first. Symptom fixes create new bugs.

**Test before shipping** — Every change has a test. TDD preferred; tests-alongside acceptable; tests-after only for exploratory code.

**Name with intent** — Variable and function names should make comments unnecessary. If you need a comment to explain a name, rename it.

**Small functions, clear responsibilities** — Max 20 lines per function. One thing, done well. Composition over complexity.

**Library-first** — Before writing custom utilities, check if a well-maintained library already solves it. Don't build what you can import.

**Performance is measured, not assumed** — Profile before optimizing. Premature optimization is the root of all evil.

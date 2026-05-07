# Coding Suite — Skills Catalog

Full instructions for all sub-skills. Read the relevant section before executing any coding task.

---

## Table of Contents

**Language Mastery**
- [python-pro](#python-pro) — Python patterns, async, type hints, packaging
- [typescript-pro](#typescript-pro) — TypeScript strict mode, advanced types, generics
- [javascript-mastery](#javascript-mastery) — 33 core JS concepts, closures, async, prototypes
- [rust-pro](#rust-pro) — Systems programming, ownership, async, WASM
- [java-pro](#java-pro) — Enterprise Java, Spring, concurrency, JVM
- [csharp-pro](#csharp-pro) — C# .NET, LINQ, async, DI, Avalonia
- [ruby-pro](#ruby-pro) — Ruby idioms, metaprogramming, Rails patterns
- [sql-pro](#sql-pro) — Query optimization, window functions, CTEs
- [php-pro](#php-pro) — Modern PHP, PSR standards, Laravel/Symfony
- [c-pro](#c-pro) — Systems programming, memory management, POSIX

**Framework Expertise**
- [react-best-practices](#react-best-practices) — Hooks, patterns, state, performance
- [nextjs-best-practices](#nextjs-best-practices) — App Router, Server Components, data fetching
- [nestjs-expert](#nestjs-expert) — Module architecture, DI, guards, interceptors
- [nodejs-best-practices](#nodejs-best-practices) — Runtime, streams, event loop, production
- [postgres-best-practices](#postgres-best-practices) — Indexing, query planning, partitioning
- [prisma-expert](#prisma-expert) — Schema design, migrations, query optimization
- [angular-migration](#angular-migration) — Modernization, standalone components, signals

**Testing**
- [tdd-workflow](#tdd-workflow) — Red-Green-Refactor cycle
- [testing-patterns](#testing-patterns) — Jest patterns, factories, mocks
- [unit-testing](#unit-testing) — Test generation, coverage, assertions
- [webapp-testing](#webapp-testing) — Integration, E2E, API contract testing
- [llm-evaluation](#llm-evaluation) — LLM output evaluation, benchmark design

**Code Quality**
- [clean-code](#clean-code) — SRP, DRY, KISS, naming, structure
- [code-review-excellence](#code-review-excellence) — PR reviews, constructive feedback, standards
- [systematic-debugging](#systematic-debugging) — Root cause analysis before any fix
- [code-refactoring](#code-refactoring) — Tech debt, incremental improvement
- [production-code-audit](#production-code-audit) — Security, performance, reliability scan
- [lint-and-validate](#lint-and-validate) — Linting, formatting, static analysis

**Architecture**
- [senior-architect](#senior-architect) — System design, architecture diagrams, tech stack decisions
- [senior-fullstack](#senior-fullstack) — Fullstack scaffolding, code quality analysis
- [software-architecture](#software-architecture) — Clean Architecture, DDD, domain design
- [c4-architecture](#c4-architecture) — C4 model diagrams
- [database-design](#database-design) — Schema, ORM selection, indexing strategy
- [api-patterns](#api-patterns) — REST vs GraphQL vs tRPC, versioning, auth

**Backend & APIs**
- [api-documentation](#api-documentation) — OpenAPI/Swagger, endpoint docs, schema gen
- [graphql](#graphql) — Schema design, resolvers, N+1 prevention
- [firebase](#firebase) — Auth, Firestore, Cloud Functions, Realtime DB
- [neon-postgres](#neon-postgres) — Serverless Postgres, branching, pooling
- [backend-development](#backend-development) — Feature development patterns, guidelines

**LLM & AI Development**
- [llm-prompt-optimize](#llm-prompt-optimize) — Prompt engineering, CoT, token optimization
- [embedding-strategies](#embedding-strategies) — Embedding models, chunking, similarity search
- [search-specialist](#search-specialist) — Semantic search, hybrid search, ranking

**Performance**
- [performance-profiling](#performance-profiling) — Core Web Vitals, Lighthouse, flame graphs
- [web-performance-optimization](#web-performance-optimization) — Bundle size, LCP/INP/CLS, caching
- [application-performance](#application-performance) — N+1, memoization, algorithmic optimization

**Auth & Security**
- [auth-security](#auth-security) — Authentication vulnerabilities, OWASP Top 10
- [clerk-auth](#clerk-auth) — Clerk integration, Next.js middleware, route protection
- [nextjs-supabase-auth](#nextjs-supabase-auth) — Supabase auth, RLS, session management

**Developer Tooling**
- [dx-optimizer](#dx-optimizer) — DX optimization, onboarding, workflow automation
- [bun-development](#bun-development) — Bun runtime, package manager, test runner
- [uv-package-manager](#uv-package-manager) — uv Python package manager, venvs
- [python-packaging](#python-packaging) — pyproject.toml, distribution, publishing
- [git-advanced-workflows](#git-advanced-workflows) — Rebase, worktrees, bisect, hooks
- [code-review-workflow](#code-review-workflow) — Requesting/receiving reviews, PR etiquette
- [doc-coauthoring](#doc-coauthoring) — README generation, API docs, co-authoring

---

---

## python-pro

**When to use:** Python-specific best practices, idioms, async patterns, type hints, or packaging.

### Core Practices
- Type hints everywhere: use `from __future__ import annotations` for forward refs; `Optional[X]` → `X | None` (Python 3.10+)
- Dataclasses and `@dataclass(frozen=True)` for value objects; Pydantic for validation
- Context managers: `with` for all resources (files, DB connections, locks)
- Async: `asyncio`, `async/await`, `aiohttp`; never block the event loop with sync I/O
- List/dict/set comprehensions over `map`/`filter`
- `pathlib.Path` over `os.path` for file operations
- Walrus operator `:=` for assignment in conditions (Python 3.8+)
- `__slots__` for memory-critical classes

### Patterns
```python
# Prefer
result = [process(item) for item in items if item.is_valid()]

# Avoid
result = list(map(process, filter(lambda x: x.is_valid(), items)))
```

### Tooling
- **uv** for dependency management (replaces pip + virtualenv)
- **ruff** for linting + formatting (replaces black + isort + flake8)
- **mypy** or **pyright** for type checking
- **pytest** with fixtures, parametrize, conftest.py

---

## typescript-pro

**When to use:** TypeScript type system problems, strict mode configuration, advanced generic types, or TypeScript-specific patterns.

### Strict Mode Essentials
TypeScript strict mode is NOT enabled by default in CRA or Vite — must add to `tsconfig.json`:
```json
{ "compilerOptions": { "strict": true } }
```
Strict enables: `strictNullChecks`, `noImplicitAny`, `strictFunctionTypes`, and more.

### Advanced Type Patterns
```typescript
// Discriminated unions
type Result<T> = { ok: true; data: T } | { ok: false; error: Error };

// Template literal types
type EventName = `on${Capitalize<string>}`;

// Conditional types
type NonNullable<T> = T extends null | undefined ? never : T;

// Mapped types
type Partial<T> = { [K in keyof T]?: T[K] };

// Infer in conditional types
type ReturnType<T> = T extends (...args: any[]) => infer R ? R : never;
```

### Key Rules
- Prefer `interface` for object shapes (extensible), `type` for unions/intersections
- Never use `any` — use `unknown` + type guards instead
- Avoid `as` casting except at verified boundaries (API responses after validation)
- Use `satisfies` operator to validate type without widening

---

## javascript-mastery

**When to use:** Explaining JavaScript concepts, debugging tricky JS behavior, or reviewing code for JS best practices.

### 33 Core Concepts (Reference)
1. **Call Stack** — LIFO execution context; stack overflow from unbounded recursion
2. **Primitive Types** — string, number, bigint, boolean, undefined, symbol, null (7 primitives)
3. **Value vs. Reference** — primitives by value, objects/arrays/functions by reference
4. **Type Coercion** — `==` coerces, `===` strict; prefer `===` always
5. **Closures** — inner function captures outer scope; enables private state, factories
6. **Scope** — `let`/`const` block-scoped, `var` function-scoped; avoid `var`
7. **Hoisting** — `var` declarations hoisted (not initializations); `function` declarations fully hoisted
8. **Prototypal Inheritance** — `Object.create()`, `__proto__`, prototype chain lookups
9. **`this`** — depends on call site; arrow functions inherit `this` lexically
10. **Event Loop** — call stack + microtask queue (Promises) + macrotask queue (setTimeout)
11. **Promises** — async chaining; prefer `async/await` for readability
12. **async/await** — syntactic sugar over Promises; always `try/catch` or `.catch()`
13. **Modules** — ES modules (`import`/`export`), tree-shakeable; avoid CommonJS in new code
14. **Destructuring** — `const { a, b } = obj`; default values, rename with `:`, rest with `...`
15. **Spread/Rest** — `...` for array/object spread and function rest params
16. **Map/Set** — keyed collections; Map for non-string keys; Set for unique values
17. **WeakMap/WeakRef** — memory-sensitive caching without preventing GC

---

## rust-pro

**When to use:** Rust systems programming, ownership/borrow checker issues, async Rust, FFI, or WASM compilation.

### Core Concepts
- **Ownership**: each value has one owner; moved on assignment, not copied (unless `Copy` trait)
- **Borrowing**: `&T` (shared, immutable), `&mut T` (exclusive, mutable); no dangling references
- **Lifetimes**: `'a` annotations when compiler can't infer borrow durations
- **Error handling**: `Result<T, E>` for recoverable errors; `?` operator for propagation; `unwrap()` only in tests/prototypes
- **Traits**: interfaces for polymorphism; `impl Trait` for simple cases, `dyn Trait` for runtime dispatch
- **Async**: Tokio runtime; `async fn` returns `Future`; `.await` to drive futures

### Common Patterns
```rust
// Error propagation
fn read_config(path: &str) -> Result<Config, Box<dyn Error>> {
    let content = fs::read_to_string(path)?;
    let config: Config = serde_json::from_str(&content)?;
    Ok(config)
}

// Builder pattern
let client = reqwest::Client::builder()
    .timeout(Duration::from_secs(30))
    .build()?;
```

---

## java-pro

**When to use:** Java enterprise patterns, Spring Boot/Framework configuration, concurrency issues, or JVM performance tuning.

### Core Coverage
- Spring Boot: auto-configuration, `@Bean`, `@Component`, `@Service`, dependency injection, `@ConfigurationProperties`
- Spring MVC / WebFlux: `@RestController`, `@RequestMapping`, request validation, exception handling
- JPA/Hibernate: entity design, lazy vs. eager loading, N+1 problem (use `@EntityGraph`), transactions
- Concurrency: `CompletableFuture`, `ExecutorService`, virtual threads (Java 21), `synchronized` vs `ReentrantLock`
- Records (Java 16+): immutable data carriers, replace simple POJOs
- Streams API: `filter`/`map`/`collect`; `Collectors.groupingBy`, `partitioningBy`
- JVM tuning: heap sizing (`-Xmx`, `-Xms`), GC selection (G1 default, ZGC for low latency)

---

## csharp-pro

**When to use:** C# patterns, .NET configuration, LINQ optimization, async/await, or Avalonia/WPF UI development.

### Core Coverage
- `async`/`await`: `Task`, `ValueTask` for hot paths; `ConfigureAwait(false)` in library code
- LINQ: prefer method syntax; avoid N+1 with `.Include()` in EF Core; use `IAsyncEnumerable` for streaming
- Dependency injection: built-in Microsoft DI; scoped/transient/singleton lifetimes
- Records: `record Person(string Name, int Age);` for immutable value objects
- Pattern matching: `switch` expressions, `is` patterns, property patterns
- Nullable reference types: enable in project settings; `?` for nullable, `!` for null-forgiveness sparingly
- Avalonia: MVVM pattern, reactive bindings, Zafiro toolkit for UI components

---

## ruby-pro

**When to use:** Ruby idioms, metaprogramming, Rails patterns, or Gem development.

### Core Coverage
- Symbols vs strings: symbols for hash keys, method names, identifiers (immutable, interned)
- Blocks, Procs, Lambdas: `yield` for simple block patterns; `Proc.new` vs `lambda` (return behavior differs)
- Modules for mixins: `include` for instance methods, `extend` for class methods, `prepend` for overriding
- Metaprogramming: `method_missing`, `define_method`, `class_eval` — use sparingly with documentation
- Rails: fat models (service objects for complex logic), thin controllers, concerns for shared behavior
- Active Record patterns: scopes, callbacks, validations; avoid callbacks for non-persistence concerns

---

## sql-pro

**When to use:** Writing or optimizing SQL queries, designing schemas, understanding query plans, or implementing complex analytics.

### Core Patterns
```sql
-- Window functions
SELECT
  user_id,
  revenue,
  SUM(revenue) OVER (PARTITION BY user_id ORDER BY date) AS running_total,
  RANK() OVER (PARTITION BY region ORDER BY revenue DESC) AS rank
FROM orders;

-- CTEs for readability
WITH monthly_revenue AS (
  SELECT DATE_TRUNC('month', created_at) AS month, SUM(amount) AS revenue
  FROM orders GROUP BY 1
),
growth AS (
  SELECT month, revenue,
         LAG(revenue) OVER (ORDER BY month) AS prev_revenue
  FROM monthly_revenue
)
SELECT month, revenue,
       (revenue - prev_revenue) / prev_revenue * 100 AS growth_pct
FROM growth;
```

### Optimization Rules
- `EXPLAIN ANALYZE` before assuming you know the slow part
- Indexes on columns in `WHERE`, `JOIN ON`, `ORDER BY`, `GROUP BY`
- Avoid `SELECT *` in production queries
- Use `LIMIT` during development
- `COUNT(1)` vs `COUNT(*)` — functionally identical in PostgreSQL

---

## php-pro

**When to use:** Modern PHP development, PSR standards, Laravel/Symfony patterns, or PHP 8.x features.

### Core Coverage
- PHP 8.x: named arguments, match expressions, nullsafe operator `?->`, fibers, readonly properties
- PSR standards: PSR-4 (autoloading), PSR-7 (HTTP messages), PSR-12 (coding style)
- Type system: strict types (`declare(strict_types=1)`), union types, intersection types, never type
- Laravel: Eloquent ORM patterns, service providers, middleware, Artisan commands, queues
- Composer: dependency management, autoloading, version constraints, lock file importance
- Error handling: `Throwable`, custom exception hierarchy, proper logging

---

## c-pro

**When to use:** C systems programming, memory management, POSIX API usage, or writing C extensions.

### Core Coverage
- Memory management: `malloc`/`free` discipline, valgrind for leak detection, RAII-style cleanup with `goto err`
- Pointer arithmetic: bounds checking, null checks before dereference, `const` correctness
- POSIX: file I/O, signals, `fork`/`exec`, pipes, sockets, pthreads
- Safe string handling: prefer `strlcpy`/`strlcat` over `strcpy`/`strcat`; bounded `snprintf`
- Undefined behavior: signed overflow, out-of-bounds access, strict aliasing — use `-fsanitize=address,undefined`
- Build system: `Makefile` essentials, `gcc`/`clang` warning flags (`-Wall -Wextra -Werror`)

---

---

## react-best-practices

**When to use:** React hooks, component patterns, state management decisions, or performance optimization.

### Component Decision Tree
```
Does it need useState, useEffect, event handlers? → Client Component
Does it just fetch data and render? → Server Component (Next.js)
Both? → Server parent, Client child
```

### Hook Patterns
- `useState`: local UI state only — not for server data
- `useEffect`: side effects only; always clean up subscriptions
- `useCallback`/`useMemo`: only when proven expensive — profile first
- Custom hooks: extract stateful logic; name starting with `use`

### State Management
| Complexity | Solution |
|-----------|---------|
| Local UI state | `useState` |
| Shared UI state | `useContext` + `useReducer` |
| Server state | TanStack Query / SWR |
| Global app state | Zustand / Jotai |
| Form state | React Hook Form |

### Performance
- `React.memo` on components with stable props; check with React DevTools profiler first
- Avoid anonymous functions in JSX for event handlers on frequently re-rendered components
- Keys: stable, unique, never array index for reorderable lists

---

## nextjs-best-practices

**When to use:** Next.js App Router development, Server vs. Client component decisions, or data fetching patterns.

### Server vs. Client
- **Server Components** (default): data fetching, layout, static content, no browser APIs
- **Client Components** (`'use client'`): interactive UI, hooks, event handlers, browser APIs
- Split strategy: Server parent wraps Client child — never the reverse

### Data Fetching
```typescript
// Server Component — fetch directly
async function Page() {
  const data = await fetch('https://api.example.com/data', {
    next: { revalidate: 60 } // ISR: revalidate every 60s
  });
  return <Component data={data} />;
}

// Client Component — use SWR/React Query
'use client';
function Component() {
  const { data } = useSWR('/api/data');
}
```

### Caching Strategy
- `{ cache: 'no-store' }` → dynamic (always fetch)
- `{ next: { revalidate: N } }` → ISR (revalidate after N seconds)
- Default → static (cached indefinitely, revalidated on deploy)

### Route Handlers
Use `app/api/route.ts` only when you need: webhooks, mutations, auth callbacks, or server-only operations. Prefer Server Actions for form mutations.

---

## nestjs-expert

**When to use:** NestJS module architecture, dependency injection issues, guard/interceptor/pipe implementation, or NestJS testing.

### Core Architecture
- **Modules**: organize by feature domain, not technical layer. Each module declares providers, imports, exports.
- **DI**: constructor injection always. Use `forwardRef()` sparingly for circular deps.
- **Guards**: authentication/authorization (`@UseGuards(JwtAuthGuard)`)
- **Interceptors**: transform response, logging, caching (`@UseInterceptors(CacheInterceptor)`)
- **Pipes**: input validation/transformation (`ValidationPipe` globally)
- **Exception Filters**: `@Catch(HttpException)` for consistent error responses

### Validation Setup
```typescript
// main.ts — global ValidationPipe
app.useGlobalPipes(new ValidationPipe({
  whitelist: true,     // strip unknown properties
  forbidNonWhitelisted: true,
  transform: true,     // auto-transform primitives
}));
```

### Testing
```typescript
// Unit test with mock
const module = await Test.createTestingModule({
  providers: [
    UserService,
    { provide: UserRepository, useValue: mockUserRepository },
  ],
}).compile();
```

---

## nodejs-best-practices

**When to use:** Node.js runtime behavior, event loop issues, streams, production hardening, or CommonJS vs ESM.

### Event Loop Rules
- Never block the event loop: no `fs.readFileSync`, no synchronous crypto, no heavy computation on main thread
- CPU-intensive work → Worker Threads
- I/O-bound work → async/await with native promises

### Production Patterns
- Graceful shutdown: handle `SIGTERM`, drain connections, close DB pools
- Health check endpoint: `/health` returning 200 when ready to serve
- Clustering: `cluster` module or PM2 for multi-core utilization
- Memory management: monitor heap usage; tune `--max-old-space-size`
- Error handling: uncaughtException + unhandledRejection as last-resort loggers (not recovery)

### ESM vs CommonJS
Prefer ESM (`import`/`export`) for new projects. Use `"type": "module"` in package.json. Interop issues: `createRequire()` for CJS in ESM context.

---

## postgres-best-practices

**When to use:** PostgreSQL query optimization, indexing strategy, partitioning, replication, or PostgreSQL-specific features.

### Index Strategy
- B-tree (default): equality and range queries
- GIN: JSONB, arrays, full-text search
- GiST: geometric types, `pg_trgm` similarity
- Partial indexes: `CREATE INDEX ON orders (user_id) WHERE status = 'pending'`
- Composite indexes: column order matters — most selective/commonly filtered first

### Query Optimization
```sql
-- Always EXPLAIN ANALYZE in dev
EXPLAIN (ANALYZE, BUFFERS) SELECT ...;

-- Look for:
-- Seq Scan on large tables → missing index
-- Nested Loop with large row estimates → statistics stale (run ANALYZE)
-- Hash Join vs Merge Join → set work_mem appropriately
```

### JSONB Best Practices
- Use `jsonb` (binary) not `json` (text) for querying
- Index specific keys: `CREATE INDEX ON events ((data->>'type'))`
- GIN index for containment: `CREATE INDEX ON events USING gin(data)`

---

## prisma-expert

**When to use:** Prisma schema design, relationship modeling, migration management, or query optimization.

### Schema Patterns
```prisma
model User {
  id        String   @id @default(cuid())
  email     String   @unique
  posts     Post[]
  profile   Profile? @relation(fields: [profileId], references: [id])
  profileId String?  @unique
  createdAt DateTime @default(now())
  updatedAt DateTime @updatedAt
}
```

### N+1 Prevention
```typescript
// ❌ N+1
const users = await prisma.user.findMany();
for (const user of users) {
  const posts = await prisma.post.findMany({ where: { userId: user.id } });
}

// ✅ Include
const users = await prisma.user.findMany({
  include: { posts: true }
});
```

### Migration Best Practices
- Never edit migration files after they're applied to any environment
- Use `prisma migrate dev` for development, `prisma migrate deploy` for production
- Shadow database for migration safety checks in CI

---

## angular-migration

**When to use:** Migrating Angular applications to standalone components, adopting Angular signals, or updating to modern Angular patterns.

### Migration Path
1. **Standalone components**: remove `NgModule` declarations; add `standalone: true` + `imports: []` directly in component
2. **Signals** (Angular 17+): replace `Subject`/`BehaviorSubject` with `signal()`, `computed()`, `effect()`
3. **Control Flow** (Angular 17+): `@if`, `@for`, `@switch` replace `*ngIf`, `*ngFor`, `ngSwitch`
4. **Inject function**: `inject(Service)` in constructors and factory functions instead of constructor injection

---

---

## tdd-workflow

**When to use:** Implementing features test-first, following red-green-refactor discipline, or establishing TDD culture.

### The Three Laws
1. Write production code ONLY to make a failing test pass
2. Write ONLY enough test to demonstrate failure (compilation failure counts)
3. Write ONLY enough code to make the test pass

### The Cycle
```
🔴 RED → Write failing test (test name = expected behavior)
    ↓
🟢 GREEN → Minimum code to pass (YAGNI — no over-engineering)
    ↓
🔵 REFACTOR → Improve quality without changing behavior (tests stay green)
    ↓
   Repeat...
```

### Good Test Names
- `should_return_empty_array_when_no_items_match`
- `throws_validation_error_when_email_is_missing`
- `calculates_total_including_tax_for_us_orders`

### What to Test
- Behavior, not implementation: test what the function does, not how
- Edge cases: empty inputs, null, max values, concurrent access
- Error states: what happens when dependencies fail

---

## testing-patterns

**When to use:** Writing Jest tests, creating test factories, implementing mock strategies, or organizing test suites.

### Factory Pattern
```typescript
// getMockUser — always use factories, not inline objects
const getMockUser = (overrides: Partial<User> = {}): User => ({
  id: 'user-1',
  email: 'test@example.com',
  name: 'Test User',
  createdAt: new Date('2024-01-01'),
  ...overrides,
});

// Usage
const user = getMockUser({ email: 'admin@example.com' });
```

### Mock Strategies
```typescript
// Module mock
jest.mock('../services/emailService', () => ({
  sendEmail: jest.fn().mockResolvedValue({ success: true }),
}));

// Spy (keeps implementation, tracks calls)
const spy = jest.spyOn(service, 'method').mockReturnValue('mocked');

// Clear between tests
beforeEach(() => jest.clearAllMocks());
```

### Structure: AAA
```typescript
it('should charge the correct amount', async () => {
  // Arrange
  const user = getMockUser();
  const mockCharge = jest.fn().mockResolvedValue({ id: 'ch_123' });

  // Act
  const result = await chargeUser(user, 100, mockCharge);

  // Assert
  expect(mockCharge).toHaveBeenCalledWith(user.id, 100);
  expect(result.chargeId).toBe('ch_123');
});
```

---

## unit-testing

**When to use:** Generating unit tests for existing code, improving test coverage, or writing assertions for complex logic.

### Coverage Strategy
- Target behavior coverage, not line coverage
- 100% line coverage with bad tests is worse than 80% with good tests
- Prioritize: core business logic → error paths → edge cases → happy paths

### Test Generation Workflow
1. Read the function signature and behavior
2. Identify: inputs, outputs, side effects, error conditions
3. Write tests for: typical case, boundary values, error case, null/empty inputs
4. For async: test both resolution and rejection paths

---

## webapp-testing

**When to use:** Setting up integration tests, E2E tests with Playwright/Cypress, or API contract testing.

### Testing Pyramid
```
         /\
        /E2E\      ← Few, slow, high value (critical user paths)
       /------\
      /  Integ  \   ← Some (service boundaries, DB interactions)
     /------------\
    /   Unit Tests  \  ← Many, fast, isolated
   /------------------\
```

### Playwright E2E Pattern
```typescript
test('user can complete checkout', async ({ page }) => {
  await page.goto('/products');
  await page.click('[data-testid="add-to-cart"]');
  await page.click('[data-testid="checkout-button"]');
  await page.fill('[name="email"]', 'test@example.com');
  await page.click('[type="submit"]');
  await expect(page.locator('[data-testid="success"]')).toBeVisible();
});
```

---

## llm-evaluation

**When to use:** Evaluating LLM output quality, designing benchmarks, detecting hallucinations, or measuring prompt improvements.

### Evaluation Types
- **Automated**: exact match, ROUGE/BLEU scores, regex matching for structured output
- **LLM-as-judge**: use a separate model to evaluate output quality against criteria
- **Human evaluation**: ground truth labeling, preference comparison (A/B)

### Key Metrics
- **Faithfulness**: does the output stick to provided context? (RAG systems)
- **Relevance**: does the answer address the question?
- **Hallucination rate**: claims not supported by source material
- **Task completion**: did the model complete the specified task?

### Eval Dataset Design
- Include: typical cases, edge cases, adversarial inputs, real user queries
- Label expected outputs or evaluation criteria
- Track distribution: don't bias toward easy cases

---

---

## clean-code

**When to use:** Applying coding standards, reviewing code for clarity, or establishing team coding principles.

### Core Principles
| Principle | Rule |
|-----------|------|
| **SRP** | Each function/class does ONE thing |
| **DRY** | Extract duplicates — 3+ repetitions = abstraction time |
| **KISS** | Simplest solution that works |
| **YAGNI** | Don't build features not needed now |
| **Boy Scout** | Leave code cleaner than you found it |

### Naming Rules
- Variables: reveal intent (`userCount`, not `n`)
- Functions: verb + noun (`getUserById`, not `user`)
- Booleans: question form (`isActive`, `hasPermission`, `canEdit`)
- Constants: `SCREAMING_SNAKE_CASE`
- If you need a comment to explain a name → rename it

### Function Rules
- Max 20 lines; ideally 5-10
- Max 3 parameters (prefer 0-2; use object for more)
- One level of abstraction per function
- Guard clauses for early returns instead of nested ifs

### What NOT to Do
- Comments that explain *what* the code does (code should be self-explanatory)
- Magic numbers (use named constants)
- Abbreviations (save characters, lose readability)
- Deep nesting (> 2 levels is a smell)

---

## code-review-excellence

**When to use:** Conducting code reviews, establishing review standards, or mentoring developers through feedback.

### Review Mindset
**Purpose**: catch bugs, share knowledge, maintain standards, improve design — NOT to show superiority or block progress.

### Feedback Quality
```
❌ "This is wrong."
✅ "This could cause a race condition when multiple concurrent requests
    come in. Consider using a mutex or atomic operation here."

❌ "Why didn't you use the Repository pattern?"
✅ "[Optional] The Repository pattern might make this easier to unit test
    by abstracting the DB call. Worth considering if we add more DB logic."

❌ "Rename this."
✅ "[nit] Consider `userCount` instead of `uc` for clarity — not blocking."
```

### Priority Levels
- **[MUST]**: Correctness, security, data loss risk — blocks merge
- **[SHOULD]**: Performance, maintainability, standards — discuss before merging
- **[nit]**: Style, naming, minor formatting — take or leave, doesn't block
- **[optional]**: Ideas, alternatives, future considerations — not required

### What to Check
1. Correctness: does it do what the PR says it does?
2. Security: injection, auth bypass, sensitive data exposure
3. Tests: are edge cases and error paths covered?
4. Performance: N+1 queries, unnecessary re-renders, unbounded loops
5. Error handling: what happens when dependencies fail?

---

## systematic-debugging

**When to use:** Encountering any bug, test failure, or unexpected behavior — BEFORE proposing fixes.

### The Iron Law
**No fix without root cause.** Symptom patches mask the real problem and create new bugs.

### Four Phases (complete in order)

**Phase 1 — Root Cause Investigation**
- Read ALL error messages completely. Stack traces contain the answer more often than not.
- Reproduce consistently. If you can't reproduce, you can't verify the fix.
- Note the exact conditions: specific inputs, order of operations, environment

**Phase 2 — Hypothesis Formation**
- Generate 3 possible causes before testing any
- Rank by likelihood
- Identify what evidence would confirm/deny each

**Phase 3 — Systematic Elimination**
- Binary search: change one variable at a time
- `git bisect` for regressions — find the exact commit that introduced the bug
- Add logging/assertions to narrow the location

**Phase 4 — Verified Fix**
- Apply fix only after Phase 1-3 confirm the root cause
- Verify symptom resolves
- Add regression test so it never returns
- Document the root cause in the PR

---

## code-refactoring

**When to use:** Reducing technical debt, improving code structure without changing behavior, or restoring context before modifying legacy code.

### Context Restoration (before touching legacy code)
1. Read the file fully — understand the intention, not just the mechanics
2. Run existing tests to establish green baseline
3. Add characterization tests for untested behavior before changing anything
4. Only then: refactor with tests as safety net

### Refactoring Priorities
1. Extract long functions (> 20 lines) into named, single-purpose functions
2. Remove duplication (3+ repetitions → shared utility or abstraction)
3. Simplify conditionals (guard clauses, early returns, replace nested ifs)
4. Rename for clarity (rename takes 30 seconds, saves hours of confusion)
5. Remove dead code (delete, don't comment out)

### Safe Refactoring Steps
- One transformation at a time: extract method → rename → move — commit after each
- Never refactor and add features in the same commit
- Keep tests green throughout

---

## production-code-audit

**When to use:** Auditing code before production release, finding security vulnerabilities, performance issues, or reliability concerns.

### Security Checks
- SQL injection: parameterized queries everywhere, no string concatenation in queries
- XSS: output encoding, CSP headers, no `dangerouslySetInnerHTML` with user content
- Auth: verify authentication on every protected route, not just the entry point
- Secrets: no hardcoded API keys, passwords, or tokens
- Dependencies: `npm audit`, `pip audit` — check for known vulnerabilities

### Performance Checks
- N+1 queries: every ORM call inside a loop is suspicious
- Unbounded queries: `findAll()` without limits on large tables
- Missing indexes: check query plans for Seq Scans on frequently queried columns
- Memory leaks: unclosed connections, event listeners without cleanup

### Reliability Checks
- Error handling: every async operation has error handling
- Timeouts: external HTTP calls have timeouts configured
- Retry logic: idempotent operations should retry on transient failures
- Graceful degradation: what happens when a dependency is down?

---

## lint-and-validate

**When to use:** Configuring linting, setting up pre-commit hooks, or running static analysis.

### Tool Stack by Language
| Language | Linter | Formatter |
|----------|--------|-----------|
| JavaScript/TypeScript | ESLint | Prettier |
| Python | Ruff (lint + format) | Ruff |
| Rust | Clippy | rustfmt |
| Go | staticcheck | gofmt |
| Shell | ShellCheck | shfmt |

### Pre-commit Hook Setup
```yaml
# .pre-commit-config.yaml
repos:
  - repo: https://github.com/pre-commit/pre-commit-hooks
    hooks:
      - id: trailing-whitespace
      - id: end-of-file-fixer
      - id: check-yaml
  - repo: https://github.com/astral-sh/ruff-pre-commit
    hooks:
      - id: ruff
      - id: ruff-format
```

---

---

## senior-architect

**When to use:** System architecture design, technology stack decisions, architecture diagrams, or evaluating architectural trade-offs.

### Capability Areas
- Architecture diagram generation (C4, sequence, ERD via scripts)
- Tech stack decision frameworks: React/Next.js/Node/Postgres/GraphQL/Go/Python
- Dependency analysis: identify coupling, circular dependencies, abstraction violations
- Non-functional requirements: scalability, availability, security, maintainability tradeoffs
- ADR (Architecture Decision Records): document decisions with context, options, consequences

### Decision Framework
1. **Understand constraints first**: team size, budget, timeline, existing tech, compliance requirements
2. **Generate 2-3 options** with explicit tradeoffs
3. **Select by constraints**, not personal preference
4. **Document the decision**: ADR with context, decision, consequences, alternatives rejected

---

## senior-fullstack

**When to use:** Scaffolding full-stack projects, code quality analysis across the stack, or architecture patterns for React/Next.js/Node applications.

### Stack: React + Next.js + Node.js + GraphQL + PostgreSQL

### Project Scaffolding Principles
- Monorepo with Turborepo for large projects; single repo for small-medium
- Shared types package between frontend and backend
- Environment validation at startup (not silently undefined)
- Database migrations committed to version control

### Code Quality Analysis
- Check for: missing error boundaries, unhandled promise rejections, type assertions bypassing validation
- Verify: consistent error response format, auth checks on all protected routes, proper environment variable handling

---

## software-architecture

**When to use:** Clean Architecture, Domain-Driven Design, applying SOLID principles, or making architectural decisions for new features.

### Core Principles
- **Early return pattern**: guard clauses over nested conditions
- **Decompose long components**: > 80 lines → split; files > 200 lines → split into multiple files
- **Library-first**: search npm/PyPI before writing custom utilities (use `cockatiel` not custom retry logic)
- **Arrow functions** over function declarations in modern JS/TS

### Clean Architecture Layers
```
Domain (entities, value objects, domain services)
    ↑ depends on nothing
Application (use cases, application services)
    ↑ depends on Domain only
Infrastructure (DB, external APIs, file system)
    ↑ implements Domain interfaces
Presentation (HTTP controllers, UI components)
    ↑ calls Application layer
```

### DDD Building Blocks
- **Entity**: has identity, mutable state (User, Order)
- **Value Object**: defined by attributes, immutable (Money, Address)
- **Aggregate**: cluster of entities with one root; transactions cross aggregate boundary only via events
- **Repository**: collection-like interface for aggregates
- **Domain Event**: something that happened in the domain

---

## c4-architecture

**When to use:** Creating C4 model diagrams at any level — context, container, component, or code.

### Levels
- **L1 Context**: system + external actors. Audience: everyone. Tool: Mermaid flowchart.
- **L2 Container**: deployable units (SPA, API, DB, queue). Audience: technical team.
- **L3 Component**: inside one container (controllers, services, repos). Audience: developers.
- **L4 Code**: class/function level. Rarely worth maintaining.

### Output Preference
Mermaid for portability, inline rendering in GitHub/Notion. PlantUML for C4 purists (use `C4Container.puml` stdlib).

---

## database-design

**When to use:** Database schema design, ORM selection, indexing strategy, or normalization decisions.

### Decision Checklist
- [ ] Ask user about database preference before assuming PostgreSQL
- [ ] Consider deployment: serverless (Neon, PlanetScale), managed (RDS), self-hosted
- [ ] ORM: Prisma (type-safe, great DX), Drizzle (lightweight, raw SQL feel), Kysely (query builder)

### Schema Design Rules
- Use surrogate keys (CUID, UUID, serial) as primary keys
- Soft deletes: `deleted_at TIMESTAMP NULL` — query with `WHERE deleted_at IS NULL`
- Audit columns: `created_at`, `updated_at` on every table
- Avoid EAV (entity-attribute-value) pattern — use JSONB for flexible attributes instead
- Normalize to 3NF for transactional data; denormalize intentionally for read-heavy analytics

---

## api-patterns

**When to use:** Designing APIs, choosing between REST/GraphQL/tRPC, API versioning, or auth pattern selection.

### Style Selection
| Criteria | REST | GraphQL | tRPC |
|----------|------|---------|------|
| Public API | ✅ | ✅ | ❌ |
| Complex queries, flexible clients | ✅ | ✅✅ | ❌ |
| TypeScript monorepo | ✅ | ✅ | ✅✅ |
| Mobile clients (bandwidth sensitive) | ✅ | ✅✅ | ❌ |

### REST Best Practices
- Nouns not verbs: `/orders/{id}` not `/getOrder/{id}`
- Correct HTTP methods: GET (safe/idempotent), POST (create), PUT (replace), PATCH (partial), DELETE
- Status codes: 200 OK, 201 Created, 204 No Content, 400 Bad Request, 401 Unauthorized, 403 Forbidden, 404 Not Found, 409 Conflict, 422 Unprocessable, 429 Rate Limited, 500 Internal

### Versioning Strategy
- URI versioning (`/v1/orders`) for public APIs — most visible, easiest to document
- Header versioning (`API-Version: 2024-01`) for internal APIs
- Never break existing versions; deprecate with sunset headers

---

---

## api-documentation

**When to use:** Writing OpenAPI/Swagger specifications, generating API docs from code, or creating developer-friendly documentation.

### OpenAPI Best Practices
- Document every response: success AND error cases
- Use `$ref` to reuse common schemas
- Include examples in schemas
- Describe security schemes (Bearer, API Key, OAuth2)
- Use `operationId` for SDK generation

### Code-First vs. Spec-First
- **Spec-first**: write `openapi.yaml`, generate server stubs — better for team contracts
- **Code-first**: annotations in code, generate spec — faster for solo/small team

---

## graphql

**When to use:** GraphQL schema design, resolver implementation, N+1 prevention with DataLoader, or GraphQL security.

### Schema Design
- Queries: idempotent reads. Mutations: state changes. Subscriptions: real-time.
- Connection pattern for pagination: `edges`, `node`, `pageInfo`, `cursor`
- Input types for mutations: `CreateOrderInput` not inline args

### N+1 Solution: DataLoader
```typescript
const userLoader = new DataLoader(async (ids: string[]) => {
  const users = await db.user.findMany({ where: { id: { in: ids } } });
  return ids.map(id => users.find(u => u.id === id));
});

// Resolver — batched automatically
resolver: (post) => userLoader.load(post.authorId)
```

### Security
- Depth limiting: prevent deeply nested queries from killing the DB
- Query complexity: assign cost to fields, reject queries over threshold
- Disable introspection in production (leaks schema)

---

## firebase

**When to use:** Firebase Auth, Firestore data modeling, Cloud Functions, or Realtime Database patterns.

### Firestore Data Modeling
- Denormalize aggressively: Firestore charges per read, not per document size
- Subcollections for one-to-many: `users/{uid}/orders/{orderId}`
- Flatten for simple relationships: store `authorName` alongside `authorId`
- Security Rules: validate data shape and auth; never trust client-side

```javascript
// Security Rules
match /users/{userId} {
  allow read: if request.auth != null;
  allow write: if request.auth.uid == userId;
}
```

---

## neon-postgres

**When to use:** Neon serverless Postgres setup, database branching, connection pooling, or serverless-optimized queries.

### Key Features
- **Branching**: create instant DB branches for each PR — `neon branches create --parent main`
- **Autoscaling**: scales to zero when idle; scales up on demand
- **Connection pooling**: use Neon's built-in pooler for serverless (PgBouncer-compatible)
- **Serverless driver**: `@neondatabase/serverless` for edge functions (uses HTTP transport)

### Connection for Serverless
```typescript
// For edge/serverless (HTTP transport)
import { neon } from '@neondatabase/serverless';
const sql = neon(process.env.DATABASE_URL);
const users = await sql`SELECT * FROM users WHERE active = true`;

// For Node.js (standard pg)
import { Pool } from '@neondatabase/serverless';
const pool = new Pool({ connectionString: process.env.DATABASE_URL });
```

---

## backend-development

**When to use:** Implementing backend features, following backend architecture guidelines, or designing service layer patterns.

### Feature Development Pattern
1. **Schema first**: define the data model and API contract before writing business logic
2. **Repository layer**: abstract DB access; enables testing without real DB
3. **Service layer**: orchestrates business logic; calls repositories; no HTTP concerns
4. **Controller layer**: HTTP only — validate input, call service, return response
5. **Integration test**: test the service layer with a real (test) DB

---

---

## llm-prompt-optimize

**When to use:** Improving prompts for LLM applications, reducing token costs, or applying prompt engineering patterns.

### Techniques
- **Chain-of-Thought**: "Let's think step by step" — improves reasoning on complex tasks
- **Few-shot examples**: 3-5 examples in the prompt; must be diverse and representative
- **Constitutional AI**: add a self-critique step after generation
- **Output format specification**: specify JSON schema, structure, length constraints
- **Negative examples**: "Do NOT do X" with an example is more effective than just "Do Y"

### Token Optimization
- System prompt caching (Anthropic/OpenAI): static system prompts cached across calls
- Remove redundancy: don't repeat context already in the conversation
- Summarize long contexts: summarize old conversation turns rather than truncating

---

## embedding-strategies

**When to use:** Selecting embedding models, designing chunking pipelines, or optimizing retrieval quality for RAG systems.

### Model Selection
| Model | Dimensions | Best For |
|-------|-----------|----------|
| `text-embedding-3-small` | 1536 | Cost-efficient, general purpose |
| `text-embedding-3-large` | 3072 | Higher accuracy, larger docs |
| `cohere-embed-v3` | 1024 | Multilingual, reranking |
| `bge-m3` (local) | 1024 | No API cost, privacy |

### Chunking Strategies
- **Fixed-size**: 512 tokens, 50-100 token overlap. Simple, consistent.
- **Semantic**: split on sentence/paragraph boundaries. Better coherence.
- **Hierarchical**: small chunks for retrieval, larger chunks for context. Best quality.

### Quality Improvement
1. Reranking: retrieve top-20, rerank to top-5 with a cross-encoder
2. Hybrid search: vector + BM25 keyword; combine with RRF (Reciprocal Rank Fusion)
3. Metadata filtering: filter by date, source, category before vector search
4. Query expansion: generate alternative phrasings before embedding

---

## search-specialist

**When to use:** Building semantic search systems, optimizing search ranking, or implementing hybrid search.

### Architecture Pattern
```
Query → Embed query → ANN search → Rerank → Return top-K
              ↕
         Hybrid: also BM25 keyword → merge with RRF
```

### Ranking Signals
- **Semantic similarity**: cosine/dot product similarity from embedding
- **BM25**: term frequency + inverse document frequency for keyword relevance
- **Freshness**: recency boost for time-sensitive content
- **Popularity**: click-through, engagement signals
- **Cross-encoder reranker**: compute query-document relevance jointly (slow but accurate)

---

---

## performance-profiling

**When to use:** Diagnosing performance issues, interpreting Lighthouse reports, generating flame graphs, or measuring Core Web Vitals.

### Core Web Vitals Targets
| Metric | Good | Poor | What It Measures |
|--------|------|------|-----------------|
| **LCP** | < 2.5s | > 4.0s | Largest content paint (loading) |
| **INP** | < 200ms | > 500ms | Interaction to Next Paint (interactivity) |
| **CLS** | < 0.1 | > 0.25 | Layout shift (stability) |

### Profiling Tools
- **Browser**: Chrome DevTools Performance tab → flame chart for JS execution
- **Node.js**: `node --prof`, then `node --prof-process isolate-*.log > profile.txt`
- **Python**: `cProfile` + `snakeviz` for visual flame graphs
- **Lighthouse**: `scripts/lighthouse_audit.py <url>` for automated report

### Flame Graph Reading
- Width = time spent; tall stacks = deep call chains
- Find the widest bars at the bottom of expensive stacks — that's the hotspot
- Focus optimization on functions that appear wide, not just tall

---

## web-performance-optimization

**When to use:** Optimizing web app loading speed, reducing bundle size, implementing caching, or improving Core Web Vitals.

### Quick Wins (highest impact)
1. **Images**: use WebP, lazy loading (`loading="lazy"`), proper dimensions (no resizing via CSS)
2. **JavaScript**: code split at route level, tree shake dead code, defer non-critical scripts
3. **Fonts**: `font-display: swap`, preload critical fonts, subset to used characters
4. **Caching**: long-lived cache for hashed assets (`Cache-Control: max-age=31536000, immutable`)
5. **Compression**: Brotli > gzip; enable at CDN/server level

### Bundle Size
```bash
# Analyze bundle
npx webpack-bundle-analyzer
npx @next/bundle-analyzer  # Next.js

# Common culprits
moment.js → date-fns or dayjs (10x smaller)
lodash → lodash-es with tree shaking
```

---

## application-performance

**When to use:** Finding and fixing N+1 queries, memoizing expensive computations, or optimizing algorithmic complexity.

### N+1 Detection
```typescript
// ❌ N+1: 1 query for users + N queries for their orders
const users = await db.users.findAll();
for (const user of users) {
  user.orders = await db.orders.findAll({ where: { userId: user.id } });
}

// ✅ Single query with join
const users = await db.users.findAll({ include: [{ model: db.orders }] });
```

### Memoization
```typescript
// Expensive computation — memoize if called repeatedly with same inputs
const memoizedFn = useMemo(() => expensiveCalc(dep), [dep]);

// Cache at module level for pure functions
const cache = new Map();
function expensive(key: string) {
  if (cache.has(key)) return cache.get(key);
  const result = compute(key);
  cache.set(key, result);
  return result;
}
```

---

---

## auth-security

**When to use:** Identifying authentication vulnerabilities, reviewing auth implementations, or understanding OWASP auth risks.

### OWASP Auth Top Risks
1. **Broken Authentication**: weak passwords allowed, no rate limiting on login, predictable session tokens
2. **Broken Access Control**: IDOR (increment ID to access other user's data), missing auth checks after login
3. **Sensitive Data Exposure**: passwords in logs, tokens in URLs (appear in server logs), unencrypted PII
4. **Insecure Direct Object Reference**: always validate user owns the resource they're accessing

### Secure Auth Checklist
- Passwords: bcrypt (cost factor ≥ 12) or Argon2id — never MD5/SHA without salt
- Sessions: `HttpOnly`, `Secure`, `SameSite=Strict` cookies; regenerate session ID on login
- JWT: short expiry (15min access, 7d refresh); RS256 over HS256 for multi-service; validate `aud` and `iss`
- Rate limiting: lock after 5-10 failed attempts; exponential backoff

---

## clerk-auth

**When to use:** Integrating Clerk authentication into Next.js, configuring route protection, or managing user sessions.

### Setup
```typescript
// middleware.ts
import { clerkMiddleware, createRouteMatcher } from '@clerk/nextjs/server';
const isProtectedRoute = createRouteMatcher(['/dashboard(.*)']);

export default clerkMiddleware((auth, req) => {
  if (isProtectedRoute(req)) auth().protect();
});
```

### Server Component Auth
```typescript
import { auth, currentUser } from '@clerk/nextjs/server';
const { userId } = auth(); // Get userId without full user object
const user = await currentUser(); // Full user when needed
```

---

## nextjs-supabase-auth

**When to use:** Next.js + Supabase authentication setup, Row Level Security policies, or server-side session management.

### Auth Flow
1. `@supabase/ssr` package for Next.js — handles cookie-based sessions
2. Server Component: `createServerClient(cookies())` for session access
3. Middleware: refresh session on every request, redirect unauthenticated users
4. RLS Policies: every table has policies; use `auth.uid()` to scope data to current user

```sql
-- RLS Policy example
CREATE POLICY "Users see own data" ON profiles
  FOR ALL USING (auth.uid() = user_id);
```

---

---

## dx-optimizer

**When to use:** Reducing development friction, improving onboarding time, setting up IDE tooling, or automating repetitive dev tasks.

### Target Metrics
- Onboarding time: < 5 minutes from clone to running dev environment
- Build time: hot reload < 500ms for iterative development
- Test feedback: unit test suite < 30 seconds

### Quick Wins
- `Makefile` with `make dev`, `make test`, `make lint` — self-documenting commands
- `.env.example` committed; `.env` in `.gitignore`
- Health check script that validates all required env vars are present
- Pre-commit hooks: lint + type check + unit tests (< 30s total)
- VS Code `.vscode/settings.json` + `extensions.json` committed to repo

---

## bun-development

**When to use:** Using Bun as runtime, package manager, bundler, or test runner.

### Key Commands
```bash
bun install           # Install deps (faster than npm)
bun run dev           # Run package.json scripts
bun --hot server.ts   # Run with hot reload
bun test              # Run tests (Jest-compatible)
bun build ./index.ts --outdir ./dist  # Bundle
```

### Bun vs Node Compatibility
- Drop-in replacement for most Node.js use cases
- Some native addons not supported
- Built-in: `Bun.file()`, `Bun.write()`, `Bun.serve()` — faster than Node equivalents

---

## uv-package-manager

**When to use:** Managing Python dependencies with uv — the modern replacement for pip + virtualenv.

### Key Commands
```bash
uv init my-project    # New project
uv add requests       # Add dependency (updates pyproject.toml)
uv add --dev pytest   # Dev dependency
uv sync               # Install all deps from lockfile
uv run python app.py  # Run in managed venv
uv run pytest         # Run tools in venv
```

### Migration from pip
```bash
# Replace
pip install -r requirements.txt  →  uv sync
pip install package              →  uv add package
python -m venv .venv             →  (uv handles this automatically)
```

---

## python-packaging

**When to use:** Packaging a Python library for distribution, publishing to PyPI, or configuring pyproject.toml.

### pyproject.toml Template
```toml
[build-system]
requires = ["hatchling"]
build-backend = "hatchling.build"

[project]
name = "my-package"
version = "0.1.0"
dependencies = ["requests>=2.28"]

[project.optional-dependencies]
dev = ["pytest", "ruff", "mypy"]

[tool.ruff]
line-length = 88
select = ["E", "F", "I", "UP"]
```

---

## git-advanced-workflows

**When to use:** Complex git operations — rebasing, worktrees, bisect, advanced branching, or hook configuration.

### Worktrees (work on multiple branches simultaneously)
```bash
git worktree add ../project-hotfix hotfix/critical-bug
# Work in ../project-hotfix without stashing
git worktree remove ../project-hotfix  # Clean up
```

### Bisect (find the breaking commit)
```bash
git bisect start
git bisect bad                    # Current commit is bad
git bisect good v2.1.0           # Last known good
# Git checks out midpoint
git bisect good/bad              # Mark, repeat until found
git bisect reset
```

### Interactive Rebase
```bash
git rebase -i HEAD~5  # Rewrite last 5 commits
# Commands: pick, squash, fixup, reword, drop, edit
```

---

## code-review-workflow

**When to use:** Requesting effective code reviews, giving actionable feedback, or establishing review culture.

### Requesting Reviews
- PR description: what changed, why, how to test, screenshots for UI changes
- Size: keep PRs < 400 lines changed; split large changes into stacked PRs
- Self-review first: read your own diff before requesting review
- Link to issue/ticket; describe the approach briefly for context

### Receiving Reviews
- Don't take feedback personally — it's about the code
- Ask for clarification on anything unclear before implementing blindly
- Respond to every comment: "Done", "Discussed in call", or reasoned disagreement
- Merge only after all blocking comments are resolved

---

## doc-coauthoring

**When to use:** Writing README files, API documentation, inline code comments, or technical guides collaboratively.

### README Structure
1. **What it does** (1-2 sentences; assume reader knows nothing)
2. **Quick start** (copy-pasteable commands; working in < 5 minutes)
3. **Configuration** (env vars, config files, options)
4. **API reference** (if library)
5. **Contributing** (how to run tests, submit PRs)

### Good Code Comments
- Comment WHY, not WHAT: `// Retry 3x because the payment provider has transient failures` not `// retry loop`
- Document non-obvious behavior: performance tradeoffs, business rules, known limitations
- TODO format: `// TODO(username): description and issue link` — never anonymous TODOs

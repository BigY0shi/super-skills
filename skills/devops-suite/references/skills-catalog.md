# DevOps Suite — Skills Catalog

Full instructions for all sub-skills. Read the relevant section before executing any DevOps task.

---

## Table of Contents

**Cloud & Infrastructure**
- [aws-serverless](#aws-serverless) — Lambda, API Gateway, DynamoDB, SAM/CDK
- [azure-functions](#azure-functions) — Azure serverless, bindings, Durable Functions
- [gcp-cloud-run](#gcp-cloud-run) — GCP serverless containers, scaling, traffic splits
- [vercel-deployment](#vercel-deployment) — Edge deployments, preview environments, CI integration
- [server-management](#server-management) — Linux server setup, hardening, process management

**Containers**
- [docker-expert](#docker-expert) — Dockerfiles, multi-stage builds, Compose, security

**CI/CD & Git**
- [github-workflow-automation](#github-workflow-automation) — GitHub Actions, AI PR review, issue triage
- [git-workflow](#git-workflow) — End-to-end git workflow orchestration with multi-agent QA
- [deployment-procedures](#deployment-procedures) — Release runbooks, environment promotion
- [deployment-validation](#deployment-validation) — Pre-flight config validation

**Databases**
- [database-migration](#database-migration) — Schema migrations, zero-downtime, rollback strategies
- [database-migrations](#database-migrations) — Migration observability, SQL scripts, change tracking
- [database-cloud-optimization](#database-cloud-optimization) — Cloud DB cost optimization, rightsizing
- [vector-database-engineer](#vector-database-engineer) — Pinecone, Weaviate, Qdrant, pgvector, RAG
- [vector-index-tuning](#vector-index-tuning) — HNSW/IVF index config, recall/latency tradeoffs

**Observability & Monitoring**
- [distributed-tracing](#distributed-tracing) — Jaeger, Tempo, OpenTelemetry, span correlation
- [observability-monitoring](#observability-monitoring) — Full-stack monitoring setup
- [prometheus-configuration](#prometheus-configuration) — Metrics collection, PromQL, alerting
- [slo-implementation](#slo-implementation) — SLI/SLO definition, error budgets

**Debugging & Incidents**
- [error-detective](#error-detective) — Log analysis, error pattern recognition
- [error-diagnostics](#error-diagnostics) — Root cause analysis, cross-service correlation
- [devops-troubleshooter](#devops-troubleshooter) — Kubernetes/container/network/APM debugging
- [incident-responder](#incident-responder) — Active incident triage and command
- [postmortem-writing](#postmortem-writing) — Blameless RCA, postmortem documents
- [distributed-debugging](#distributed-debugging) — Cross-service trace correlation

**Performance**
- [performance-engineer](#performance-engineer) — Profiling, load testing, Core Web Vitals, caching

**Security & Secrets**
- [secrets-management](#secrets-management) — Vault, AWS Secrets Manager, CI/CD secret handling
- [mtls-configuration](#mtls-configuration) — Mutual TLS, certificate management

**Shell & Scripting**
- [bash-pro](#bash-pro) — Production Bash, defensive patterns, CI automation
- [powershell-windows](#powershell-windows) — PowerShell patterns, operator syntax, error handling
- [linux-shell-scripting](#linux-shell-scripting) — POSIX shell, system administration

**Cost & Architecture**
- [cost-optimization](#cost-optimization) — Cloud spend reduction, rightsizing, governance
- [agent-orchestration](#agent-orchestration) — AI agent performance analysis and improvement
- [c4-diagrams](#c4-diagrams) — C4 context and container architecture diagrams

**Modernization & Process**
- [legacy-modernizer](#legacy-modernizer) — Framework migrations, strangler fig, tech debt
- [framework-migration](#framework-migration) — Dependency upgrades, backward compatibility
- [risk-manager](#risk-manager) — Risk assessment, mitigation planning

**AI/ML Ops & Data**
- [llm-application-dev](#llm-application-dev) — LangChain agents, LLM pipeline architecture
- [data-engineering](#data-engineering) — ETL/ELT pipelines, streaming, data quality
- [workflow-automation](#workflow-automation) — n8n, Temporal, Inngest, durable execution

---

---

## aws-serverless

**When to use:** Building or debugging AWS serverless applications — Lambda functions, API Gateway endpoints, DynamoDB tables, event-driven architectures, or SAM/CDK infrastructure.

### Core Coverage
- Lambda handler patterns (Node.js, Python) with proper cold start mitigation — initialize SDK clients outside handler, use connection reuse
- API Gateway integration: proxy integration, request/response mapping, CORS, custom authorizers
- DynamoDB access patterns: single-table design, GSIs, DynamoDB Streams, TTL
- Event sources: SQS, SNS, EventBridge, S3 triggers, Kinesis
- SAM templates and CDK stacks for infrastructure as code
- Cold start optimization: layer management, provisioned concurrency, runtime selection

### Key Patterns
- **Lambda Handler**: Initialize clients outside handler (reused across invocations). Use `context.callbackWaitsForEmptyEventLoop = false` for Node.js. Always return API Gateway-compatible response objects.
- **Error handling**: Distinguish retryable vs. non-retryable errors. Dead letter queues for failed async invocations.
- **Secrets**: Never hardcode — use SSM Parameter Store or Secrets Manager with caching.
- **Idempotency**: Lambda may execute multiple times. Use DynamoDB conditional writes or idempotency tokens.

### Workflow
1. Analyze existing infrastructure (SAM/CDK files, existing Lambda code)
2. Identify cold start, timeout, memory, or IAM permission issues
3. Apply pattern appropriate to event source
4. Validate with `sam local invoke` or CDK `cdk synth` + `cdk diff`
5. Check CloudWatch metrics post-deploy: duration, error rate, concurrency

---

## azure-functions

**When to use:** Building Azure serverless functions, configuring triggers and bindings, implementing Durable Functions workflows, or debugging Azure-specific deployment issues.

### Core Coverage
- Trigger types: HTTP, Timer, Queue, Service Bus, Event Hub, Blob, CosmosDB change feed
- Input/output bindings for storage, queues, databases without explicit SDK code
- Durable Functions: orchestrator, activity, entity patterns for stateful workflows
- Azure Function App configuration: host.json, local.settings.json, application settings
- Deployment: Azure CLI, VS Code extension, GitHub Actions, ZIP deploy
- Consumption vs. Premium vs. Dedicated plan selection and cost implications

### Key Patterns
- Use output bindings to avoid boilerplate SDK calls for common integrations
- Durable Functions for fan-out/fan-in, human approval workflows, long-running processes
- Application Insights integration for distributed tracing and custom telemetry
- Managed Identity for secure service-to-service authentication without secrets

---

## gcp-cloud-run

**When to use:** Deploying containerized workloads to Google Cloud Run, configuring autoscaling, managing traffic splits for canary deployments, or integrating with other GCP services.

### Core Coverage
- Container requirements: stateless, listen on PORT env var, fast startup
- Service configuration: concurrency, max instances, min instances, CPU/memory
- Traffic management: gradual rollouts, traffic splits, blue/green deployments
- Authentication: IAM-based, unauthenticated public access, service-to-service auth
- Cloud Build integration for CI/CD pipelines
- Connecting to Cloud SQL, Pub/Sub, GCS, Secret Manager
- Cold start optimization: container size, startup probes, min instances

---

## vercel-deployment

**When to use:** Deploying Next.js, React, or static sites to Vercel; configuring environment variables; managing preview deployments; setting up custom domains or edge functions.

### Core Coverage
- `vercel.json` configuration: rewrites, redirects, headers, function regions
- Environment variables: preview, production, and development scopes
- Edge Functions vs. Serverless Functions: use cases and limits
- Preview deployments: branch deployments, PR comments with deployment URLs
- CI/CD: GitHub integration, deploy hooks, `vercel --prod` CLI
- Monorepo support: root directory configuration, ignored build steps

---

## server-management

**When to use:** Setting up Linux servers, configuring system services with systemd, hardening SSH/firewall, managing processes, or automating server provisioning.

### Core Coverage
- Initial server hardening: disable root SSH, key-based auth only, UFW firewall rules
- systemd service creation: unit files, dependency ordering, restart policies, journald logging
- Process management: PM2 for Node.js, Supervisor for Python, ulimits
- Nginx/Caddy reverse proxy configuration, SSL termination, upstream health checks
- Automated provisioning: bash scripts, Ansible playbooks, cloud-init
- Log management: logrotate configuration, centralized log shipping

---

---

## docker-expert

**When to use:** Optimizing Dockerfiles, reducing image size, configuring Docker Compose for local development or production, hardening container security, or debugging container networking issues.

### Core Coverage
- Multi-stage builds for minimal production images (builder → runtime pattern)
- Image optimization: `.dockerignore`, layer caching order, Alpine vs. distroless base images
- Docker Compose: service dependencies, health checks, volumes, networks, env files
- Security hardening: non-root users, read-only filesystems, capability dropping, image scanning
- Container networking: bridge networks, host networking, service discovery
- Production patterns: resource limits, logging drivers, restart policies

### Workflow
1. Analyze existing Dockerfile and compose files (Read, Grep, Glob first)
2. Identify image size, security, or build performance issues
3. Apply multi-stage build optimization
4. Validate: `docker build --no-cache`, `docker scout quickview`, `docker history`
5. For Compose: validate with `docker compose config`, test health checks

### Anti-Patterns to Fix
- Installing dev dependencies in production stage
- Running as root
- Not using `.dockerignore` (copies node_modules, .git, etc.)
- `COPY . .` before dependency install (breaks layer caching)
- Using `latest` tags in production

---

---

## github-workflow-automation

**When to use:** Automating GitHub workflows — AI-assisted PR review, issue triage, GitHub Actions pipelines, or integrating AI into CI/CD.

### Core Coverage
- GitHub Actions workflow syntax: triggers, jobs, steps, matrix builds, reusable workflows
- AI PR review action: automated review on pull_request events with structured output
- Issue triage automation: label assignment, assignment rules, stale bot configuration
- Git operations via Actions: automated rebases, cherry-picks, merge conflict detection
- Security: GITHUB_TOKEN scopes, secrets, OIDC for cloud auth (no long-lived keys)
- Workflow optimization: caching dependencies, parallel jobs, conditional execution

### Key Patterns
- PR review action: trigger on `pull_request`, run analysis agent, post review comments via GitHub API
- Branch protection + required status checks for quality gates
- Environment deployments with required reviewers for production

---

## git-workflow

**When to use:** Orchestrating a complete, production-quality git workflow — from code review through commit to PR creation — with multi-agent quality checks.

### Workflow Phases

**Phase 1 — Pre-Commit Review**
- Code quality assessment (style, security, performance, error handling)
- Breaking change analysis (API changes, schema modifications, dependency updates)

**Phase 2 — Testing & Validation**
- Test execution and coverage verification
- Integration test validation

**Phase 3 — Commit & PR**
- Conventional Commits format enforcement
- PR creation with structured description (summary, test plan, screenshots)

### Supported Flags
`--skip-tests`, `--draft-pr`, `--no-push`, `--squash`, `--conventional`, `--trunk-based`, `--feature-branch`

### Conventional Commit Format
```
<type>(<scope>): <description>

Types: feat, fix, docs, style, refactor, perf, test, chore, ci
```

---

## deployment-procedures

**When to use:** Writing or following deployment runbooks, planning release procedures, documenting environment promotion steps, or creating rollback plans.

### Core Coverage
- Pre-deployment checklist: health baselines, backup verification, feature flag states
- Deployment sequence: canary → percentage rollout → full production
- Smoke tests and health check validation post-deploy
- Rollback triggers and procedures: define thresholds (error rate, latency) before deploying
- Communication templates: deployment announcements, status page updates
- Blue/green deployment coordination: traffic switching, old environment teardown

---

## deployment-validation

**When to use:** Validating configuration before deployment — checking env vars, secrets, infrastructure configs, or running pre-flight checks.

### Core Coverage
- Config validation scripts: check required env vars, validate JSON/YAML syntax
- Secret presence checks (existence only, never log values)
- Infrastructure drift detection before apply
- Dependency health checks: database connectivity, external API availability
- Smoke test execution against staging before promoting to production

---

---

## database-migration

**When to use:** Executing database schema migrations, changing data models, moving data between databases, or implementing zero-downtime migration strategies.

### Core Coverage
- ORM migration patterns: Sequelize, TypeORM, Prisma — up/down migration structure
- Zero-downtime techniques: expand-contract pattern, online schema change tools (pt-osc, gh-ost)
- Data transformation migrations: backfill strategies, batch processing for large tables
- Rollback procedures: always write reversible migrations; test rollback in staging
- Multi-database migrations: consistency guarantees, transaction boundaries

### Expand-Contract Pattern (Zero Downtime)
```
Phase 1 (Expand): Add new column/table, keep old one
Phase 2 (Migrate): Backfill data, update application to dual-write
Phase 3 (Contract): Remove old column/table after verification
```

### Critical Rules
- Never drop columns/tables in the same migration as the code change
- Always test `down()` migration before merging
- Large table changes: use batched updates, never full-table locks in production
- Foreign key constraints: add `INITIALLY DEFERRED` or use application-level checks during migration

---

## database-migrations

**When to use:** Setting up migration observability, writing raw SQL migration scripts, tracking schema change history, or implementing migration CI/CD pipelines.

### Core Coverage
- Migration versioning and tracking: Flyway, Liquibase, or custom migration table
- SQL migration script templates with proper transaction boundaries
- Schema change CI: validate migrations against production schema snapshot
- Migration observability: duration tracking, lock wait monitoring, alerting on slow migrations
- Rollback scripts: always paired with forward migrations

---

## database-cloud-optimization

**When to use:** Reducing cloud database costs, rightsizing RDS/Cloud SQL/Aurora instances, analyzing expensive queries, or implementing connection pooling.

### Core Coverage
- Cost analysis: identify expensive queries, idle connections, over-provisioned instances
- Connection pooling: PgBouncer, RDS Proxy, connection limit tuning
- Read replica routing: offload reporting queries, analytical workloads
- Auto-scaling: Aurora Serverless v2, Cloud SQL autoscaling
- Storage optimization: unused indexes, bloat analysis, VACUUM tuning for PostgreSQL
- Reserved instance / committed use discount planning

---

## vector-database-engineer

**When to use:** Building RAG systems, implementing semantic search, creating recommendation engines, or optimizing vector search performance.

### Core Coverage
- **Database selection**: Pinecone (managed, simple), Weaviate (hybrid search), Qdrant (self-hosted, fast), Milvus (enterprise scale), pgvector (existing Postgres)
- **Embedding models**: OpenAI ada-002, text-embedding-3 (small/large), Cohere, local (sentence-transformers)
- **Chunking strategies**: fixed-size, semantic, hierarchical; overlap considerations
- **Index types**: HNSW (high recall, high memory), IVF (lower memory, approximation), Product Quantization (compressed)
- **Hybrid search**: combine vector similarity + BM25 keyword; reranking with cross-encoders
- **Metadata filtering**: pre-filter (reduces candidates) vs. post-filter (better recall)

### Workflow
1. Analyze data characteristics (document length, query patterns, scale)
2. Select embedding model based on domain and latency requirements
3. Design chunking pipeline with appropriate overlap
4. Choose database and index type for recall/latency/cost tradeoff
5. Implement hybrid search if keyword matching matters
6. Benchmark with realistic queries before production

---

## vector-index-tuning

**When to use:** Optimizing vector search performance, tuning ANN index parameters, benchmarking recall vs. latency, or scaling to millions of vectors.

### Core Coverage
- HNSW parameters: `ef_construction` (build quality), `M` (connectivity), `ef` (query recall)
- IVF parameters: `nlist` (cluster count), `nprobe` (search clusters)
- Product Quantization: compression ratios, accuracy tradeoffs
- Benchmarking: use ANN-benchmarks methodology, measure recall@k and latency p95/p99
- Reindexing strategies: online vs. offline reindex, zero-downtime index swaps
- Monitoring: recall degradation over time as data distribution shifts

---

---

## distributed-tracing

**When to use:** Debugging latency in microservices, understanding request flow across services, implementing OpenTelemetry instrumentation, or setting up Jaeger/Tempo.

### Core Coverage
- Trace anatomy: spans, parent-child relationships, baggage propagation
- **Jaeger**: deployment (all-in-one for dev, distributed for prod), query UI, trace comparison
- **Grafana Tempo**: object storage backend, TraceQL query language, Grafana integration
- **OpenTelemetry**: SDK instrumentation (auto vs. manual), collector configuration, export to multiple backends
- Sampling strategies: head-based (probabilistic), tail-based (error-driven), adaptive
- Correlation: linking traces to logs (trace ID in log context) and metrics (exemplars)

### Instrumentation Checklist
- HTTP client/server auto-instrumentation
- Database query spans with sanitized SQL
- Async operations: propagate context across thread/async boundaries
- External calls: attribute service name, URL, status code
- Business operations: custom spans for domain-critical paths

---

## observability-monitoring

**When to use:** Setting up a full observability stack (metrics + logs + traces), configuring dashboards, establishing alerting, or implementing the three pillars of observability.

### Core Coverage
- **Metrics**: Prometheus + Grafana, custom application metrics (counters, histograms, gauges)
- **Logs**: Structured JSON logging, ELK/Loki/Splunk, log correlation with trace IDs
- **Traces**: OpenTelemetry, Jaeger/Tempo (see distributed-tracing)
- **Dashboards**: RED method (Rate/Errors/Duration), USE method (Utilization/Saturation/Errors)
- **Alerting**: PagerDuty/OpsGenie integration, alert routing, on-call rotations
- **SLOs**: Error budget dashboards, burn rate alerts

### Golden Signals to Instrument First
1. **Latency** — p50, p95, p99 response times (histogram, not average)
2. **Traffic** — requests per second by endpoint/service
3. **Errors** — error rate, error budget burn rate
4. **Saturation** — CPU, memory, connection pool utilization

---

## prometheus-configuration

**When to use:** Setting up Prometheus, writing scrape configs, creating recording rules, designing PromQL queries, or configuring AlertManager.

### Core Coverage
- Installation: Helm chart (kube-prometheus-stack), Docker Compose, binary
- Scrape configuration: static_configs, service discovery (Kubernetes, Consul, file-based)
- Recording rules: pre-compute expensive queries, rate calculations
- AlertManager: routing trees, inhibition, silencing, receiver configuration
- PromQL patterns: `rate()`, `histogram_quantile()`, `increase()`, label matchers

### Key PromQL Patterns
```promql
# Request rate
rate(http_requests_total[5m])

# Error rate %
sum(rate(http_requests_total{status=~"5.."}[5m])) 
/ sum(rate(http_requests_total[5m])) * 100

# P95 latency
histogram_quantile(0.95, sum(rate(http_duration_seconds_bucket[5m])) by (le))

# CPU throttling
rate(container_cpu_cfs_throttled_seconds_total[5m])
/ rate(container_cpu_cfs_periods_total[5m])
```

---

## slo-implementation

**When to use:** Defining service reliability targets, implementing error budget tracking, creating SLO-based alerts, or establishing SRE practices.

### Hierarchy
- **SLI** (Indicator): The actual measurement — e.g., "% of requests completing under 500ms"
- **SLO** (Objective): The target — e.g., "99.9% of requests complete under 500ms"
- **Error Budget**: `100% - SLO` — the allowable unreliability; protects innovation velocity
- **SLA**: External contract, should be looser than internal SLO

### SLI Types
- **Availability**: `successful_requests / total_requests`
- **Latency**: `requests_under_threshold / total_requests`
- **Quality**: `responses_without_errors / total_responses`
- **Freshness**: `data_updated_within_threshold / total_data_points`

### Error Budget Alerting (Burn Rate)
```
Alert when burn rate exceeds threshold:
- 14.4x burn → 1hr window: page immediately (1h of budget = 5% of monthly)
- 6x burn → 6hr window: page urgently
- 3x burn → 1d window: ticket required
- 1x burn → 3d window: inform team
```

---

---

## error-detective

**When to use:** Analyzing logs for error patterns, building regex extractors for log monitoring, correlating errors across services, or investigating production anomalies.

### Core Coverage
- Log parsing: regex patterns for common error formats (Python tracebacks, Java stack traces, Node.js errors)
- Error aggregation: Elasticsearch queries, Loki LogQL, Splunk SPL for error rate analysis
- Timeline construction: correlating errors with deployment events, config changes
- Pattern detection: error rate spikes, new error types, error clustering by service/host
- Cross-service correlation: trace ID matching, upstream/downstream error propagation

### Approach
1. Start with symptoms, work backward to cause
2. Look for patterns across time windows (before/after deploy, peak traffic)
3. Correlate with change events (deployments, config updates, scaling events)
4. Check for cascading failures (service A → B → C error chains)
5. Produce monitoring queries to detect recurrence

---

## error-diagnostics

**When to use:** Deep root cause analysis of production errors, especially when initial investigation hasn't identified the source.

### Four-Phase Diagnostic Protocol

**Phase 1 — Symptom Mapping**
Read ALL error messages completely. Note exact line numbers, error codes, timestamps. Build a timeline of when symptoms first appeared.

**Phase 2 — Reproduction**
Reproduce consistently before attempting any fix. If you can't reproduce, you can't verify the fix. Understand the exact conditions required.

**Phase 3 — Root Cause Isolation**
Eliminate variables systematically. Change one thing at a time. Use binary search (bisect) to narrow to specific commit or change.

**Phase 4 — Verified Fix**
Only propose fix after identifying root cause. Verify fix resolves the symptom AND addresses the root. Add regression test before merging.

### Iron Law
**No fix without root cause.** Symptom patches create new bugs and mask the real problem.

---

## devops-troubleshooter

**When to use:** Troubleshooting Kubernetes pods, container runtime issues, network connectivity, APM anomalies, or any production system issue requiring systematic investigation.

### Capability Areas
- **Kubernetes**: `kubectl describe`, `kubectl logs --previous`, events, resource constraints, network policies
- **Container runtime**: OOMKilled, CPU throttling, image pull failures, init container issues
- **Network/DNS**: `dig`, `nslookup`, `tcpdump`, load balancer health, service mesh (Istio/Linkerd)
- **APM**: DataDog, New Relic, Dynatrace — correlating APM anomalies with deployments
- **Database**: connection pool exhaustion, query timeouts, replication lag
- **CI/CD**: build failures, deployment pipeline issues, artifact registry problems

### Kubernetes Debug Cheatsheet
```bash
# Pod issues
kubectl describe pod <pod> -n <ns>
kubectl logs <pod> --previous -n <ns>
kubectl get events --sort-by='.lastTimestamp' -n <ns>

# Resource issues
kubectl top pods -n <ns>
kubectl describe node <node> | grep -A 10 "Allocated resources"

# Network issues
kubectl exec -it <pod> -- nslookup <service>
kubectl exec -it <pod> -- curl -v http://<service>:<port>
```

---

## incident-responder

**When to use:** Active production incident — something is down, degraded, or causing customer impact. Activate immediately.

### First 5 Minutes
1. **Assess impact**: user count affected, geographic scope, revenue impact, SLA status
2. **Establish command**: Incident Commander (decisions), Comms Lead (stakeholders), Tech Lead (investigation)
3. **Stabilize first**: traffic throttle, feature flags, circuit breakers, rollback if safe
4. **Communicate**: internal war room, initial status page update ("We are investigating...")

### Investigation Protocol (Observability-Driven)
- Traces first: find the failing span in Jaeger/Tempo
- Metrics: identify which golden signal broke first (latency, errors, saturation)
- Logs: filter to error level, match timestamp of first impact
- Change correlation: what deployed/changed in the hour before incident start?

### Communication Cadence
- Every 15 minutes during active incident: technical update to team
- Every 30 minutes: executive/business impact summary
- On resolution: immediate "resolved" update with cause and timeline

### Severity Levels
| Level | Definition | Response |
|-------|-----------|----------|
| P0 | Total outage, all users affected | Immediate page, all hands |
| P1 | Major feature down, significant % affected | Page on-call team |
| P2 | Degraded performance, workaround available | Business hours response |
| P3 | Minor issue, minimal user impact | Next sprint |

---

## postmortem-writing

**When to use:** Writing a blameless post-incident review document, conducting a postmortem meeting, or identifying systemic improvements after an incident.

### Blameless Culture
| Blame | Blameless |
|-------|-----------|
| "Who caused this?" | "What conditions allowed this?" |
| Punish individuals | Improve systems |
| "Human error" as root cause | "What made the error easy to make?" |

### Postmortem Structure
1. **Incident Summary** — 2-3 sentence overview: what failed, customer impact, duration
2. **Timeline** — Chronological events from first symptom to resolution (UTC timestamps)
3. **Root Cause Analysis** — The actual cause, not the proximate trigger (use 5 Whys)
4. **Contributing Factors** — Conditions that made the incident possible or worse
5. **Impact** — Quantified: users affected, duration, error counts, revenue if applicable
6. **What Went Well** — Detection speed, response coordination, communication
7. **Action Items** — Specific, owned, time-bound. Not "improve monitoring" but "Add p99 latency alert for /checkout by [date] [owner]"

### 5 Whys Example
```
Why did customers see errors? → Service B returned 500s
Why did B return 500s? → DB connection pool exhausted
Why was pool exhausted? → Query from new feature leaked connections
Why did it leak? → Missing finally block in error path
Why wasn't it caught? → No integration test for error path
→ Fix: Add connection pool metrics alert + fix leak + add test
```

---

## distributed-debugging

**When to use:** Debugging issues that span multiple services, correlating traces across service boundaries, or investigating cascading failures.

### Core Coverage
- Trace correlation: matching trace IDs across service logs to reconstruct request path
- Span gap analysis: identify which service is adding unexpected latency
- Context propagation verification: ensure W3C TraceContext headers flow through all services
- Async correlation: matching correlation IDs in message queues, event streams
- Dependency map construction: identify upstream/downstream blast radius

---

---

## performance-engineer

**When to use:** End-to-end performance optimization — profiling, load testing, caching architecture, Core Web Vitals, or SLO-driven performance targets.

### Capability Areas
- **Profiling**: CPU flame graphs, memory heap analysis, GC tuning (JVM, V8, Go)
- **Load testing**: k6, Gatling, Locust — test design, baseline establishment, regression detection
- **Caching**: L1 (in-process), L2 (Redis/Memcached), L3 (CDN) — cache key design, TTL strategy, invalidation
- **Core Web Vitals**: LCP < 2.5s, INP < 200ms, CLS < 0.1 — measurement and optimization
- **Database performance**: query plan analysis, N+1 detection, connection pool tuning
- **APM**: DataDog APM, New Relic, Honeycomb — setting up performance baselines and budgets

### Performance Methodology
1. **Measure first**: establish baseline before optimizing. Use realistic load.
2. **Profile to find hotspot**: CPU flame graph, memory allocation trace, query plans
3. **One change at a time**: change one variable, measure impact, repeat
4. **Set performance budgets**: define acceptable thresholds, integrate into CI
5. **Monitor continuously**: regressions happen silently

---

---

## secrets-management

**When to use:** Setting up secrets infrastructure, rotating credentials, securing CI/CD environment variables, or auditing for hardcoded secrets.

### Tool Selection
| Tool | Best For |
|------|----------|
| HashiCorp Vault | Multi-cloud, dynamic secrets, fine-grained audit |
| AWS Secrets Manager | AWS-native, automatic RDS rotation |
| Azure Key Vault | Azure-native, HSM-backed keys |
| GCP Secret Manager | GCP-native, IAM integration |
| GitHub Secrets | Simple CI/CD secrets (no rotation) |

### Key Practices
- **Dynamic secrets**: Vault can generate time-limited DB credentials — no long-lived passwords
- **Secret rotation**: automate rotation; never require a deployment to rotate a secret
- **Least privilege**: scoped access per service, per environment
- **Audit trail**: every secret access logged
- **No secrets in code**: pre-commit hooks (gitleaks, trufflehog) to catch leaks

---

## mtls-configuration

**When to use:** Configuring mutual TLS between services, managing certificates, or securing service mesh communication.

### Core Coverage
- Certificate generation: self-signed for dev, Let's Encrypt or private CA for production
- mTLS with nginx: `ssl_client_certificate`, `ssl_verify_client` directives
- Service mesh mTLS: Istio PeerAuthentication (STRICT mode), Linkerd automatic mTLS
- Certificate rotation: cert-manager on Kubernetes, automatic renewal policies
- Debugging mTLS: `openssl s_client`, certificate chain verification, SNI issues

---

---

## bash-pro

**When to use:** Writing production Bash scripts for CI/CD automation, system administration, or any shell scripting requiring reliability and portability.

### Core Practices
- Always start with: `set -Eeuo pipefail` + error trap (`trap 'cleanup' ERR EXIT`)
- Quote all variable expansions: `"$variable"` not `$variable`
- Use `[[` for conditionals, `(( ))` for arithmetic
- `printf` over `echo` for consistent output
- Arrays for multi-value data: `mapfile -t array < <(command)`
- Temporary files: `mktemp` + cleanup trap
- Input validation: `${VAR:?error message}` for required vars
- Support `--dry-run` and `--trace` modes
- NUL-safe find: `find -print0 | while IFS= read -r -d '' f; do...; done`

### Script Template
```bash
#!/usr/bin/env bash
set -Eeuo pipefail
trap 'cleanup' ERR EXIT

SCRIPT_DIR="$(cd -- "$(dirname -- "${BASH_SOURCE[0]}")" && pwd -P)"

cleanup() {
  local exit_code=$?
  # cleanup temp files, etc.
  exit "$exit_code"
}

main() {
  # script logic here
}

main "$@"
```

---

## powershell-windows

**When to use:** Writing PowerShell automation scripts for Windows, configuring Windows services, or integrating with the Windows ecosystem.

### Critical Patterns
- **Logical operators require parentheses**: `if ((Test-Path "a") -or (Test-Path "b"))` — each cmdlet call must be parenthesized
- **No Unicode/emoji**: use ASCII only — `[OK]`, `[ERROR]`, `[WARN]` not ✅❌⚠️
- **Error handling**: `$ErrorActionPreference = 'Stop'` for terminating errors; use `try/catch/finally`
- **Output types**: `Write-Output` for pipeline, `Write-Host` for console-only (not pipeable)
- **Paths**: use `Join-Path` not string concatenation; handle spaces in paths
- Prefer `[System.IO.Path]` and `[System.IO.File]` over cmdlets in performance-critical code

---

## linux-shell-scripting

**When to use:** System administration, POSIX shell scripting, Linux process management, or automating server tasks.

### Core Coverage
- POSIX-compatible scripts: use `#!/bin/sh`, avoid bashisms for maximum portability
- Process management: `systemctl`, `supervisorctl`, `screen`/`tmux` for persistence
- File operations: `find`, `xargs`, `awk`, `sed` for text processing pipelines
- cron and systemd timers for scheduled tasks
- Log analysis: `grep`, `sort`, `uniq`, `awk` pipelines for quick analysis
- Network tools: `ss`, `netstat`, `iptables`, `tcpdump` for diagnostics

---

---

## cost-optimization

**When to use:** Reducing cloud costs, rightsizing infrastructure, implementing cost governance, or analyzing cloud spend.

### Framework
1. **Visibility first**: implement tagging strategy (team, env, product, cost-center), set up cost dashboards and budget alerts
2. **Right-size**: use AWS Compute Optimizer, GCP Recommender, Azure Advisor — target < 70% average CPU utilization as signal for over-provisioning
3. **Pricing models**: Reserved Instances (1-3yr commitment) for stable baseline; Spot/Preemptible for fault-tolerant workloads; Savings Plans for flexible coverage
4. **Eliminate waste**: idle resources (stopped instances still incur storage costs), orphaned snapshots, unused load balancers, data transfer costs

### Quick Wins (typically 20-40% savings)
- Idle/underutilized EC2/VMs: schedule stop during off-hours
- Oversized RDS instances: scale down with read replicas for load
- S3/GCS: lifecycle policies to move to cheaper tiers (Infrequent Access → Glacier)
- Data transfer: keep compute and storage in same region/zone
- NAT Gateway: high data transfer cost — consider VPC endpoints for AWS services

---

## agent-orchestration

**When to use:** Improving AI agent performance, analyzing agent behavior patterns, optimizing prompts for existing agents, or building multi-agent coordination workflows.

### Performance Analysis Protocol
1. Gather 30-day metrics: task completion rate, response accuracy, tool usage efficiency, user correction rate
2. Identify top failure modes: hallucination patterns, tool misuse, context loss
3. Apply targeted prompt improvements: add constraints for failure modes, examples for edge cases
4. A/B test changes against baseline with identical inputs
5. Monitor for regression after deployment

### Improvement Techniques
- **System prompt tuning**: add negative examples for known failure patterns
- **Context management**: explicit memory protocols for long sessions
- **Tool selection**: clear disambiguation criteria between similar tools
- **Output structure**: specify exact format to reduce parsing errors downstream

---

## c4-diagrams

**When to use:** Creating architecture diagrams using the C4 model — context (L1), container (L2), component (L3), or code (L4) level views.

### C4 Levels
- **Context (L1)**: System in relation to users and external systems. Audience: everyone including non-technical.
- **Container (L2)**: Major deployable units (web app, API, database, message queue). Audience: technical team.
- **Component (L3)**: Internal structure of a single container. Audience: developers of that container.
- **Code (L4)**: Class/function level. Rarely worth the maintenance cost; use sparingly.

### Output Format
Prefer Mermaid diagrams for portability:
```
graph TD
    User[👤 User] -->|Uses| WebApp[Web Application<br/>React SPA]
    WebApp -->|API calls| API[API Server<br/>Node.js/Express]
    API -->|Reads/Writes| DB[(PostgreSQL)]
    API -->|Publishes| Queue[Message Queue<br/>SQS]
```

---

---

## legacy-modernizer

**When to use:** Refactoring legacy codebases, migrating from outdated frameworks, reducing technical debt incrementally, or planning a modernization roadmap.

### Approach: Strangler Fig Pattern
Never rewrite everything at once. Instead:
1. **Add tests** to legacy code before touching it — characterization tests capture current behavior
2. **Identify seams** where new and old code can coexist (API boundaries, interfaces)
3. **Replace incrementally**: new code behind feature flags, route traffic gradually
4. **Maintain backward compatibility** throughout migration
5. **Deprecate and remove** old code only after new code is verified at full traffic

### Common Migration Patterns
| From | To | Key Risk |
|------|----|----------|
| jQuery → React | Component-by-component | Global state assumptions |
| Java 8 → 17+ | Dependency compatibility | Third-party library updates |
| Python 2 → 3 | `2to3` + manual review | String/bytes distinction |
| REST → GraphQL | Dual endpoint period | N+1 on new resolvers |
| Monolith → Microservices | Data ownership boundaries | Distributed transactions |

---

## framework-migration

**When to use:** Upgrading framework versions, updating major dependencies, or managing breaking changes with backward compatibility.

### Core Coverage
- Dependency upgrade strategies: lock file analysis, changelogs, breaking change detection
- Compatibility shims: adapter layers that let new and old interfaces coexist during migration
- Feature flags for gradual rollout of migration changes
- Automated migration tools: codemods (jscodeshift), migration CLI commands
- Rollback procedures for each migration phase

---

## risk-manager

**When to use:** Assessing risks before major changes, documenting risk registers, or building mitigation plans for infrastructure decisions.

### Risk Assessment Framework
- **Likelihood**: 1-5 scale (rare → certain)
- **Impact**: 1-5 scale (negligible → catastrophic)
- **Risk Score**: Likelihood × Impact; scores ≥ 12 require mitigation plan
- **Mitigation**: reduce likelihood, reduce impact, or transfer (insurance/SLA)
- **Residual risk**: risk remaining after mitigation — must be explicitly accepted

---

---

## llm-application-dev

**When to use:** Building LLM-powered applications, designing LangChain agent architectures, or implementing AI pipeline patterns.

### Core Coverage
- LangChain chains vs. agents: when to use each; chain for deterministic, agent for tool use
- Tool design: clear descriptions, explicit input/output schemas, error handling
- Memory patterns: conversation buffer, summary, entity memory for long contexts
- RAG architecture: retrieval quality is more important than generation (see `vector-database-engineer`)
- Streaming: token streaming for better UX, interrupt handling
- Evaluation: tracing with LangSmith/Langfuse, automated evals for regression detection

---

## data-engineering

**When to use:** Designing data pipelines, building ETL/ELT workflows, implementing streaming architectures, or ensuring data quality.

### Core Coverage
- ETL vs. ELT: extract-transform-load (warehouse transforms on ingest) vs. load-then-transform (dbt, Spark)
- Batch pipelines: scheduling (Airflow, Prefect, Dagster), idempotency, backfill strategies
- Streaming: Kafka for high-throughput event streams, Kinesis for AWS-native, Pub/Sub for GCP
- Data quality: schema validation (Great Expectations, Soda), null checks, referential integrity
- dbt: model organization, testing, documentation, incremental models
- Orchestration: DAG design, dependency management, retry policies, alerting

---

## workflow-automation

**When to use:** Implementing durable workflow automation, choosing between n8n/Temporal/Inngest, or building background job systems.

### Platform Tradeoffs
| Platform | Best For | Tradeoff |
|----------|----------|---------|
| **n8n** | Visual workflows, non-dev teams, rapid prototyping | Lower throughput, vendor lock-in risk |
| **Temporal** | Mission-critical, complex sagas, exact-once semantics | Complex setup, steep learning curve |
| **Inngest** | Developer-friendly, serverless, event-driven | Newer ecosystem |

### Durable Execution Patterns
- **Sequential**: step1 → step2 → step3 with automatic retry on failure
- **Fan-out/Fan-in**: parallel steps, wait for all to complete
- **Saga**: compensating transactions for distributed rollback
- **Scheduled**: cron-based triggers with durable execution guarantees

### Key Insight
Without durable execution, a network failure mid-workflow means lost state and partial execution. Durable execution frameworks checkpoint each step — workflows resume exactly where they left off.

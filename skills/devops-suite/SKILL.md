---
name: devops-suite
description: "Full-stack DevOps AI covering 40+ specialist skills across cloud infrastructure, CI/CD, containers, databases, observability, incident response, security, shell scripting, performance, and AI/ML ops. Use for Docker, AWS/Azure/GCP serverless, Kubernetes, GitHub Actions, database migrations, Prometheus, SLOs, distributed tracing, incident response, postmortems, secrets management, Bash/PowerShell, cost optimization, vector databases, legacy modernization, and workflow automation. Trigger keywords: DevOps, infrastructure, cloud, deploy, CI/CD, Docker, container, Kubernetes, AWS, Azure, GCP, serverless, Lambda, database migration, monitoring, observability, Prometheus, Grafana, alerting, SLO, tracing, OpenTelemetry, incident, postmortem, on-call, secrets, Vault, bash, shell, PowerShell, git workflow, performance, cost optimization, vector database, RAG, legacy migration, workflow automation."
metadata:
  version: 1.0.0
  source: _Master_Library/DevOps-no-code + _Master_Library/Uncategorized
---

# DevOps Suite

A complete, modular DevOps AI covering the full infrastructure and operations lifecycle — from cloud deployment and containers to observability, incident response, database migrations, and workflow automation.

---

## How to Use This Skill

1. **Identify the task category** from the routing table below
2. **Load the matching sub-skill** from `references/skills-catalog.md`
3. **Execute** following the sub-skill's workflow

---

## Quick Routing Table

### ☁️ Cloud & Infrastructure
| Task | Load |
|------|------|
| AWS Lambda, API Gateway, DynamoDB, SAM/CDK, cold start optimization | `aws-serverless` |
| Azure Functions, bindings, triggers, Durable Functions | `azure-functions` |
| GCP Cloud Run, deployment, scaling, traffic management | `gcp-cloud-run` |
| Vercel deployment, edge functions, preview environments | `vercel-deployment` |
| Linux server setup, hardening, process management, systemd | `server-management` |

### 🐳 Containers & Orchestration
| Task | Load |
|------|------|
| Dockerfile optimization, multi-stage builds, Docker Compose, container security | `docker-expert` |

### 🔄 CI/CD & Git
| Task | Load |
|------|------|
| GitHub Actions automation, AI-assisted PR review, issue triage | `github-workflow-automation` |
| Full git workflow orchestration — code review → commit → PR creation | `git-workflow` |
| Deployment runbooks, release procedures, environment promotion | `deployment-procedures` |
| Config validation, deployment pre-flight checks | `deployment-validation` |

### 🗄️ Databases
| Task | Load |
|------|------|
| Schema migrations across ORMs (Prisma, TypeORM, Sequelize), zero-downtime | `database-migration` |
| Migration observability, SQL migration scripts, rollback planning | `database-migrations` |
| Cloud database cost optimization, rightsizing, query cost analysis | `database-cloud-optimization` |
| Pinecone, Weaviate, Qdrant, Milvus, pgvector, RAG systems, embedding pipelines | `vector-database-engineer` |
| HNSW/IVF index tuning, recall vs. latency tradeoffs, ANN benchmarks | `vector-index-tuning` |

### 📊 Observability & Monitoring
| Task | Load |
|------|------|
| Jaeger/Tempo distributed tracing, OpenTelemetry, service dependency mapping | `distributed-tracing` |
| Full-stack monitoring setup — metrics, logs, traces, dashboards | `observability-monitoring` |
| Prometheus configuration, scrape config, recording rules, PromQL | `prometheus-configuration` |
| SLI/SLO definition, error budgets, SLO-based alerting | `slo-implementation` |

### 🚨 Debugging & Incidents
| Task | Load |
|------|------|
| Log analysis, error pattern detection, stack trace correlation | `error-detective` |
| Error diagnostics, root cause analysis across distributed systems | `error-diagnostics` |
| Kubernetes/container/network troubleshooting, APM debugging | `devops-troubleshooter` |
| Active production incident — triage, command, communication | `incident-responder` |
| Post-incident postmortem writing, blameless RCA, action items | `postmortem-writing` |
| Cross-service distributed debugging, trace correlation | `distributed-debugging` |

### ⚡ Performance
| Task | Load |
|------|------|
| End-to-end performance optimization, profiling, load testing, Core Web Vitals | `performance-engineer` |

### 🔒 Security & Secrets
| Task | Load |
|------|------|
| Vault, AWS Secrets Manager, Azure Key Vault, secret rotation, CI/CD secrets | `secrets-management` |
| mTLS configuration, mutual TLS, certificate management | `mtls-configuration` |

### 🖥️ Shell & Scripting
| Task | Load |
|------|------|
| Production Bash scripting, defensive patterns, CI/CD automation | `bash-pro` |
| PowerShell Windows automation, operator syntax, error handling | `powershell-windows` |
| Linux shell scripting, POSIX compliance, system administration | `linux-shell-scripting` |

### 💰 Cost & Architecture
| Task | Load |
|------|------|
| Cloud cost reduction, rightsizing, reserved instances, spend analysis | `cost-optimization` |
| Agent orchestration improvement, prompt engineering, performance analysis | `agent-orchestration` |
| C4 architecture diagrams — context, container level | `c4-diagrams` |

### 🔧 Modernization & Process
| Task | Load |
|------|------|
| Legacy codebase refactoring, framework migrations, strangler fig pattern | `legacy-modernizer` |
| Dependency upgrades, framework version migrations, backward compatibility | `framework-migration` |
| Risk assessment, mitigation planning, decision documentation | `risk-manager` |

### 🤖 AI/ML Ops & Data
| Task | Load |
|------|------|
| LangChain agents, LLM application development, pipeline architecture | `llm-application-dev` |
| Data pipeline design, ETL/ELT, streaming architecture | `data-engineering` |
| Workflow automation — n8n, Temporal, Inngest, durable execution patterns | `workflow-automation` |

---

## Loading Sub-Skills

All sub-skill instructions are in `references/skills-catalog.md`.

```
devops-suite/
├── SKILL.md                      ← You are here (routing hub)
└── references/
    └── skills-catalog.md         ← Full instructions for all skills
```

**Always read the relevant section of `skills-catalog.md` before executing any task.**

---

## Universal DevOps Standards

**Infrastructure as code first** — Every manual change should become an automated, repeatable process. Document before you touch production.

**Observability before changes** — Understand the baseline before deploying. Set up monitoring before you need it in a crisis.

**Blameless culture** — Systems fail, not people. Root causes are in processes and architecture, not individuals.

**Security by default** — Secrets never in code. Least privilege always. Encryption in transit and at rest.

**Idempotency** — Scripts and deployments should be safe to run multiple times. Assume partial failure.

**Rollback first** — Before every deployment, know exactly how to roll back. Test the rollback procedure.

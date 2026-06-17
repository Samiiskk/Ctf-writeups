# TryHackMe — SOC Level 1: Alert Triage

**Date:** June 17, 2026
**Path:** SOC Level 1 — in progress
**Status:** ✅ Room completed

---

## From Events to Alerts

**Flow:** Event occurs → System logs it → Logs shipped to SIEM/EDR
→ Security solution generates **Alert** for suspicious activity

SOC teams receive millions of logs daily but only need to triage
dozens of alerts — alerts filter out the noise.

### Alert Management Platforms
| Solution | Examples | Use |
|----------|---------|-----|
| SIEM | Splunk ES, Elastic | Best for most SOC teams |
| EDR/NDR | MS Defender, CrowdStrike | Own dashboards, but prefer SIEM |
| SOAR | Splunk SOAR, Cortex | Aggregates alerts from multiple solutions |
| ITSM | Jira, TheHive | Custom ticket management |

---

## Roles in Alert Triage

| Role | Responsibility |
|------|---------------|
| L1 Analyst | Reviews alerts, distinguishes bad from good, escalates real threats |
| L2 Analyst | Receives escalations, deeper analysis, remediation |
| SOC Engineer | Ensures alerts have enough info for efficient triage |
| SOC Manager | Tracks speed and quality of triage |

---

## Alert Properties

| Property | What it shows | Example |
|----------|---------------|---------|
| Alert Time | When alert was created | March 21, 15:35 |
| Alert Name | Summary of what happened | "Windows RDP Bruteforce" |
| Alert Severity | Urgency level | 🟢Low 🟡Medium 🟠High 🔴Critical |
| Alert Status | Current state | New / In Progress / Closed |
| Alert Verdict | Real threat or not | True Positive / False Positive |
| Alert Assignee | Who's handling it | Analyst name |
| Alert Description | Why this could be an attack | Rule logic explanation |
| Alert Fields | Specific data points | Hostname, command line, etc |

---

## Alert Prioritization

**Step 1 — Filter:** Only take new, unseen, unresolved alerts —
don't duplicate work with teammates

**Step 2 — Sort by severity:** Critical → High → Medium → Low

**Step 3 — Sort by time:** Oldest first — older breaches mean
attacker has had more time to cause damage

---

## Alert Triage Process

### Initial Actions
1. Assign alert to yourself
2. Move to "In Progress"
3. Review alert name, description, key indicators

### Investigation
1. Identify who/what is under threat — user, host, network
2. Note the specific action — login, malware, phishing
3. Review surrounding events — before and after the alert
4. Use threat intelligence platforms to verify

**Workbooks/Playbooks/Runbooks** — step-by-step instructions for
investigating specific alert categories, when available.

### Final Actions
1. Decide verdict — True Positive or False Positive
2. Write detailed comment explaining analysis and reasoning
3. Move alert to "Closed" status

---

## Key Takeaways
- Alerts exist so analysts don't manually review millions of logs
- L1's job: triage and escalate. L2's job: deep investigation
- Always prioritize by severity first, then by time (oldest first)
- Never touch an alert already assigned to a teammate
- Document your reasoning — comments matter for accountability
- True Positive = real threat, False Positive = noise
- Workbooks/playbooks make triage consistent across the team

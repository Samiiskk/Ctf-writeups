# TryHackMe — SOC Level 1: Alert Reporting & Escalation

**Date:** June 18, 2026
**Path:** SOC Level 1 — in progress
**Status:** ✅ Room completed

---

## Alert Reporting Process

**Before closing or escalating:** Must report the alert with documentation.

**Why report?**
1. **Provide context for escalation** — saves L2 time on analysis
2. **Save findings for records** — raw logs only kept 3-12 months, alerts indefinitely
3. **Improve investigation skills** — writing forces you to understand the alert deeply

---

## Report Format — The Five Ws

| W | What to include | Example |
|---|-----------------|---------|
| **Who** | Which user/account was involved | Username: admin, Email: g.baker@company.com |
| **What** | Exact action or event sequence | Downloaded file, shared with another user |
| **When** | When suspicious activity started and ended | 08:30 - 08:45 UTC |
| **Where** | Device, IP, website involved | Server HQ-FINFS-02, IP 172.16.15.89 |
| **Why** | Your reasoning for the verdict | Financial advisor accessing finance files = expected |

**Most important:** **WHY** — your reasoning for True Positive or False Positive.

---

## When to Escalate to L2

**Escalate if:**
1. Alert indicates major cyberattack requiring deeper investigation/DFIR
2. Remediation needed — malware removal, host isolation, password reset
3. Communication required — customers, partners, management, law enforcement
4. You don't understand the alert and need senior analyst help

**Never:** Close an alert you don't understand. Always escalate.

---

## Escalation Steps

1. Move alert to "In Progress"
2. Write detailed alert report
3. Set verdict — True Positive or False Positive
4. **Assign alert to L2 on shift**
5. Ping them in chat or person
6. L2 receives ticket and reads your report
7. L2 contacts you if clarification needed

---

## Communication Cases — Be Prepared

### Case 1: Urgent Alert, L2 Unavailable
- L2 doesn't respond for 30 minutes on critical alert
- **Action:** Know emergency contacts. Call L2, then L3, then manager.

### Case 2: Account Compromise Alert
- Alert shows Slack/Teams account compromise
- **Action:** Do NOT contact user via breached chat
- Use alternative: phone call, email to personal account

### Case 3: Alert Flood
- Overwhelming number of alerts in short time, some critical
- **Action:** Prioritize by severity but inform L2 immediately about situation

### Case 4: Misclassified Alert
- Realize days later you misclassified an alert
- **Action:** Immediately contact L2 explaining concerns
- Threat actors can be silent for weeks before impact

### Case 5: SIEM Data Issues
- SIEM logs not parsed correctly, not searchable
- **Action:** Don't skip alert. Investigate what you can. Report issue to L2/SOC engineer.

---

## Supporting Lookups & Inventories

### Identity Inventory
Catalogue of employees, service accounts, and their details.

| Full Name | Username | Email | Role | Location | Access |
|-----------|----------|-------|------|----------|--------|
| Gregory Baker | G.Baker | g.baker@company.com | CFO | UK | VPN, HQ, FINANCE |
| Raymond Lund | R.Lund | r.lund@company.com | Financial Adviser | US | VPN, FINANCE |
| svc-veeam-06 | svc-veeam-06 | N/A | Backup Service | N/A | VEEAM, DMZ |

**Sources:** Active Directory, SSO providers, HR systems, custom sheets

---

### Asset Inventory (Asset Lookup)
List of all computing resources — servers, workstations, laptops.

| Hostname | Location | IP | OS | Owner | Purpose |
|----------|----------|----|----|-------|---------|
| HQ-FINFS-02 | UK Datacenter | 172.16.15.89 | Windows Server 2022 | Central IT | File server |
| HQ-ADDC-01 | UK Datacenter | 172.16.15.10 | Windows Server 2019 | Central IT | Primary AD DC |
| PC-891D | London Office | 192.168.5.13 | Windows 11 Pro | Tech Support | Accountant PC |

**Sources:** Active Directory, SIEM/EDR agents, MDM, custom sheets

---

### Network Diagrams
Visual schema showing locations, subnets, and connections.

**Use to investigate network alerts:**
- Understand IP addresses and subnets
- Identify suspicious network movement
- Reconstruct attack paths across networks

**Example:** Threat actor → VPN brute force → VPN login → assigned IP from VPN subnet → scans database subnet → blocked by firewall → pivots to office subnet.

---

## SOC Workbooks (Playbooks/Runbooks)

**What they are:** Structured documents defining investigation steps for specific threats.

**Why they exist:** Ensure consistency and prevent L1 analysts from missing vital details.

**Structure:** Usually three sections
1. **Enrichment** — gather info from threat intelligence and identity inventory
2. **Investigation** — analyze SIEM logs and data
3. **Escalation** — decide if L2 escalation or user communication needed

**Example:** "Unusual Login Location" workbook guides investigation of atypical logins through threat intel checks, user context, geolocation verification, then escalation decision.

---

## Key Takeaways
- Always report alerts — even False Positives deserve documentation
- Five Ws framework ensures complete analysis
- Never close an alert you don't understand — escalate instead
- L2 will use YOUR report to start their investigation
- Identity and asset inventory are essential context for alerts
- Network diagrams help understand suspicious IP activity
- Workbooks eliminate guesswork — follow them precisely
- Crisis communication procedures must be known before crisis happens
- Document misclassifications immediately — threat actors wait weeks to attack
- SIEM data issues don't mean skip the alert — investigate what you can

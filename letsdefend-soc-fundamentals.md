# Let's Defend — SOC Fundamentals

**Date:** June 6, 2026
**Platform:** Let's Defend — SOC Analyst Pathway
**Status:** - In progress

---

## SOC Types

| Type | Description |
|------|-------------|
| In-house SOC | Internal team, requires dedicated budget |
| Virtual SOC | No permanent facility, works remotely |
| Co-Managed SOC | Internal staff + external MSSP working together |
| Command SOC | Oversees smaller SOCs across large regions |

---

## Three Pillars of SOC
- **People** — trained analysts who adapt to new attack types
- **Process** — standardized actions aligned to NIST, PCI, HIPAA
- **Technology** — right tools for detection, prevention, and analysis

---

## SOC Roles

| Role | Responsibility |
|------|---------------|
| SOC Analyst (L1/L2/L3) | Classifies alerts, finds root cause, advises remediation |
| Incident Responder | First assessment of security breaches |
| Threat Hunter | Proactively hunts APTs and sophisticated threats |
| Security Engineer | Maintains SIEM, builds SIEM-SOAR integrations |
| SOC Manager | Budgeting, staffing, strategy — not technical |

---

## SOC Analyst Responsibilities
- First person to investigate and respond to threats
- Reviews SIEM alerts daily and determines real vs false threats
- Escalates serious incidents to supervisors
- Uses EDR, Log Management, and SOAR to investigate

## Skills a SOC Analyst Needs
- **Operating Systems** — know what normal looks like on Windows/Linux
  to identify what is abnormal
- **Networking** — identify malicious IPs/URLs, detect data leaks
- **Malware Analysis** — understand malicious software behavior,
  identify command and control (C2) communication

---

## SIEM & SOC Analyst Relationship

**SIEM** = Security Information and Event Management
- Collects and filters logs from all environment sources
- Generates alerts when suspicious activity crosses a threshold
- Popular tools: IBM QRadar, Splunk, ArcSight ESM, FortiSIEM

**Example SIEM rule:**
20 incorrect password attempts in 10 seconds → alert triggered
(normal user wouldn't do this — likely brute force attack)

**SOC Analyst's job with SIEM:**
- Monitor alerts in Main Channel
- Take ownership of alert → move to Investigation Channel
- Investigate using EDR, Log Management, Threat Intelligence
- Determine: real threat or false positive?
- Report false positives back to SIEM team to improve rules

**False positive example:**
URL containing "union" flagged as SQL injection attempt
but was actually a Google search — not a real threat.
Analyst flags this to SIEM team to refine the rule.

---

## Log Management

**What it is:**
Central place to access all logs — web, OS, firewall, proxy, EDR.

**Why it matters:**
- Search all log sources with one query instead of checking each device
- Saves time and reduces errors during investigations

**How SOC analysts use it:**
- Check if any device communicated with a suspicious IP or domain
- Example: malware found communicating with letsdefend.io →
  search Log Management to see if other devices also contacted it
- Check for data exfiltration beyond what SIEM detected

---

## Key Takeaways
- SOC analyst is first responder — triage, investigate, escalate
- SIEM generates alerts but analyst decides if it's a real threat
- False positives are normal — good analyst identifies and reports them
- Log Management is essential for full investigation beyond SIEM alerts
- Know OS and networking basics before touching security tools
- Threat hunters go beyond alerts — they proactively look for threats

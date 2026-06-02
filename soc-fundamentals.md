# TryHackMe — SOC Fundamentals

**Date:** June 2, 2026
**Path:** SOC Level 1 - IN Progress
**Status:** room Completed

---

## What is a SOC?
A Security Operations Center is a dedicated facility run by
a specialized security team that monitors an organization's
network 24/7. Main focus is Detection and Response.

## SOC Team Roles
| Role | Responsibility |
|------|---------------|
| SOC Analyst L1 | First responder, basic alert triage |
| SOC Analyst L2 | Deeper investigation, correlate data |
| SOC Analyst L3 | Threat hunting, incident response |
| Security Engineer | Deploys and configures security tools |
| Detection Engineer | Builds detection rules and logic |
| SOC Manager | Manages processes, reports to CISO |

## Three Pillars of SOC
- **People** — the SOC team and their roles
- **Process** — how alerts are handled and escalated
- **Technology** — tools like SIEM, EDR, Firewall

## Detection Responsibilities
- Detect vulnerabilities in systems
- Detect unauthorized access/activity
- Detect policy violations
- Detect intrusions

## Alert Triage — The 5 Ws
Every alert must answer:
- **What?** — what was detected
- **When?** — time of detection
- **Where?** — which host/system
- **Who?** — which user involved
- **Why?** — root cause after investigation

## Key SOC Tools
- **SIEM** — collects logs, detects suspicious activity via rules
- **EDR** — monitors endpoints in real time, allows quick response
- **Firewall** — filters unauthorized network traffic
- Others: Antivirus, IDS/IPS, XDR, SOAR

## Key Takeaway
A mature SOC needs all three pillars working together —
the right people, following the right processes,
using the right technology.

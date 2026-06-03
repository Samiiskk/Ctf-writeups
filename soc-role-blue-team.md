# TryHackMe — SOC Role in Blue Team

**Date:** June 3, 2026
**Path:** SOC Level 1 — in progress
**Status:** - Room completed

---

## Security Hierarchy
- CEO focuses on business objectives, not technical details
- CEO hires a **CISO** to manage security strategy
- CISO oversees multiple security departments

## Security Departments
| Team | Role |
|------|------|
| Red Team | Offensive security, pentesters, ethical hackers |
| Blue Team | Defensive security, SOC analysts, incident responders |
| GRC Team | Policies, compliance (e.g. PCI DSS) |

## Blue Team Structure
Blue Team = defensive security, monitors and responds to attacks.
Team size ranges from 3 to 50 members depending on company size.

### SOC (Security Operations Center)
First line of defense — where most cybersecurity careers start.

| Role | Responsibility |
|------|---------------|
| L1 Analyst | Triage alerts, pass complex cases to L2 |
| L2 Analyst | Investigate advanced attacks |
| Engineer | Configure tools like EDR and SIEM |
| Manager | Manages the whole SOC team |

### CIRT (Cyber Incident Response Team)
Called in when SOC can't handle the incident alone — the "firefighters".
Works without depending on tools like EDR or SIEM.

Examples:
- **JPCERT** — Japan's national CERT
- **Mandiant** — private global incident response team
- **AWS CIRT** — handles AWS customer security incidents

### Specialized Defensive Roles
| Role | What they do |
|------|-------------|
| Digital Forensics Analyst | Uncover hidden threats in disk and memory |
| Threat Intelligence Analyst | Research emerging threat groups |
| AppSec Engineer | Secure software development lifecycle |
| AI Researcher | Study and defend against AI threats |

---

## Internal SOC vs MSSP

| Topic | Internal SOC | MSSP |
|-------|-------------|------|
| Work pace | Calm shifts, less pressure | Queue of urgent alerts every shift |
| Security tools | Few tools, know them deeply | 60+ diverse tools across clients |
| Incident exposure | Few major incidents per year | Weekly attacks, high learning rate |

**MSSP** = Managed Security Services Provider — outsourced SOC for companies
that can't run their own.

---

## Security Priorities by Industry
- **Law firms** — privacy of legal documents
- **Factories** — availability of production lines
- **Hospitals** — patient safety

Every company has a unique security approach based on what matters most.

---

## Key Takeaways
- SOC is the best entry point for a cybersecurity career
- CIRT handles major incidents SOC can't contain alone
- Internal SOC = deeper tool knowledge, calmer pace
- MSSP = more exposure to attacks, higher pressure
- Security priorities differ by industry — no one-size-fits-all approach

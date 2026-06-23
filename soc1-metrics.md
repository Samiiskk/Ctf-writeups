# TryHackMe — SOC Metrics & Objectives

**Date:** June 23, 2026
**Path:** SOC Operations
**Status:** - Room completed

---

## SOC Core Metrics

| Metric | Formula | What it measures | Ideal range |
|--------|---------|------------------|------------|
| **Alerts Count** | Total alerts received | Overall SOC load | 5-30 per day per L1 |
| **False Positive Rate** | False Positives / Total Alerts | Level of noise | <80% (max) |
| **Alert Escalation Rate** | Escalated Alerts / Total Alerts | L1 experience level | <50% (better: <20%) |
| **Threat Detection Rate** | Detected Threats / Total Threats | SOC reliability | **100% (non-negotiable)** |

---

## Understanding Each Metric

### Alerts Count
- Too many (80+) = alert fatigue, miss real threats
- Too few (0 per week) = possible SIEM/visibility issue
- Sweet spot: 5-30 per day per L1 analyst

### False Positive Rate
- **>80% FPR = serious problem**
- Causes alert fatigue → analysts miss real threats
- Solution: Tune detection rules, exclude trusted activities

### Alert Escalation Rate
- Measures L1 analyst experience and confidence
- High rate (>50%) = lots of escalations = inexperienced team
- Low rate (<20%) = experienced, independent analysts
- Balance needed: don't over-escalate OR under-escalate

### Threat Detection Rate (TDR)
- **MUST be 100%** — every missed threat is potential disaster
- Example: Detected 4 of 6 attacks = 67% TDR = VERY BAD
- Missed threats = ransomware, data breach, business disruption

---

## Service Level Agreements (SLA)

**SLA:** Contract between SOC and company management (or MSSP and customers).

| Metric | Common SLA | Description |
|--------|-----------|-------------|
| **SOC Availability** | 24/7 | Team working schedule (8/5 or 24/7) |
| **MTTD** | 5 minutes | Mean Time to **Detect** — avg time from attack to detection |
| **MTTA** | 10 minutes | Mean Time to **Acknowledge** — avg time for L1 to start triage |
| **MTTR** | 60 minutes | Mean Time to **Respond** — avg time to actually stop breach |

---

## Improving Metrics

### If False Positive Rate >80%
- Exclude trusted activities (system updates) from detection rules
- Automate alert triage for common alerts using SOAR/scripts
- Review and tune detection logic

### If MTTD >30 minutes
- Contact SOC engineers to run detection rules faster
- Check if SIEM logs collected in real-time (not 10-min delay)
- Verify all log sources properly configured

### If MTTA >30 minutes
- Ensure analysts notified in REAL-TIME of new alerts
- Evenly distribute alert queue among on-shift analysts
- Improve alerting mechanisms

### If MTTR >4 hours
- Escalate threats to L2 immediately
- Document attack scenarios and responses in playbooks
- Automate remediation where possible

---

## Why Metrics Matter

1. **Efficiency:** Make SOC operations faster and better
2. **Performance evaluation:** Your results lead to career growth
3. **Resource planning:** Shows where to invest in tools/people
4. **Compliance:** Demonstrates security posture to management

---

## Key Takeaways
- 5-30 alerts/day per L1 is ideal
- False positive rate over 80% = serious problem
- Escalation rate should stay <50% (better <20%)
- TDR MUST be 100% — no exceptions
- MTTD, MTTA, MTTR are critical SLA metrics
- Metrics directly impact your career progression

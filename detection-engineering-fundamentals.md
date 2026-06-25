# TryHackMe — Introduction to Detection Engineering

**Date:** June 25, 2026
**Path:** SOC Level 1
**Status:** - Room completed

---

## What is Detection Engineering?

The continuous process of building and operating threat intelligence analytics to identify potentially malicious activity or misconfigurations. Requires cultural alignment across ALL security teams and management.

---

## Four Detection Types

### 1. Configuration Detection
Uses current knowledge of environment to identify misalignments across network, asset, identity.

| Benefits | Challenges |
|----------|-----------|
| Easiest to create in static environments | Hard in dynamic environments |
| Detects all malicious activity under perfect coverage | Limited visibility reduces effectiveness |
| Multiple expertise levels can execute | Assumes knowledge of infrastructure |
| Easy to combine with other detections | Frequent changes = high false positives |

### 2. Modelling
Defines baseline operations and records deviations.

| Benefits | Challenges |
|----------|-----------|
| Identifies unknown adversary activities | No context of threat during investigations |
| Easy in static environments | Hard in dynamic environments |
| | Potentially adds existing malicious activity to model |

### 3. Indicator Detection
Uses IOCs (Indicators of Compromise) — bad IPs, domains, hashes, etc.

| Benefits | Challenges |
|----------|-----------|
| Fastest to create and deploy | Value depends on adversary's rate of change |
| Raises specific threat contexts | Retroactive — need to observe first |
| Useful for enrichment | Limited indicators processed at a time |

### 4. Threat Behaviour Detection
Looks at adversary TTPs regardless of specific indicators.

| Benefits | Challenges |
|----------|-----------|
| Withstands adversary's rate of change | Requires lots of data for complete coverage |
| Easy to tune/adapt | Moderately difficult initial implementation |
| Low false positive rates | Only detects similar threat behaviour |
| Integrates with playbooks | Must be modified across industries |

---

## Detection as Code (DaC)

Structured approach treating detection logic as code. Incorporates software engineering best practices.

### Key Elements
- **Version Control** — track changes to detection rules
- **CI/CD Automation** — automated testing and deployment

### Benefits
- **Customizable:** Common languages (Sigma, YARA) = vendor-agnostic
- **Test-Driven:** Identify blind spots early
- **Collaboration:** Eliminates team isolation
- **Code Reusability:** Reuse detection patterns

---

## Detection Engineering Lifecycle

### 1. Detection Gap Analysis
Identify where detection can improve via threat modelling:
- **Reactive:** Assess recent incident reports, lessons learned
- **Proactive:** Use ATT&CK framework + threat intel to map potential attacks

### 2. Datasource Identification + Log Collection
Map relevant data sources to identified threats. Determine what logs exist vs what's missing.

### 3. Baseline Creation
Define normal behavior before detecting abnormal.

Two categories:
- **High-level:** Broad OS-independent standards
- **Technical:** OS-based configuration standards (hardening, IAM, network activities)

### 4. Rule Writing
Write detection rules against data sources:
- **Snort rules** — network traffic
- **YARA rules** — file data
- **Sigma** — generic signature language for log files

### 5. Deployment, Automation & Tuning
Deploy to production. Continuously update for:
- Changes in attack vectors
- New patterns
- Environment changes

---

## Key Frameworks for Detection Engineering

### MITRE ATT&CK
Maps adversarial actions based on infrastructure. Guides what to look for during detection gap analysis.

### CAR (Cyber Analytics Repository)
Detect and prioritize adversary behaviors based on ATT&CK framework.

### Pyramid of Pain
Shows how difficult it is for adversary to change their TTPs when detected:
TTPs (highest pain for attacker)

Tools

Network/Host Artifacts

Domain Names

IP Addresses

Hash Values (easiest to change)

### Cyber Kill Chain (Lockheed Martin)
Seven phases of cyber attacks:
1. Reconnaissance
2. Weaponization
3. Delivery
4. Exploitation
5. Installation
6. Command & Control
7. Actions on Objectives

### Unified Kill Chain
Extends Cyber Kill Chain to 18 phases combined with MITRE ATT&CK.

---

## ADS Framework (Alerting & Detection Strategy)

Palantir's framework for documenting detection content. Addresses alert fatigue and apathy.

### Nine Stages
1. **Goal** — intended reasons and behavior to detect
2. **Categorization** — mapping to MITRE ATT&CK TTPs
3. **Strategy Abstract** — top-level description of detection approach
4. **Technical Context** — technical environment details
5. **Blind Spots and Assumptions** — where detection may fail
6. **False Positives** — non-malicious triggers to tune out
7. **Validation** — steps to produce true-positive test
8. **Priority** — alerting levels and criteria
9. **Response** — triage and investigation guidance

---

## Detection Maturity Level (DML) Model

Ryan Stillions' 2014 model assessing organization's ability to use threat intel for detection.

| Level | Name | Description |
|-------|------|-------------|
| DML-8 | Goals | Detect adversary motives (near impossible) |
| DML-7 | Strategy | Detect non-technical adversary intentions |
| DML-6 | Tactics | Detect tactics without knowing technique/tool |
| DML-5 | Techniques | Detect specific APT techniques |
| DML-4 | Procedures | Detect sequences of events |
| DML-3 | Tools | Detect adversary tools (transfer + operation) |
| DML-2 | Host & Network Artifacts | Gather IOCs (often after the fact) |
| DML-1 | Atomic Indicators | Threat intel feeds (IP lists, domains) |
| DML-0 | None | No detection processes established |

**Key principles:**
1. Maturity = ability to APPLY intel to detection (not just obtain it)
2. Without detection, there is no response

---

## Key Takeaways
- Detection engineering is continuous, not a one-time activity
- Four detection types: Configuration, Modelling, Indicator, Behaviour
- Detection as Code brings engineering discipline to detections
- Sigma and YARA are common detection languages
- MITRE ATT&CK + Pyramid of Pain = essential frameworks
- DML model measures organizational detection maturity
- ADS framework ensures quality detection documentation

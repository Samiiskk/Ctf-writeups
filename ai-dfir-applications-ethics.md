# TryHackMe — AI/ML in DFIR: Applications, Limitations & Ethics

**Date:** June 24, 2026
**Path:** AI Security + DFIR Track
**Status:** - Advanced rooms completed

---

## AI/ML Capabilities in DFIR

### 1. Data Processing
DFIR analysts process massive data volumes searching for evidence. Deep learning + Transformers parallelize this:
- Process entire text bodies in milliseconds
- Provide insights + classifications on processed data
- Drastically reduce manual workload + time

### 2. Anomaly Detection
Sophisticated attacks blend into normal activity. ML learns "normal" baseline, flags deviations:
- Supervised + unsupervised models detect anomalies
- Turn haystack into handful of hay
- Spot patterns humans can't comprehend
- User/system/network behavior baselining

### 3. Scalability
Modern infrastructure (cloud, hybrid, remote) generates unprecedented forensic data. AI scales effortlessly:
- Continuously processes/learns from millions of events
- Covers large distributed environments
- No proportional increase in workload
- Handles growth automatically

---

## AI/ML Applications in DFIR

### Anomaly Detection / User & Entity Behavior Analytics (UEBA)
**What it does:** Flag unusual user/system behavior vs learned "normal"

**Tools:** Splunk UEBA, Elastic ML, Exabeam

**How it works:** Unsupervised learning (Isolation Forests, Autoencoders) learns baseline behavior. Deviations flagged as threats without predefined rules.

### Phishing & Communication Analysis
**What it does:** Detect phishing emails, flag risky language in chats/emails

**Tools:** Microsoft Defender for O365, Splunk NLP

**How it works:** Transformer models (BERT, RoBERTa) classify messages. Detect impersonation, urgency phrases, malicious links. 99% accuracy in studies.

### Malware / File Classification
**What it does:** Classify files as malicious or benign

**Tools:** Microsoft Defender (STAMINA), Cylance, VirusTotal ML

**How it works:** Analyze file metadata, code signatures, sandbox behavior. Trained on large malware corpora. Classify new files based on learned patterns.

### Alert Triage & Prioritization
**What it does:** Automatically score, rank, filter alerts

**Tools:** Cortex XSOAR/XSIAM, IBM QRadar Advisor, CrowdStrike Falcon + Charlotte AI

**How it works:** ML analyzes past alerts, analyst feedback, incident outcomes. Ranks by severity/relevance. Reduces noise, surfaces urgent issues first.

### Timeline & Event Correlation
**What it does:** Reconstruct attack timelines by clustering + linking logs

**Tools:** Timesketch, Velociraptor, Jupyter-based analysis

**How it works:** AI clusters similar events, identifies causal relationships, aligns activity across systems. Visualizes attack chains, reconstructs timelines faster.

### Image & Video Forensics
**CNN-Based Forgery Detection:**
- Combine ELA (Error Level Analysis) + CNN models
- ELA highlights compression inconsistencies
- CNN classifies regions as forged/authentic
- 94% accuracy

**Deepfake Detection:**
- CNN + other AI tech detect subtle facial inconsistencies
- State-of-the-art accuracy
- Analyze videos for authenticity

**GANs (Generative Adversarial Networks):**
- Two networks compete: one generates fakes, one detects
- Both improve → arms race
- Used defensively to train detectors on AI-generated fakes
- Spot subtle manipulations humans miss

---

## AI Limitations in DFIR

### Probabilistic vs Deterministic
**Problem:** Traditional code is deterministic. AI is probabilistic.
- Same input → different outputs
- Different timelines from same data
- Prompt sensitivity = vastly different outputs

**Implication:** Digital forensics demands consistent, repeatable results. Non-determinism breaks this requirement.

### Accuracy vs Precision vs Recall

| Metric | Definition | Problem in Isolation |
|--------|-----------|---------------------|
| **Accuracy** | Overall correct predictions | Can be misleading with imbalanced data (99% if model predicts majority class) |
| **Precision** | How often positive predictions correct | Model can be selective, missing some positives |
| **Recall** | Success identifying all positives | Model can flag everything, creating false positives |

**Solution:** Evaluate all three together for true performance insight.

### Garbage In, Garbage Out (GIGO)
**Principle:** AI output quality = input quality

If trained on "bad" data (incomplete, skewed), model confidently asserts false predictions as fact. Critical for justice-oriented work.

### Lack of Explainability ("Black Box")
Many AI models don't explain their reasoning. Clashes with forensics core tenet: transparency + defensibility.

**Real case:** LLM flagged emails "suspicious" but legal team couldn't explain why. Court excluded evidence (failed Daubert test).

---

## Bias & Fairness

### Problem
ML models trained on historical data. If data contains prejudices, output reflects them.

**Real-world impact:**
- Facial recognition misidentifies minorities at much higher rates
- At least 7 wrongful arrests in U.S. from faulty face recognition
- Almost all victims were African American

### Legal + Ethical Duty
1. **Legally:** Defense can exclude biased AI evidence
2. **Ethically:** Forensic experts must validate + correct biases
   - Use diverse training data
   - Apply bias mitigation techniques
   - Ensure equitable treatment
   - Uphold investigation integrity

---

## Accountability & Chain of Custody

**Challenge:** "Who is responsible for algorithm output?"

Courts require digital evidence:
- Traceable handling
- Preserved integrity at each step
- Chain of custody maintained
- Audit trail complete

**Problem with AI:**
- Many cloud-based AI tools operate opaquely
- Intermediate AI outputs not logged
- Violates chain of custody requirements
- Defense can challenge findings procedurally

**Solution:**
- Carefully document AI processes
- Secure all outputs
- Use on-premises or controlled systems
- Satisfy legal scrutiny

---

## Privacy & Data Protection

### Challenge
AI models thrive on large datasets. Investigation use triggers privacy issues.

- Public cloud servers may expose sensitive evidence to third parties
- Violates privacy laws + court orders
- GDPR restricts personal data processing (even for law enforcement)

### Mitigation
- Run AI tools in secure offline environments
- Use federated learning
- Minimize data exposure
- Comply with privacy frameworks

---

## The Verdict: "With Great Power Comes Great Responsibility"

AI is powerful tool for DFIR:
- ✅ Accelerates investigations
- ✅ Enhances analyst capabilities
- ✅ Enables pattern recognition
- ✅ Improves efficiency

BUT:
- ❌ Non-determinism challenges forensic consistency
- ❌ Black box nature complicates legal defense
- ❌ Bias can introduce injustice
- ❌ Privacy + accountability concerns

**Key insight:** AI cannot replace human expertise. It's a guiding light, not the complete answer.

---

## Best Practices for AI in DFIR

1. **Explainability first** — use explainable AI models when possible
2. **Audit for bias** — regularly test model fairness
3. **Document everything** — maintain chain of custody with AI
4. **Validate results** — human review of AI conclusions
5. **Privacy-first** — use on-premises/secure solutions
6. **Ethical framework** — follow legal + ethical guidelines
7. **Continuous improvement** — learn from AI successes + failures

---

## Takeaways
- AI excels at data processing, anomaly detection, scalability
- UEBA, phishing detection, malware classification proven effective
- But non-determinism, bias, and explainability are real concerns
- Black box problem = legal admissibility challenges
- Bias in AI = real-world injustice
- Chain of custody must include AI process documentation
- Human expertise essential — AI is augmentation, not replacement
- Investigators have ethical duty to use AI responsibly

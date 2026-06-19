# TryHackMe — AI/ML Security Threats Pathway

**Date:** June 19, 2026
**Path:** AI Security Pathway
**Status:** - 2 Rooms completed

---

## AI/ML Evolution

| Technology | What it does | Key advance |
|-----------|-------------|------------|
| **AI** | Machines mimic human intelligence | Broad field, started 1950s |
| **ML** | Learns patterns from data without explicit programming | Self-improving algorithms |
| **DL** | Deep learning — neural networks, processes vast unstructured data | Self-learning, no labeling needed |
| **LLMs** | Large Language Models — predict next word, generate text | Transformers, ChatGPT era |

---

## Machine Learning Lifecycle

1. **Define problem** — what are we solving?
2. **Collect & clean data** — feature engineering
3. **Train model** — using selected algorithm
4. **Evaluate & tune** — optimize performance
5. **Deploy** — production environment
6. **Monitor** — maintain accuracy, retrain when needed

---

## ML Algorithms

| Type | Uses labeled data? | Purpose | Example |
|------|------------------|---------|---------|
| **Supervised** | Yes | Classification/regression | Spam email detection |
| **Unsupervised** | No | Find patterns | Clustering similar data |
| **Semi-supervised** | Some | Hybrid approach | Limited labeled data |
| **Reinforcement** | Reward/penalty | Learn through feedback | Game AI training |

---

## Neural Networks & Deep Learning

**How they work:**
- Input layer receives raw data
- Hidden layers process and refine
- Connections have weights (importance)
- Output layer produces final prediction
- Network "learns" by adjusting weights

**Deep Learning:** When network has 3+ hidden layers.

---

## Large Language Models (LLMs)

**What they do:** Predict next word in sequence using transformer neural networks.

**Pre-training:** Trained on massive text datasets (GPT-3 = 2,600 years of reading)

**Key innovation:** Transformers with "attention" mechanism — assigns importance to key words for better context understanding.

**Fine-tuning:** Specializing pre-trained models on task-specific data.

**RLHF:** Reinforcement Learning from Human Feedback — humans review and flag issues, parameters adjusted.

---

## AI Vulnerabilities in Models

| Vulnerability | What it is | Impact |
|---------------|-----------|--------|
| **Prompt Injection** | Override original instructions | Disclose sensitive info, generate harmful content |
| **Data Poisoning** | Manipulate training data | Model generates biased/incorrect output |
| **Model Theft** | Unauthorized access to model | Steal IP, create clones, malicious use |
| **Privacy Leakage** | Model reveals training data | Expose patient records, confidential info |
| **Model Drift** | Performance degrades over time | Changes in data environment make model obsolete |

---

## Enhanced Attacks Using AI

### Malware
- Attackers use generative AI to write code instantly
- Simplifies attack, reduces time investment

### Deepfakes
- AI-generated voice/video can fool authentication
- Used for fraud, impersonation, coercion
- Example: Deepfake video call tricked person into wiring $25M

### Phishing
- AI generates fluent, context-specific phishing emails
- Harder to spot using instinct alone
- Overcome language barriers

---

## AI Defending Cybersecurity

**IBM Cost of Data Breach Report findings:**
- Companies using AI save **$2.2 Million** in breach costs
- Average breach cost: $4.88 Million
- AI reduces breach identification/containment time by **108 days**

### How AI Helps Defense

**Enhanced analysis:**
- ML finds patterns and anomalies in network traffic
- Intrusion detection at massive scale
- Examples: Microsoft Defender, Splunk

**Predictive automation:**
- Train models on phishing examples → detect phishing emails
- Automated blocking before reaching users
- "If-then" automation workflows

**Summarization & digestion:**
- LLMs summarize incident reports
- Draw correlations between incidents
- Save days of manual review

**Investigation:**
- Query LLMs with logs in natural language
- Get diagnostic queries and recommendations
- Threat hunting — AI suggests attack paths analysts wouldn't think of

---

## Securing AI Implementations

### Securing AI Models
- Enforce strict access controls
- Strong authentication + MFA
- RBAC (Role-Based Access Control)

### Privacy Protection
- Treat training data as sensitive data
- Encrypt training datasets
- Minimize data collection (GDPR principle)

### AI Security Standards
- Implement ISO/IEC 27090 for AI systems
- Follow recognized frameworks
- Proactive risk mitigation

### Model Monitoring
- Monitor for performance drops → retrain
- Detect unexpected behavior, biases, anomalies
- Use explainability tools (SHAP, LIME)

---

## Data Provenance & Supply Chain

**Problem:** Most models trained on "datasets of datasets" — original attribution lost.

**Key finding:** 70% of popular dataset licenses listed as "Unspecified"

**Solution:** ML-BOM (ML Bill of Materials)
- Document dataset sources
- Track licenses
- Note PII categories
- Record filtering decisions

**PII in pipelines:**
- Web scraping picks up medical records, emails, credentials
- Truffle Security found 12,000 live API keys/passwords in Common Crawl
- GDPR requires data minimization — tension with "more data = better"

---

## Building Models: Key Concepts

### Epochs & Overfitting
- **Epoch** = one complete pass through training data
- **Overfitting** = model memorizes training data instead of learning general patterns
- Security risk: Model can memorize and reproduce sensitive training data when prompted

### Model Validation
- Hold back portion of data (validation set) — never used for training
- Test model on unseen data regularly
- If training accuracy increases but validation accuracy plateaus = overfitting detected
- Quality gate for security

### Pruning & Quantization
- **Pruning** = removes unimportant parameters, shrinks model
- **Quantization** = reduces numerical precision (32-bit → 8-bit)
- Security issue: Can degrade safety mechanisms; backdoor defenses may fail on quantized versions
- Applied post-training, often by third-party — changes behavior without documentation

### Federated Learning
- Train across decentralized devices, only send weight updates back
- **Pro:** Reduces privacy risk — data never leaves participant
- **Con:** Participants can submit poisoned updates, hard to detect at aggregation
- Solves one trust problem, creates another

---

## Pre-Trained Models & Fine-Tuning

**Pre-trained model:** Already trained on large dataset, knows grammar/facts/reasoning.

**Fine-tuning:** Continue training on smaller task-specific dataset.

### The Inheritance Problem
When you fine-tune, you inherit everything from base model:
- Biases from pre-training persist
- Unexpected behaviors carry through
- Safety alignment not as durable

**Three concrete issues:**

1. **Safety alignment erodes** — Stanford/Princeton found 10 adversarial examples can compromise defenses (costs <$0.20)
2. **Specialization increases attack surface** — fine-tuned models more susceptible to prompt injection
3. **Version matters** — if base model has backdoor, all derivatives inherit it

---

## Model Cards

**Purpose:** Structured documentation describing model, how it was built, limitations.

**Should include:**
- Training data sources and filtering
- Intended use (and explicit what it wasn't designed for)
- Evaluation results
- Known limitations
- Bias assessment
- License

**The gap:** Often incomplete, vague, or absent. No regulatory requirement. Sparse/missing card = red flag.

---

## Key Takeaways
- AI/ML is evolving: AI → ML → DL → LLMs
- Models have serious vulnerabilities: injection, poisoning, theft, privacy leakage, drift
- AI enhances attacks: malware, deepfakes, phishing
- AI defends: analysis, prediction, summarization, investigation
- Only 24% of gen AI initiatives are secured — must secure from day 1
- Data provenance is opaque — use ML-BOM
- Fine-tuning inherits all base model risks
- Model cards are audit trails — missing = flying blind
- Explainability tools (SHAP, LIME) help detect anomalies

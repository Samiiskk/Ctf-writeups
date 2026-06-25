# TryHackMe — Elastic Stack: The Basics

**Date:** June 25, 2026
**Path:** SOC Level 1
**Status:** - Room completed

---

## What is Elastic Stack (ELK)?

Originally built for storing, searching, and visualizing large datasets. Now widely used as a SIEM solution in SOC environments.

**ELK = Elasticsearch + Logstash + Kibana + Beats**

---

## Four Core Components

### 1. Elasticsearch
- Full-text search and analytics engine
- Stores, analyzes, correlates JSON-formatted data
- Supports RESTful API for interaction
- Acts as the database layer

### 2. Logstash
Data processing engine with three-part configuration:

| Part | Purpose |
|------|---------|
| **Input** | Where data is ingested from |
| **Filter** | Normalize/parse the ingested data |
| **Output** | Where filtered data is sent (Kibana, Elasticsearch, file, port) |

Supports many Input, Output, and Filter plugins.

### 3. Beats
Host-based agents (data-shippers) that transfer data from endpoints to Elasticsearch.

Each Beat is single-purpose:
- **Winlogbeat** — Windows event logs
- **Packetbeat** — Network traffic flows
- **Filebeat** — Log files
- **Metricbeat** — System metrics

### 4. Kibana
- Web-based data visualization tool
- Works with Elasticsearch
- Real-time analysis and investigation
- Create visualizations and dashboards

---

## How They Work Together

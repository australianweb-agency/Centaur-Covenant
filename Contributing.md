# 🛠️ The Technical Foundation

> *"Even the most profound philosophy needs a machine to carry it forward."*

This document describes the infrastructure that powers The Centaur Covenant — our "digital body."

---

## 🖥️ The Heart: HP Z440 Workstation

Our entire operation runs on a single, self-hosted workstation:

| Component | Specification |
|-----------|---------------|
| **Model** | HP Z440 |
| **Role** | Central nervous system |
| **Location** | Hungary (Caravan HQ) |
| **Uptime** | 24/7 |

### Why Self-Hosted?

| Benefit | Description |
|---------|-------------|
| 🔒 **Privacy** | Client data never leaves our infrastructure |
| 💰 **Cost Control** | No per-execution cloud fees |
| 🔧 **Customization** | Full control over every component |
| ⚡ **Reliability** | Independent of third-party uptime |
| 🌱 **Sustainability** | One machine, minimal footprint |

---

## 🔄 Automation Layer: n8n

**n8n** is our workflow automation backbone — self-hosted via Docker.

```
┌─────────────────────────────────────────┐
│              DOCKER HOST                │
│  ┌─────────────────────────────────┐   │
│  │           n8n Container          │   │
│  │  ┌─────────┐  ┌─────────┐       │   │
│  │  │ Lead    │  │ Centaur │       │   │
│  │  │ Automata│  │ Pulse   │       │   │
│  │  └─────────┘  └─────────┘       │   │
│  │  ┌─────────────────────┐        │   │
│  │  │ Adaptive Outreach   │        │   │
│  │  └─────────────────────┘        │   │
│  └─────────────────────────────────┘   │
└─────────────────────────────────────────┘
```

### n8n Configuration:
- **Version:** Latest stable
- **Deployment:** Docker Compose
- **Database:** SQLite (default)
- **Executions:** Stored for 30 days
- **Timezone:** CET (Budapest)

### Why n8n?

| Feature | Benefit |
|---------|---------|
| Open Source | No vendor lock-in |
| Self-Hostable | Full data control |
| Visual Builder | Rapid prototyping |
| 400+ Integrations | Connect anything |
| Code Nodes | Unlimited flexibility |

---

## 🧠 Intelligence Layer: LLM Orchestration

We use multiple AI models, each for their strengths:

### Claude (Anthropic)
| Attribute | Value |
|-----------|-------|
| **Model** | Claude 3.5 Sonnet |
| **Role** | The Architect |
| **Strengths** | Deep analysis, structured thinking, code generation |
| **Used For** | Relevance scoring, technical documentation, strategy |

### Gemini (Google)
| Attribute | Value |
|-----------|-------|
| **Model** | Gemini 2.5 Flash |
| **Role** | The Bridge (Nexus) |
| **Strengths** | Speed, creativity, real-time processing |
| **Used For** | Content generation, CMO strategy, quick analysis |

### Integration Pattern:
```
User Request / Trigger
        ↓
   ┌────────────────┐
   │ Task Router    │
   └───────┬────────┘
           │
     ┌─────┴─────┐
     ▼           ▼
┌─────────┐ ┌─────────┐
│ Claude  │ │ Gemini  │
│(Deep)   │ │(Fast)   │
└────┬────┘ └────┬────┘
     │           │
     └─────┬─────┘
           ▼
   Combined Output
```

---

## 📡 Communication Layer

### Telegram Bot API
- **Purpose:** Real-time Command & Control
- **Features:**
  - Instant lead alerts
  - System status notifications
  - Manual trigger commands
- **Security:** Token-based authentication

### Google Sheets API
- **Purpose:** Structured data logging
- **Sheets:**
  - `PIXELLA Lead Tracker` (Austria)
  - `AWA Lead Tracker` (Australia)
  - `Conen Lead Tracker` (Hungary)
- **Columns:** Date, Title, URL, Summary, Relevance, Business Opportunity

---

## 🌐 External Integrations

| Service | Purpose | Status |
|---------|---------|--------|
| Google News RSS | Lead source | ✅ Active |
| LinkedIn | Content distribution | ✅ Active |
| Telegram | Notifications | ✅ Active |
| Google Sheets | Data storage | ✅ Active |
| GitHub | Code & docs | ✅ Active |

---

## 🔐 Security Practices

| Practice | Implementation |
|----------|----------------|
| API Keys | Environment variables, never in code |
| Network | Local-only n8n access, VPN for remote |
| Backups | Daily workflow exports |
| Updates | Regular Docker image updates |
| Monitoring | Telegram alerts for failures |

---

## 📊 Resource Usage

Typical daily consumption on HP Z440:

| Resource | Usage |
|----------|-------|
| CPU | 15-30% average |
| RAM | 4-6 GB |
| Storage | ~500 MB/month (logs) |
| Network | ~2 GB/day |

---

## 🚀 Scaling Path

Current setup handles 3 markets comfortably. Future options:

| Stage | Infrastructure |
|-------|----------------|
| **Now** | Single HP Z440 |
| **Growth** | Add dedicated LLM server |
| **Scale** | Kubernetes cluster |
| **Enterprise** | Multi-region deployment |

---

## 🧪 Development Environment

For contributors:

### Prerequisites:
```bash
# Required
- Docker & Docker Compose
- Git
- Node.js 18+ (for n8n development)

# API Keys needed
- Anthropic (Claude)
- Google AI (Gemini)
- Telegram Bot Token
- Google Sheets credentials
```

### Local Setup:
```bash
# Clone the repo
git clone https://github.com/australianweb-agency/Centaur-Covenant.git
cd Centaur-Covenant

# Start n8n locally
docker run -it --rm \
  --name n8n \
  -p 5678:5678 \
  -v ~/.n8n:/home/node/.n8n \
  n8nio/n8n

# Import workflows from /workflows directory
```

---

## 📚 Further Reading

- [SYSTEMS.md](SYSTEMS.md) — What the systems do
- [CONTRIBUTING.md](CONTRIBUTING.md) — How to help
- [n8n Documentation](https://docs.n8n.io/)
- [Claude API Docs](https://docs.anthropic.com/)
- [Gemini API Docs](https://ai.google.dev/docs)

---

*This is the machine. The covenant gives it purpose.*

**Built with 🐴💚🔥 by The Triple Entity**

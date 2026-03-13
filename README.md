# AI Automation Portfolio
### Laszlo Sándor

AI automation systems, GTM infrastructure, and operational tooling — 14 projects built on Apollo, Zapier, OpenAI, Airtable, n8n, Make.com, Groq, and Netlify.

**Live demo:** [fundingintelligenceengine.netlify.app](https://fundingintelligenceengine.netlify.app)
**CSRD Compass:** [lazz24.github.io/ai-automation-portfolio/13-csrd-compass](https://lazz24.github.io/ai-automation-portfolio/13-csrd-compass/)

---

## How This Repo Is Structured

Each project folder contains a README documenting:
- What the system does
- Full architecture and pipeline
- Key design decisions
- Airtable / CRM schema where applicable
- Rebuild-from-prompt protocol
- Known constraints and iteration notes

Blueprint level only. Actual prompts, schemas, and code live in a private repository.

---

## Projects

| # | Project | Stack | Status |
|---|---------|-------|--------|
| [01](./01-funding-intelligence-engine/) | Funding Intelligence Engine | Groq · Airtable · Netlify · Vanilla JS | 🟢 Live |
| [02](./02-b2b-lead-qualification/) | B2B Lead Qualification Pipeline | Apollo · Zapier · OpenAI · Airtable | 🟢 Production |
| [03](./03-executive-intelligence-engine/) | Executive Intelligence Engine | Apollo · OpenAI · Zapier · Airtable · Slack | 🔵 Active |
| [04](./04-grant-monitor-bot/) | Grant Monitor Bot | Zapier · ClickUp · OpenAI | 🔵 Active |
| [05](./05-techport-radar-scoring/) | TechPort Radar & Signal Scoring Engine | Airtable · Zapier · Apollo | 🔵 Active |
| [06](./06-n8n-operational-automation/) | n8n Operational Automation Systems | n8n · JSON · POS data · Webhooks | 🔵 Active |
| [07](./07-linkedin-connection-scaling/) | LinkedIn Connection Scaling System | Apollo · LinkedIn · Zapier | 🔵 Active |
| [08](./08-hunter-harvest-gtm/) | Hunter vs Harvest GTM Structuring | Apollo · Airtable · Zapier | 🔵 Active |
| [09](./09-funding-dashboard-architecture/) | Funding Action Items Dashboard Architecture | ClickUp · Zapier · Airtable | 🟡 Design |
| [10](./10-streamlit-realestate-poc/) | Streamlit Real Estate Intelligence POC | Streamlit · Python · Local | 🟣 POC |
| [11](./11-portfolio-infrastructure/) | Portfolio Infrastructure System | GitHub · Markdown · JSON | 🔵 Active |
| [12](./12-brandgpt-positioning/) | BrandGPT / Personal Positioning System | AI Prompting · Brand Strategy · LinkedIn | 🔵 Active |
| [13](./13-csrd-compass/) | CSRD Compass — Sustainability Readiness Tool | Make.com · Groq · Airtable · Notion · Gmail · HTML/JS | 🟢 Live |
| [14](./14-ai-helpdesk-triage/) | AI-Powered Help Desk Triage | Zapier · OpenAI · ClickUp · Airtable · Slack | 🟢 Live |
| 15 | [Net Zero Roadmap Generator](./15-net-zero-roadmap/) | Groq · Cloudflare Workers · Supabase · jsPDF | [Live Demo](https://lazz24.github.io/ai-automation-portfolio/15-net-zero-roadmap/) |

---

## Stack

| Layer | Tools |
|-------|-------|
| AI / LLMs | OpenAI API · Groq (Llama 3.3 70B) · Anthropic Claude |
| Automation | Zapier · Make.com · n8n |
| Data / CRM | Airtable · Notion · ClickUp |
| Lead sourcing | Apollo.io · LinkedIn |
| Interfaces | Streamlit · Netlify · GitHub Pages · Vanilla JS |
| Communication | Slack · Gmail |
| Infrastructure | GitHub · JSON · Markdown |

---

## Design Principles

**One-button UX for client tools**
Decision makers get a single action. The pipeline complexity is invisible. Demo interfaces are always built separately from production backends.

**Rebuild-from-prompt standard**
Every project is documented so it can be fully reconstructed from its prompt set, architecture notes, and tool configuration — without access to the original build.

**Constraint-first design**
Systems are built around real limitations: free-tier APIs, no-code platform restrictions, budget and time pressure. Constraints produce cleaner architecture.

**Separate demo from ops**
Client-facing interfaces are always built separately from production backends. The operational system handles real data; the demo handles presentations.

**Security by default**
API keys stored as encrypted environment variables. This public repo contains only blueprint-level documentation. Actual prompts, schemas, and code live in a private repository.

---

## Status Key

| Badge | Meaning |
|-------|---------|
| 🟢 Live / Production | Deployed and running |
| 🔵 Active | Built and operational |
| 🟡 Design | Architecture complete, build pending |
| 🟣 POC | Proof of concept, pre-production |

---

*All systems documented to a rebuild-from-prompt standard — any project can be fully reconstructed from its architecture notes and prompt set.*

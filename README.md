# AI Automation & GTM Systems — Portfolio
> **Builder-focused. Prompt-driven. Rebuild-ready.**

This repository documents a working portfolio of AI automation systems, GTM infrastructure, and operational tooling built across Apollo, Zapier, n8n, Airtable, OpenAI, Groq, ClickUp, Streamlit, Netlify, and GitHub.

Every project reflects real architecture decisions, real constraints, and real workflows. Each folder contains enough context to understand, replicate, or extend the system from scratch using the rebuild-from-prompt protocol.

---

## Repository Structure

```
ai-automation-portfolio/
├── 01-funding-intelligence-engine/
├── 02-b2b-lead-qualification/
├── 03-executive-intelligence-engine/
├── 04-grant-monitor-bot/
├── 05-techport-radar-scoring/
├── 06-n8n-operational-automation/
├── 07-linkedin-connection-scaling/
├── 08-hunter-harvest-gtm/
├── 09-funding-dashboard-architecture/
├── 10-streamlit-realestate-poc/
├── 11-portfolio-infrastructure/
├── 12-brandgpt-positioning/
├── .gitignore
└── README.md
```

---

## Projects at a Glance

| # | Project | Stack | Status |
|---|---------|-------|--------|
| 01 | Funding Intelligence Engine | Groq · Airtable · Netlify · JS | Live |
| 02 | B2B Lead Qualification Pipeline | Apollo · Zapier · OpenAI · Airtable | Production |
| 03 | Apollo → AI → Executive Intelligence Engine | Apollo · OpenAI · Zapier · Slack | Active |
| 04 | Grant Monitor Bot | Zapier · ClickUp · OpenAI | Active |
| 05 | TechPort Radar & Signal Scoring Engine | Airtable · Zapier · Apollo | Active |
| 06 | n8n Operational Automation Systems | n8n · JSON · Webhooks | Active |
| 07 | LinkedIn Connection Scaling System | Apollo · LinkedIn · Zapier | Active |
| 08 | Hunter vs Harvest GTM Structuring | Apollo · Airtable · Zapier | Active |
| 09 | Funding Action Items Dashboard | ClickUp · Zapier · Airtable | Design |
| 10 | Streamlit Real Estate Intelligence POC | Streamlit · Python | POC |
| 11 | Portfolio Infrastructure System | GitHub · Markdown · JSON | Active |
| 12 | BrandGPT / Personal Positioning System | AI Prompting · Brand Strategy | Active |

---

## Design Principles

- **Rebuild-from-prompt** — every project is documented so it can be fully reconstructed from its prompt set, architecture notes, and tool config
- **Constraint-first design** — systems are built around real limitations: budget, time, data access, platform restrictions
- **No fluff** — documentation describes what the system does and how it was built
- **Separate demo from ops** — client-facing interfaces are built separately from production backends
- **Security-aware** — API keys, credentials, and sensitive identifiers are excluded from all committed files

---

## Tech Stack Reference

| Layer | Tools |
|-------|-------|
| AI / LLMs | OpenAI API · Groq (Llama 3.3 70B) · Anthropic Claude |
| Automation | Zapier · n8n · Make |
| Data / CRM | Airtable · ClickUp · Notion |
| Lead sourcing | Apollo.io · LinkedIn |
| Interfaces | Streamlit · Netlify · Vanilla JS |
| Communication | Slack · Gmail |
| Infrastructure | GitHub · JSON · Markdown |

---

## Folder Contents Standard

Each project folder contains:

```
README.md       → system overview, architecture, components, rebuild prompts
prompts/        → AI prompt files used in the system
schemas/        → Airtable configs, JSON structures, field maps
workflows/      → Zapier/n8n exports or workflow descriptions
notes/          → design decisions, constraints, iteration logs
```

Only folders that have content are included per project.

---

*This portfolio is maintained as a living document. Systems are updated as they evolve in production.*
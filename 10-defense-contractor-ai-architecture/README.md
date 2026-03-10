# 10 — Defense Contractor AI Architecture Model

> Closed AI system design for a defense context. RAG vs private LLM comparison and daily-use enablement model.

**Status:** `Design`
**Stack:** RAG architecture · Private LLM · AI workflow tooling
**Tags:** `#architecture-design` `#ai-prompt-engineering`

---

## What It Does

An architecture model for deploying AI in a defense contractor environment where data cannot leave a closed system. Covers the comparison between RAG (Retrieval-Augmented Generation) and private LLM deployment, a model for enabling day-to-day AI use across teams, and integration with existing workflow tools — with operational focus throughout.

---

## System Components

| Component | Description |
|-----------|-------------|
| RAG vs Private LLM | Comparison of architectures for closed-system AI |
| Closed system design | Architecture for air-gapped or restricted deployment |
| Daily-use enablement | Model for embedding AI into existing team workflows |
| Workflow integration | Mapping AI tools to operational tasks |

---

## Key Design Decisions

- Operational focus throughout — architecture decisions evaluated on usability, not capability benchmarks
- RAG chosen as preferred path for most use cases — lower infrastructure burden than full private LLM
- Daily-use enablement model designed for non-technical operators

---

## Rebuild-From-Prompt Protocol

**Files in this folder:**
- `notes/` — RAG vs private LLM comparison, closed AI system architecture, daily-use enablement model
- `schemas/` — workflow tool integration map

---

## Known Constraints

- Design phase only — implementation depends on client infrastructure
- Specifics of closed system requirements vary by contractor and clearance level

---

## Iteration Notes

- `2025-01` — Architecture design completed

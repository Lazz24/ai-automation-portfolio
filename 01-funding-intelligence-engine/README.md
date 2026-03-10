# 01 — Funding Intelligence Engine

> One-button grant analysis tool. Paste a grant description, get a structured fit assessment and effort estimate. Live on Netlify.

**Status:** `Live` — [fundingintelligenceengine.netlify.app](https://fundingintelligenceengine.netlify.app)
**Stack:** Groq · Airtable · Netlify · Vanilla JS
**Tags:** `#automation` `#ai-prompt-engineering` `#airtable` `#netlify`

---

## What It Does

A single-action web interface for grant analysis. The user pastes a grant description and clicks Analyse. A Netlify serverless function calls the Groq API (Llama 3.3 70B), returns a structured breakdown of fit, required actions, and effort estimate, and writes the result to Airtable for tracking.

Built for decision-making speed — the goal is a usable output in under 30 seconds, not a deep research report.

---

## System Components

| Component | Description |
|-----------|-------------|
| Frontend | Dark-themed single-page HTML/CSS/JS interface |
| Serverless function | Netlify function acting as API proxy |
| LLM | Groq free-tier (Llama 3.3 70B) |
| Database | Airtable — auto-populated on each analysis |

---

## Architecture

```
User pastes grant description → clicks Analyse
→ Netlify serverless function receives request
→ Function calls Groq API with structured prompt
→ Response returned to frontend and displayed
→ Result written to Airtable base (appmuzgkbZqGleLsv)
```

---

## Key Design Decisions

- Switched LLM provider from Anthropic → Gemini → Groq to stay on free tier throughout build
- Serverless proxy required — direct browser calls to Groq fail due to CORS and expose the API key
- Airtable field names in the base match the function code exactly — do not rename fields without updating the function
- One-button UX was non-negotiable — clients and operators need zero learning curve

---

## Rebuild-From-Prompt Protocol

**Accounts required:**
- [ ] Netlify (free tier)
- [ ] Groq (free tier) — groq.com
- [ ] Airtable (free tier) — base ID: `appmuzgkbZqGleLsv`

**Steps:**
1. Build single HTML file with form input and results display area
2. Create `functions/analyze.js` at repo root (not nested under `netlify/`)
3. Add `netlify.toml` with `functions = "functions"` explicitly set
4. Add `GROQ_API_KEY`, `AIRTABLE_API_KEY`, and `AIRTABLE_BASE_ID` to Netlify environment variables
5. Deploy via Netlify drag-and-drop
6. Test with a real grant description

**Files in this folder:**
- `prompts/` — grant analysis system prompt
- `schemas/` — Airtable field map
- `notes/` — LLM provider switch log, deployment issues

---

## Known Constraints

- Groq free tier has rate limits — not suitable for high-volume usage
- Airtable write will fail silently if field names do not match exactly
- No authentication on the frontend — anyone with the URL can use it
- API credits refresh on a monthly cycle

---

## Iteration Notes

- `2025-03` — Switched from Gemini (`gemini-2.0-flash` quota error) to Groq `llama-3.3-70b-versatile`
- `2025-02` — Switched from Anthropic to Gemini due to API credit requirements
- `2025-02` — Initial build and Netlify deployment

# 15 — Net Zero Roadmap Generator

## Overview
AI-powered tool that generates a structured Net Zero roadmap from a 4-field company profile. Delivers an executive summary, milestone timeline, quick wins, risks, and a downloadable branded PDF.

## Stack
- **Frontend:** HTML + JS → GitHub Pages
- **API Proxy:** Cloudflare Workers (key vault, CORS, routing)
- **AI:** Groq API (llama-3.3-70b-versatile) — free tier
- **Database:** Supabase (Postgres) — free tier
- **PDF:** jsPDF (client-side, no dependency)

## Live URL
https://lazz24.github.io/ai-automation-portfolio/15-net-zero-roadmap/

## User Flow
1. User fills 4 fields: sector, company size, baseline emissions, target year
2. POST sent to Cloudflare Worker
3. Worker calls Groq with structured prompt
4. Groq returns JSON roadmap
5. Worker writes record to Supabase
6. Frontend renders roadmap + PDF download

## Key Learnings
- Cloudflare Workers reset headers/body on navigation — use PowerShell or Postman for testing
- Supabase enables RLS by default — must disable or add policy for anon writes
- jsPDF renders client-side, no server needed
- Cloudflare HTTP tester sends GET by default, not POST

# Magic Hat Radar — Prophyl
### Client Execution Intelligence System

Built by László Sándor for Magic Hat Consulting  
Client engagement: Prophyl  
Status: Live

---

## What This Is

Magic Hat Radar is a client execution intelligence system that sits above a client's existing project management workflow and turns raw operational data into consultant-ready intelligence. It reads, never writes. It synthesises, never decides.

Built for Béla Sándor of Magic Hat Consulting to manage the Prophyl engagement — a multi-division client with complex cross-functional projects, stalling decisions, and leadership engagement risks that were invisible without a dedicated intelligence layer.

---

## The Problem It Solves

Consultants managing complex engagements face four recurring problems:

- **Too much raw data, not enough signal** — project management tools contain everything but surface nothing
- **Patterns are invisible until too late** — repeated date slippage, accumulating overdue tasks, and stalling decisions only become visible in retrospect
- **Leadership engagement is unmeasured** — when a senior stakeholder goes quiet, there is no alert
- **Meeting prep is manual** — synthesising what changed, what's at risk, and what needs a decision before every client meeting takes time a consultant doesn't have

Magic Hat Radar solves all four automatically.

---

## Stack

| Layer | Tool |
|---|---|
| Data store | Airtable |
| Automation | Zapier |
| AI / LLM | Groq (llama-3.3-70b-versatile) |
| Source of truth | ClickUp (client's existing tool) |
| Delivery | Gmail + Slack |

---

## Architecture

### Airtable Base: Magic Hat Radar
**Base ID:** 

7 tables:
- **Projects** — synced from ClickUp, includes Health Flag, Engagement Risk formula, Date Change Count, Last Activity Date
- **Tasks** — synced from ClickUp, includes Overdue flag (Yes/No), Due Date, Parent Project link
- **Stakeholders** — manually maintained, linked to Projects
- **Weekly Snapshots** — auto-created every Monday by Auto 1, one record per project per week
- **Assumptions** — strategic layer, manually maintained
- **Decision Points** — strategic layer, includes Delayed Flag formula, Due Date, Status
- **Dependencies** — strategic layer, manually maintained

**Formula fields of note:**
- `Engagement Risk` (Projects) — formula detecting Silent, Drifting, and Stalled patterns
- `Delayed Flag` (Decision Points) — formula returning "Overdue" when decision due date has passed

---

### Zapier Automations — 8 Live

| Auto | Name | Trigger | Function |
|---|---|---|---|
| 1 | Weekly Snapshot Creator | Monday 7am | Creates one snapshot record per project |
| 2 | Overdue Count Updater | Monday 7:15am | Counts overdue tasks per project |
| 3 | ClickUp Project Sync | ClickUp project update | Syncs project changes to Airtable |
| 4 | ClickUp Task Sync | ClickUp task update | Syncs task changes + Last Activity Date |
| 5 | Weekly Digest | Friday 3:30pm | Structured data summary to Slack + email |
| 6 | Pre-Meeting Brief (paused) | Monday 8am | Raw data brief — superseded by Auto 7 |
| 7 | AI Meeting Prep Brief | Monday 8:30am | Groq-generated brief to Slack + email |
| 8 | Weekly AI Change Summary | Friday 4pm | Groq-generated summary to Slack + email |

**Auto 7 and Auto 8 use Code by Zapier (JavaScript) to call the Groq API directly. This is the correct pattern — Zapier Webhooks cannot reliably handle nested JSON with embedded data pills.**

---

### Airtable Interface Pages — 2 Published

- **Execution Radar** — operational view, projects by division, health status, overdue counts
- **Strategic Radar** — strategic layer, assumptions, decision points, dependencies

---

### Analytical Views — 6 Built in Phase 3

| View | Table | Purpose |
|---|---|---|
| Division Slip Tracker | Projects | Which divisions have the most at-risk projects |
| Date Drift Log | Weekly Snapshots | Which projects repeatedly move their due dates |
| Overdue Accumulation Map | Tasks | Which projects carry the most overdue tasks |
| Decision Stall Radar | Decision Points | Which decisions are overdue and unresolved |
| Leadership Engagement Radar | Projects | Which projects have gone silent or are drifting |
| (existing) Critical & Warning | Projects | All non-healthy projects |

---

## AI Brief Structure

Both Auto 7 and Auto 8 use Groq (llama-3.3-70b-versatile) with the following prompt structure:

**Monday Brief (Auto 7):**
- 🧭 Situation Summary
- 🔴 Immediate Attention Required
- ⚠️ Watch List
- 📋 Decisions Stalled
- 👁️ Where Judgment Is Needed This Week

**Friday Summary (Auto 8):**
- 📊 Week in Review
- 🔺 Things That Got Worse
- ✅ Things That Improved
- 🔁 Patterns Emerging
- 👁️ Where Béla's Judgment Is Needed Next Week

Data inputs for both: Projects, Tasks, Decision Points + Assumptions (Auto 7) or Weekly Snapshots (Auto 8).

---

## Engagement Risk Formula
IF(
AND(
DATETIME_DIFF(TODAY(), {Last Activity Date}, 'days') > 14,
{Health Flag} != "🟢 Healthy"
),
"⚠️ Silent",
IF(
{Date Change Count} >= 3,
"🔄 Drifting",
IF(
AND(
{Health Flag} = "🔴 Critical",
{Overdue Task Count} >= 3
),
"🚨 Stalled",
""
)
)
)
---

## Key Technical Decisions

**Why Code by Zapier instead of Webhooks for Groq calls:**
Zapier's Webhooks by Zapier step cannot reliably send nested JSON when data pills are embedded in the Raw payload field. Code by Zapier (JavaScript) accepts named input variables, builds the payload in code, and makes the HTTP POST directly. This is the reliable pattern for any LLM API call in Zapier.

**Why Groq instead of OpenAI:**
Free tier available with no regional restrictions. Model llama-3.3-70b-versatile produces high-quality synthesis output suitable for executive briefing.

**Why Airtable instead of a custom database:**
Interface publishing, formula fields, and view configuration provide a no-code intelligence layer that a consultant can maintain and extend without developer involvement. Supabase or a custom backend would require ongoing technical maintenance.

**Why ClickUp is source of truth and not Airtable:**
The client already uses ClickUp. Asking them to change their workflow to serve the consultant's intelligence needs would create friction and reduce adoption. The system adapts to them, not the other way around.

---

## Build Log

Full phase-by-phase build log maintained in ClickUp:
- Folder: Magic Hat Radar — Prophyl
- Space: Magic Hat Radar
- Lists: Phase 1 Build Log, Phase 2 Next Steps, Phase 3 Intelligence Layer

---

## Replication

To replicate this system for a different client engagement:

1. Create a new Airtable base using the same 7-table schema
2. Replace all Airtable base IDs and table IDs in the Zapier automations
3. Point the ClickUp sync automations at the new client's ClickUp workspace and folder
4. Update the Groq prompt in Auto 7 and Auto 8 to reference the new client name and consultant name
5. Update the Gmail recipient and Slack channel in all output steps
6. Seed the base with the client's live project and task data
7. Publish the two interface pages and share links with the consultant

Estimated replication time: 3–4 hours for an experienced operator.

---

## Contact

Built by László Sándor  
GitHub: Lazz24

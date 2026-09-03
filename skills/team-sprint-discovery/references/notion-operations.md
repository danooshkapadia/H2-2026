# Notion Operations Guide

All database URLs, page IDs, and structural references for the discovery skill.

---

## Canonical Databases

### Meetings Database (transcripts live here)
**URL:** https://www.notion.so/danoosh/d0921b86c2478342b8eb81fbbab6f743?v=b6721b86c24783c2a592089cc607359b
**Use:** Search for Fathom transcripts of discovery interviews. This is the primary source for progressive discovery. Search by client name + interviewee name.

### Contacts Database
**URL:** https://www.notion.so/danoosh/61421b86c247824aac1d81414a568789?v=8a321b86c24783aea8dc088a6a293508
**Use:** Log contact information for everyone encountered during discovery: sponsors, team leads, interviewees. Fields: name, role, email, phone. Source this from Gmail email signatures.

### Client Projects Database (All External Projects)
**URL:** https://www.notion.so/danoosh/3c921b86c247831197f901cd9ce42712?v=20921b86c2478306b09c080a56f0b988
**Use:** Find the client's project page. Discovery pages are created as children under the Discovery milestone within the project.

---

## Where Discovery Artifacts Go

All discovery prep docs, strategy docs, debrief notes, and the Readiness Brief are created as **child pages under the client's Discovery milestone page** in Notion.

**Pattern:** Client Project → Milestones → Discovery → [child pages]

**Example (Rockline):** https://www.notion.so/danoosh/Discovery-35321b86c2478119b51dd77520ce2055
This is the structural reference. Discovery pages should follow this layout: Overview (design challenge, research design), Survey Analysis, Discovery Interviews (plan + notes), Key Communications.

**Example (Amada):** https://www.notion.so/danoosh/Amada-Discovery-35d21b86c24780558756c69b4796d5c9
This was the first Sprint discovery. Interview prep docs and the setup call doc are child pages here.

---

## Page Creation Patterns

### Discovery Strategy Page
Create as content on the main Discovery page (not a child page). Includes: design challenge, research design, interview plan table, what-feeds-what mapping, pre-sprint checklist, open items, key communications log.

### Interview Prep Docs
Create as **child pages** under the Discovery page. Naming: "🎯 Interview Prep — [Name] ([Date])"

### Post-Interview Debrief Notes
Update the Discovery page content directly (under Interview Notes section) OR create child pages. Naming: "🎙️ Discovery Debrief — [Name] ([Date])"

### Setup Call Docs
Create as **child pages** under the Discovery page. Naming: "⚙️ [Topic] — [Date]"

### Combined Readiness Brief
Create as a **child page** under the Discovery page. Naming: "📊 Team AI Readiness Brief — [Client]"

---

## How to Find Things

**Finding a client's Discovery page:** Search Notion for "[Client name] Discovery" or navigate: Client Projects database → find the project → look at 📦 Deliverables relation → find the Discovery milestone.

**Finding an interview transcript:** Search the Meetings database for the interviewee's name + "discovery" or the client name. Fathom syncs transcripts here automatically.

**Finding prior interview prep docs:** Navigate to the client's Discovery page and look at child pages.

**Finding the SOW:** Search Gmail for "[Client name] SOW" or "Statement of Work" or check Google Drive.

---

## Transcripts & Project Tracking (canonical rules)

**Transcripts:** Fathom via the connector is CANONICAL — always pull the FULL transcript (`search_meetings` → `get_meeting_transcript`), never just the synthesized notes. Fallback: Notion "All Meeting Notes [CC]" (https://app.notion.com/p/d0921b86c2478342b8eb81fbbab6f743) — use the Meeting Transcript file, not only the Meeting Summary.

**Project tracking:** canonical in Mission Control → "All External Projects [CC]". One project per Sprint (Project Type: AI Team Sprint). Status "Won" auto-builds the Milestones Calendar — VERIFY milestones populated exactly once (known duplication bug), set Project Timeframe, adjust milestone dates to the locked session schedule. Tick milestones as phases complete so the Health formula stays honest.


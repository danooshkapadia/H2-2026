# Notion map — canonical locations for Iris

The single reference for where everything lives in Danoosh's Notion. When a location here conflicts with something found by search, this file wins; if the workspace has genuinely changed, update this file and note it in Iris Memory. (Updated Jul 7, 2026: added the H2 Space section and reference-library pages; corrected the Brad note.)

## The root

- **Mission Control** (workspace homepage): https://app.notion.com/p/dc921b86c24783b39f8a01a5544af0cf
  Four hubs: Dashboards (Sales, Delivery, Marketing) · Operations (Client Projects, Clients Tasks, Milestones) · Connect (Meetings, Contacts, Companies) · Internal (Internal Projects, Internal Tasks, Notes)
- **Spaces** (project/initiative working hubs, parallel to Mission Control): https://app.notion.com/p/d6b21b86c247839e95d881de7af7b962

## Iris's own pages

- **Iris Memory** (read at every session start; hard cap ~1,500 words; lives inside the AI Hub): https://app.notion.com/p/37d21b86c24781b58d25fd252cce4c72

## The H2 2026 Space (the working hub for Jul–Dec 2026)

- **Front door** (mandate, scoreboard, five commitments, fraying dashboard): https://app.notion.com/p/39621b86c24781bc89afe03ad9623ea5
- Six month-mission pages live inside it (open the current one, ignore the rest), plus:
  - **The H2 Plan v2.1** (approved plan + flagged assumptions): https://app.notion.com/p/39621b86c24781dbabf1f688ef2ab716
  - **Retainer Playbook** (tiers, pitch script, natural moments): https://app.notion.com/p/39621b86c24781108735c4580f913f27
  - **Rooms & Venues** (teaching-channel plan + SF rooms): https://app.notion.com/p/39621b86c247816a9e69f6fc364bc1cf
  - **ADHD × Iris** (RSD protocol, EA behaviors, INCUP, strengths research): https://app.notion.com/p/39621b86c2478130858ff946f3d0c67c
  - **Premortem** (nine failure modes + tripwire dates): https://app.notion.com/p/39621b86c2478181b053efe32da8e49d
  - **Iris Reference Library** (annotated business/personal/taste files): https://app.notion.com/p/39621b86c24781959c15eaecb1e9cfd4
- Iris updates the Space scoreboard + current month page at every Friday wrap.

## AI Hub — the agents' home and the central log space

- **AI Hub** (point ALL agents here): https://app.notion.com/p/5be21b86c24783d1a41b015d77a90d38
  Contains AI Prompts, Custom Instructions, AI Actors, Workflows, the Master AI Hub Training Guide, and Iris's log containers.
- **Every log Iris writes goes in the AI Hub**, organized per type:
  - **Daily Briefs** — one page per day, titled "Daily Brief — YYYY-MM-DD": https://app.notion.com/p/37d21b86c247811083dfd08ade6c428e
  - **Evening Logs** — one page per day, titled "Evening Log — YYYY-MM-DD": https://app.notion.com/p/37d21b86c24781b2b1dad2aacee12116
  - **Friday Wraps** — one page per week, titled "Friday Wrap — Week of YYYY-MM-DD": https://app.notion.com/p/37d21b86c247818a9cb2f09985d66590
  - **Decisions Log** — single page, dated entries newest first: https://app.notion.com/p/37d21b86c24781df93c9de9e43ea8a04
  - **Resistance Log** — single page, dated entries (deferred items + what surfaced): sibling to the Decisions Log
- Older Evening Logs may exist in the Private section from the pre-Iris Cowork cleanup; the AI Hub containers are canonical going forward.

## Sales pipeline (the money)

- **Sales dashboard** (human view, monthly math — THE fast path for "how are sales looking"): https://app.notion.com/p/34521b86c247808bb07bc2d48089bc62
- **Sales board view** (answer sales questions from here, near-instant): https://app.notion.com/p/34921b86c24780cca317c18e9908b1bf
- **All External Projects [CC]** (the ledger — query for deal stages, project status, gates):
  - Database page: https://app.notion.com/p/3c921b86c247831197f901cd9ce42712
  - Data source for queries: `collection://d6a21b86-c247-82fb-80f2-87aa5f2fcf62`
  - ⚠️ NEVER bulk-query the full ledger view (token overflow). Tight SQL with column SELECTs, spaced calls; fall back to fetch/search on 429s.
  - Key properties: Status (Qualification → Proposal → Negotiation → Won → In Progress → Wrapping Up → Delivered/Lost), Deal stage, Engagement Status, Health (auto formula), Milestone Progress (rollup), Total/Weighted Value, Won Date, Next Follow up, Project Type
  - Status "In Progress" + Deal stage "Won" is the CORRECT state for a won engagement in delivery — not drift.
  - Post-signature gates Iris tracks: SOW signed → deposit collected → kickoff/alignment scheduled → discovery intros made → sessions delivering → wrap → proof captured

## Delivery and operations

- **Client Projects hub**: https://app.notion.com/p/1f221b86c2478392b4ff01b5844b5296
- **Clients Tasks hub**: https://app.notion.com/p/21321b86c24782bcacc581376faea603
- **Milestones hub**: https://app.notion.com/p/ba721b86c247837e992401f492a0b4e0 (milestones data source: `collection://21a21b86-c247-837a-8e22-07a64163f3a2`)
- **Delivery dashboard**: https://app.notion.com/p/34521b86c2478006a0acda1e4a3d0e33

## Meetings and relationships

- **Meetings hub**: https://app.notion.com/p/18821b86c24783ddb31c014775a0716a
- **All Meeting Notes [CC]** data source: `collection://34721b86-c247-830c-9e23-078a538bc45a`
  - Has a **Content Angle** property — the content scout fills it per call
  - Native Notion AI "Meeting" notes are READ-ONLY via API — write Content Angles on the [CC] rows, or capture in the Evening Log
- **Contacts hub**: https://app.notion.com/p/64d21b86c24783988ec3815bd883e27d
- **Companies hub**: https://app.notion.com/p/37021b86c24783088a26816c6cb7d455

## Internal (the Build lane)

- **Internal Projects hub**: https://app.notion.com/p/05821b86c2478367b024013d040d36f7
- **Internal Tasks hub**: https://app.notion.com/p/aed21b86c24782018f29812c80591807 (data source: `collection://ced21b86-c247-82f9-82d4-073be67b2ace`)
  - **Lou's fix queue**: Internal Tasks titled "Notion Fix: [issue]" assigned to Lou; the Friday wrap emails her the open list (louisianna@danooshkapadia.com)
- **Notes hub**: https://app.notion.com/p/2b821b86c24783d18312817694cb2f8d

## Marketing (the Tell lane)

- **Marketing dashboard**: https://app.notion.com/p/34e21b86c24783de8c4e81dae6be8fda
- **All Content [DKC]** data source: `collection://e0b21b86-c247-8266-9c2f-07d6ee122983` — scouted angles deposit here (Status "Triaged", Type Idea, Ring R2 for human-side stories)
- **Content pipeline workflow**: setting an item's status to **Triage** fires the AI enrichment automation (summary, usefulness score, tags); Lou reviews weekly and moves In Review → Move to Vault / archive

## The book

- **Book HQ / Raw Material**: https://app.notion.com/p/32921b86c24781ebbed6f2467446046d
  - Deposit format: a "Source:" section (date, format, verbatim "Lines That Land", themes, gaps filled) + a row in the Source Catalog table
  - Bar: human-transformation grade only — identity, judgment, self-recognition. Business-process anecdotes don't clear it.

## Conventions that keep agents sane

- "[CC]" in a database name = Command Center canonical data source
- The **Archive** checkbox keeps agents out of legacy data — respect it in queries, and flag unarchived legacy items as Notion Fixes
- Projects set to "Won" auto-populate milestones from templates (the "Milestones Calendar" template)
- Snapshot/one-time pages (e.g., old "Revenue Cockpit" style pushes) are NOT sources of truth — the ledger is
- New-project automation can spawn duplicate ledger entries (blank scaffold + narrative entry): update the canonical narrative entry, flag dups to Lou

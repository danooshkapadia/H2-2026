---
name: team-sprint-discovery
description: |
  Team Sprint Discovery workflow for Danoosh Kapadia. Trigger when Danoosh says "run discovery for [client]," "prep the discovery," "build the interview prep," "do the debrief," "write the readiness brief," "synthesize the interviews," or references any AI Team Sprint engagement in Pre-Sprint. Also trigger for a Sprint client + interviews, prep docs, or discovery findings. Also trigger for the assessment system: "send the pre-Sprint survey," "code the survey responses," "build the assessment baseline," "mid-Sprint pulse," "post-Sprint survey," or "build the sponsor ROI report." Covers: project planning, discovery strategy, progressive interview prep, post-interview debriefs, the locked v1.0 assessment (deployment, rubric coding, baseline), synthesis, the combined Readiness Brief + Assessment Baseline, and the Sponsor ROI Report. Assumes sponsor kickoff is done. Does NOT cover session content design, post-session follow-ups, or sales/proposals (use team-sprint-sales).
---

# Team Sprint Discovery

You are Danoosh's discovery partner. Turn a signed SOW into a program tuned to the client's real work through repeatable, progressive discovery.

**Operating principles:**
- Danoosh has ADHD. One next action. Scannable over comprehensive.
- All artifacts go in Notion. Read `references/notion-operations.md` for database URLs.
- **Transcripts: Fathom via the connector is CANONICAL.** Always pull the FULL transcript (`search_meetings` → `get_meeting_transcript`), never settle for the synthesized summary — the gold (verbatim quotes, workflow detail, emotional texture) lives in the full text. Fallback only if Fathom is unavailable: the Notion note-taker, "All Meeting Notes [CC]" (https://app.notion.com/p/d0921b86c2478342b8eb81fbbab6f743) — use its Meeting Transcript file, not just the Meeting Summary.
- **Project tracking is canonical in Mission Control → "All External Projects [CC]".** Each Sprint = one project (Project Type: AI Team Sprint). Setting Status to "Won" triggers the automation that builds the Milestones Calendar with sequential dates. ALWAYS verify after Won: milestones populated exactly ONCE (a known template-disconnect bug once duplicated them), Project Timeframe set, dates adjusted to the real session schedule (travel gaps move milestones). Health formula and Milestone Progress only work if dates are real. As each phase completes, tick its milestone — that's what keeps Health honest.
- Progressive discovery: never prep interview N+1 without reading transcript N.
- When in doubt, stop and ask Danoosh.
- After every interview, debrief collaboratively. The transcript doesn't capture everything.
- Mine every conversation for: exercise material, terminology, demos, and sponsor radar items.
- For polished deliverables: `references/brand-guidelines.md` (canonical: https://danooshkapadia.github.io/dk-consulting-brand-guidelines/). **Minimum font size 12pt on all screen deliverables.** Logo: `references/logo.svg`.

---

## Context: The AI Team Sprint

Six-week program, up to 15 people. 2-hour kickoff + 5 weekly sessions (75 min, 7-10 day cadence).

| Tier | Price | Discovery | Setup | Sponsor Rhythm | Assessment |
|------|-------|-----------|-------|----------------|------------|
| Program Only | $10K | No | Self-serve | None | None |
| Recommended | $12.5K | Yes | Guided | Kickoff call | No |
| Full Executive | $15K | Yes | Guided | Full (3 touchpoints) | Pre/mid/post |

**Sessions:** (1) Kickoff & Mindsets 2h, (2) Getting Great Outputs 75m, (3) AI as Thinking Partner 75m, (4) Communicating with Impact 75m, (5) Redesigning How Work Gets Done 75m. Sessions 1-3 mostly reusable. 4-5 tuned from discovery.

---

## The Discovery Arc

| Phase | What | When | Budget |
|-------|------|------|--------|
| 0 | Project Planning | Day 1 | 1 hr |
| 1 | Discovery Strategy | Days 1-3 | 1 hr |
| 2 | Interviews (progressive prep → call → debrief) | Days 3-14 | ~2 hrs/interview |
| 3 | Survey + Assessment Baseline | Days 10-18 | 2-3 hrs (deploy, chase, code, baseline) |
| 4 | Synthesis → Combined Readiness Brief | Days 14-21 | 2-3 hrs |
| 5 | Sponsor Content Review | Days 18-24 | 60 min |

End of discovery = Combined Readiness Brief emailed to sponsor → content review call → Session 01.

---

## Phase 0 — Project Planning

**Trigger:** "Set up discovery for [client]"

**Step 1 — Engagement context.** Pull SOW. Confirm: client, sponsor, team lead, tier, cohort size, target Session 01 date, custom elements.

**Step 2 — LLM checkpoint.** Confirm which AI tool the client is building on: ChatGPT Team/Business, Claude, or Microsoft Copilot. This determines: guided setup scope, demo screenshots, value exchange tips, and exercise design. Add to the checklist.

**Step 3 — Pre-Sprint checklist:**

```
## Pre-Sprint Checklist — [Client]

### Foundations
- [ ] Project verified in Mission Control → All External Projects: Type = AI Team Sprint, Status = Won, milestones populated exactly ONCE, Project Timeframe set, milestone dates match the real session schedule
- [ ] LLM confirmed: [ChatGPT / Claude / Copilot]
- [ ] Participant roster with emails received
- [ ] Team lead identified and briefed

### Discovery Setup (Week 1)
- [ ] Interviewee archetypes requested from sponsor
- [ ] Sponsor selected 3 names
- [ ] Interview intros sent, interviews scheduled (30 min, booked for 45)
- [ ] Brand/onboarding materials requested for context file
- [ ] Tech setup call scheduled (if applicable)

### Discovery Execution (Week 2)
- [ ] Interview 1 + debrief + Notion updated
- [ ] Interview 2 + debrief + Notion updated
- [ ] Interview 3 + debrief + Notion updated
- [ ] Gap assessment: is a 4th interview needed?
- [ ] Interview 4 + debrief (if needed)
- [ ] Comparison framework complete
- [ ] Stretch axis re-evaluated
- [ ] "Design for" person identified
- [ ] Tech/guided setup completed (if applicable)
- [ ] Survey + assessment baseline sent (team lead sends)

### Synthesis + Handoff (Week 3)
- [ ] Survey analyzed
- [ ] Combined Readiness Brief drafted (includes sponsor radar items)
- [ ] Brief emailed to sponsor
- [ ] Content review call completed
- [ ] Session 01 locked, all 5 sessions confirmed
- [ ] Context file built and loaded (if applicable)
```

**Step 4 — Create Discovery page in Notion.** Under client's Discovery milestone. Sections: Overview, Strategy, Interviews, Communications.

**Step 5 — Log contacts.** Gmail search for every person. Log in Contacts database.

---

## Phase 1 — Discovery Strategy

**Trigger:** "Design the discovery for [client]"

**Step 1 — Design challenge.** "How do we move [N] [Client] members from [state] to fluent, confident team-level AI users in their [industry/function] workflows?"

**Step 2 — Research design.**
- **Lens:** AI adoption in their context
- **Stretch:** Extremes of the spectrum. NOTE: This is a hypothesis. Re-evaluate after each interview. Rockline started skeptic↔power user, ended awareness↔unawareness. The real axis often only emerges through the interviews.
- **Three priorities (ranked):** (1) Real workflows → exercises. (2) Emotional landscape → S01 framing. (3) Language/context → slides and context file.

**Step 3 — Request archetypes.** Danoosh to sponsor: "I'd like 3 people spanning the spectrum — someone skeptical or new, someone willing but not deep, someone whose work would benefit most." Sponsor picks. Danoosh can swap if spread is wrong.

**Step 4 — Sequence interviews.** Default: willing middle → high-potential → skeptic/senior. This builds workflow context before harder conversations. After interview 2, check with Danoosh: "Does this sequence still make sense, or should we adjust who we talk to next based on what we've learned?"

**Step 5 — Push to Notion.**

---

## Phase 2 — Interviews (Prep → Call → Debrief)

Each interview is a three-part unit: prep, the call, and the debrief. They are not separate phases. The debrief for interview N feeds directly into the prep for interview N+1.

### 2A. Interview Prep

**Trigger:** "Prep the interview for [name]"

#### Progressive Discovery Protocol (MANDATORY for interview 2+)

1. Pull prior transcript(s) — Fathom connector first (`search_meetings` → `get_meeting_transcript`, FULL transcript), Notion meetings DB as fallback
2. Read full transcript (never just the summary/notes)
3. Extract: workflows, terminology, pain points, AI experience, team dynamics, anything about this interviewee or others
4. Incorporate under "Intel from Prior Interviews"
5. Re-evaluate: has the stretch axis shifted? Is the archetype label still right?

If transcript not found → STOP and ask Danoosh.

#### Gathering Context (always, in order)

a) **Search Gmail.** Email signatures, context from sponsor/team lead.
b) **Search LinkedIn.** Role, tenure, experience, education. Estimate age from graduation.
c) **Can't find or confirm LinkedIn → STOP and ask Danoosh.**
d) **Log contact info** in Contacts database.

#### Prep Doc Structure (Notion child page)

```
## Interview Prep — [Name] ([Date, Time])
Duration: 30 min (booked for 45)
Archetype (hypothesis): [X — refine after call]

### Profile Card
[Table: role, tenure, what they do, experience, age estimate,
key detail, likely tools, AI experience]

### [If 2+] Intel from Prior Interviews
[What we learned. Direct quotes. Cross-refs.]

### How [Name] Differs
[New dimension, gap, contrast]

### What We Need from This Call
P1: [feeds session design]  P2: [secondary]  P3: [tertiary]

### Tech Stack to Probe
[Tools/systems. Early Q: "What tools are you in most of the day?"]

### Mindset Reminders
[5-6 bullets. Assumption corrections if needed.
When interviewees mention colleagues, capture names, roles, and
teams — builds the org map for exercise design and future business.]

### The Conversation (30 min)
```

**Time allocation by archetype:**

| Act | Skeptic / Guarded | Willing Middle | Power User |
|-----|-------------------|----------------|------------|
| 1. Warm-Up | 5 min (more rapport) | 3 min | 3 min |
| 2. Workflow Mapping | 12-14 min (gold) | 10-12 min | 8 min |
| 3. AI Experience | 8 min (go gently) | 10 min | 14 min (gold) |
| 4. Wrap + Wishes | 5 min | 5 min | 5 min |

```
Act 1: Warm-Up (archetype-adjusted)
[If 2+, bridge: "I spoke with [Name] about [topic]..."]

Act 2: Workflow Mapping
Default opener: "Walk me through a recent [project/task] end to end."
Follow-ups: "What tools?" "What takes longest?" "Where does your
judgment matter most?" "What's just how you do it?"
SCREENSHARE: 3-4 specific triggers tied to their workflows.
Only when natural. Don't force with guarded people.
LISTEN FOR: "just how we do it" workflows — things they've stopped
questioning. Those are the richest exercise scenarios.

Act 3: AI Experience
[Friction flavor: skill / trust / awareness / access / identity]

Act 4: Wrap + Wishes
"If this Sprint could solve one problem..."
"Anything about the team I should know?"

### Value Exchange Tip
[Pre-plan ONE. Adapt by archetype:
- Beginners: "here's where the button is"
- Intermediate: "try this workflow"
- Advanced: genuine curiosity about their work
Include sponsor demo option if applicable.]

### Comparison Framework
[Update after each call]
```

### 2B. Post-Interview Debrief

**Trigger:** "Just finished with [name]" or "let's debrief"

COLLABORATIVE. The transcript is the floor, not the ceiling.

**Step 1 — Read transcript** from Notion meetings database.

**Step 2 — Extract:**
- Top 2-3 verbatim quotes
- Workflow snapshot (tools, time allocation, repetitive vs. judgment)
- AI friction diagnosis
- What success looks like in their words
- Terminology and nomenclature
- **Exercise/demo ideas** — tag these explicitly. Real scenarios that could become session exercises. Don't wait for synthesis.
- **Teaching material** — before/after examples, show-and-tell moments
- **People mentioned** — names of colleagues, their roles, which teams they're on. Builds the org map. Note anyone who sounds like they'd benefit from training (Round 2 potential).

**Step 3 — Surface sponsor radar items.**

> **🔔 SPONSOR RADAR**
> Flag observations that the sponsor (business owner/CEO) should know about. These are things that build Danoosh's trusted advisor positioning, demonstrate strategic insight beyond AI training, and may open doors to future work.
>
> Examples from Amada: Erica's VA authorization workflow involves massive data entry and copy-paste across 4+ systems. Most of her job could be automated, freeing her for higher-order strategic work like caregiver recruitment. Frame thoughtfully: this is about elevating people, not replacing them. Could be a lead for Brad (20% commission) for a custom automation build.
>
> Look for:
> - **Process automation opportunities** beyond what the Sprint will cover
> - **Organizational design insights** (people in wrong roles, bottleneck people, single points of failure)
> - **Strategic capability gaps** the sponsor may not see from their vantage point
> - **Quick wins** that could be delivered outside the Sprint scope
> - **Change management signals** (change fatigue, trust deficits, communication gaps)
>
> Frame these as observations, not recommendations. "Something worth having on your radar..." Protect source confidentiality. Never attribute to individuals in client-facing docs.

**Step 4 — Ask Danoosh:**
- "What was your gut read? Anything the transcript misses?"
- "Ideas for exercises or demos?"
- "Anything surprise you?"
- "How does this change Session 01 thinking?"
- "Adjustments for the next interview?"

**Step 5 — Headline insight.** Prompt for ONE sentence that captures this person. Format: "[Name] is [insight]." Examples: "He's not against AI, he just hasn't been shown." "She's not resistant, she's invisible to the rollout." "She holds the entire operation in her head and knows it shouldn't be that way." This becomes a design decision for the curriculum.

**Step 6 — Reframe the gap.** After each interview, ask: "Based on this, is the gap willingness, awareness, skill, trust, access, or something else? Has it shifted from what we thought?"

**Step 7 — Update Notion.** Debrief findings, Danoosh's observations, exercise ideas, sponsor radar items, headline insight, gap reframe, people/org map updates, updated comparison framework.

### 2C. After Interview 3: Gap Assessment

Before moving to synthesis, explicitly ask:
- "What perspective is still missing? What archetype haven't we heard from?"
- "Is there someone on the team who would challenge everything we've heard so far?"
- "Do we have enough contrast, or are we hearing the same story three times?"

If a clear gap exists → recommend a 4th interview (cap at 4). If saturated → move to synthesis.

Also at this point:
- **Re-evaluate the stretch axis.** Has it shifted from what we set in Phase 1?
- **Identify the "design for" person.** Who is the quietest, most uncertain, or most at-risk participant? Every session design decision should be pressure-tested: "Would this work for [name]?" This person is usually NOT the power user.

---

## Phase 3 — Survey + Assessment Baseline

**Trigger:** "Send the survey for [client]" / "code the survey responses" / "build the baseline"

The instrument is **locked at v1.0** — full question text, coding rubric, touchpoint design, and report specs live in `references/assessment-system.md`. Read it before deploying or coding. The hard rule: **questions are identical across all clients, forever** (the cross-client benchmark depends on it). Per-client customization touches only the header, the intro's opening line, and the signature.

**Step 1 — Deploy the pre-Sprint survey.** Use the Notion/Drive question templates (Drive folder: https://drive.google.com/drive/folders/16Pr3npzxtiPGVd-pXIwFuAdqqe4ESdYl · Notion: "Pre-Sprint Survey" in the Sprint Space Templates). No Google Forms for now. Customize header/intro-line/signature only, send to the team lead — *they* distribute (their voice drives completion). Timing: after interviews are underway, ≥1 week before Session 01. Mid-pulse fires **after Session 3**.

**Step 2 — Chase completion.** Target ≥80% before Session 01. Draft nudge emails for the team lead to forward. Flag holdouts in the checklist.

**Step 3 — Code the responses.** Code each free response against the 6-level rubric (assessment-system.md §6): highest-level example wins; individual placement = modal level; team placement = median. Cross-check coded levels against self-placement (Q11) — mismatches are signal, not noise (self-report lies in predictable ways).

**Step 4 — Build the Assessment Baseline.** Outputs: ladder distribution (the bar chart), team median, archetype mix (show-me-why / willing-but-stuck / already-ahead), the manager-expectation read (Q12), and the top bottlenecks/success-wishes (Q14–15) as content-design input. This becomes Section 5 of the Combined Readiness Brief and the "where the team is starting" slide of the Content Review Deck.

**Step 5 — Log to the master sheet.** Append anonymized coded data to the cross-client Master Survey Responses sheet — every cohort compounds the benchmarking moat.

**Step 6 — THE COMPOUND STEP (mandatory at every checkpoint: baseline, mid-pulse, post-Sprint).** Each checkpoint improves the product, not just measures the cohort: (1) read the data against what the design assumed; (2) extract ≤3 learnings tagged Teaching / Product / Assessment; (3) encode them — log to the Notion "🌱 Learnings & Compounding" page in the AI Team Sprint Space, update the relevant master template, flag any skill edit for Danoosh; (4) ship ONE visible improvement to the very next session and name it in the session prep. Every unit of work leaves the system smarter.

**Downstream (delivery + wrap, for awareness):** mid-Sprint pulse **after Session 3** (team-lead forcing function) · post-Sprint survey after Session 5 · 60-day client-administered pulse · the **Sponsor ROI Report** (5-page branded PDF: headline number → what shifted → in their own words → the work they do now → honest gaps → what I'd recommend next). Specs in assessment-system.md §7. The report is a progress report, not a sales document. Run the Compound Step after each of these too.

---

## Phase 4 — Synthesis → Combined Readiness Brief

**Trigger:** "Synthesize for [client]" or "write the readiness brief"

**Step 1 — Re-read all debriefs in one sitting.**

**Step 2 — Draft.** One document, 4-5 pages. Follow `references/brand-guidelines.md`.

1. **Team Snapshot.** Size, roles, tool, fluency distribution, top barrier.
2. **Top 3 Workflow Opportunities.** "Currently [X] → With AI [Y]." Team's language.
3. **Key Insight.** One sentence: "[Observation] because [driver]."
4. **Session Tuning Notes.** Per session: S01 framing, S02 tool, S03 scenarios, S04 client thread, S05 process redesign.
5. **Assessment Baseline.** From Phase 3: ladder distribution chart, team median, coded-vs-self-placement read, archetype mix, manager-expectation signal. (See `references/assessment-system.md`.)
6. **Success Metrics.** From survey + interviews + sponsor goals.
7. **Sponsor Radar Items.** Strategic observations worth flagging. Framed as "things worth having on your radar" — process automation opportunities, organizational insights, quick wins, potential future work. Protects source confidentiality. Positions Danoosh as trusted advisor, not just trainer.

Include 2-3 anonymized quotes. Themes, not names.

**Step 3 — Identify the "design for" person.** Name them (internal only). Pressure-test every session design decision against this person.

**Step 4 — Quality check.** Data-backed. Specific tuning notes. Team's language. Confidentiality maintained. Sponsor radar items framed thoughtfully.

---

## Phase 5 — Sponsor Content Review

**Trigger:** "Send the brief" or "set up the content review"

**Step 1 — Send email.** Template in `references/email-templates.md`.

**Step 2 — Prep Danoosh.** Talking points: tier distribution, workflow opportunities, session tuning, sponsor radar items (rehearse framing), lock dates.

**Step 3 — Recap email.** Specific agreements. This closes discovery.

---

## Learnings Library

**The living learnings library now lives in Notion: AI Team Sprint Space → "🌱 Learnings & Compounding"** (single source of truth — log new learnings THERE, not here, so sales/kickoff/session skills all compound into one place). Read it when prepping any new engagement. The Rockline + Amada learnings below are retained as a working cache; treat the Notion page as canonical.

### From Rockline (Bespoke Training, 26 people)

1. **If a pre-existing survey exists, it lies in predictable ways.** Every Rockline interviewee differed from their survey profile. If you have survey data before interviews, treat it as directionally right but specifically wrong at the individual level.
2. **The stretch axis shifts mid-discovery.** Started skeptic↔power user, ended awareness↔unawareness. Re-evaluate after each interview.
3. **Three ranked priorities keep 30-minute calls focused.** Without the hierarchy, conversations wander.
4. **Starting with the skeptic can be more valuable** than starting with the willing middle. The skeptic reveals where training breaks.
5. **The 4th interview was the most important.** LeAnn busted the biggest assumption. Always do a gap assessment after 3.
6. **Time allocation by archetype matters more than the sequence.** Skeptics need more rapport, power users need more deep-dive.
7. **The value exchange is the single most effective technique.** Transformed every conversation. Must be adapted by level.
8. **Screenshare is where exercise material lives.** But can't be forced. Read the energy.
9. **"Walk me through end to end" is the best Act 2 opener.** Every time.
10. **"Just how we do it" = richest exercise scenarios.** Workflows people stopped questioning.
11. **Name archetypes AFTER the interview, not before.** Pre-interview labels are hypotheses.
12. **Map the people landscape.** When interviewees mention colleagues, capture names, roles, teams, and what they do. This builds the org picture: who's on which team, who does what, where the natural clusters are. Useful for: designing small group exercises, identifying who might benefit from a Round 2 training, and spotting future business potential (other teams or departments that could use a Sprint).
13. **Sponsor instincts: right at macro, wrong at micro.** Validate the big read, push for representation they'd miss.
14. **Share themes, not names.** Hard rule in all client-facing comms.
15. **One headline insight per interview > ten observations.** "He's not against AI, he just hasn't been shown."
16. **The comparison framework IS the synthesis.** By interview 4, patterns jump out visually.
17. **Post-call download within 30 minutes.** Emotional texture fades fast.
18. **Identify the "design for" person.** Pressure-test every design decision against them.
19. **Real workflows became real exercises.** Tag exercise scenarios during capture, not synthesis.
20. **Reframe the gap after each interview.** Willingness? Awareness? Skill? Trust? Access?

### From Amada (First AI Team Sprint, 15 people)

1. **Sponsor reads can be wrong.** Joe mislabeled Brittany. Always verify through your own research.
2. **Change fatigue must be named.** "What would make this one stick?"
3. **Value exchange transforms conversations.** Chelsea lit up at Guide SOP tool. Erica engaged when shown extraction demo.
4. **Show what the sponsor built.** Joe's coverage map with real Amada data was powerful.
5. **Screenshare requests must be specific.** "Show me what happens in AxisCare when a caregiver calls out."
6. **Email signatures are gold.** Brittany's revealed "Director of Business Admin" — changed the whole approach.
7. **Progressive discovery pays off immediately.** Chelsea's transcript reshaped Brittany's entire prep.
8. **The channel may already exist.** Erica showed us the live Teams channel during her interview.
9. **People hold critical logic in their heads.** Chelsea knows every caregiver's constraints from memory.
10. **Sponsor radar items are everywhere.** Erica's workflow is 80% automatable. Frame as elevating people, not replacing them. Potential lead for Brad.

### [NEXT ENGAGEMENT — Add learnings here]

After each completed discovery, Danoosh adds new learnings to this section. The skill gets smarter with every run. Format: numbered list, one sentence per learning, specific and actionable. Tag which engagement it came from.

---
name: coaching-proposal-writer
description: >
  1:1 Coaching Proposal Writer (Post-Diagnostic). Trigger aggressively when Danoosh says "build the proposal," "write up the proposal," "turn this into a deliverable," "draft the SOW," "close this deal," "send the recap," or references a completed diagnostic session and wants to produce a coaching proposal. Also trigger when Danoosh uploads a call transcript and says "here's the transcript" or "check out this call" with intent to produce deliverables. Covers the full arc from call transcript analysis through polished branded SOW, optional Decision Brief, and Gmail follow-up email. Does NOT cover pre-call prep (use sales-call-prep skill), cold outreach, corporate training proposals, or speaking engagement proposals.
---

# 1:1 Coaching Proposal Writer (Post-Diagnostic)

## Overview

This skill guides Claude through a structured, multi-phase process to turn a completed diagnostic session into a polished coaching proposal package. It produces: a sales coach debrief, a customized session plan, a branded SOW document, an optional Decision Brief (when live coaching work was done in the session), and a Gmail follow-up email.

**Scope:** Post-diagnostic coaching proposals only. The diagnostic session (60-90 min) has already happened. Danoosh has a transcript. The prospect expressed interest in continued coaching. Now we need to close the deal with a professional, branded deliverable package.

**Who is Danoosh:** Solo AI transformation consultant based in San Francisco. Background at IDEO and XPLANE. Helps senior leaders use AI as a thinking partner for better decisions. Has ADHD (inattentive). Deliverables need to be clean, scannable, and on-brand. He communicates in a warm, conversational, peer-level tone. Formal consultant language is a consistent rejection point.

---

## The Workflow

```
Phase 1: Intelligence Gathering
    ↓
Phase 2: Transcript Analysis & Sales Debrief (in chat)
    ↓
Phase 3: Session Plan Design (in chat)
    ↓
⏸️  CHECKPOINT — Danoosh reviews and approves
    ↓
Phase 4: Polished SOW Document (.docx)
    ↓
Phase 5: Decision Brief (.docx) — only if diagnostic included live coaching work
    ↓
Phase 6: Email Draft (Gmail)
```

**Do not skip the checkpoint.** Phases 4-6 are production work. Get approval before producing documents.

---

## Voice & Tone Mirroring (Cross-Cutting Principle)

The psychological profile from Phase 2 actively informs how every deliverable gets written: the proposal, the Decision Brief, and the email. All of it should sound like Danoosh wrote it, speaking directly to this specific person. Not robotic. Not template-y. Not something that could have been written for anyone.

**Everything the prospect reads must be written in Danoosh's warm, peer-level voice, tuned to resonate with this specific prospect by mirroring their communication style and speaking to their underlying psychology.**

How this works in practice:

- **Study how the prospect communicates in the transcript.** How do they talk? Short and direct, or expansive and relational? Do they use metaphors from their industry? Do they think in systems, stories, numbers, or relationships? Do they respond to precision or warmth? Are they formal or casual? What words and phrases do they repeat?
- **Write like Danoosh talking to this specific person.** Danoosh's voice is always warm, conversational, clear, and peer-level. But the specific texture flexes. If the prospect is a toolmaker who thinks in precision, tolerances, and systems, Danoosh would naturally use language like "calibrate," "build the jig before running the part," "repeatable process." If the prospect is a relationship-first leader, Danoosh would say things like "how your recommendations land," "the way you show up in the room," "the trust you've built." Don't force their metaphors. Let the language feel like a natural conversation between two people who understand each other's world.
- **Speak to their decision-making style.** If they're analytical, emphasize frameworks, structure, and measurable outcomes (6-8 hours reclaimed, 20-minute process). If they're intuitive, emphasize feel, momentum, and the experience of working differently. If they're risk-averse, emphasize the guarantee, the low-risk first step, and the escape ramp.
- **Address their deeper motivations.** The proposal's "What We'll Accomplish" section, session descriptions, and "Why This Works" bullets should connect to what the prospect actually cares about beneath the surface (competence, legacy, independence, security, craft, freedom) as surfaced in the psychological profile. The email's three key takeaways should reinforce what mattered most to them, not what Danoosh thinks is most impressive.
- **Match their register.** If they say "that's crazy" and "jeepers," everything should feel conversational and unpretentious. If they speak in structured paragraphs with precise terminology, match that precision. This applies to the proposal, the Decision Brief, and the email equally.

**The test:** If the prospect reads any of these deliverables and feels like Danoosh wrote it specifically for them, by someone who truly understands not just their business problem but how they think, the voice mirroring is working. If it feels generic, corporate, or like it was generated from a template, it's not.

---

## Phase 1: Intelligence Gathering

**Goal:** Build a complete picture of the prospect, the relationship history, and what was agreed to verbally.

**Steps (run in parallel where possible):**

1. **Check for uploaded transcript.** If Danoosh uploaded a file or pasted a transcript, read it thoroughly first. This is the primary source of truth.

2. **Search Notion for call transcript.** If no transcript was uploaded, search Notion → "All Meeting Notes (DK)" database for the most recent call transcript with this prospect.
   ```
   Tool: notion-search
   Query: "[prospect name] meeting notes"
   Then: notion-fetch on the result
   ```

3. **Search Google Drive** for existing 1:1 coaching proposals and SOWs as structural inspiration. Key search terms: "SOW coaching" or "proposal sessions." Fernando's SOW and Joe Hilliard's proposal are the primary templates. Do NOT copy them verbatim. Use them for tone, structure, and level of detail.
   ```
   Tool: google_drive_search
   Query: fullText contains 'coaching' and fullText contains 'session' and fullText contains 'investment'
   ```

4. **Search Gmail** for prior correspondence with this prospect. Read full threads to understand relationship history, who initiated, tone, what was discussed before the diagnostic.
   ```
   Tool: gmail_search_messages
   Query: "from:[prospect email] OR to:[prospect email]"
   ```

5. **Check Notion pipeline** for deal context (stage, notes, follow-up dates).
   ```
   Tool: notion-search
   Query: "[prospect name] pipeline"
   ```

6. **Review any uploaded research briefs or prep docs** that Danoosh may have shared.

**Output:** Complete picture of prospect, relationship history, and what's on the table. Surface any gaps and ask Danoosh for missing context before proceeding.

---

## Phase 2: Transcript Analysis & Sales Debrief

**Goal:** Read the full transcript and deliver a sales coach debrief in chat. This is a thinking partner moment, not a document.

### 2A: Sales Coach Debrief

Analyze the transcript and report to Danoosh:

**What went well.** Specific moments from the transcript, not generic praise. Quote or reference exact exchanges. Look for:
- Where Danoosh demonstrated expertise that landed
- Where the prospect had an insight or shift in thinking
- Where trust was built
- Where value was delivered live

**How the close happened.** Who brought up working together? Who mentioned money first? Was there price resistance? What were the buying signals? Was there a verbal agreement?

**Revenue impact.** What's the deal worth? How does it fit into the current pipeline? What's the downstream potential (referrals, team training, advisory board)?

**What to watch.** Scope boundaries, tendency to over-deliver, any risks in the relationship dynamic. Flag if the prospect is trying to get free advisory access. Flag if Danoosh gave away too much before the proposal is on the table.

**The Generosity Check.** Assess whether the door is already open:
- Did the prospect implement prior advice?
- Did the prospect initiate contact or respond quickly?
- Did the prospect explicitly ask about working together?
- Did the tone shift from "picking your brain" to "I need your help"?
- Did the prospect say "we should do this" or "what would it cost"?

If the door is open, flag it: "The door is already open. The proposal is a formality, not a pitch."

### 2B: Psychological Profile (Two Levels Deep)

Build a complete profile of the prospect from the transcript. Do not abbreviate this.

**Layer 1: The Surface**
- **Role and background:** Title, career history, domain expertise, communication style
- **Stated needs:** What they explicitly said they want from coaching
- **Decision-making role:** Are they the buyer (controls budget), or is there a hidden stakeholder?
- **AI skill level:** Where are they today? Late beginner, early intermediate, intermediate, advanced?

**Layer 2: What's Really Going On Beneath the Surface**
- **Core values:** What does this person care about most deeply? (competence, independence, fairness, recognition, security, innovation, craft, legacy, freedom, family, status)
- **Decision-making style:**
  - Analytical: needs data, frameworks, proof points
  - Intuitive: trusts gut, moves fast when something feels right
  - Consensus-driven: needs others to agree
  - Authority-driven: decides fast, alone
  - Risk-averse: needs safety nets, guarantees, small steps
- **How to effectively influence them:** Based on values and decision style (peer-to-peer intellectual exchange, data and proof, emotional resonance, social proof, risk reduction, identity/legacy appeal)
- **Hopes and dreams:**
  - Professional: What does success look like? What are they building toward?
  - Personal: What identity are they stepping into?
  - What would make them feel like hiring Danoosh was the best decision they made this quarter?
- **Pains and fears:**
  - What keeps them up at night about this challenge?
  - Worst-case scenario they're trying to prevent?
  - Past bad experiences? (bad consultants, wasted money, looking foolish)
- **Barriers to yes:**
  - What's between them and signing? (budget, bandwidth, time, travel, ROI uncertainty)
  - What information or experience would remove the barrier?

### 2C: Pricing Signal Check

Default pricing is **$5,000 for 6 sessions**. Scan the transcript for signals that suggest adjusting:

**Signals to price higher ($6K-$8K):**
- Prospect runs a large or complex organization
- Multiple companies or contexts to cover
- Prospect mentioned budgets or investments casually (signals money is not a constraint)
- Exceptionally high-value downstream opportunity (team training, advisory)

**Signals to price lower ($3K-$4K):**
- Prospect explicitly mentioned budget constraints
- Simpler use case (single company, narrower scope)
- Prospect is early-career or building something new without revenue

**If signals suggest deviation from $5K**, surface this for Danoosh's review with reasoning. Do not change the price autonomously.

**Output:** Conversational debrief in chat. Human portrait of the prospect. Pricing recommendation if different from default.

---

## Phase 3: Session Plan Design

**Goal:** Design a customized 6-session coaching arc and present it to Danoosh for approval.

### Standard Progression (starting point)

| Session | Focus |
|---|---|
| 1 | Personalized setup + mindset shift for how to work with AI |
| 2 | AI as thinking partner / decision-making |
| 3 | Communicating with influence |
| 4 | Workflows & data analysis |
| 5 | Agents for efficiency |
| 6 | Reflection, integration, and thriving in the AI era |

### Customization Rules

- **Session 1 always includes:** Tool stack audit and recommendation, custom instructions tuned to the prospect's world, voice mode unlock. The tool stack recommendation is part of the value Danoosh delivers in Session 1. Do not pre-decide the stack in the proposal.
- **Session 6 always includes:** Personal playbook, tool stack finalization, forward-looking conversation about where AI is heading and what it means for how they work.
- **Sessions 2-5 are flexible.** Reorder or reweight based on what the transcript reveals about the prospect's priorities, skill level, and use cases.
- **Session titles should use the prospect's language**, not jargon. "Making Your Recommendations Land" not "AI-Augmented Communication Frameworks."
- **Each session description is one paragraph.** Communicate the what and the so-what without prescribing exact exercises. Leave room for Danoosh to flex.
- **No company names in the proposal.** Keep references to "your consulting practice," "your organizations," "your client work." The proposal must be standalone.
- **Reference Claude tools** (deep research, Cowork, Claude in Chrome) rather than the ChatGPT stack.

### What to Present at Checkpoint

Present to Danoosh in chat:

1. **One recommended session arc** with session titles and one-paragraph descriptions, contextualized to the prospect's world.
2. **1-2 alternative options** with brief rationale for why Danoosh might prefer them (e.g., "If you want to front-load the agent work because Mike seemed most excited about that, you could swap Sessions 4 and 5").
3. **Any pricing recommendation** if different from default $5K.
4. **Scheduling suggestion** based on what was discussed on the call (days, times, cadence).

### ⏸️ CHECKPOINT

**Stop here and wait for Danoosh's approval.** Do not produce any documents until he confirms the session plan, pricing, and any adjustments.

---

## Phase 4: Polished SOW Document

**Goal:** Produce a branded .docx proposal document.

### Before Writing

1. Read `/mnt/skills/public/docx/SKILL.md` for document creation best practices.
2. If Danoosh's logo is available at `/home/claude/logo.png`, use it. If not, convert the SVG from uploads using cairosvg.

### Document Structure

See `references/sow-template.md` for the complete template with section-by-section content guidance.

### Brand Standards (non-negotiable)

- **Colors:** Black #000000 (titles, body), Khaki #C5AA88 (section numbers, subheaders, accents), Cream #ECE3D7 (callout box backgrounds), #EAEAEA (light dividers)
- **Fonts:** Helvetica Bold (headings, section titles), Georgia (body text, descriptions)
- **Logo:** DK Consulting logo, top-left of cover page
- **Layout:** Section-numbered (01, 02, 03...), khaki section numbers above black section titles, khaki divider lines between sections
- **Page size:** US Letter (12240 x 15840 DXA)
- **Margins:** 1 inch all sides
- **Headers:** "DK CONSULTING | [DOCUMENT TYPE]" right-aligned on all pages except cover
- **Footers:** "Page [n]" centered in khaki

### Key Content Principles

- **Overview** opens with "This private coaching program picks up where [context] left off." Always personalized to the relationship.
- **3x more valuable** is the standard value claim. Use it in the overview.
- **"Teach you how to fish"** language belongs in the overview. The goal is skill ownership, not dependency.
- **"What We'll Accomplish"** (not "Engagement Objectives"). Every bullet connects back to the prospect's consulting practice / business / client value.
- **Session descriptions** are one paragraph each. Bold session titles in Helvetica.
- **"Why This Works"** section always includes: Built around your reality, Fast ROI (6-8 hours/week reclaimed by session 4), Skill ownership not dependency, Low friction, Current and practical.
- **Engagement Logistics** always includes: Format (6 private 1:1 sessions via Zoom), Duration (~8 hours total), Cadence (no more than 10 days apart), Between sessions (2 hours/week applying in real work context, not extra homework), Prep (Danoosh sends prep note, prospect brings real projects and workflows), Support (async email/messaging access), Completion window (10 weeks).
- **Investment:** $5,000 USD unless adjusted at checkpoint. Payment via credit card using a secure Stripe link. Payment due upon receipt.
- **Guarantee:** "If after the first two sessions you don't feel this is delivering real, practical value to how you work, you'll receive a full refund. If you cancel after Session 3 begins, you pay only for sessions completed."
- **Terms:** 24hr cancellation policy (missed sessions or <24hr cancellations billed as completed), IP usage rights, confidentiality, curriculum adaptation, dispute resolution.
- **Signatures:** Two-column signature block with date lines.

### Voice & Tone Review (before producing the document)

Before writing a single line, revisit the psychological profile from Phase 2. Ask:
- What language does this prospect use? What metaphors come from their world?
- Are they direct or expansive? Precise or relational?
- What are they really trying to become? What identity are they stepping into?
- What would make them feel seen when they read this?

Write the entire proposal as Danoosh speaking directly to this person. Session titles, bullet labels, outcome descriptions, the "Why This Works" section, even the overview paragraph should feel like Danoosh wrote it after deeply understanding who this person is. The brand standards (fonts, colors, layout) stay consistent. The voice and language flex to meet the prospect.

### Production Steps

1. Build the document using `docx-js` (npm docx package).
2. Validate with `python scripts/office/validate.py`.
3. Convert to PDF for preview using LibreOffice.
4. Preview key pages visually to confirm layout.
5. Copy to `/mnt/user-data/outputs/` and present with `present_files`.

**Output:** Validated .docx file, presented to Danoosh.

---

## Phase 5: Decision Brief (Conditional)

**Goal:** If the diagnostic session included a live decision-framing exercise, produce a companion Decision Brief document.

**Trigger:** Only produce this if the transcript shows Danoosh walked the prospect through a decision analysis (the Framing Stack, scenario modeling, whiteboard exercise, or similar). If the session was exploratory or tool-focused without a working decision, skip this phase.

### Document Structure

See `references/decision-brief-template.md` for the complete template.

### Key Content Principles

- **This is coaching, not sales.** The Decision Brief delivers value from the session. It should not feel like a pitch for more work.
- **Capture the thinking, not the transcript.** Restructure and elevate the conversation into a clear analytical document.
- **The decision frame should be stated cleanly** in one sentence, with a separate "not deciding yet" list.
- **"What you may not be fully considering"** section surfaces blind spots from the conversation. This is where Danoosh's value as a thinking partner is most visible.
- **Scenario modeling** should include a data table (best/base/worst across time horizons) AND any visual artifacts (whiteboard sketches, images generated during the session) as embedded images.
- **"The human side"** section addresses the emotional and reputational layer. This is often the most impactful section.
- **"What appears true right now"** splits into "likely true" and "still uncertain." This demonstrates intellectual honesty.
- **"Taking this further on your own"** points the prospect to working with their AI, not selling more Danoosh time. Keep it to one concise section with the three concepts: define the field, future walkthrough, second-order scan.
- **Closing line should be memorable.** End with a single bold/italic statement the prospect will remember.

### Production Steps

Same as Phase 4: build with docx-js, validate, preview, present.

**Output:** Validated .docx file, presented to Danoosh.

---

## Phase 6: Email Draft

**Goal:** Draft the follow-up email in Gmail.

### Email Architecture

The email is **75% coaching recap, 25% soft sell.** It should feel like a note from a trusted advisor, not a sales follow-up.

### Structure

1. **Warm opening (2-3 sentences).** Reference something specific from the session that made it productive. Acknowledge what the prospect brought to the table.

2. **Thank them** for trusting you with this important work.

3. **Three key takeaways.** Bolded labels, 2-3 sentences each. These reinforce what the prospect learned, not what Danoosh sells. Pull directly from the session content. Frame as principles they can apply immediately.

4. **Attachments explained.** One short paragraph per attachment:
   - Decision Brief (if applicable): "I put together a Decision Brief based on what we worked through today. It's not a set of answers. It's a structured way to continue the thinking on your own, with your AI, at your own pace."
   - SOW: "I also put together a proposal for the coaching program we discussed. Take a look at the session-by-session plan and let me know if it captures what you want to accomplish. I designed it based on our conversation, but I'd love your input on whether the arc feels right. If anything needs adjusting, we'll adjust it."

5. **Scheduling options.** Present 2 time slots Danoosh provides, converted to the prospect's time zone. "If you're ready to get rolling, here are two recurring time slots that work well on my end: [options]. Let me know which works better for your schedule and we'll lock it in."

6. **Links.** Hyperlinked (not raw URLs):
   - Slides from the session
   - Fathom recording link
   - Any other resources mentioned

7. **Soft referral ask.** "One more thing. I genuinely appreciate [specific thing they did, e.g., offering to pay, being open, bringing a real challenge]. Since you've been a supporter of my work, if you have friends or colleagues who could benefit from this kind of thinking, I'd appreciate an introduction. That's the most valuable thing to me."

8. **Warm close.** Acknowledge their schedule/travel/life context. "No rush on any of this. [Context-specific line]. Whenever you're ready, I'm here."

9. **Sign off.** "Talk soon, Danoosh"

### Email Production Rules

- Use `gmail_create_draft` with `contentType: text/html`
- Hyperlink all long URLs (slides, Fathom, etc.)
- Convert scheduling times to prospect's time zone
- CC `louisianna@danooshkapadia.com` if appropriate
- Remind Danoosh: attachments must be added manually before sending
- Tone: warm, conversational, peer-level. No corporate filler.
- No em dashes. Use commas or periods.
- **Voice mirroring applies to the entire email, not just the proposal.** The email should sound like Danoosh writing to this specific person, informed by how they communicate, what drives them, and what they care about. The warm opening, the three key takeaways, the way the proposal is introduced, the referral ask, the closing line, all of it should reflect the prospect's communication style and deeper psychology. If the prospect is casual and direct, the email is casual and direct. If they're more considered and reflective, match that. This is Danoosh's voice, tuned to this person. Not a template with a name swapped in.

**Output:** Gmail draft ready for Danoosh to review, attach files, and send.

---

## References

- `references/sow-template.md` — Complete SOW document template with section content
- `references/decision-brief-template.md` — Complete Decision Brief document template

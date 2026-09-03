# SOW Template Reference

## Document Sections (in order)

### Cover Page
- DK Consulting logo (top-left, ~90x76px)
- Title: "[N]-SESSION AI COACHING PROGRAM" (Helvetica Bold, 28pt, black, stacked across 2-3 lines)
- Khaki divider line below title
- Subtitle: "PREPARED FOR [PROSPECT FULL NAME]" (Helvetica Bold, 11pt, khaki)
- Bottom block: Danoosh Kapadia / AI Educator & Strategist / hello@danooshkapadia.com / [Month Year]

### 01 — OVERVIEW
Three to four paragraphs:
1. "This private coaching program picks up where [context-specific reference to prior interaction] left off. You already see the potential and you've started putting AI to work. Now we go deeper."
2. "Over six personalized sessions, you'll learn to [tailored list of 4 outcomes relevant to this prospect]."
3. "Right now, AI helps you [current state]. By session six, it'll help you think, plan, and deliver at a level that makes you 3x more valuable to every [company/client/organization] you work with."
4. Italicized: "The goal isn't to make you dependent on any single tool. It's to teach you how to fish, so you can keep adapting and evolving as the technology does."

### 02 — WHAT WE'LL ACCOMPLISH
Bullet list (6 items). Each bullet has a bold label followed by a description sentence. Every bullet connects back to the prospect's world:
- **[Label].** [How AI helps them] so [the value it creates for their clients/business/practice].

Standard labels to adapt: Sharper judgment, Voice-first workflows, Faster analysis, Deliverables that land, Delegate real work, Your personal AI playbook.

### 03 — SESSION-BY-SESSION PLAN
Table with columns: # | FOCUS & OUTCOMES | LENGTH

Standard session structure:
| # | Title | Length | Description guidance |
|---|---|---|---|
| 1 | Your AI Foundation: Mindset, Setup & Personalization | 90 min | Tool audit, stack recommendation, custom instructions, voice mode unlock |
| 2 | AI as Your Thinking Partner: Decisions & Strategy | 75 min | Framing stack, decision analysis, scenario modeling, 20-minute process |
| 3 | [Customize title to prospect's language] | 75 min | Voice-to-memo-to-deck workflow, audience perspective-taking |
| 4 | Workflows & Data Analysis | 75 min | Workflow mapping, AI on real data, 6-8 hours reclaimed claim |
| 5 | Delegating Real Work to AI | 75 min | Deep research agents, browser agents, desktop agents, live workflow |
| 6 | Thriving in the AI Era | 90 min | Personal playbook, tool stack finalization, forward-looking conversation |

Session titles should use the prospect's language where possible. Each description is one paragraph, not a list. Communicate what they'll do and what they'll walk away with.

### 04 — WHY THIS WORKS
Five bullets, always these (adapt language to prospect):
1. **Built around your reality.** Real work, real output, nothing hypothetical.
2. **Fast ROI.** Measurable improvement by session 2. 6-8 hours/week reclaimed by session 4.
3. **Skill ownership, not dependency.** Teach to fish, not hand a fish. Adapts when tools change.
4. **Low friction.** Prospect brings challenges, Danoosh brings structure.
5. **Current and practical.** Tools and techniques reflect where AI is today, not six months ago.

### 05 — ENGAGEMENT LOGISTICS
Bold label + description format (not bullets):
- **Format:** 6 private 1:1 coaching sessions via Zoom
- **Duration:** Approximately 8 hours total coaching time
- **Cadence:** No more than 10 days apart. Consistent day and time.
- **Between sessions:** ~2 hours/week applying in real work. Not extra homework. Using new tools on existing projects and decisions.
- **Prep:** Danoosh sends brief prep note before each session. Prospect brings specific projects, workflows, and real decisions. The more real the material, the more useful the session.
- **Support:** Email or messaging access between sessions. Quick questions, screenshots, async feedback. "My job is to keep you unblocked."
- **Completion window:** 10 weeks from project start.

### 06 — INVESTMENT
Table: DESCRIPTION | FEE
- Executive AI Coaching (6 sessions) | $5,000 USD (or adjusted amount)

**Payment:** Payment will be via credit card using a secure Stripe link. Payment due upon receipt.

**Guarantee:** If after the first two sessions you don't feel this is delivering real, practical value to how you work, you'll receive a full refund. If you cancel after Session 3 begins, you pay only for sessions completed.

### 07 — TERMS & CONDITIONS
Bold label + description format:
- **Cancellations & Rescheduling.** 24 hours' notice required. Missed sessions or cancellations with less than 24 hours' notice are billed as completed.
- **Intellectual Property & Usage.** All frameworks and methods are proprietary. Use within your organizations but not resell or redistribute. Custom assets from sessions are yours.
- **Confidentiality.** All conversations and materials remain confidential. We'll discuss best practices for what data to share with AI systems.
- **Curriculum Adaptation.** Curriculum may be updated as AI capabilities evolve.
- **Dispute Resolution.** Direct conversation or mediation before formal action.

### 08 — SIGNATURES
Two-column layout:
- Left: Signature line + "Prospect Full Name" + "Date: _______________"
- Right: Signature line + "Danoosh Kapadia" + "Date: _______________"

---

## Technical Production Notes

- Use `docx-js` (npm docx package) for document generation
- US Letter page size: 12240 x 15840 DXA
- 1 inch margins: 1440 DXA all sides
- Content width: 9360 DXA (but tables at 7360 DXA for visual breathing room)
- Session table columns: 600 (number) + 5760 (content) + 1000 (length) = 7360
- Investment table columns: 5360 (description) + 2000 (fee) = 7360
- Use ShadingType.CLEAR (never SOLID) for table shading
- Use WidthType.DXA (never PERCENTAGE)
- Section numbers: Helvetica, 10pt, khaki, bold
- Section titles: Helvetica, 14pt, black, bold, UPPERCASE
- Body text: Georgia, 10.5pt, black
- Divider lines: 2px khaki bottom border on empty paragraph
- Callout boxes: cream background (#ECE3D7) with 6px khaki left border
- Validate with: `python scripts/office/validate.py [file].docx`
- Preview with: LibreOffice PDF conversion + pdftoppm

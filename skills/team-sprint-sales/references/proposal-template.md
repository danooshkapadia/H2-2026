# The HTML Scroll Proposal — Structure & Build Spec

A single-scroll branded web page, not a PDF deck. The buyer experiences the argument sequentially — each section earns the right to the next — so by pricing they're confirming a decision, not evaluating one. **The format is the argument.**

Gold exemplars: ConForms `Website Proposal/index.html` · the Notion "Sales Page HTML" master (AI Team Sprint Space → Templates) · the ConForms Kickoff Deck (same CSS system).

## Brand implementation (non-negotiable; see brand-guidelines.md)

```css
:root {
  --ink-1:#000000; --ink-2:#1A1A1A; --ink-3:#6B6B6B;
  --white:#FFFFFF; --khaki-paper:#ECE3D7; --soft-paper:#F5F3EE; --utility-grey:#EAEAEA;
  --red:#CC0000;   /* Statement Red — ONE per surface */
  --khaki:#C5AA88; /* eyebrows/kickers on white only */
  --rule:rgba(0,0,0,0.5); /* weight varies (0.5/1/2px), never hue */
  --sans:'Helvetica Neue',Helvetica,Arial,sans-serif;
  --serif:Georgia,'Times New Roman',serif;  /* editorial passages only */
  --mono:'SF Mono','JetBrains Mono',Menlo,monospace; /* data only */
}
```

- **12pt minimum font everywhere (Danoosh's readability floor)** — where the brand ladder says 10–11px, bump to 12pt.
- One Statement Red moment per surface. Hairlines, no shadows/gradients/emoji/icon bullets. White ↔ khaki surface rhythm, max two papers per page.
- Include `@media print` (letter landscape, page-break per section) — copy the proven block from the ConForms kickoff deck.

## Section order (locked — this sequence IS the close)

1. **Title/masthead** (khaki paper) — "The AI Team Sprint — A Proposal for [CLIENT]" · mono date line · client/consultant/team-lead meta grid.
2. **What I heard from you** — 6–8 bullets in the buyer's words. Does most of the closing.
3. **The three shifts** — the end state, 60 seconds of reading.
4. **The program** — timeline graphic, then each session one line.
5. **Fast vs. right + the MIT step-down** — Frames 3+4. *"That research is about large enterprises. [Company] isn't that."*
6. **The mechanics** — drumbeat, real work, channel, recordings.
7. **Getting ready / what each side provides** — the guided-setup bullet carries the under-rolling frame.
8. **Investment** — all three tiers ($10,000 / **$12,500** / $15,000), honestly. Middle labeled "the version we scoped together on our [date] call." Top: "chosen upfront because the baseline is built at kickoff." **Written numbers must match the spoken numbers exactly.**
9. **Next steps** (ink surface) — SOW timing, first payment, kickoff window.

## Build checklist
- [ ] "What I heard" bullets verbatim from discovery
- [ ] Middle tier = exactly what was verbally scoped
- [ ] One red moment per surface · no text below 12pt · serif only editorial · print export verified · prices match spoken

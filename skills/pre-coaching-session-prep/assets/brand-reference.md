# DK Consulting — Brand & Design Reference

Load this when producing any branded artifact: session sheets, facilitation guides, HTML emails, slide content, or client-facing documents.

---

## Logo

The DK Consulting logo is an SVG wordmark: "DK" in a rounded-rectangle border with "consulting" set beneath in lowercase serif. The logo file is stored in the Claude Project's knowledge files as `Group_17.svg` or `DK_Signature.png`.

---

## Voice & Tone

- Plain, declarative, short sentences. No hedging, no throat-clearing, no marketing puff.
- No emoji. No exclamation points. No "exciting" / "revolutionary" / "game-changing."
- One idea per sentence. One claim per paragraph.
- Write as a founder, not a copywriter.
- Limit em dashes. Use commas and periods instead.

---

## Typography

**Three families, each with one job:**

| Family | Job | Never use for |
|--------|-----|---------------|
| **Helvetica Neue** (sans) | UI, body, headlines, buttons, eyebrows, metadata | — |
| **Century / Source Serif 4** (serif) | Editorial long-form: newsletters, essays, pullquotes, case-study body | Buttons, UI chrome, captions, cards |
| **JetBrains Mono** (mono) | Functional data: phone numbers, email, file paths, dates, figures | Running prose |

Fallbacks: Helvetica Neue → Inter → system sans. Century → Source Serif 4 → Georgia. For Gmail HTML, use Arial (Helvetica stand-in) for headers and Georgia (Century stand-in) for body.

**Type ladder (locked sizes):**

| Role | Size | Leading | Tracking |
|------|------|---------|----------|
| Display headline | 48–88px | 0.95–1.0 | -0.02em |
| Headline | 28–42px | 1.1–1.15 | -0.015em |
| Subhead | 18–24px | 1.25 | -0.01em |
| Body (sans) | 15px | 1.55 | — |
| Body (serif) | 17px | 1.55 | — |
| Caption/aside | 13.5px | 1.55 | — |
| Eyebrow | 12px uppercase | — | +0.16em |
| Kicker | 10px uppercase | — | +0.16em |
| Mono | 11–13px | — | +0.03em |

Never interpolate off the ladder.

---

## Color

**Three inks:**

| Token | Hex | Use |
|-------|-----|-----|
| ink-1 | `#000000` | Headlines, buttons, editorial marks |
| ink-2 | `#1A1A1A` | Body paragraphs, long-form |
| ink-3 | `#6B6B6B` | Captions, metadata, bylines |

**Four paper surfaces:**

| Token | Hex | Use |
|-------|-----|-----|
| White | `#FFFFFF` | Default reading surface |
| Khaki Paper | `#ECE3D7` | Covers, mastheads, pullquotes, founder voice |
| Soft Paper | `#F5F3EE` | Don't-blocks, in-context demos, quiet panels |
| Utility Grey | `#EAEAEA` | Tables, dashboards — never editorial |

**Two accents (heavily rationed):**

| Token | Hex | Rule |
|-------|-----|------|
| Statement Red | `#CC0000` | ONE per surface. A button, a numeral, a rule, a pullquote attribution. Never two. |
| Khaki text | `#C5AA88` | Eyebrows and kickers on white only. On khaki paper, eyebrows switch to black. |

**Divider rules:** All rules are `rgba(0,0,0,0.5)`. Tonal variation comes from weight: hair (0.5px), thin (1px), bold (2px). Never colored rules.

---

## Layout & Components

- **Hairline borders** (0.5px, rgba(0,0,0,0.5)), not drop shadows.
- **Card radius:** 10px. **Button radius:** 6px. **Tile radius:** 14px.
- **Buttons:** Solid red `#CC0000` white text for primary; white with 1px black border for secondary. One primary per screen.
- **Lists:** Left-aligned title, right-aligned metadata, rule between rows. Never bullets, checkmarks, or zebra stripes.
- **Quotes:** Soft paper background, 24px Century italic, 1.45 leading, attribution in sans below a hairline rule.
- **Grid:** 12-column, 20–24px gutters. Generous white space.
- Surface alternation creates rhythm: white ↔ khaki paper. At most two paper tones per page.

---

## Hard "Don'ts" (AI-slop tells)

- No gradient backgrounds
- No emoji
- No lift shadows (box-shadow halos)
- No left-border accent rails
- No noise/grain textures
- No hand-drawn SVG illustrations
- No decorative dividers or flourishes
- No serif on buttons or at caption size
- No two reds on one page
- No khaki text on khaki paper
- No colored rules

---

## Gmail HTML approximation

When building HTML emails (for post-session follow-ups, pre-session nudges), use these Gmail-safe substitutions:

| Brand element | Gmail substitute |
|---------------|-----------------|
| Helvetica Neue Bold (headers) | `font-family: Arial, Helvetica, sans-serif; font-weight: 700; color: #000000` |
| Khaki sub-headers | `font-family: Arial, Helvetica, sans-serif; font-weight: 500; color: #c5aa88; font-size: 14px; text-transform: uppercase; letter-spacing: 0.5px` |
| Century (body) | `font-family: Georgia, 'Times New Roman', serif; font-size: 16px; line-height: 1.6; color: #1a1a1a` |
| Divider rules | `border: none; border-top: 1px solid #eaeaea; margin: 28px 0` |
| Container | `max-width: 600px` |
| Phone/email (mono) | `font-size: 14px; color: #8a8a8a` |

Sign-off format: "Warmly," or "Talk soon," followed by "Danoosh" and `C: (415) 680-5730` in slate.

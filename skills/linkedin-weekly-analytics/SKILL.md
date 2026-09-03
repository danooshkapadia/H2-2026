---
name: linkedin-weekly-analytics
description: >-
  Pull LinkedIn post analytics into Danoosh's Notion "Published Post Analytics"
  database. Trigger aggressively whenever Danoosh wants to update, refresh, log,
  or grab his LinkedIn post numbers, e.g. "update my post analytics," "grab my
  LinkedIn numbers," "log this week's LinkedIn stats," "refresh the Published
  Post Analytics," "fill in views and likes for my posts," or when backfilling
  missing Views/Likes/Comments/Shares on published posts. Also the engine behind
  the recurring Friday 4pm Pacific scheduled task. For each published LinkedIn
  post in the target week it reads impressions, reactions, comments, and reposts
  from LinkedIn and writes them to the matching Notion row. Does NOT write
  content, schedule posts, or analyze performance narratively — it just moves the
  numbers.
---

# LinkedIn Weekly Analytics → Notion

## What this does (the outcome)

For every LinkedIn post Danoosh published in a target week, fill in the numeric
columns of his Notion **Published Post Analytics** database so the row is
complete: **Views** (LinkedIn impressions), **Likes** (reactions), **Comments**,
**Shares** (reposts), the post **Link**, and a confirmed **Publish Date**.

The derived columns — **Analytics**, **Engagement**, **Likes/Views**,
**Comments/Views** — are Notion formulas. They recalculate on their own the
moment the raw numbers land. Never try to set them; they are read-only.

This is a data-moving task, not a judgment task. Success = every published post
in the week has accurate numbers. Re-running is safe and idempotent: it just
overwrites the fields with a fresh read.

## Fixed locations (don't rediscover these)

- **Notion database:** "View of All Content [DKC]" — the Published Post
  Analytics view is a filter on it.
  - Data source URL (for SQL queries): `collection://e0b21b86-c247-8266-9c2f-07d6ee122983`
  - The Published Post Analytics view keeps Status = `Published` or `✅ Published`.
- **LinkedIn creator analytics:** `https://www.linkedin.com/analytics/creator/content/`
  (Me → Analytics → Content analytics). Per-post detail lives at
  `https://www.linkedin.com/analytics/post-summary/urn:li:activity:<id>/`.

## The five steps

### 1 — Determine the target week (Monday–Sunday, Pacific)

Default scope is the **current Monday–Sunday week in Pacific time** — the Mon–Sun
window that contains the day the task runs. Compute it explicitly with a shell
command so you don't fencepost it:

```bash
TZ=America/Los_Angeles date +%Y-%m-%d   # today, Pacific
# Monday of this week and the following Sunday:
python3 - <<'PY'
import datetime, zoneinfo
now = datetime.datetime.now(zoneinfo.ZoneInfo("America/Los_Angeles")).date()
mon = now - datetime.timedelta(days=now.weekday())
sun = mon + datetime.timedelta(days=6)
print(mon.isoformat(), sun.isoformat())
PY
```

If Danoosh names a different window ("last week," "the week of the 10th," "just
backfill anything missing"), honor that instead. For "anything missing," drop the
date filter and instead select rows where the numbers are blank (see the query
note below).

### 2 — Find that week's published LinkedIn posts in Notion

Query the data source directly. Filter on **Status + Platforms**, NOT Channel —
Channel is frequently blank on real rows, so a Channel filter silently drops
posts. Both LinkedIn platform options begin with `LI`, so match on that.

```sql
SELECT "Name",
       "date:Publish Date:start" AS publish,
       "Platforms", "Views", "Likes", "Comments", "Shares",
       "Link", "Post URL", url
FROM   "collection://e0b21b86-c247-8266-9c2f-07d6ee122983"
WHERE  "Status" IN ('Published', '✅ Published')
  AND  ("Platforms" LIKE '%LI-PAGE%' OR "Platforms" LIKE '%LI@%')
  AND  date("date:Publish Date:start") >= date(:week_start)
  AND  date("date:Publish Date:start") <= date(:week_end)
ORDER BY publish DESC
```

`url` is the Notion page ID you'll update in step 5. `Name` is usually the post's
opening line (the hook), which is how you'll match it to the LinkedIn post.

For the "anything missing" variant, replace the two date lines with
`AND ("Views" IS NULL OR "Views" = 0)`.

If the query returns zero rows, the week has no published LinkedIn posts. Say so
plainly and stop — that's a valid, complete outcome, not a failure.

### 3 — Read each post's numbers from LinkedIn (browser)

This step needs Danoosh's authenticated LinkedIn session, so it runs through the
Claude-in-Chrome bridge against his logged-in browser. **First confirm the bridge
is reachable** (e.g. `tabs_context_mcp` / `list_connected_browsers`). If it is
not, do NOT fail — jump to the Fallback section.

Prefer reading text over clicking pixels: use `navigate` + `get_page_text` /
`read_page` and pull the numbers from the page content. LinkedIn's DOM shifts
often, so adapt to what the page actually says rather than hunting fixed
coordinates.

For each post you need four numbers plus the permalink:

- **Impressions** → these live only in the analytics view. Open the post's
  analytics detail (`/analytics/post-summary/urn:li:activity:<id>/`) or the
  Content analytics list (set the range to **Past 7 days**), which lists each
  recent post with its impressions.
- **Reactions, Comments, Reposts** → these are on the post itself, in the social
  action bar. Open the post permalink and read the counts.
- **Permalink** → the post's own URL (`/feed/update/urn:li:activity:<id>/` or
  `/posts/...`). Capture it for the Notion **Link** field.

A reliable path: from Content analytics (Past 7 days) collect the list of this
week's posts and their impressions and activity IDs; then for each, open the
post to read reactions/comments/reposts and grab the permalink.

### 4 — Match each LinkedIn post to its Notion row

Match in this order of confidence:

1. **Link / Post URL already in the Notion row** — if present, match by the
   activity ID in the URL. Most reliable.
2. **Opening text** — compare the LinkedIn post's first line to the Notion
   **Name**. They usually match closely (Name is the hook).
3. **Publish date** — as a tiebreaker, the LinkedIn post date should equal the
   row's Publish Date.

If a LinkedIn post has no confident Notion match, don't guess — list it in the
recap as unmatched so Danoosh can sort it out. If a Notion row has no matching
LinkedIn post (e.g. deleted post), leave it and note it.

### 5 — Write the numbers back to Notion

Update each matched row with `notion-update-page`, `command: "update_properties"`,
`page_id` = the row's `url` from step 2. Field mapping:

| LinkedIn value        | Notion property         | Format |
|-----------------------|-------------------------|--------|
| Impressions           | `Views`                 | number |
| Reactions             | `Likes`                 | number |
| Comments              | `Comments`              | number |
| Reposts               | `Shares`                | number |
| Post permalink        | `Link`                  | url string |
| Post publish date     | `date:Publish Date:start` + `date:Publish Date:is_datetime` = 0 | ISO date |

Example properties payload:

```json
{
  "Views": 216,
  "Likes": 19,
  "Comments": 4,
  "Shares": 0,
  "Link": "https://www.linkedin.com/feed/update/urn:li:activity:7483871757003685890/"
}
```

**Platforms:** if the row already has a Platforms value, leave it alone. If it's
empty, set it from where the post lives: a personal-profile post →
`["LI@danooshk"]`; a company-page post → `["LI-PAGE@danoosh-kapadia-consulting"]`.

**Publish Date:** only set it if the row's date is missing or clearly wrong.
Don't overwrite a correct existing date.

Do not send values for Analytics, Engagement, Likes/Views, or Comments/Views —
those are formulas and will error or be ignored.

## Fallback: browser not reachable

The Friday run happens in the cloud. If Danoosh's Claude desktop app isn't
connected at that moment, the Chrome bridge won't be there and LinkedIn's private
impression data can't be read (LinkedIn only shows it to his logged-in session).

When that happens, do the half you *can* do and hand off cleanly rather than
failing silently:

1. Still run steps 1–2 so you know exactly which posts need numbers this week.
2. In the completion recap, list those posts (Name + Publish Date + Notion link)
   and the four fields each still needs.
3. Tell Danoosh he can finish it in seconds by opening this session on his
   computer (or replying while the desktop app is open) so the browser is
   reachable, and you'll fill everything in.

This keeps the weekly rhythm intact even on a week the automation can't complete
on its own.

## Recap format

Close every run with a short, skimmable recap — Danoosh has ADHD, so lead with
what changed and keep it tight:

- Week covered (the Mon–Sun dates).
- Each post updated: short title → Views / Likes / Comments / Shares.
- Anything left open: unmatched posts, rows still missing numbers, or the
  browser-unreachable handoff.

Keep it to a few lines per post at most. No preamble.

## Gotchas worth remembering

- **Filter on Platforms, not Channel.** Channel is often null; Platforms is the
  dependable LinkedIn signal.
- **Impressions ≠ a count on the post.** Views/impressions live only in the
  analytics surface; reactions/comments/reposts live on the post. You need both
  surfaces.
- **Formulas recalc themselves.** Once raw numbers are in, Analytics and
  Engagement update automatically. Nothing to do there.
- **Idempotent by design.** Safe to re-run any time; it refreshes the numbers.
- **Zero is a real value.** 0 reposts means write `0`, not blank.

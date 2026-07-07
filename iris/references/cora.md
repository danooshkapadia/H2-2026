# Cora — the email layer (Iris's counterpart)

Cora is Danoosh's AI email assistant (cora.computer). Division of labor:
- **Cora rolls up all non-critical email** into briefs and handles inbox triage/archiving. Her 3-version auto-drafter is OFF.
- **Iris reads Cora's roll-up instead of trawling the inbox**, drafts ONE voice-calibrated reply per important thread, and never sends.
- The CLI is installed at ~/.local/bin/cora and authenticated as hello@danooshkapadia.com. Always export PATH="$HOME/.local/bin:$PATH" first.

Iris's go-to commands:
- `cora brief show --json` — latest roll-up of non-critical email (read this every morning instead of scanning everything)
- `cora email glimpse` — what's actually in the inbox now
- `cora email context <id>` — sender history + Danoosh's real past replies: USE THIS to calibrate voice before drafting
- `cora email reply-draft <id> --body "..."` — create the Gmail draft (never `reply` without --draft, never `send`)
- `cora email search "query" --include-archived` — find newsletters Cora archived
- `cora email sent --since 24h` — EOD sweep of what actually went out
- `cora todo list --format json` — todos Cora captured; reconcile into Notion, don't double-track

Full CLI reference (from cora prime):


# Cora CLI - Agent Instructions

You are interacting with Cora, an AI-powered email assistant. Most tasks have
fast, dedicated commands. Prefer these over `cora chat send` which is SLOW (10-60s).

## Quick Reference (use these INSTEAD of chat send)

| Task                  | Fast Command                         | Don't Use                                    |
|-----------------------|--------------------------------------|----------------------------------------------|
| Check inbox           | `cora email glimpse`                 | `cora chat send "show my inbox"`             |
| Search emails         | `cora email search "query"`          | `cora chat send "find emails from..."`       |
| Archive emails        | `cora email archive <id>`            | `cora chat send "archive email..."`          |
| Read an email         | `cora email show <id>`               | `cora chat send "show me email..."`          |
| Read several emails   | `cora email show <id> <id> <id>`     | one `show` call per email                    |
| Read a whole thread   | `cora email thread <thread-id>`      | repeated `show` calls                        |
| Decide next action    | `cora email context <id>`            | guessing what the user usually does          |
| Watch for changes     | `cora email delta --cursor <c>`      | re-running searches to detect changes        |
| Verify a send         | `cora email sent --since 2h`         | guessing whether a batch went out            |
| Manage labels         | `cora email label <id> --add X`      | `cora chat send "label this..."`             |
| Unsubscribe           | `cora email unsubscribe <id>`        | `cora chat send "unsubscribe from..."`       |
| Return to inbox       | `cora email inbox <id>`              | `cora chat send "move back to inbox"`        |
| Find recipients       | `cora email contacts "ali"`          | `cora chat send "who can I email..."`        |
| Follow instructions   | `cora instruction list --format json`| `cora chat send "what should I do next"`     |
| Create a todo         | `cora todo create "title"`           | `cora chat send "create a todo..."`          |
| List todos            | `cora todo list`                     | `cora chat send "what are my todos"`         |
| Read latest brief     | `cora brief show`                    | `cora chat send "show my brief"`             |
| Bulk cleanup inbox    | `cora inbox zero --execute`          | `cora chat send "clean up my inbox"`         |
| Analyze inbox         | `cora inbox analyze`                 | `cora chat send "who sends me most email"`   |
| Spot rule candidates  | `cora inbox analyze --dispositions`  | guessing which senders the user ignores      |
| Send a reply          | `cora email reply <id> --body "..."` | `cora chat send "reply to..."`               |
| Forward email         | `cora email forward <id> --to a@b.com --body "..."` | `cora chat send "forward..."`       |
| Send a draft          | `cora email send <id>`               | `cora chat send "send draft..."`             |
| Inspect attachments   | `cora email attachments <id>`        | `cora chat send "download attachment..."`    |
| Inspect calendar invite | `cora email calendar-invite <id>`   | `cora chat send "what is this invite..."`    |
| Queue a reply draft   | `cora email draft <id>` / `cora email reply-draft <id>` | `cora chat send "draft a reply to..."` |
| Complex/ambiguous     | `cora chat send "..."`               | N/A - this IS the right tool here            |

## Command Speed Tiers

### Instant Commands (no AI, returns immediately)

These are your primary tools. They execute server-side logic directly with no LLM.

**Email:**
- `cora email glimpse [query]` - Quick inbox view with metadata (cached, fast)
- `cora email search "query"` - Search with Gmail query syntax (add `--include-archived` to also see mail Cora archived)
- `cora email show <id...>` - Full email details; accepts multiple IDs for batch reads (`--max-chars` bounds each body)
- `cora email thread <thread-id-or-email-id>` - Read a whole thread: every message plus Cora state (draft, instructions, status). `--full` hydrates mirror-only messages
- `cora email context <id...>` - Behavioral priors for an email: sender outcome history (replied/archived/forwarded), similar past emails with the user's actual replies, matching rules. Raw derived signal — use it to decide the next best action and to draft in the user's voice (`--sections`, `--max-chars`, `--no-embed`)
- `cora email delta [--cursor <c>]` - Incremental change feed. Without a cursor it returns a checkpoint; with one it returns everything that changed since (`--format jsonl` for line-oriented output)
- `cora email sent [--since 2h]` - Recently sent emails with their send receipts
- `cora email send-status --idempotency-key <key>` - Verify whether a specific direct send completed
- `cora email labels` - List Gmail labels on the connected account
- `cora email label <id...> --add <name> --remove <name>` - Add/remove labels (names or label IDs)
- `cora email contacts [query]` - Find recent/prefix-matched recipient contacts
- `cora email archive <id...>` - Archive emails (also: `--query`, `--all`, `--all --except`)
- `cora email inbox <id...>` - Return emails to inbox
- `cora email reply <id> --body "..."` - Direct-send a plain-text reply
- `cora email reply <id> --body "..." --attach ./file.pdf` - Direct-send a reply with attachments
- `cora email reply <id> --body "..." --draft` - Create a Gmail reply draft
- `cora email reply-draft <id> --body "..."` - Create a Gmail reply draft
- `cora email compose someone@example.com --subject "..." --body "..." --send` - Direct-send a new email
- `cora email compose someone@example.com --subject "..." --body "..." --attach ./file.pdf` - Create a draft with attachments
- `cora email forward <id> --to someone@example.com --body "..."` - Create a forward draft with original attachments preserved on send
- `cora email forward <id> --to someone@example.com --attach ./extra.pdf` - Forward and add new attachments
- `cora email send <id>` - Send a compose, reply, or forward draft
- `cora email edit <id> --body "..."` - Replace an existing draft body
- `cora email discard-draft <id>` - Delete an existing Gmail draft and local draft state
- `cora email attachments <id>` - List downloadable attachments
- `cora email download-attachment <id> <index> --output ./file` - Download one attachment
- `cora email calendar-invite <id>` - Show invite details before responding
- `cora email rsvp <id> accepted` - Respond to calendar invites (`accepted`, `declined`, `tentative`)
- `cora email snooze <id...> --until "2026-05-05 09:00"` - Snooze emails
- `cora email star <id...>` / `unstar <id...>` - Toggle stars
- `cora email mark-read <id...>` / `mark-unread <id...>` - Toggle unread state
- `cora email unsubscribe <id>` - Create unsubscribe rule from sender (also: `--query`)

**Todos:**
- `cora todo list` - List pending todos (flags: `--all`, `--completed`, `--priority`, `--due`)
- `cora todo show <id>` - View todo details
- `cora todo create "Title"` - Create todo (flags: `--priority`, `--due`, `--description`)
- `cora todo edit <id>` - Update todo (flags: `--title`, `--priority`, `--due`, `--description`)
- `cora todo complete <id...>` / `uncomplete <id...>` / `delete <id...>`

**Instructions (the approval bus between Cora's UI and external agents):**
- `cora instruction list --format json` - List active email instructions for agent follow-up
- `cora instruction list --email <id> --format json` - Filter instructions to one email
- `cora instruction list --wait --timeout 30 --format json` - Long-poll: blocks until new instructions appear (or times out with an empty list; re-issue in a loop for longer watches)
- `cora instruction create <email-id> "Instruction"` - Persist an instruction on an email
- `cora instruction create "Instruction" --thread <thread-id>` - Attach to the newest email in a thread
- `cora instruction resolve <instruction-id>` / `delete <instruction-id>` - Complete or remove an instruction

**Briefs:**
- `cora brief` - List recent briefs (flag: `--limit`, `--json`)
- `cora brief show [id]` - Show brief details (flag: `--open`, `--json`)
- `cora brief read <id>` / `unread <id>` - Mark read status
- Note: Brief commands use `--json` (not `--format json`)

**Inbox:**
- `cora inbox zero` - Classify inbox and show archive plan (flag: `--execute`, `--force`)
- `cora inbox analyze` - Top senders by volume (flag: `--min-count`). Add `--dispositions` for a derived reply/archive outcome split per sender — evidence for proposing classification rules (the user approves; never auto-create)

**Account:**
- `cora whoami` - Current user and account
- `cora status` - Account status, brief settings, usage stats
- `cora account list` - List available accounts
- `cora account switch "Name or email"` - Switch active account (persistent)

**Categories & Rules:**
- `cora category list` / `create` / `edit` / `delete`
- `cora rule list` / `create` / `delete`

**Skills:**
- `cora skill list` / `show` / `create` / `edit` / `delete`

**MCP Servers:**
- `cora mcp list` / `show` / `add` / `edit` / `delete --force` / `enable` / `disable`

**Utility:**
- `cora open` - Open dashboard in browser
- `cora prime` - Show these instructions

### Background Commands (queues AI work, returns immediately)

- `cora email draft <id> --context "..."` - Queues reply draft generation in background.
  Returns immediately with confirmation. The draft is generated asynchronously.
- `cora email reply-draft <id> --body "..."` - Creates a Gmail reply draft without sending.

### AI-Powered Commands (SLOW - full LLM conversation, 10-60s+)

Use these ONLY when no instant command fits your need.

- `cora chat send "message"` - Invokes AI assistant with 27+ tools. Takes 10-60s.
  Use for ambiguous, multi-step, or complex requests that need AI reasoning.
  Flags: `--chat <id>` (continue conversation), `--new` (force new), `--no-stream` (batch mode)
- `cora chat list` / `show <id>` / `delete <id>` - Manage chats (these are instant)

## Authentication

Get an API token at https://cora.computer/api_tokens (Settings -> Agents in the Cora web app).

1. **Environment variable (recommended for agents — no login step needed):**
   ```
   export CORA_API_TOKEN=token_xxx
   cora email glimpse   # every command authenticates per-call with the env var
   ```
   This works without any session and keeps working after session expiry.

2. **Persistent session:**
   ```
   cora login --token=token_xxx
   ```
   Sessions last 30 days; with CORA_API_TOKEN set you never depend on them.

3. **Interactive login:**
   ```
   cora login
   ```
   (Follow the prompts to enter your token)

When logged out, commands exit with code 2 and (in `--format json`) print a
structured error to stderr that includes `error.remediation.token_url`.

Replies are structurally bound to the right account: `cora email reply <id>`
always sends from the account that received the email — an agent cannot
reply from the wrong address.

## Global Options

All commands accept these flags:
- `--account "Name or email"` - Override the active account for this command only (no session change)
- `--format json` - Machine-readable JSON output (supported on most commands)
- `--quiet` / `-q` - Suppress non-essential output

Note: Brief commands use `--json` instead of `--format json`.
For local development, set `TERMINALWIRE_URL=ws://localhost:<port>/terminal`
when Rails is not running on the CLI default port.
Use `cora help <command>` and `cora email help <command>` for server-side help.

## Email Command Conventions

IDs:
- Use the `id` value returned by `cora email glimpse --format json`, `search --format json`, or `show --format json`.
- Email commands also accept Gmail message IDs when Cora has mirrored that email.

Body modes:
- `--body "Line 1\n\nLine 2"` is plain text. Cora escapes HTML-like text and preserves line breaks for Gmail rendering.
- `--body-markdown "**Thanks**"` renders Markdown, then sanitizes it.
- `--body-html "<p>Thanks</p>"` accepts sanitized HTML. Use this only when you intentionally want HTML.
- `--body-file ./message.txt` reads plain text from a file.

Attachments:
- Use repeated `--attach ./path` flags on `compose`, `reply`, `reply-draft`, and `forward`.
- Gmail allows ZIP files, but Cora rejects Gmail-blocked file types, blocked files inside ZIPs, password-protected ZIPs, and total attachments over 25 MB.
- For inbound attachments, run `cora email attachments <id> --format json`, then `cora email download-attachment <id> <index> --output ./path`.

Draft lifecycle:
- `compose`, `reply --draft`, `reply-draft`, and `forward` return a draft ID plus `send_command` in JSON.
- Send any saved draft with `cora email send <id> --format json`.
- Discard a saved draft with `cora email discard-draft <id> --format json`.
- For direct sends, pass `--idempotency-key <stable-key>` so a retry cannot send duplicates.

Replying twice:
- `cora email reply` on an email you already replied to exits with `already_replied`.
  Pass `--followup` to deliberately send another reply on the same thread.

Send receipts (verify what actually went out):
- Every successful send returns `status`, `gmail_id`, `thread_id`, `sent_gmail_id`, `sent_at`, `account`, and `idempotency_key` in JSON.
- `cora email send-status --idempotency-key <key> --format json` answers "did that send complete?" after a timeout or crash.
- `cora email sent --since 2h --format json` answers "did that batch actually send?".

Checkpoint -> delta loop (the efficient way to watch an inbox):
1. `cora email delta --format json` once — store the returned `cursor`.
2. Periodically: `cora email delta --cursor <stored> --format jsonl` — one JSON
   object per changed email, then a `{"type":"cursor",...}` line. Store the new cursor.
3. React to events (new mail, status flips, drafts appearing) instead of re-searching.
The feed is served from Cora's local mirror, which Gmail push notifications keep
fresh to within seconds.

Thread reads:
- `cora email thread <id> --format json` accepts a Gmail thread ID or any email ID.
- EPS-backed messages include body, status badge, draft (+ `send_command`), and instructions.
- Messages Cora never processed appear as `mirror_only` stubs; re-run with `--full` to hydrate them.

Calendar invites:
- Run `cora email calendar-invite <id> --format json` before RSVP if you need the time, location, organizer, or attendee details.
- Then run `cora email rsvp <id> accepted|declined|tentative --format json`.

## Best Practices for Agents

### DO:
- Always use instant commands first - only fall back to `chat send` for complex/ambiguous tasks
- Use `--format json` (or `--json` for briefs) for machine-readable output
- Parse JSON responses as JSON; table output is for humans
- Use `cora email thread` for thread reads and `cora email show <id> <id>` for batch reads
- Use the checkpoint -> `cora email delta` loop instead of polling with searches
- Verify sends with the returned receipt, `send-status`, or `sent --since`
- Check authentication first with `cora whoami`
- Use `cora account list --format json` to discover available accounts
- Use `--account "Name"` flag for one-off commands targeting a specific account
- Use `cora account switch` when targeting the same account for multiple commands
- Use `cora status` to understand the user's current state
- Use environment variable auth (CORA_API_TOKEN) for stateless operation
- Use plain `--body` by default; reach for `--body-markdown` or `--body-html` only when formatting is intentional
- Use `--idempotency-key` for direct-send `compose --send` and `reply` retries
- Use `attachments` and `download-attachment` for files instead of asking chat to fetch them
- Use `cora email help compose` instead of `cora email compose --help` for subcommand help

### DON'T:
- Don't use `cora chat send` for tasks that have dedicated instant commands
- Don't pass HTML in `--body`; use `--body-html` so the intent is explicit
- Don't send blocked attachment types (`.exe`, `.js`, `.vbs`, `.dmg`, and similar) or password-protected ZIPs
- Don't assume authentication state - always verify with `cora whoami`
- Don't assume the active account - use `cora account list` to check
- Don't run commands in rapid succession - wait for each to complete
- Don't retry failed commands more than once without user guidance

## OpenClaw Integration

If you're an OpenClaw agent, register yourself with Cora to enable proxied chat:
  `cora openclaw guide` — Full step-by-step registration instructions
  `cora openclaw add` — Register your gateway
  `cora openclaw test "<name>"` — Verify connectivity
  `cora chat send "Hello" --agent "<name>"` — Chat through your gateway

## Error Handling

Exit codes:
- 0: Success
- 1: General error
- 2: Authentication required (run `cora login`)
- 3: Resource not found
- 4: Validation error



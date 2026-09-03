# Guided Setup Checklists

1-2 working sessions with the team lead, 60 minutes each.

---

## ChatGPT Business (formerly Team) Setup

### Before the session
- [ ] Confirm ChatGPT Business subscription is active
- [ ] Confirm seat count matches cohort (up to 15 + sponsor + team lead + Danoosh)
- [ ] Pricing: $25/seat/month annual, $30/seat/month monthly
- [ ] Get admin access confirmation from team lead
- [ ] Have context file draft ready

### Workspace configuration
- [ ] Workspace name set
- [ ] Logo uploaded (optional)
- [ ] Default seat type = standard ChatGPT (not Codex)

### User provisioning
- [ ] All participants invited (bulk CSV: email,role,seat type)
- [ ] Invitations accepted / accounts created
- [ ] Verify all can log in at chatgpt.com

### Roles
- [ ] Sponsor = Owner
- [ ] Team lead = Admin
- [ ] Danoosh = Admin (temporary)
- [ ] All participants = Member

### Data controls
- [ ] Business plan = data excluded from training by default (no toggle needed)
- [ ] Verify workspace is on Business plan, not individual Plus
- [ ] No BAA available on Business — client owns HIPAA/compliance

### M365 app connections (if applicable)
**Step 1 — Microsoft Entra ID (admin-side):**
- [ ] Identify who has Entra admin access
- [ ] Approve ChatGPT app scopes for: Outlook Email, Outlook Calendar, SharePoint, Teams
- [ ] Each app has its own scopes requiring approval

**Step 2 — ChatGPT workspace (admin-side):**
- [ ] Go to Workspace Settings > Apps
- [ ] Enable each Microsoft app
- [ ] Set action control (recommend read-only to start)

**Step 3 — Individual users (self-serve):**
- [ ] Each user: Settings > Apps > connect Microsoft account via OAuth
- [ ] Must be done person-by-person (no admin bulk connect on Business)
- [ ] Plan a 5-min walkthrough at Session 01 or send instructions before

### Context file
- [ ] Built from brand/onboarding materials
- [ ] Loaded into workspace custom instructions
- [ ] Tested: new chat returns context-aware responses

### Verification
- [ ] Team lead can use ChatGPT with context
- [ ] One participant tested
- [ ] Team lead comfortable in admin panel

---

## Microsoft Copilot Setup

### Before the session
- [ ] Confirm all participants have M365 Copilot licenses ($30/user/month add-on)
- [ ] Confirm full Copilot (Word, Excel, PPT, Outlook, Teams), not just Copilot Chat
- [ ] Identify IT contact for access issues

### License verification
- [ ] Each participant: open Word/Excel/Outlook, confirm Copilot icon present
- [ ] Flag missing licenses to IT immediately
- [ ] Test basic prompt in Word

### SharePoint / OneDrive
- [ ] Copilot can access relevant SharePoint sites
- [ ] Copilot can access OneDrive files
- [ ] Test: "Summarize the document at [URL]"

### Data governance
- [ ] Review which SharePoint sites Copilot can access
- [ ] Confirm restricted areas are fenced
- [ ] Review sensitivity labels if in use

### Teams integration
- [ ] Copilot enabled in Teams meetings
- [ ] Meeting recap tested
- [ ] Sprint channel created, all participants added

### Scope boundary
Technical issues beyond workspace configuration (SharePoint policies, network restrictions, SSO) are outside Sprint scope. Flag and recommend client's IT team.

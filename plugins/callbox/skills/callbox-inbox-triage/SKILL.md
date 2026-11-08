---
name: callbox-inbox-triage
description: >
  File the recordings in the Callbox Inbox (no project) into the right
  projects, and propose routing rules so the next calls file themselves. Use
  when the user asks to clean up, sort or triage their Callbox Inbox, or when
  get_overview shows recordings in the Inbox.
---

# Inbox triage

1. `list_recordings` with `inbox: true`, and `list_projects` (with their
   rules from `get_project` when needed).
2. For each recording, pick a project from its participants' domains and
   emails, and its title. When nothing fits, leave it: never guess.
3. Show the user the plan in one list: recording (title, date) → project,
   and the rules you propose (`acme.com` → ACME). Ask once for approval.
4. On approval: `move_recording` for each, then `add_project_rule` for each
   new rule. A rule must be a company domain or one email: public domains
   (gmail.com, outlook.com...) and the user's own addresses are refused.
   Rules, and moves into a team's project, need the "Route calls"
   permission (`callbox.routing`): on `[insufficient_scope]`, tell the user
   to tick it in Callbox's Settings → Connected agents.
   Rules file only Meet calls with a matching Calendar event, and only with
   Calendar routing on: if `get_overview` shows it off, tell the user rules
   do nothing until it is on (`update_settings`, after they grant Calendar
   access in the web app).
5. Report what moved, what stayed in the Inbox and why, and the rules added.

New clients: propose `create_project` with the company's name, then move
their recordings there.

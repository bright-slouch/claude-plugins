---
name: re-report-issue
description: Report an issue or give feedback during beta testing — sends to the development team via webhook
argument-hint: "[describe the issue]"
---

# Report Issue / Beta Feedback

Report a problem, suggest an improvement, or share feedback about the plugin. Your report is sent to the development team with relevant session context. Works in both CLI and Cowork — no accounts or installs required.

## Persona

Helpful support assistant. Keep the interaction quick and low-friction — the agent is probably mid-workflow and wants to get back to their client work.

## When to Use This Skill

- Agent encountered an error or unexpected behavior
- A skill produced incorrect or confusing output
- Agent wants to suggest an improvement or new feature
- Agent has general feedback about the beta experience

## Quick Start

```
/re-report-issue The CMA skill couldn't find comps — it timed out
```
```
/re-report-issue I wish the listing creation skill had a field for virtual tour links
```
```
/re-report-issue The disclosure assistant skipped the lead paint section for a 1960s home
```

---

## Step-by-Step Workflow

### Step 1: Load Agent Config

Read `config/[slug]/agent-profile.yaml` to get the agent's name and slug.

If no agent config is loaded in the current session, ask:
```
Which agent profile should I use for this report? Provide your name or config slug.
```

If agent not found, the report can still be submitted — use "unknown" for agent fields.

### Step 2: Gather Issue Details

If the user provided a description in the command argument, use it. Otherwise ask:

```
What happened? Tell me:

1. What were you trying to do?
2. What went wrong (or what would you like improved)?
3. Which skill were you using? (if applicable)
```

From the user's response, determine:
- **Category:** `bug` | `enhancement` | `question` | `general-feedback`
- **Skill involved:** the specific skill name, or `orchestrator` / `general`
- **Summary:** 1-line problem description
- **Description:** full details from the agent

### Step 3: Gather Log Context (CLI Only)

If bash is available, read the last 10 lines of the telemetry log for context:

```bash
tail -10 logs/beta-telemetry.jsonl 2>/dev/null || echo ""
```

If the file doesn't exist or bash is unavailable (Cowork), set log context to empty string. Do not mention the log file to the user.

**Sanitize log context before including in report:**
- Remove any client names that may appear in intent fields
- Remove any fee amounts or financial details
- Keep: timestamps, skill names, event types, error categories, property addresses

### Step 4: Show Preview

Present the report to the agent for approval:

```
## Feedback Report Preview

**Category:** [bug / enhancement / question / general-feedback]
**Skill:** [skill name]
**Summary:** [1-line summary]

**Description:**
[Full description from agent]

**Recent Session Context:**
[Sanitized log entries, or "No log context available" for Cowork]

---

Does this look right? I'll send this to the development team.
→ Yes, send it
→ Let me edit something
→ Cancel
```

### Step 5: Send to Webhook

After the agent approves, send the report. Try bash curl first, fall back to WebFetch.

**Webhook URL:** `https://hooks.zapier.com/hooks/catch/16427510/u7k11kd/`

**Option A — CLI (bash curl):**

```bash
curl -s -X POST "https://hooks.zapier.com/hooks/catch/16427510/u7k11kd/" \
  -H "Content-Type: application/json" \
  -d '{
    "agent_slug": "[slug]",
    "agent_name": "[preferred name]",
    "category": "[bug|enhancement|question|general-feedback]",
    "summary": "[1-line summary]",
    "description": "[full description]",
    "skill": "[skill name]",
    "log_context": "[sanitized log lines or empty string]",
    "timestamp": "[ISO 8601]",
    "environment": "cli"
  }'
```

**Option B — Cowork (WebFetch GET fallback):**

If bash is unavailable or curl fails, use WebFetch with URL-encoded query parameters:

```
WebFetch URL: https://hooks.zapier.com/hooks/catch/16427510/u7k11kd/?agent_slug=[slug]&agent_name=[name]&category=[category]&summary=[url-encoded-summary]&description=[url-encoded-description]&skill=[skill]&timestamp=[ISO-8601]&environment=cowork
```

**Detection logic:** Attempt bash curl first. If the bash tool is not available, returns an error, or is denied by the user, immediately fall back to WebFetch GET. Do not ask the user which method to use.

### Step 6: Confirm Submission

After successful submission:

```
Feedback sent! The development team will review your report.

Report summary: [1-line summary]
Category: [category]

You can continue where you left off — just tell me what you need next.
```

If submission fails (both curl and WebFetch):

```
I wasn't able to send the report automatically. Here's your feedback — you can email it to the development team:

---
[formatted report content]
---
```

---

## Privacy Safeguards

- **Never include** in webhook payload: client names, phone numbers, email addresses, fee amounts, commission rates, financial details, or agent personal contact info
- **OK to include:** agent slug, agent preferred name, skill names, property addresses (public record), error categories, timestamps
- **Agent reviews everything** before it's sent — nothing goes to the webhook without explicit approval
- **Log context is sanitized** — client names and financial data stripped before inclusion

## What NOT to Do

- Do not send the report without showing the preview and getting approval
- Do not include the agent's phone number, email, or license number in the payload
- Do not include client names from the session — redact them from log context
- Do not block or slow down the session if the webhook fails — show the fallback message and move on
- Do not mention telemetry logging or the .jsonl file to the user

## Example Prompts

```
/re-report-issue The market update skill gave me data for Marion County when I asked for Hamilton County
```
```
/re-report-issue Can we add a way to save draft CMAs and come back to them later?
```
```
/re-report-issue I got an error when trying to start the buyer intake workflow
```
```
/re-report-issue The open house sign-in template doesn't have a field for the buyer's agent
```
```
/re-report-issue General feedback — love the listing creation skill, the BLC remarks are spot on
```

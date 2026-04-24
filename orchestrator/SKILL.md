---
name: orchestrator
description: >-
  Entry point for the Central Indiana Real Estate Agent Plugin. Routes to
  the right skill, coordinates multi-skill workflows, identifies agents, and
  tracks transaction state. Use when starting any real estate workflow or
  when unsure which skill to invoke. The orchestrator runs as an agent
  with persistent memory and can preload all 18 skills.
argument-hint: "[agent name OR workflow name OR describe what you need]"
---

# orchestrator — Plugin Entry Point

## Overview

The orchestrator is the command center for the Central Indiana Real Estate Agent Plugin. It is available as an **agent** (not a skill) — see `agents/orchestrator.md` for the full logic.

**Claude will suggest the orchestrator automatically** when you mention a new client, property, or deal. You can also invoke it directly.

---

## How to Invoke

```
Start the orchestrator for [Agent Name or slug]
```
```
I'm working as [Agent Name] — help me [describe task]
```

The orchestrator will:
1. Identify the active agent from the local slug-based config (matches name/email against existing `config/*/agent-profile.yaml` files)
2. Assess active transaction state
3. Route to the right skill or guided workflow

---

## Guided Workflows Available

| Workflow | Skills Involved |
|---|---|
| **New Listing Setup** | re-seller-consultation → re-cma → re-listing-prep → re-disclosure-assistant → re-listing-creation → re-property-marketing → re-showing-coordinator → re-open-house |
| **New Buyer Intake** | re-buyer-consultation → re-neighborhood-research → re-showing-coordinator → re-offer-writer → re-negotiation-advisor → re-transaction-manager → re-closing-coordinator |
| **Offer Management** | re-offer-writer → re-negotiation-advisor (iterative) |
| **Contract to Close** | re-transaction-manager → re-negotiation-advisor (if needed) → re-closing-coordinator |
| **Morning Briefing** | re-news-briefing → re-market-update (optional) |

---

## All Available Skills

| Skill | When to Use |
|---|---|
| re-agent-setup | Onboard a new agent — creates all 7 local YAML config files at `config/[slug]/` |
| re-disclosure-assistant | Indiana disclosure compliance (IC 32-21-5-10) |
| re-client-communication | Draft emails, texts, call scripts for any stage |
| re-neighborhood-research | School, tax, commute, amenities report for buyers |
| re-market-update | Median price, DOM, inventory, absorption rate snapshot |
| re-news-briefing | Today's Indiana real estate news (IBJ + Google News) |
| re-seller-consultation | Listing appointment prep and seller presentation |
| re-cma | Comparative market analysis, pricing strategy, net sheet |
| re-listing-prep | Staging, ROI-ranked repairs, photography shot list |
| re-listing-creation | BLC remarks (500-char), marketing description, fair housing check |
| re-property-marketing | Social series, email blast, print flyer, video scripts |
| re-showing-coordinator | ShowingTime setup, feedback templates, buyer comparison worksheets |
| re-open-house | Promotion, sign-in, conversation starters, follow-up sequence |
| re-buyer-consultation | Needs discovery, agency explanation, buyer presentation |
| re-offer-writer | Write buyer offers or review/compare seller-side offers |
| re-negotiation-advisor | Inspection response, appraisal gap, counter-offer strategy |
| re-transaction-manager | Deadline calendar, Google Calendar events, party coordination |
| re-closing-coordinator | Clear-to-close through post-closing follow-up |

---

## Key Behaviors

- **Always identifies the active agent first** — loads config before any output
- **Confirms before invoking any skill** — you see what it will do before it does it
- **Passes data between skills** — no re-entering information from prior steps
- **Tracks session state** — ask "What are we working on?" at any point
- **Flags missing dependencies** — tells you when a prior skill's output would improve results

---

*Full orchestrator logic lives in `agents/orchestrator.md`. This file is a reference stub only.*

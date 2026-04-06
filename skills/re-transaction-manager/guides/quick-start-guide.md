# re-transaction-manager — Quick Start Guide

## What This Skill Does

`re-transaction-manager` is the post-contract command center. From the moment an offer
is accepted through clear-to-close, it:

- Computes every contract deadline from your accepted offer terms
- Creates Google Calendar events for each deadline (with reminders)
- Drafts coordination emails to lender, title, and other agent
- Generates weekly client status updates
- Handles mid-transaction issues: extensions, amendments, appraisal delays, title problems

---

## 5-Minute Setup

**Prerequisites:**
1. Agent config must be set up: `/re-agent-setup`
2. You need the fully executed purchase agreement in hand

**Invoke at contract acceptance:**
```
/re-transaction-manager new transaction setup

Property: [address]
Accepted: [date]
Close date: [date]
Inspection period: [X] calendar days
Financing contingency: [X] days
Earnest money: $[X] due [X] business days from acceptance
Buyer financing type: [Conventional / FHA / VA / Cash]
Lender: [name, phone, email]
Title: [name, phone, email]
Other agent: [name, phone, email]
Slug: [your-slug]
```

That's it. The skill generates the full deadline calendar, creates all calendar events, and
drafts your three kickoff emails.

---

## Quick Reference by Task

| Task | What to Type |
|---|---|
| New transaction setup | `/re-transaction-manager new transaction setup — [contract details]` |
| Weekly client update | `/re-transaction-manager weekly update — [property], [what happened this week]` |
| Inspection extension | `/re-transaction-manager inspection extension — [property, current deadline, new deadline needed, reason]` |
| Appraisal delay | `/re-transaction-manager appraisal delay — [property, where things stand, closing date]` |
| Financing contingency extension | `/re-transaction-manager financing extension needed — [property, current deadline, issue]` |
| Title problem discovered | `/re-transaction-manager title issue — [property, what title found]` |
| Amendment executed | `/re-transaction-manager amendment — [property, what changed]` |
| Financing fell through | `/re-transaction-manager financing fell through — [property, when contingency expired, EM amount]` |

---

## Google Calendar Integration

The skill uses `gcal_create_event` to create events automatically. Each event includes:
- Exact deadline date and time
- Who owns the action
- What happens if missed
- All relevant party contact info
- 1-day and 1-hour reminders

When deadlines change, use the amendment prompt and the skill will call `gcal_update_event`
to update the affected events automatically.

---

## Key Indiana Rules Built In

- **Inspection period = calendar days** (not business days). Day 10 falls on a Sunday? Still Day 10.
- **Contingency auto-waivers**: Inspection, financing, and appraisal contingencies auto-waive if nothing is filed before the deadline. The skill flags every contingency deadline as high priority.
- **FHA/VA loans**: timeline is built with 45-day assumption instead of 30-day. Skill flags if a shorter close is in the contract with an FHA/VA buyer.
- **Closing Disclosure**: federal TRID requires the CD to reach the buyer 3 business days before closing. Skill creates a CD delivery reminder event 4 business days before close.

---

## Handoff to re-closing-coordinator

When the lender issues "Clear to Close," hand off to:
```
/re-closing-coordinator clear to close — [property], [closing date], [agent slug]
```

`re-closing-coordinator` handles the final walkthrough, closing day prep, utility transfers,
closing document review, and the full post-closing sequence.

---

## Critical Principles

- **Never let a contingency deadline pass silently** — the skill flags every deadline 48 hours in advance
- **All amendments in writing** — every deadline change should be documented via IAR Form 157
- **Earnest money disputes need a broker** — the skill flags financing fallouts and directs agents to consult their managing broker before taking any EM action
- **Calendar events update when contracts change** — always run the amendment prompt so the calendar stays accurate

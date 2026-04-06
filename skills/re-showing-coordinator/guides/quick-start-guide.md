# Quick Start Guide — re-showing-coordinator

5-minute overview for agents on both sides of the showing process.

---

## What This Skill Does

`re-showing-coordinator` covers showings from two angles:

**Listing side** — Set up showing instructions, request and collect feedback, report activity to sellers, and analyze patterns from feedback.

**Buyer side** — Prepare buyers for tour days, compare multiple properties, and guide the decision process after showings.

---

## How to Invoke

```
/re-showing-coordinator [listing or buyer side] — [address or scenario]
```

Or in plain language:

```
Set up ShowingTime instructions for [address]
```
```
Weekly showing report for my seller at [address] — [X] showings, [Y] feedback responses
```
```
Buyer tour prep for tomorrow — [buyer names] seeing [N] homes in [city]
```
```
Help my buyers choose between two homes they both loved
```

---

## Listing Side — 3 Most Common Uses

### 1. ShowingTime Setup

Tell the skill:
- Occupancy status (owner-occupied / vacant / tenant-occupied)
- Access method (lockbox type and location)
- Notice requirement
- Showing hours
- Pet and shoe instructions
- Any special notes

The skill generates a clean instruction sheet to paste into ShowingTime and a recommendation for what to put in BLC agent remarks vs. ShowingTime private notes.

```
Set up ShowingTime for [address] — occupied, lockbox on door, 1-hour notice, no showings before 9am, dog in crate
```

### 2. Weekly Seller Report

Summarize weekly showing activity with a seller-facing report:

```
Showing report for [address] — [N] showings this week, [N] feedback received. Feedback: [summary of what agents said]
```

The skill formats a professional seller report using the `weekly-status-update.md` template, interprets the feedback themes, and — if the data supports it — recommends a conversation about price or other adjustments.

### 3. Feedback Analysis

When multiple feedback responses tell the same story:

```
Analyze feedback for [address] — 3 of 5 agents said price is high, 2 said kitchen needs updating
```

The skill identifies the pattern, rates severity, and gives the agent a script for the price-reduction or repair conversation with the seller.

---

## Buyer Side — 3 Most Common Uses

### 1. Tour Day Prep

Before a multi-property showing day:

```
Buyer tour prep for [buyer name(s)] — seeing [N] homes tomorrow. They want: [criteria]. Properties: [list addresses/details]
```

The skill generates a one-page prep sheet per property (key features aligned to buyer criteria, things to evaluate in person, questions to ask), a recommended tour order by geography, and a briefing message to send the buyers the night before.

### 2. Post-Tour Comparison

After touring multiple properties:

```
Comparison worksheet for [buyer name(s)] — they saw [N] homes. Top two are [address 1] and [address 2].
```

The skill builds a side-by-side comparison with pros, cons, a gut-reaction score prompt, and a decision framework. Includes a script for the decision conversation.

### 3. "Thinking It Over" Sequence

When buyers liked homes but haven't decided:

```
Buyer [name] saw [address] 3 days ago and still hasn't decided. Generate a follow-up sequence.
```

The skill produces a 3-touch sequence (same day, 2 days, 1 week) that's supportive without being pushy. Each touch has a clear purpose and is written in the agent's configured voice.

---

## Key Reminders

**Listing side:**
- ShowingTime codes (alarm, garage, lockbox) go in ShowingTime agent notes — NEVER in BLC public remarks
- Tenant-occupied properties require proper notice to tenants before entry (Indiana law)
- Never tell sellers feedback is positive when it isn't — accurate data leads to better decisions
- Low showing volume is a signal. The skill helps you diagnose the cause before defaulting to "price reduction"

**Buyer side:**
- Urgency should never be fabricated. Only surface it when real evidence exists (multiple offer activity, days on market moving, listing agent confirms interest)
- The comparison worksheet surfaces dealbreakers — if a buyer can't identify one pro that outweighs a dealbreaker, that house is not the right one
- For out-of-town buyers doing virtual showings, the skill helps you build a narrated walkthrough checklist so you capture everything they need to decide

---

## Legal Disclaimer

> *This output is for guidance and informational purposes only. It does not constitute legal advice. Agents should consult their managing broker and/or a licensed Indiana real estate attorney for situation-specific guidance. Always comply with Indiana Real Estate Commission rules and your brokerage's policies.*

# re-offer-writer — Quick Start Guide

## What This Skill Does

`re-offer-writer` handles both sides of every offer situation:

**Buyer side:**
- Purchase price strategy based on market conditions
- Contingency selection with plain-English explanations
- Earnest money recommendations (Indiana norms)
- Escalation clause drafting (with draft language)
- Personal letter guidance (fair housing compliant)

**Seller side:**
- Offer comparison spreadsheet (side-by-side)
- Plain-English explanation of each offer's terms
- Multiple-offer framework (highest-and-best call)
- Counteroffer drafting (ready to transfer to IAR Counter form)

---

## 5-Minute Setup

**1. Make sure your agent config is ready:**
```
/re-agent-setup
```

**2. Invoke with a clear buyer or seller context:**

Buyer:
```
/re-offer-writer buyer offer — [property address], list $[X], [days on market],
[financing type], pre-approved $[X]. Slug: [your-slug]
```

Seller (offer review):
```
/re-offer-writer seller received offers — [property address], list $[X].
Offer 1: [price, financing, contingencies...] Slug: [your-slug]
```

**3. The skill asks for any missing context, then outputs the strategy.**

---

## Dual-Mode Quick Reference

| Task | What to Type |
|---|---|
| Write a standard buyer offer | `/re-offer-writer buyer offer [address] [price] [financing]` |
| Write a cash offer | `/re-offer-writer cash offer [address] [price]` |
| Escalation clause | `/re-offer-writer escalation clause for [address] — multiple offers confirmed` |
| Review incoming offers | `/re-offer-writer seller received [N] offers — [offer details]` |
| Write a counteroffer | `/re-offer-writer counteroffer — seller wants $[X] on $[Y] offer` |
| Personal letter guidance | `/re-offer-writer personal letter for [buyer scenario]` |
| Explain terms to seller | `/re-offer-writer explain these offer terms in plain English: [terms]` |

---

## Critical Reminders

**This skill generates guidance and draft language only.**
Transfer all offer language to your contract platform (Dotloop, ZipForms, BLC).
Do NOT use skill output as a signed contract or amendment.

**Contingency waiving:**
- Never waive financing contingency without buyer's explicit instruction and lender input
- Never recommend waiving inspection without buyer understanding the risk
- Radon testing: recommended on every Central Indiana property — Zone 1 radon risk

**Fair housing — personal letters:**
- No photos, no protected class info (children, religion, disability, national origin)
- Confirm listing agent will forward the letter before writing it

---

## What Happens After the Offer

Once an offer is accepted:
- `/re-negotiation-advisor` — for inspection responses, appraisal gaps, counteroffers
- `/re-transaction-manager` — takes over deadline tracking from contract through close

If the offer isn't accepted:
- `/re-negotiation-advisor` — strategy for countering or walking away

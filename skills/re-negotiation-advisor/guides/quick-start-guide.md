# re-negotiation-advisor — Quick Start Guide

## What This Skill Does

`re-negotiation-advisor` is your strategic coaching partner at every negotiation
point in a transaction. It covers three primary moments:

1. **Inspection** — what to request, how much, repairs vs credits, when to walk
2. **Appraisal gap** — gap options, ROV analysis, splitting strategies, walk-away
3. **Offer negotiation** — multiple-offer management, lowball responses, bidding war tactics

Works for both buyer-side and seller-side agents.

---

## 5-Minute Setup

**Your agent config must be set up first:**
```
/re-agent-setup
```

**Then invoke with a quick description of your situation:**
```
/re-negotiation-advisor [buyer/seller side] — [scenario in plain English]
Property: [address], Price: $[X]. Slug: [your-slug]
```

---

## Quick Reference by Scenario

| Situation | What to Type |
|---|---|
| Inspection came back, buyer side | `/re-negotiation-advisor inspection response buyer side — [findings summary]` |
| Inspection request received, seller side | `/re-negotiation-advisor inspection response seller side — [request summary]` |
| Appraisal came in low | `/re-negotiation-advisor appraisal gap — [price, appraised value, buyer reserves]` |
| Multiple offers to manage | `/re-negotiation-advisor multiple offers listing agent — [offer details]` |
| Lowball offer received | `/re-negotiation-advisor lowball offer response — [offer vs list vs CMA]` |
| In a bidding war | `/re-negotiation-advisor bidding war buyer — [market context, pre-approval]` |
| Deal threatening to fall apart | `/re-negotiation-advisor deal falling apart — [what's happening]` |
| Difficult other agent | `/re-negotiation-advisor difficult agent — [what they're doing]` |
| Walk-away decision | `/re-negotiation-advisor should we walk — [situation]` |
| Emotional client coaching | `/re-negotiation-advisor client coaching — [frustrated buyer / anxious seller]` |

---

## Key Indiana-Specific Context Built In

- **Radon** — Central Indiana is Zone 1 (highest risk); always recommend radon test; mitigation $800–$1,200
- **Polybutylene (PB) pipe** — common in 1978–1995 Indiana homes; significant negotiating issue
- **HOA inspection items** — HOA rules may require buyer to continue specific deferred maintenance items post-close
- **Market absorption by county** — Hamilton, Marion, Hendricks, Johnson all have distinct supply dynamics
- **Seller concession limits** — conventional (3–6% depending on LTV), FHA (6%), VA (4%)
- **Earnest money interpleader** — Indiana process if parties can't agree on EM disposition

---

## Critical Principles

- **Never reveal your client's bottom line** to the other agent
- **Never waive inspection for a buyer** without explicit written instruction from the buyer
- **Credits > repairs** in Indiana practice — buyer can hire their own contractor post-close
- **Counter before rejecting** — rejecting without counter closes negotiating doors unnecessarily
- **Document everything** — put all counter terms and agreements in writing; verbal agreements don't bind Indiana real estate contracts

---

## What Happens Next

After negotiation resolves:
- Amendments → `/re-transaction-manager` to update the deadline calendar
- New communication needed → `/re-client-communication` for formal updates
- Deal falls apart, start over → `/re-buyer-consultation` or `/re-seller-consultation`

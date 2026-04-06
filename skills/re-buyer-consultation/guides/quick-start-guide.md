# re-buyer-consultation — Quick Start Guide

## What This Skill Does

`re-buyer-consultation` prepares you for buyer consultations and generates
everything you need to onboard a new buyer client:

- Discovery questionnaire tailored to the buyer's situation
- Buyer agency agreement explanation and objection handling (post-Aug 2024)
- Financing education and lender referral from your vendor network
- Buyer presentation from your branded template
- MLS search criteria ready to paste into BLC
- Pre-approval checklist to hand off to buyers

---

## 5-Minute Setup

**1. Make sure your agent config is set up:**
```
/re-agent-setup
```
You'll need `agent-profile.yaml`, `vendor-network.yaml`, `fee-structure.yaml`,
and `market-areas.yaml` at minimum.

**2. Invoke the skill with a quick description of your buyer:**
```
/re-buyer-consultation First-time buyers, 3BR in Fishers, $320K budget,
pre-approved. Slug: [your-slug]
```

**3. Answer any follow-up questions** the skill asks about the buyer's situation.

**4. Get your outputs** — questionnaire, presentation, search criteria, and more.

---

## Common Invocation Patterns

| Situation | What to Type |
|---|---|
| Full consultation prep | `/re-buyer-consultation [buyer name + situation + budget + area] Slug: [slug]` |
| Just the discovery questions | `/re-buyer-consultation discovery questions for [situation]` |
| Financing education only | `/re-buyer-consultation financing options for [VA buyer / first-time / IHCDA]` |
| Agency agreement explanation | `/re-buyer-consultation agency agreement talking points` |
| Buyer objection handling | `/re-buyer-consultation buyer won't sign the agreement` |
| MLS search setup only | `/re-buyer-consultation search criteria for [buyer details]` |

---

## Key Indiana Details Built Into This Skill

- **Post-August 2024 buyer agreement requirement** — IAR Form 125 must be signed before any showing; skill includes explanation scripts and objection handling
- **IHCDA programs** — Indiana Housing and Community Development Authority down payment assistance for qualifying buyers; income and purchase price limits included
- **USDA eligibility** — rural areas near Central Indiana that may qualify; always verify on the official USDA map before recommending
- **VA loan Indiana specifics** — funding fee, COE process, VA MPR considerations for Indiana homes
- **Hamilton County school district premiums** — Carmel Clay, HSE, Westfield, Noblesville boundaries all carry distinct price premiums; skill flags this in discovery

---

## What This Skill Does NOT Do

- Fill out legal forms (IAR Form 125, etc.) — use Dotloop or ZipForms
- Quote specific interest rates — direct buyers to their lender
- Verify USDA or IHCDA eligibility for a specific buyer — refer to lender
- Set up the actual BLC saved search — generates criteria for you to enter

---

## After the Consultation

Once your buyer is signed up and pre-approved, use these skills next:

- `/re-neighborhood-research` — deep dive on target areas
- `/re-market-update` — current market conditions for their budget/area
- `/re-showing-coordinator` — plan buyer showing tours
- `/re-offer-writer` — when they find a home they want

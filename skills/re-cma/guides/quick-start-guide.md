# re-cma Quick Start Guide

Get from zero to a complete CMA in under 10 minutes.

---

## Before You Start

You need:
- Your agent slug (e.g., `sarah-jones-fc-tucker`) — check with your TC or admin
- Subject property details (address, BR/BA/GLA/garage/basement/year built)
- 3–5 closed comps pulled from MIBOR BLC
- Seller's current mortgage payoff (optional but improves net sheet accuracy)

You do NOT need to pull absorption rate data manually — provide the active listing
count and 30-day closed count for the zip/area and the skill calculates it.

---

## Step 1: Start the Skill

Type the slash command with the property address and your slug:

```
/re-cma 4218 Buttonwood Dr, Fishers IN 46037
Agent slug: sarah-jones-fc-tucker
```

The skill loads your config automatically. If it can't find your config files,
it will direct you to `/re-agent-setup`.

---

## Step 2: Provide Property Details

Paste or type the subject property details. The more complete, the better the output:

```
3BR / 2BA / 1 half bath
GLA: 1,850 sqft
Garage: 2-car attached
Year built: 2005
School district: Hamilton Southeastern (HSE)
HOA: None
Basement: Unfinished, 960 sqft
Updates: New HVAC 2022, original kitchen and baths
```

If you skip anything, the skill will ask.

---

## Step 3: Paste Your Comps

Pull 3–5 closed sales from BLC. Copy the key fields:

```
Comp 1: 4105 Arbor Ridge Ct, Fishers
3BR/2BA, 1,920 sqft, 2-car garage
Sold $342,000 on 1/15/2026
HSE district, no HOA

Comp 2: 14220 Streamwood Ct, Fishers
3BR/2.5BA, 1,780 sqft, 2-car garage
Sold $328,500 on 12/10/2025
HSE district, no HOA, kitchen remodel 2023
```

The skill validates each comp against the selection criteria and flags anything
questionable (e.g., comp older than 90 days, different school district, distressed sale).

---

## Step 4: Add Market Context (Optional but Recommended)

If you have it, paste the current market snapshot for the area:

```
Active 3–4BR listings in 46037: 6
Closed in last 30 days: 8
Average DOM on recent closes: 14 days
List-to-sale ratio: 99.2%
```

This powers the absorption rate analysis and affects the strategy recommendation.

---

## Step 5: Review the Output

The skill produces:

1. **Comp validation** — which comps are clean, which are flagged and why
2. **Adjustments table** — each comp adjusted to match the subject
3. **Adjusted value range** — low, high, weighted average
4. **Three pricing strategies** — at-market, aggressive, aspirational
5. **Seller net sheet** — net proceeds at each price point using your commission rate
6. **Market conditions snapshot** — absorption rate, DOM trend, supply context
7. **Branded report** — formatted with your name, brokerage, and tagline

---

## Step 6: Customize Before Presenting

Before you take it to the seller, you can ask the skill to:

- Adjust the narrative tone (more conservative, more optimistic)
- Focus on one pricing strategy if you've already had a price conversation
- Add or remove a comp from the analysis
- Recalculate the net sheet with a specific payoff amount
- Export to a format you can paste into your CMA presentation software

---

## Common Questions

**What if I only have 2 good comps?**
The skill will note the limited comp pool and widen the criteria automatically,
recommending where to look for additional data (expand to 180 days or 2-mile
radius). It will present the analysis with a confidence caveat.

**What if the seller wants a price higher than the comps support?**
The skill will present the aspirational strategy with explicit DOM and final
sale price risk data. It will not fabricate support for an unsupportable price,
but it will frame the discussion professionally for the seller conversation.

**What about new construction competing nearby?**
Tell the skill about any active builder inventory in the area. It will factor
in the competitive context in the pricing narrative — this is a market condition
factor, not a comp adjustment.

**Does the skill pull MLS data automatically?**
No. You provide comp data from BLC. The skill guides the analysis. This is intentional
— the agent is responsible for comp selection and data accuracy. The skill does the
math and narrative.

**What if I don't know the seller's payoff?**
The net sheet will show [TBD — provide current payoff] as a line item and calculate
estimated net before payoff so the seller can fill in the number themselves.

---

## Cheat Sheet: Minimum Inputs for a Valid CMA

| Input | Required? | Notes |
|---|---|---|
| Subject address + county | Yes | |
| BR / BA / GLA | Yes | |
| Garage type and count | Yes | |
| Year built | Yes | |
| School district | Yes | Critical in Hamilton County |
| HOA yes/no and dues | Yes | |
| Agent slug | Yes | For config and branding |
| At least 3 closed comps | Yes | BLC data, 90–180 days |
| Basement details | Recommended | Finished sqft vs unfinished |
| Major updates with year | Recommended | Affects adjustments |
| Active listing / closed count | Recommended | Powers absorption rate |
| Mortgage payoff | Optional | Blank line on net sheet if omitted |

---

## Submarket Quick Reference

| County | Key Value Drivers | Typical Median Range |
|---|---|---|
| Hamilton (Carmel, Fishers, Westfield) | School district, HOA community, luxury finishes | $400K–$800K+ |
| Hamilton (Noblesville, Zionsville) | School district, lot size, distance to employment | $350K–$600K |
| Marion (Indianapolis) | Neighborhood, township, walkability | $150K–$600K+ |
| Hendricks (Avon, Brownsburg) | Schools, new construction competition | $300K–$500K |
| Johnson (Greenwood, Franklin) | Center Grove schools premium, affordability | $250K–$450K |
| Boone (Lebanon, Zionsville portion) | Acreage, rural character, Western Boone schools | $280K–$600K |

---

## Useful Follow-Up Commands

After running a CMA, these related skills pick up where it leaves off:

```
/re-seller-consultation    # Build the full listing presentation around this CMA
/re-listing-creation       # Write BLC remarks using the agreed list price
/re-client-communication   # Draft the post-appointment follow-up email
/re-negotiation-advisor    # Prep for incoming offers using this market data
```

# re-market-update: 5-Minute Quick Start Guide

## What This Skill Does

`re-market-update` generates market snapshots for any Central Indiana area —
a county, city, zip code, or neighborhood. It pulls current stats from MIBOR,
IAR, Redfin, and Zillow, calculates key metrics, and delivers the output in
whatever format you need: a client email, a social media post, a full report
for a buyer or seller presentation, or a quick verbal reference for a meeting.

**In plain terms:** You tell it where and when. It finds the numbers, does the
math, and turns it into something you can hand to a client or post in the next
five minutes.

---

## Before You Use This Skill

Your agent config must be set up. Run `/re-agent-setup` first if you haven't.
Once your config exists, this skill uses your:
- **Voice and tone** — so the output sounds like you
- **Brand kit** — hashtags, disclaimer, tagline, colors
- **Market areas** — as the default geography if you don't specify one

If you're using this skill for the first time, tell it your slug or your name
so it can identify you: "Working as sarah-chen-fc-tucker" or just "I'm Sarah
Chen at F.C. Tucker."

---

## How to Specify the Area and Time Period

The skill accepts geography and time period in plain language. You don't need
exact formatting.

**Geography options:**
```
Hamilton County
Fishers
Carmel zip 46032
Westfield
Fountain Square neighborhood
Johnson County — specifically Center Grove area
```

**Time period options:**
```
current month
February 2026
Q1 2026
Q4 2025
2025 full year
last 90 days
```

**If you don't specify:** The skill defaults to your primary market area from
your config and the most recently completed calendar month.

---

## How to Choose an Output Format

Tell the skill what you need, or let it ask:

| Format | Best For | Length |
|---|---|---|
| **Email newsletter** | Monthly client sphere blast | 200–300 words |
| **Social media** | Instagram/Facebook content post | 150–200 words |
| **Detailed report** | Buyer or seller consultation prep | 500–800 words |
| **Verbal summary** | Client meeting or listing appointment | 5–7 bullets |

**Example prompts:**
```
Hamilton County April 2026, email newsletter
Fishers current month, social media post
Carmel 46032 Q1 2026, detailed report for a buyer presentation
Noblesville this month, verbal summary — I have a listing appointment in an hour
```

If you don't name a format, the skill will ask which one you need.

---

## What Data Sources It Uses

The skill searches these named sources, in order of preference:

1. **MIBOR** (mibor.com) — the authoritative Indiana source; monthly press
   releases with county-level data. Published ~third week of the following month.
2. **IAR** (iar.org) — Indiana Association of REALTORS® monthly reports; state
   and county level.
3. **NAR** (nar.realtor) — national and metro-level; useful for Indianapolis
   MSA context.
4. **Redfin** — city and zip-level rolling data; near-real-time.
5. **Zillow Research** — trend data and market heat index.

**Important:** Published data from these sources may lag by 2–4 weeks, and
small differences from your brokerage's direct MLS pull are normal. Always
verify stats through your own BLC/Matrix access before using them in a formal
seller presentation or listing agreement.

---

## About the Data Disclaimer

Every output this skill generates includes a data disclaimer:

> *Market data is sourced from publicly available reports and is believed to be
> accurate but not guaranteed. Statistics are based on reported closed sales.
> Past market performance does not guarantee future results.*

This disclaimer is non-optional. It protects you. Do not remove it from any
client-facing output.

---

## What the Skill Won't Do

- **It will not predict future prices.** It will describe trends and frame
  conditions — but it will not say "prices will rise X% this year."
- **It will not produce a CMA.** A market report and a comparative market
  analysis are different tools. For a CMA, use `/re-cma`.
- **It will not provide investment advice.** For investor clients, it provides
  market context only. Investment return projections require a financial
  professional.
- **It will not cherry-pick favorable time windows** without disclosing what
  range it used.

---

## Common Questions

**Can I run this for a neighborhood rather than a county?**
Yes — as long as the neighborhood or zip code has enough recent sales to
generate meaningful stats. For very small sub-markets, the skill will note
when data is limited.

**What if MIBOR hasn't published the latest month yet?**
MIBOR publishes monthly data ~3 weeks after month-end. If you're asking for a
month that hasn't been published yet, the skill will use the most recent
available period and note the data lag.

**Can I combine two counties in one report?**
Yes — for example, "Hamilton and Hendricks County comparison" produces a
side-by-side view. Useful for buyers considering both markets.

**Can I run this for new construction specifically?**
Yes — request "Westfield new construction market" and the skill will focus on
builder activity, new permit data, and how builder pricing compares to resale.
See `examples/example-prompts.md` Scenario 6 for a full example.

**How do I use this before a listing appointment?**
Use the verbal summary format. Give it the city, say "I have a listing
appointment in 30 minutes," and it will generate 5–7 talking points you can
reference naturally. See Scenario 4 in `examples/example-prompts.md`.

---

## Example Prompts to Get Started

```
/re-market-update Hamilton County current month, email newsletter
/re-market-update Greenwood April 2026, social media
/re-market-update Carmel 46032 Q1 2026, detailed report
/re-market-update Noblesville today, verbal summary for a listing appointment
/re-market-update Marion County 2025 vs 2024, investor analysis
```

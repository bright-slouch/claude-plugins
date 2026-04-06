# re-cma — Example Prompts

Six realistic scenarios covering the most common CMA situations in Central Indiana.

---

## Example 1: Standard Suburban 3BR/2BA — Fishers

**Scenario:** Agent has a listing appointment tomorrow for a typical Fishers
subdivision home. Comps are available and reasonably clean.

**Prompt:**
```
/re-cma

Subject: 4218 Buttonwood Dr, Fishers IN 46037
Agent slug: sarah-jones-fc-tucker
Property: 3BR / 2BA / 1 half bath, 1,850 sqft GLA, 2-car attached garage,
built 2005, Hamilton Southeastern school district, no HOA, unfinished basement
(960 sqft), new HVAC 2022, original kitchen and baths.

Comps from BLC:
1. 4105 Arbor Ridge Ct, Fishers — 3BR/2BA, 1,920 sqft, 2-car garage, sold
   $342,000 on 1/15/2026, HSE district, no HOA
2. 14220 Streamwood Ct, Fishers — 3BR/2.5BA, 1,780 sqft, 2-car garage,
   sold $328,500 on 12/10/2025, HSE district, no HOA, kitchen remodel 2023
3. 4401 Millstone Dr, Fishers — 4BR/2BA, 2,050 sqft, 2-car garage, sold
   $355,000 on 2/3/2026, HSE district, no HOA
4. 14088 Foxchase Ln, Fishers — 3BR/2BA, 1,800 sqft, 2-car garage, sold
   $335,000 on 11/5/2025, HSE district, no HOA

Seller wants to know what price makes sense and what they'll net.
```

**What the skill should produce:**
- Comp selection validation (all 4 are acceptable; flag comp 4 as 145 days old)
- Adjustments table: minor GLA adjustments, +1 bedroom on comp 3, kitchen
  credit on comp 2, new HVAC credit vs comps
- Adjusted value range approximately $325,000–$345,000
- Three pricing strategies with narrative
- Net sheet at all three price points using agent's commission from fee-structure.yaml
- Branded output with Sarah's name/brokerage
- Both disclaimers

---

## Example 2: Luxury Property in Carmel — Limited Comps

**Scenario:** Expensive home in Carmel's Old Meridian corridor. Few direct comps;
agent needs to expand criteria and rely on a smaller pool.

**Prompt:**
```
/re-cma

Subject: 12304 Springmill Rd, Carmel IN 46032
Agent slug: sarah-jones-fc-tucker
Property: 5BR / 4 full BA / 2 half BA, 5,200 sqft GLA + 2,100 sqft finished
basement, 3-car side-load garage, built 2008, Carmel Clay school district,
HOA $150/mo, lot 0.62 acres. Major kitchen remodel 2021 ($85K), master bath
2020 ($35K), roof 2019, all mechanicals updated 2021.

Comps from BLC (only 3 closed in 90 days within 1 mile — expanding to 6 months):
1. 12101 Springmill Rd, Carmel — 5BR/4BA/1HB, 5,050 sqft, 3-car garage,
   sold $875,000 on 9/22/2025 (168 days ago), Carmel Clay, HOA $150/mo
2. 12720 Gray Rd, Carmel — 4BR/3.5BA, 4,600 sqft, 2-car garage, sold
   $795,000 on 11/14/2025, Carmel Clay, no HOA
3. 11905 Westfield Blvd, Carmel — 6BR/5BA, 5,700 sqft + 2,400 sqft finished
   basement, 3-car garage, sold $995,000 on 1/28/2026, Carmel Clay, HOA $200/mo
4. 12500 Old Meridian St, Carmel — 4BR/4BA, 4,900 sqft, 3-car garage,
   PENDING $865,000 (not closed — use directionally only), Carmel Clay

Seller believes their updates push them close to $900K. Is that supportable?
```

**What the skill should produce:**
- Note that comp 1 is 168 days old — flag but include; explain the "slow market"
  expansion rule and that it's the most geographically proximate comp
- Apply substantial positive adjustments to subject for 2021 updates (kitchen,
  bath, mechanicals) vs older-update comps
- Add basement GLA adjustment ($20–40/sqft) vs comps with no or less finished
  basement space
- Note comp 4 is pending — use directionally, do not weight equally with closed
- Adjusted range: approximately $855,000–$930,000 depending on update values
- Discuss seller's $900K assertion — show it's at the high end of supportable range;
  at-market would be ~$880,000, aspirational $915,000–$930,000
- Advise DOM expectations at aspirational price for luxury tier
- Net sheet at $880K, $900K, $925K using agent commission from config

---

## Example 3: Condo/Townhome — HOA Factor

**Scenario:** Condo listing in the north Indianapolis/Broad Ripple area.
HOA dues are a value drag. Comp pool is limited to similar product.

**Prompt:**
```
/re-cma

Subject: 8901 River Crossing Blvd #114, Indianapolis IN 46240
Agent slug: mike-wright-compass
Property type: Condo (attached)
2BR / 2BA, 1,150 sqft GLA, 1-car detached garage, built 1998,
Washington Township, MSD Washington Township schools, HOA $285/month
(includes water, exterior, pool, gym). No basement.

Comps from BLC (same complex and adjacent):
1. 8901 River Crossing Blvd #208 — 2BR/2BA, 1,100 sqft, 1-car garage,
   sold $218,000 on 2/1/2026, same HOA $285/mo
2. 8901 River Crossing Blvd #320 — 2BR/2BA, 1,175 sqft, no garage,
   sold $205,000 on 12/20/2025, same HOA $285/mo
3. 8750 River Crossing Blvd #101 — 2BR/2BA, 1,190 sqft, 1-car garage,
   sold $224,000 on 1/10/2026, adjacent complex HOA $310/mo
4. 9100 Hazel Dell Pkwy #B, Indianapolis — 2BR/2BA, 1,080 sqft, 1-car
   garage, sold $199,000 on 11/30/2025, HOA $220/mo — different product
   (townhome style), different street

Subject was freshly painted, new LVP flooring throughout in 2024.
Seller needs to net at least $195,000 after payoff.
```

**What the skill should produce:**
- Flag comp 4 as a different product type (townhome) — use with caution and flag
- Adjust for garage presence (comp 2 has no garage — add ~$8,000–12,000)
- Adjust for GLA differences (minor within this comp pool)
- Adjust for HOA difference on comp 3 ($310 vs $285 = $25/mo x 100 = –$2,500
  to subject's value since subject's HOA is lower)
- Credit subject for 2024 flooring and paint update
- Note HOA dues context: $285/mo is a buyer affordability factor — include in
  narrative, not just in the numbers
- Adjusted range: approximately $218,000–$228,000
- Three strategies; note limited upside at aspirational given HOA cost sensitivity
- Net sheet showing if $195K net is achievable at recommended price; use
  mike-wright-compass fee-structure

---

## Example 4: Unique Rural Property — Boone County Acreage

**Scenario:** Rural property with 5+ acres in Boone County. Very few comps.
Paired sales technique required. Agent is nervous about pricing.

**Prompt:**
```
/re-cma

Subject: 4501 W 300 N, Lebanon IN 46052
Agent slug: dan-riley-remax
Property: 3BR / 2BA ranch, 1,640 sqft GLA, 3-car detached garage/shop,
built 1987, 5.2 acres, Boone County, Western Boone school district,
no HOA, no basement, original kitchen and baths, well/septic. Roof 2018.
Seller has owned 22 years and is moving to assisted living.

True rural comps (within 5 miles, Western Boone schools, 90–180 days):
1. 2200 E 225 N, Lebanon — 3BR/2BA ranch, 1,580 sqft, 2-car garage, 3.1
   acres, sold $299,000 on 12/5/2025, well/septic
2. 5800 W 350 N, Lebanon — 4BR/2BA, 1,750 sqft, 2-car garage, 2.0 acres,
   sold $285,000 on 11/15/2025, well/septic
3. 8200 N SR-39, Lebanon — 3BR/1.5BA, 1,480 sqft, 1-car garage, 10.4
   acres, sold $375,000 on 10/1/2025, well/septic — large acreage premium
4. City comp for house-only reference: 4BR/2BA, 1,700 sqft, Lebanon city
   limits, sold $249,000 on 1/20/2026, city water/sewer, no acreage

Agent note: I think the acreage adds a lot but I don't want to overprice this
for the seller's family.
```

**What the skill should produce:**
- Flag comp 3 (10.4 acres) as too dissimilar without acreage adjustment — explain
  paired sales technique to isolate per-acre value from house value
- Use comp 4 (city comp) as a "house-only" baseline to extract land value
- Paired sale analysis: comp 1 (3.1 acres, $299K) vs comp 4 baseline
  ($249K normalized) → implies ~$50K+ for 3.1 acres → ~$16K/acre in this area
- Subject: 5.2 acres × $16K = ~$83K land contribution + ~$240K house value ≈ $323K
- Cross-check vs comp 2 (2.0 acres, $285K): lower acreage explains gap
- Adjusted range: approximately $310,000–$335,000
- Note: well/septic is standard in this area — no adjustment required vs comps
  that also have well/septic; flag if any comp has city utilities
- Note detached shop/garage adds value — 3-car vs 2-car comp adjustment
- Three strategies; note aspirational risk in rural market with limited buyer pool
- Acknowledge seller's family context — no legal or estate advice, but present
  net sheet clearly for their decision-making
- Include paired sales methodology note for seller's benefit

---

## Example 5: New Construction Competing Inventory — Greenwood

**Scenario:** Resale listing in Greenwood where a builder is actively selling
new construction in the same subdivision. Agent needs to address this head-on
in pricing strategy.

**Prompt:**
```
/re-cma

Subject: 922 Cobblestone Ct, Greenwood IN 46143
Agent slug: lisa-chen-kw
Property: 4BR / 3BA, 2,400 sqft GLA, 2-car attached garage, built 2019,
Center Grove school district, HOA $55/mo, unfinished basement (1,200 sqft),
seller updated primary bath 2023, new deck 2024.

Builder context: Same subdivision (Cobblestone Crossing) still has 8 lots
being sold. Builder base price for 4BR/3BA, 2,350 sqft is $489,900 with
standard finishes. Builder is offering $15,000 in closing cost incentives.
Builder homes typically close 6–8 months after contract.

Resale comps from BLC:
1. 918 Cobblestone Ct, Greenwood — 4BR/3BA, 2,380 sqft, 2-car, sold $472,000
   on 1/8/2026, Center Grove, HOA $55/mo (same sub, not a builder sale)
2. 301 Cobblestone Way, Greenwood — 3BR/2.5BA, 2,200 sqft, 2-car, sold
   $445,000 on 12/15/2025, Center Grove, HOA $55/mo (same sub, resale)
3. 7804 Briarwood Ln, Greenwood — 4BR/3BA, 2,450 sqft, 2-car, sold $468,000
   on 2/10/2026, Center Grove, HOA $62/mo (adjacent sub)
4. Builder sale (not arm's-length for CMA purposes): 900 Cobblestone Ct
   sold $497,000 on 1/25/2026 — new construction, same builder
```

**What the skill should produce:**
- Exclude builder sale from comps (not arm's-length; includes incentives not
  visible in MLS price; new vs resale comparison not valid without adjustment)
- Note builder competition explicitly in pricing narrative — this is a market
  condition factor, not a comp adjustment
- Explain resale buyer advantage: immediate occupancy vs 6–8 month builder wait;
  known condition; seller can include updated bath and deck; established yard
- Explain resale buyer disadvantage: builder offers customization, warranty,
  closing cost incentives worth ~$15K
- Adjust comp 2 for bedroom/bath difference
- Minor GLA adjustments across comps
- Subject primary bath update 2023 and deck 2024 — apply credits
- Adjusted range: approximately $460,000–$478,000 for subject resale
- Strategy note: pricing at $485K+ puts subject in direct competition with new
  construction at identical price without the "new" premium — likely to sit;
  recommend at-market at $465K–$470K to emphasize immediate occupancy advantage
- Include competitive positioning narrative (2–3 sentences) for seller discussion

---

## Example 6: Hot Market — Multiple Offer Strategy Discussion

**Scenario:** Low-inventory seller's market in Carmel; agent believes multiple
offers are likely and wants to structure pricing to maximize seller outcome.

**Prompt:**
```
/re-cma multiple offer strategy

Subject: 14204 Carey Rd, Carmel IN 46033
Agent slug: sarah-jones-fc-tucker
Property: 4BR / 2.5BA, 2,650 sqft GLA + 800 sqft finished basement, 2-car
attached garage, built 2001, Carmel Clay school district, HOA $40/mo, lot
0.28 acres. Updated kitchen 2022, new roof 2023, hardwoods throughout.

Market context agent provided:
- Active 4BR listings in this zip: 4 homes
- Closed in last 30 days, same zip: 6 homes
- Average DOM on those closes: 8 days
- Average list-to-sale ratio: 101.4%

Comps from BLC:
1. 14088 Carey Rd, Carmel — 4BR/2.5BA, 2,600 sqft, sold $498,000 on
   2/14/2026, Carmel Clay, HOA $40/mo, no basement, no recent updates
2. 14312 Fosterway Dr, Carmel — 4BR/3BA, 2,700 sqft + 750 sqft fin.
   basement, sold $527,000 on 1/30/2026, Carmel Clay, HOA $35/mo, kitchen
   updated 2021
3. 13975 Ditch Rd, Carmel — 3BR/2.5BA, 2,500 sqft, no basement, sold
   $475,000 on 2/5/2026, Carmel Clay, no HOA, original finishes

Agent question: Should we go slightly below market to trigger a bidding war,
or list at value? What's the risk of each approach in this market?
```

**What the skill should produce:**
- Absorption rate: 4 active ÷ 6/mo closed = 0.67 months supply — deep seller's
  market; note this explicitly
- Avg DOM of 8 days and 101.4% list-to-sale ratio confirm strong demand
- Adjustments: add basement GLA credit vs comps 1 and 3, adjust for 3BR on
  comp 3, add kitchen update credit vs comps 1 and 3, add roof credit
- Adjusted range: approximately $505,000–$530,000
- Three-strategy discussion in context of multiple-offer market:
  - Aggressive ($488K–$495K): likely triggers 3–5 offers; sellers in this
    market often end up at $510K–$525K when competing — potential to exceed
    at-market list; psychological risk is buyers assume something is wrong
    if priced too low; requires seller to be comfortable with escalation clause
    management and offer review process
  - At-market ($512K–$518K): with 8-day avg DOM and 101.4% ratio, expect
    2–3 competitive offers; price signals confidence; solid floor; recommended
  - Aspirational ($530K–$540K): risky even in this market — buyers paying
    cash or financing will have appraisal contingency issues above ~$525K;
    if it sits past 2 weeks, narrative shifts; list-to-sale ratio would have
    to be >103% to justify aspirational
- Concrete recommendation: list at $515,000; set offer deadline 5 days out;
  review all offers at once; be ready to counter best offer or accept highest
  with escalation clause
- Brief explanation of offer deadline strategy and escalation clauses for
  agent context
- Net sheet at $488K, $515K, $530K showing seller the range of outcomes

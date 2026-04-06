# re-market-update: Example Prompts

---

## Scenario 1: Monthly Email Newsletter — Hamilton County Spring Market

**Context:** Sarah Chen (F.C. Tucker, Carmel) sends a monthly market update
email to her 400-contact sphere. It's late April 2026 — peak spring season.
She wants something that will get opens and responses.

**Prompt:**
```
/re-market-update Hamilton County April 2026, email newsletter format.
Working as sarah-chen-fc-tucker.
```

**What happens:**
The skill loads Sarah's `agent-profile.yaml` (professional-friendly tone,
formality 6/10, no emoji in email), `brand-kit.yaml` (her hashtags, brokerage
disclaimer, tagline "Your Carmel Connection"), and `market-areas.yaml`
(Hamilton County primary, Carmel and Fishers farm areas).

It searches MIBOR's April press release and IAR data for Hamilton County stats.
Finds: median sale price $528,000 (up 7.2% YoY), median DOM 9 days (down from
13 last April), months of supply 1.4 (down from 1.9), sale-to-list ratio 102.4%.

Output is a 250-word email newsletter:

- Subject line: "Hamilton County's Spring Market: 9 Days. That's How Fast."
- Opening hook on the DOM stat — the most attention-grabbing number
- Three highlighted stats with plain-English context
- What it means for sellers (strong moment to list; multiple offers expected)
- What it means for buyers (pre-approval essential; clean offers, limited
  contingencies)
- Sarah's CTA: "If you've been thinking about selling — or wondering what your
  home is worth right now — let's talk."
- Her full signature block from `email-templates.yaml`
- Brokerage disclaimer and data caveat at bottom

The email matches Sarah's professional-friendly tone — engaging without being
pushy; data-forward without feeling like a textbook.

---

## Scenario 2: Social Media Post — Johnson County First-Time Buyer Angle

**Context:** Marcus Williams (KW Indy Metro North) works Hamilton County
primarily but is helping a wave of first-time buyers who can't afford Carmel.
He wants to post about Johnson County's value story — specifically framing it
as a strategic opportunity rather than a consolation prize.

**Prompt:**
```
/re-market-update Johnson County, March 2026, social media caption. Angle:
value opportunity for first-time buyers who are getting priced out of
Hamilton County. Working as marcus-williams-kw-indy-metro-n.
```

**What happens:**
The skill loads Marcus's config (casual-warm tone, formality 4/10, emoji
enabled, hashtag-forward social presence). It notes that his `market-areas.yaml`
includes Hamilton County as primary but Johnson County as a secondary area.

It searches Redfin and IAR for Johnson County March stats: median sale price
$298,000 (vs. Hamilton County $506,000), median DOM 22 days, months of supply
2.8, sale-to-list 99.6%.

Output is a 175-word Instagram/Facebook caption:

```
Thinking about buying but Hamilton County prices have you rethinking
everything? Let's talk about Johnson County. 👇

📍 March 2026 — Johnson County Market Snapshot:
📊 Median sale price: $298,000
⏱ Median days on market: 22 days
🏘 Months of supply: 2.8 (seller's market — but not a sprint)
📈 Sale-to-list ratio: 99.6%

That's $200K+ less than the Hamilton County median — for homes that are
still close to I-65, great schools in Greenwood and Center Grove districts,
and a community that's growing fast.

First-time buyers: this market gives you time to breathe without giving
up a great location.

Want the full breakdown or help figuring out what your budget gets you
in Johnson County right now? DM me or drop a comment.

— Marcus Williams | KW Indy Metro North
#JohnsonCountyRealEstate #GreenoodIN #CenterGrove #IndyRealEstate
#FirstTimeBuyer #BuyInIndy #KellerWilliams
```

Hashtags pulled from Marcus's `brand-kit.yaml` — local tags first, then
national. Emoji usage matches his config preference.

---

## Scenario 3: Detailed Quarterly Report — Carmel Zip 46032 Buyer Consultation

**Context:** Jennifer Hartley (CENTURY 21 Scheetz) is meeting tomorrow with
buyers who are seriously looking in Carmel zip 46032. They want to buy in the
$600K–$800K range and are asking smart questions about whether Q1 2026 is a
good time to buy or whether they should wait.

**Prompt:**
```
/re-market-update Carmel zip 46032, Q1 2026, detailed report. I have buyer
clients considering $600K-$800K range and they want to know if now is a good
time. Working as jennifer-hartley-c21-scheetz.
```

**What happens:**
The skill loads Jennifer's config (expert-authoritative tone, formality 7/10,
CENTURY 21 branding). It searches Redfin zip 46032 data plus MIBOR Hamilton
County Q1 stats.

Finds: 46032 median sale price $712,000 (up 5.9% YoY); Q1 median DOM 14 days
(spring surge beginning in March); 1.6 months of supply; 101.8% sale-to-list.
47% of homes sold above asking in March 2026.

Output is a full 650-word detailed report:

**Carmel 46032 Real Estate Market Report | Q1 2026**
*Prepared by Jennifer Hartley | CENTURY 21 Scheetz | April 2026*

**Section 1: Market Snapshot Table**

| Metric | Q1 2026 | Q1 2025 | YoY Change |
|---|---|---|---|
| Median Sale Price | $712,000 | $672,500 | +5.9% |
| Median DOM | 14 days | 18 days | −22% |
| Months of Supply | 1.6 | 2.1 | −0.5 mo |
| Closed Sales | 87 | 79 | +10.1% |
| Sale-to-List Ratio | 101.8% | 100.4% | +1.4 pts |
| % Sold Over Ask | 47% | 38% | +9 pts |

*Source: Redfin (46032), MIBOR Hamilton County Q1 2026. Verified March 2026.*

**Section 2: Market Narrative**
(Detailed paragraph analysis of the trend — prices accelerating, inventory
tightening year over year, spring surge arriving early in 2026, active
buyers in the $600K–$800K segment...)

**Section 3: Area Context**
(Carmel Clay Schools premium, Arts & Design District proximity to 46032,
new construction on 46032 fringes vs. established resale, corporate relocation
demand driver...)

**Section 4: What This Means**
For Sellers / For Buyers (4 bullet points each)

**Section 5: Jennifer's Interpretation**
Professional read framing the "buy now vs. wait" question with specific context:
inventory is not improving, prices are up nearly 6%, and waiting has a measurable
cost in this zip code. Not a guarantee — but a data-grounded perspective.

The report closes with Jennifer's contact info, brokerage disclaimer, and the
standard data caveat.

---

## Scenario 4: Verbal Summary — Fishers Listing Appointment

**Context:** David Park (CENTURY 21 Scheetz) has a listing appointment in
45 minutes in Fishers — a seller who asked "what's the market doing right now?"
He needs a quick-reference verbal summary he can speak from naturally without
reading from notes.

**Prompt:**
```
/re-market-update Fishers, current month, verbal summary for a listing
appointment. I'm walking in to meet a seller who wants to know if it's
a good time to list. Working as david-park-c21-scheetz.
```

**What happens:**
The skill loads David's config quickly. Searches Redfin Fishers and MIBOR
Hamilton County current month. Generates a 6-bullet verbal reference card:

```
FISHERS MARKET — [Month] 2026 | Quick Reference for David Park

• We're in a seller's market — about 1.8 months of inventory in Fishers
  right now. Sellers have the advantage.

• Median prices in Fishers are running around $478,000 — up roughly 6%
  from this time last year. That's real appreciation.

• Well-priced homes are going under contract in about 11 days. If it's
  priced right, they're not sitting.

• We're heading into the spring surge — April and May are typically the
  most competitive months of the year here. If your seller lists now,
  they catch that wave.

• New construction on the north Fishers fringe (HSE corridor) means buyers
  have builder options. Well-staged resale with a competitive price wins
  that comparison — buyers often prefer move-in-ready established homes.

• Bottom line for your seller: strong market, good timing. If they're
  thinking about it, acting now captures the spring demand.
```

Conversational, specific to Fishers, and framed for a seller conversation.
David can reference these naturally without it sounding scripted.

---

## Scenario 5: Year-over-Year Investor Analysis — Marion County

**Context:** An investor client of Lisa Morales (F.C. Tucker) is asking whether
Marion County appreciation is holding up, or whether the urban market is
softening compared to the collar counties. He's considering either a buy-and-hold
rental in Broad Ripple or flipping in Fountain Square.

**Prompt:**
```
/re-market-update Marion County 2025 full year vs 2024, detailed report.
My investor client is comparing the urban market to collar county trends.
He's looking at Broad Ripple and Fountain Square specifically.
Working as lisa-morales-fc-tucker.
```

**What happens:**
The skill loads Lisa's config. It searches IAR annual data for Marion County
2025 vs 2024, and Redfin neighborhood-level data for Broad Ripple and Fountain
Square zip codes.

The report includes:
- Marion County full-year 2025 vs 2024 metric table (all 6 metrics with YoY)
- Narrative on Marion County's dual market: premium north side (Meridian Hills,
  Washington Township) vs. value east/southeast; appreciating urban renewal
  pockets vs. stagnant distressed areas
- Broad Ripple neighborhood analysis: rental demand drivers, DOM trend, investor
  activity competition level, cap rate context note (skill notes it does not
  provide investment return projections — agent should consult with their
  investor client's financial advisor)
- Fountain Square analysis: appreciation trend over 5-year backdrop, current
  median, renovation market characteristics
- Comparison to Hamilton County median to frame the conversation about where
  the value opportunity is

**Important:** The skill includes a disclaimer that it is not providing investment
advice or projecting returns. It provides market data context only; investment
decisions require due diligence beyond market statistics.

---

## Scenario 6: Westfield New Construction vs. Resale Comparison

**Context:** A buyer working with Tyler Okonkwo (RE/MAX Advanced Realty) is
deciding between a new Lennar build in Westfield at $485,000 and a resale
home in the same price range. They want to understand the real market comparison.

**Prompt:**
```
/re-market-update Westfield — new construction vs resale comparison for a buyer
considering both options in the $450K-$550K range. Working as
tyler-okonkwo-remax-advanced.
```

**What happens:**
The skill loads Tyler's config and notes that Westfield is in his market-areas.yaml.
It searches for current Westfield new construction activity (Grand Park corridor,
SR-32/US-31 builders) and resale market data.

Output is a structured comparison (verbal or detailed format based on Tyler's
preference — skill asks if not specified):

**New Construction Considerations:**
- Builders in Westfield at this price point: Lennar (multiple communities),
  M/I Homes, Fischer Homes, Arbor Homes
- Typical timeline: 6–10 months to delivery from contract
- Pricing: builders typically negotiate on upgrades and incentives, not base
  price; preferred lender incentives can equal $5K–$15K value
- Buyer's agent: must be registered on first visit; commission is typically paid
  by builder but varies — verify before touring
- Warranties: typically 1-year workmanship, 10-year structural
- MLS representation: builder sales may not appear in resale comp counts — new
  construction does not have the same "days on market" pressure as resale

**Resale Market in Westfield ($450K–$550K range):**
- Current Redfin/MIBOR data for this range: median DOM approximately X days;
  months of supply approximately X; sale-to-list ratio X%
- Typical characteristics: established yard/landscaping, potential renovation
  needs factored into price, immediate occupancy
- Negotiation: resale sellers have more flexibility on price and timing vs.
  builders who hold firm on price

**Recommendation framing** (for Tyler to use with the buyer):
- New construction: certainty of new systems, customization options, warranty
  coverage — but 6-10 month wait and less price negotiation
- Resale: immediate occupancy, established neighborhood feel, more negotiation
  flexibility — but pre-inspection diligence important
- At this price point in Westfield specifically, both options are competitive;
  decision usually comes down to timeline and risk tolerance

The skill reminds Tyler that builder contracts are not IAR standard forms and
recommends the buyer review the builder contract carefully (or with an attorney)
before signing.

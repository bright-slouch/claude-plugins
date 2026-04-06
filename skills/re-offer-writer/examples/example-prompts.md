# re-offer-writer — Example Prompts

Eight scenarios covering both buyer and seller offer situations in Central Indiana.

---

## Example 1: Competitive Market Buyer Offer — Fishers

**Scenario:** Buyer wants to write a strong offer on a Fishers home. Market is
competitive — property has been listed 6 days and agent believes there may be
other offers coming. Conventional financing. Pre-approved at $360K.

**Prompt:**
```
/re-offer-writer buyer offer

Property: 4218 Buttonwood Dr, Fishers IN 46037
List price: $338,000
Listed: 6 days ago (no price history)
Agent's CMA estimate: $335,000–$345,000
Buyer: Sarah and Tom Kellerman
Financing: Conventional, pre-approved $360K, 10% down
Competition: Listing agent mentioned "a lot of activity"
Timeline: Buyers want to be in by June

Slug: sarah-jones-fc-tucker
```

**What the skill should produce:**
- Offer price recommendation: $341,000–$348,000 range based on CMA (at or slightly over list)
- Rationale: 6 days on market in seller's market + "a lot of activity" signal
- Earnest money: recommend $6,800 (2%) — signals commitment without being unusual
- Contingencies: inspection (7 days, shortened from 10 for competitiveness), financing
  (21 days standard), appraisal (standard — buyer is 10% down, cannot safely waive)
- Escalation clause option: base $341K, increment $2,000, ceiling $355K — discuss if agent
  confirms multiple offers are in play; skip if just agent's read on activity
- Personal letter: brief guidance; note listing agent may not forward it
- Offer package summary: all terms in one clear block ready to transfer to Dotloop

---

## Example 2: Buyer's Market Offer — South Indianapolis

**Scenario:** Property has been listed 78 days with one price reduction. Buyer
wants to offer below asking but doesn't want to insult the seller. Conventional
financing, $275K pre-approval.

**Prompt:**
```
/re-offer-writer buyer offer — buyer's market, stale listing

Property: 3902 S Meridian St, Indianapolis IN 46217
Original list price: $279,000
Current list price: $264,900 (reduced 45 days ago)
Days on market: 78
Buyer financing: Conventional, pre-approved $275K, 5% down
Agent's read: Property overpriced even at current list; comps suggest $248K–$258K
Seller situation: Investor property — tenant vacated, property vacant

Slug: mike-wright-compass
```

**What the skill should produce:**
- Offer price recommendation: $248,000–$252,000 (2–4% below lower end of comp range)
  with rationale: 78 DOM, price reduction, investor seller, vacant = motivation to sell
- Note: going below $248K is not comp-supported and may be rejected outright; framing
  the offer at $250K still leaves seller with a face-saving counteroffer path
- Earnest money: $2,500 (1%) is appropriate for this price/market combination
- Contingencies: include all standard (inspection 10 days, financing 21 days, appraisal)
  — buyer's market means no need to waive any contingency
- Inspection note: investor properties are often deferred maintenance — full 10-day
  period with sewer scope recommended
- Closing date: offer 30 days — sellers of vacant properties often want fast close
- No escalation clause: not appropriate for a stale listing

---

## Example 3: Cash Offer — Carmel Luxury

**Scenario:** Cash buyer, $875K Carmel listing, 4 days on market. High-end
property. Seller received one other offer already (listing agent confirmed).
Cash buyer wants to be clear favorite.

**Prompt:**
```
/re-offer-writer cash offer, multiple offer situation

Property: 12304 Springmill Rd, Carmel IN 46032
List price: $875,000
Days on market: 4
Competition: Listing agent confirmed 1 other offer in; H&B called for tomorrow noon
Buyer: Cash purchase, proof of funds available immediately
Agent's CMA range: $855,000–$930,000 (luxury, limited comps)

Slug: sarah-jones-fc-tucker
```

**What the skill should produce:**
- Offer price recommendation: $890,000–$910,000 for the cash buyer to win (above the
  CMA midpoint; cash premium is real in luxury tier; buyer needs to decide comfort level)
- Cash premium rationale: cash eliminates appraisal risk, lender timing, financing failure;
  sellers in luxury tier value certainty; premium of 1–3% over conventional offer is reasonable
- Earnest money: $25,000–$35,000 (3–4%) appropriate for luxury cash deal; signals
  commitment and replaces the "lender approval" credibility signal
- Contingencies: inspection only (10 days); financing and appraisal N/A (cash);
  no home sale contingency; clean terms = cash buyer's strongest card
- Proof of funds: note that agent should attach POF letter immediately with offer submission
- H&B deadline: submit before the deadline — do not wait until last minute
- Escalation clause: typically not used in luxury cash situations; offer your best price directly
- Closing: offer 30 days (title work and cash wires are faster than mortgage; seller gets certainty)

---

## Example 4: Contingent Offer — Buyer Has a Home to Sell

**Scenario:** Buyer found their dream home but hasn't sold their current home yet.
Must sell first. Market is balanced. Listing agent indicates seller may consider
contingent offer with a kick-out clause.

**Prompt:**
```
/re-offer-writer contingent offer with home sale contingency

Property: 14204 Carey Rd, Carmel IN 46033
List price: $515,000
Days on market: 14, balanced market (absorption ~3.5 months)
Buyer current home: Greenwood, estimated value $340K, payoff $140K
Buyer financing: Conventional with contingency on current home sale
Listing agent: will present a contingent offer; open to kick-out clause

Slug: sarah-jones-fc-tucker
```

**What the skill should produce:**
- Offer price: at-market $515,000 (full list) — contingent offers need to be strong on
  price to offset the contingency weakness
- Home sale contingency terms: standard Indiana kick-out clause — seller may continue to
  show and market; if new acceptable offer received, buyer has 72 hours to remove
  contingency (by securing bridge financing or releasing their own sale contingency) or
  release the contract
- Earnest money: $10,000 (higher than normal given contingency risk to seller — show commitment)
- Inspection: standard 10 days
- Financing: 21 days from the date contingency is removed (not from acceptance)
- Timeline: realistic explanation — Greenwood home needs to list first; provide a 60-day
  purchase closing target from the date buyer's home is under contract
- Alternatives: remind agent to discuss bridge loan option with buyer's lender — eliminates
  the contingency and significantly strengthens the offer

---

## Example 5: Multiple Offer Situation — Listing Agent Perspective

**Scenario:** Listing agent is representing a seller. 4 offers have come in on a
Westfield listing priced at $429K. Agent needs to present the offers clearly,
explain the terms, and help the seller make a rational decision.

**Prompt:**
```
/re-offer-writer seller multiple offer review

Property: 2204 Meadow Creek Ln, Westfield IN 46074
List price: $429,000
Days on market: 5

Offer 1: $435,000, conventional, 5% down, $8,600 EM, 10-day inspection, 21-day financing,
  standard appraisal, close 4/30, possession at close, no concessions

Offer 2: $442,000, conventional, 10% down, $8,840 EM, 7-day inspection, 14-day financing,
  $5,000 appraisal gap coverage, close 5/10, possession at close, no concessions

Offer 3: $425,000, FHA, 3.5% down, $4,250 EM, 10-day inspection, 21-day financing,
  standard appraisal, close 5/15, possession at close, $4,000 CC assistance

Offer 4: $438,000, cash, POF provided, $15,000 EM, inspection waived, no financing/appraisal,
  close 4/15, 3-day post-possession, no concessions

Slug: lisa-chen-kw
```

**What the skill should produce:**
- Side-by-side comparison table with all 4 offers
- Net-to-seller calculation for each (subtract concessions from gross)
- Plain-English explanation of each key term for the seller
- Strength ratings: Offer 4 (cash) = ★★★★★; Offer 2 = ★★★★; Offer 1 = ★★★; Offer 3 = ★★
- Analysis narrative:
  - Offer 4 wins on certainty and net at $438K cash (no appraisal risk) with 15-day
    close; 3-day post-possession is a minor inconvenience
  - Offer 2 is the strongest financed offer at $442K with gap coverage and shortened terms
  - Offer 4 vs Offer 2: Seller gets $4K more with Offer 2 but takes on appraisal risk;
    gap coverage caps that risk at $5K; close date 25 days later
  - Offer 3 (FHA) has the lowest net ($421K after CC) and the slowest close — seller should
    only consider if 1 and 2 and 4 all fall through
- Recommendation: present to seller with no explicit instruction to accept one; lay out the
  trade-offs and let seller decide; offer counter if seller wants to test Offer 2 price with
  Offer 4 terms

---

## Example 6: Counteroffer — Seller Wants More

**Scenario:** Seller received a $415K offer on a $429K list. Market is balanced.
Inspection is 10 days, buyer requested $3,000 in closing cost assistance.
Agent needs to draft a clean counteroffer at $425K, no concessions.

**Prompt:**
```
/re-offer-writer counteroffer

Property: 2204 Meadow Creek Ln, Westfield IN 46074
Offer received: $415,000, 10-day inspection, $3,000 CC assistance, conventional financing,
  close 5/15
Seller's position: Will accept $425,000, no closing cost assistance, everything else same
Slug: lisa-chen-kw
```

**What the skill should produce:**
- Clean counter proposal language formatted for transfer to IAR Counter form:
  - Purchase price: $425,000
  - Closing cost assistance: None (seller removes the $3,000 request)
  - All other terms: unchanged (inspection 10 days, financing as offered, 5/15 close)
  - Counter expires: [date + time — recommend 24 hours]
- Brief strategic note: this is a $10K gap from a $14K list reduction request (buyer asked
  for $14K off list via price + concessions); counter at $425K is a reasonable split
- Note that if buyer rejects: next move is at seller's discretion (accept their price, split
  difference at $420K, or let expire)

---

## Example 7: Escalation Clause Scenario

**Scenario:** Buyer loves a home in Hamilton Southeastern schools. Listing agent
confirmed there are 2 other offers already. Buyer's agent wants to use an
escalation clause to win without leaving too much money on the table.

**Prompt:**
```
/re-offer-writer escalation clause for multiple offer

Property: 14088 Foxchase Ln, Fishers IN 46037
List price: $335,000
CMA value: $330,000–$342,000
Buyer: Conventional, pre-approved $360K, 5% down
Competition: 2 other offers confirmed by listing agent
Agent's read: probably sells in the $340K–$350K range

Slug: sarah-jones-fc-tucker
```

**What the skill should produce:**
- Base offer price: $338,000 (slightly above list; not leaving it at list since competition is known)
- Escalation terms:
  - Increment: $2,000 above any bona fide competing offer
  - Ceiling: $352,000 (keeps buyer below $360K pre-approval with buffer; above agent's
    expected market at $350K; signals buyer is committed to win)
  - Documentation: seller must provide copy of competing offer to trigger escalation
- Draft escalation language (ready to add as addendum)
- Warning: ceiling $352K is above CMA high end ($342K); if property appraises at $342K
  and buyer escalates to $352K, they face a $10K appraisal gap — confirm buyer understands
  and has $10K cash available for the gap
- Note: appraisal contingency should remain unless buyer explicitly instructs otherwise

---

## Example 8: Investor Offer — AS-IS Terms

**Scenario:** Investor buyer wants to purchase a tenant-vacated rental property.
Plans to renovate and re-rent. Wants AS-IS terms, fast close, conventional
investment property financing.

**Prompt:**
```
/re-offer-writer investor offer, AS-IS, fast close

Property: 3902 S Meridian St, Indianapolis IN 46217
List price: $264,900 (reduced, 78 DOM)
Buyer: Investor, conventional investment loan, 20% down, pre-approved $280K
Plans to renovate; wants property AS-IS, no repair requests
Wants to close in 21 days
Slug: mike-wright-compass
```

**What the skill should produce:**
- Offer price: $248,000–$252,000 (below current list; 78 DOM supports negotiation)
- AS-IS terms language: "Property is sold in its current condition, AS-IS. Buyer retains
  right to inspect for informational purposes only and will not request repairs, credits,
  or price reductions as a result of the inspection. Buyer's sole remedy if property
  condition is unacceptable is to terminate prior to the end of the inspection period."
- Inspection: keep it (10 days) — even AS-IS buyers should inspect to confirm scope of
  renovation; they just won't use it to negotiate; this is for due diligence only
- Financing: note that investment property financing cannot waive appraisal contingency
  as easily — lender requires appraisal; keep standard appraisal contingency
- Earnest money: $2,500 (1%) — appropriate for investment offer at this price
- Closing: 21 days is aggressive; achievable if lender is ready; note that investment
  property loans can take 25–30 days; advise checking with lender before committing to 21
- Post-closing possession: at close (vacant property; tenant has vacated)

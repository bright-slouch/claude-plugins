# CMA Methodology Reference

Detailed reference for the re-cma skill. Covers adjustment methodology,
comp selection decision trees, absorption rate calculations, paired sales technique,
handling unique and rural properties, new construction competition, and the
CMA-vs-appraisal distinction.

---

## Adjustment Methodology by Submarket

Adjustments convert a comp's sale price into an equivalent price for the subject.
All values below are ranges — use paired sales analysis to calibrate to the
specific neighborhood whenever possible.

### Hamilton County (Carmel, Fishers, Westfield, Noblesville, Zionsville)

| Feature | Typical Adjustment | Notes |
|---|---|---|
| GLA per sqft | $100–$180 | Carmel/Zionsville at high end; Noblesville lower end |
| Bedroom | $5,000–$10,000 | |
| Full bath | $7,000–$12,000 | |
| Half bath | $3,500–$6,000 | |
| Garage stall | $8,000–$15,000 | Heated/finished garage higher |
| Finished basement per sqft | $25–$40 | |
| Lot (suburban, <0.5 ac) | $2–$5/sqft premium | Over lot-size norm for sub |
| Lot (suburban, >0.5 ac) | Paired sales | Scarce; use comps with acreage |
| Kitchen remodel (quality) | $15,000–$30,000 | High-end finishes command premium |
| Bath remodel | $8,000–$18,000 | |
| New roof | $4,000–$8,000 | |
| HVAC replacement | $3,000–$6,000 | |
| Condition (cosmetic) | $5,000–$12,000 | |
| Condition (systems deferred) | $12,000–$25,000 | |
| Pool (in-ground) | +$0 to –$10,000 | Negative in some areas; verify locally |
| School district premium | $20,000–$50,000+ | Carmel Clay and HSE command most; quantify from pairs |

### Marion County (Indianapolis)

Highly neighborhood-dependent. Adjustments vary by township and micro-market.
Washington Township (north Indianapolis, Meridian-Kessler, Broad Ripple) is closest
to Hamilton County in adjustment values. Southside and east-side neighborhoods have
compressed per-sqft values.

| Feature | Typical Adjustment | Notes |
|---|---|---|
| GLA per sqft | $80–$140 | North Marion at high end |
| Bedroom | $3,000–$7,000 | |
| Full bath | $5,000–$10,000 | |
| Half bath | $2,500–$4,500 | |
| Garage stall | $5,000–$10,000 | |
| Finished basement per sqft | $20–$35 | |
| Condition (cosmetic) | $5,000–$10,000 | |
| Condition (systems deferred) | $10,000–$20,000 | |

### Hendricks County (Avon, Brownsburg, Plainfield)

Avon and Brownsburg school districts command a modest premium over Plainfield.
New construction competition is active in all three markets — always note builder
inventory when pricing resale.

| Feature | Typical Adjustment | Notes |
|---|---|---|
| GLA per sqft | $90–$140 | |
| Bedroom | $4,000–$8,000 | |
| Full bath | $6,000–$10,000 | |
| Garage stall | $7,000–$12,000 | |
| Finished basement per sqft | $22–$38 | |

### Johnson County (Greenwood, Franklin)

Center Grove school district commands a 10–15% premium over other Johnson County
schools. New construction is active in Center Grove corridor.

| Feature | Typical Adjustment | Notes |
|---|---|---|
| GLA per sqft | $85–$130 | Center Grove at high end |
| Bedroom | $3,500–$7,000 | |
| Full bath | $5,500–$9,000 | |
| Garage stall | $6,000–$10,000 | |
| Finished basement per sqft | $20–$35 | |

### Boone County (Lebanon, Zionsville area, rural)

Zionsville portion of Boone County often prices similarly to Hamilton County
(Carmel Clay schools influence). Rural/Lebanon areas have significantly lower
per-sqft values. Acreage commands a per-acre premium that must be extracted
via paired sales.

| Feature | Typical Adjustment | Notes |
|---|---|---|
| GLA per sqft | $85–$160 | Zionsville portion higher; Lebanon/rural lower |
| Land value (rural) | $10,000–$20,000/acre | Verify from paired sales |
| Well/septic vs city | $0 | Standard in rural areas; only adjust if mixed comps |
| Outbuilding/shop (1,200–2,400 sqft) | $15,000–$40,000 | Condition-dependent |

---

## Comp Selection Decision Tree

Use this logic sequence when evaluating whether a comp is valid:

```
1. Same property type?
   YES → continue
   NO  → exclude (SFR ≠ condo ≠ townhome unless noted with major adjustment)

2. Arm's-length transaction?
   YES → continue
   NO  → exclude (REO, short sale, estate, builder-to-buyer with incentives)

3. Within 90 days of list date?
   YES → accept (Tier 1)
   NO, within 180 days → accept with date flag (Tier 2)
   NO, older than 180 days → use only if no alternatives; note trend adjustment

4. Within 1 mile (suburban) or 3 miles (rural)?
   YES → continue
   NO, within 2 miles (suburban) → accept with location flag
   NO, beyond → use only if unavoidable; explain similarity rationale

5. Within 20% of subject GLA?
   YES → continue
   NO → flag; ensure GLA adjustment does not exceed 10% of comp sale price

6. Same school district?
   YES → continue (Tier 1)
   NO, adjacent district → accept with required school district adjustment
   NO, distant district → exclude

7. HOA status match?
   YES → continue
   NO  → apply HOA capitalization adjustment (monthly dues × 100)

8. Net adjustment within 10% of comp sale price?
   YES → comp is reliable
   NO  → comp may be too dissimilar; flag and consider replacing
```

### When to Include Pending Sales

Pending sales are not confirmed prices. Use them as directional indicators only:
- Include in a "market direction" note section
- Do not weight them equally with closed comps
- Do not use a pending sale as one of your primary 3 comps
- Note: if a pending sale is significantly above or below closed comps, discuss
  the discrepancy with the agent — it may reflect market movement

### How to Weight Comps

Not all comps deserve equal weight. Weight more heavily when a comp is:
- More recent (closed within 60 days > 60–90 days > 90–180 days)
- More similar in size (within 5% GLA > 10% > 20%)
- Geographically closer (< 0.5 miles > 0.5–1 mile > 1–2 miles)
- Same school district with no boundary adjustment required
- Lower net adjustment (smaller total adjustment = more similar property)

When expressing weighted average, you may use a simple weight scale:
- Tier 1 comp (recent, close, similar): weight 3
- Tier 2 comp (one flag): weight 2
- Tier 3 comp (two flags): weight 1

---

## Absorption Rate Calculation Walkthrough

**Formula:**
```
Months of Supply = Active Listings ÷ (Closed Sales in Last 90 Days ÷ 3)
```

**Example:**
- Active 3–4BR listings in zip 46037: 8
- Closed 3–4BR in last 90 days: 18
- Monthly sales rate: 18 ÷ 3 = 6/month
- Months of supply: 8 ÷ 6 = 1.33 months → Seller's market

**Interpretation:**

| Months of Supply | Market | Strategy Implication |
|---|---|---|
| < 2 months | Very strong seller's | Multiple offers likely; at-market may generate above-list |
| 2–3 months | Seller's market | Strong demand; at-market recommended |
| 3–4 months | Slightly favors sellers | At-market; test the upper end if property is updated |
| 4–6 months | Balanced | At-market; negotiation expected |
| 6–9 months | Buyer's market | Aggressive pricing advised; overpricing = longer DOM |
| > 9 months | Strong buyer's market | Aggressive; expect price reductions without it |

**Supporting metrics to include alongside absorption rate:**
- Average DOM of closed comps: < 14 days = hot; 14–30 days = normal; > 45 days = soft
- List-to-sale price ratio: > 100% = buyers are bidding over; < 98% = buyers are negotiating down
- Price reduction frequency: what percentage of closed comps had a price reduction?

---

## Paired Sales Analysis Technique

Use paired sales when you need to isolate the value contribution of a single
feature (lot size, garage, finished basement) that is inconsistent across comps.

**How it works:**
Find two sales that are identical in all features except the one you are measuring.
The price difference is the market's implied value for that feature.

**Example — isolating acreage value in Boone County:**

- Sale A: 3BR/2BA ranch, 1,580 sqft, Lebanon IN, city utilities, 0.25 acres → $249,000
- Sale B: 3BR/2BA ranch, 1,600 sqft, Lebanon IN, well/septic, 3.1 acres → $299,000

Price difference: $50,000
Acreage difference: 2.85 acres
Implied per-acre value: $50,000 ÷ 2.85 = ~$17,500/acre

Apply this rate to the subject's acreage above the standard suburban lot.

**Limitations of paired sales:**
- Rarely find a perfect pair — note and adjust for any remaining differences
- The more different the two sales are beyond the target feature, the less reliable
  the extraction
- Always use multiple pairs when available and average the result
- Disclose the technique limitation in the CMA narrative when the comp pool is thin

---

## How to Handle New Construction Competing Inventory

When a builder is actively selling nearby, this is a market condition, not a
comp adjustment. Handle it as follows:

**Do not use builder sales as comps** unless:
- The builder sale is listed on MLS as a standard transaction
- You can confirm the final sale price reflects no non-MLS incentives
  (closing cost credits, appliance packages, rate buydowns not visible in price)

**In the pricing narrative, address builder competition explicitly:**

1. State what the builder is selling and at what price
2. State what builder incentives exist and their approximate value
3. Articulate the resale advantages the seller can offer:
   - Immediate occupancy (vs 6–8 month builder timeline)
   - Known condition of home and systems
   - Established yard and landscaping
   - No risk of construction delays or spec changes
   - Seller may include updates, appliances, or personal property
4. Articulate the resale disadvantage:
   - Buyer cannot customize finishes on a resale
   - New construction typically carries a new home warranty
   - Builder may have more marketing exposure and a model home
5. Recommended pricing approach: price at or slightly below builder base (before
   incentives) to reflect immediate-delivery premium while not directly competing
   on price with the new product

---

## How to Handle Unique Properties and Rural Acreage with No Good Comps

When the subject property is genuinely unique (historic home, rural acreage,
unusual architecture, hobby farm, mixed-use residential), use these techniques:

### Step 1: Decompose the Property

Separate the value components:
- Land value (from land sales or paired sales)
- Dwelling value (house-only comps in the area)
- Outbuildings/improvements value (paired sales or cost approach as reference)

### Step 2: Collect Reference Data

Even if no direct comp exists, gather:
- Nearest subdivision sales with similar house specs (ignore the land difference)
- Recent vacant land sales in the area (derive per-acre value)
- County assessor's market value as a sanity check (not a comp, but a floor)
- Any sales of similar unique properties within a 10-mile radius, even if 2–3 years old

### Step 3: Build the Value Opinion

Add the components:
```
Estimated Value = Dwelling Value + Land Value + Outbuilding/Improvement Value
```

Adjust dwelling value from house-only comps for condition and feature differences.
Apply the per-acre land value from Step 2.
Apply a reasonable cost-minus-depreciation for significant outbuildings.

### Step 4: Disclose the Limitation

Always include a confidence statement in the CMA output when comp support is limited:

> *Due to the unique nature of this property and limited availability of directly
> comparable closed sales, this CMA provides a value estimate range with wider
> uncertainty than a typical suburban analysis. The agent recommends discussing
> with the seller whether a licensed appraisal may provide additional confidence
> for pricing this property.*

---

## CMA vs. Appraisal — Key Differences

Agents must understand and communicate this distinction to sellers.

| Dimension | CMA | Licensed Appraisal |
|---|---|---|
| Who prepares it | Licensed real estate agent | State-certified or state-licensed appraiser |
| Legal standing | None — informational only | Accepted by lenders; legal document |
| Methodology | Agent judgment, market expertise, comp selection | USPAP-governed uniform standards |
| Data inspection | Agent reviews MLS data; typically no interior inspection | Appraiser physically inspects property |
| Adjustments | Agent applies judgment; ranges vary | Appraiser documents methodology; must be supportable |
| Purpose | Listing strategy and seller education | Lender underwriting, estate, tax, legal proceedings |
| Cost | Free (agent provides as part of service) | $400–$700+ depending on property complexity |
| Binding | Not binding on any party | Binding for lender; subject to review |

**When to recommend a licensed appraisal:**
- Property is unique or rural with very limited comps
- Seller and agent cannot agree on value after reviewing comps
- Estate settlement or divorce requires an official number
- Seller wants to challenge a tax assessment
- Property has complex improvements (commercial components, multiple structures)

**What the appraiser will do differently:**
- Physically inspect the interior and document condition, room count, finish quality
- Apply USPAP methodology including cost approach and income approach where applicable
- Provide written report with all adjustments documented and supportable
- May not use the same comps the agent selected — appraisers have their own criteria
- Will adjust for market conditions (time adjustments) if comps are older than 90 days

**Why CMAs often differ from appraisals:**
- CMAs reflect current market pricing momentum; appraisals reflect historical evidence
- In rising markets, CMAs may be higher (ahead of the evidence); in falling markets, lower
- Appraiser adjustments are capped by supportable market evidence; agent adjustments are judgments
- Appraisers must account for any lender overlays; agents do not

---

## Sources for Comp Data

**Primary (required):**
- MIBOR BLC (MLS) — closed, pending, and active listings; most complete Indiana data
- Pull from BLC first. BLC is the authoritative source for MIBOR territory.

**Cross-check (recommended):**
- Marion County Assessor / Hamilton County Assessor public records — confirm sale prices,
  actual square footage, lot size
- Indiana Gateway (county assessor data) — useful for properties in rural counties with
  limited BLC history

**Sanity check only (never primary):**
- Zillow — AVM estimates can be useful as a range check but are unreliable for individual
  property pricing; do not cite Zillow as a comp or as evidence of value
- Redfin — same limitation; use as a directional sanity check only
- Realtor.com — same limitation

**What to say to a seller who cites Zillow:**
> "Zillow's Zestimate is an automated model that cannot inspect the property, account for
> your specific updates, or reflect what buyers in your neighborhood are actually paying
> right now for comparable homes. Our CMA uses actual closed sale data from the MLS and
> reflects adjustments specific to your home. Let me show you the evidence."

---

## Glossary of CMA Terms

**Absorption rate:** Rate at which available homes in a market are sold. Expressed in months
of supply. Lower = seller's market.

**Arm's-length transaction:** A sale between unrelated, unaffiliated parties acting in their
own self-interest. Required for a comp to be valid.

**Gross Living Area (GLA):** Finished above-grade living space in square feet. Does not include
basement, garage, or unfinished areas. Standard measure for residential adjustments.

**List-to-sale ratio:** Final sale price divided by list price. Above 100% = sold over asking.
Trailing 90-day ratio indicates current buyer aggression.

**Months of supply:** See absorption rate. The number of months it would take to sell all
current listings at the current sales pace if no new listings came to market.

**Net adjustment:** The total of all positive and negative adjustments applied to a comp.
Industry practice: flag if net adjustment exceeds 10% of comp sale price.

**Paired sales analysis:** Technique to isolate the value contribution of a single feature
by finding two otherwise similar sales that differ only in that feature.

**Price per square foot ($/sqft):** Useful as a cross-check; use with caution as the primary
metric since it does not account for absolute size (smaller homes often have higher $/sqft).

**Seller's market:** Market condition where demand exceeds supply; typically under 3 months
of supply. Sellers have negotiating leverage.

**USPAP:** Uniform Standards of Professional Appraisal Practice. The regulatory framework
governing licensed appraisers. CMAs are not subject to USPAP.

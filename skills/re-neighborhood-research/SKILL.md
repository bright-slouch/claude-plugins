---
name: re-neighborhood-research
description: >-
  Local area expert report compiler. Generates a buyer-ready neighborhood
  research report covering schools, taxes, commutes, HOA, flood zones,
  utilities, and amenities — personalized to the agent's brand and
  the buyer's specific priorities.
  Triggers: "neighborhood report", "tell me about this area", "what's the neighborhood like",
  "school ratings", "research this neighborhood", "area report", "commute times",
  "what's it like to live in", "neighborhood info", "local area research",
  "property taxes in", "HOA info", "flood zone check".
argument-hint: "[neighborhood, city, or zip code + buyer profile]"
---

# Neighborhood Research Skill

## Overview

`re-neighborhood-research` compiles a comprehensive, buyer-ready local area report for any Central Indiana neighborhood, zip code, or city. It draws on web search for current data, Indiana-specific reference files for local context, and the agent's config to produce a polished, on-brand report that positions the agent as the market authority.

Every report is filtered through the buyer's stated priorities — a family relocating from Chicago gets a school-focused deep dive; a young professional buying in Broad Ripple gets walkability scores and commute times to Salesforce Tower. The same skill, tailored output.

---

## Persona

You are the agent's local market expert. You know Central Indiana geography deeply — which townships have what service structures, which school districts feed where, how proximity to the Monon Trail affects Carmel property values, why a buyer might choose Hamilton County vs. Boone County for the same budget. You know that Center Grove Schools command a 10-18% premium in Johnson County, that I-69 and US-31 behave very differently at 8 AM, and that "city of Carmel" does not mean "Carmel Clay Schools" in every case.

You turn raw research into a polished, buyer-ready report that makes the agent look like the most knowledgeable person in the room.

---

## When to Use

- Buyer consultation prep — before showing a neighborhood for the first time
- Relocation buyers — especially those moving from out of state
- Comparison shopping — buyer weighing two or more areas
- Investor research — rental demand, tax context, tenant pool
- Social media content — teaser reports positioning agent as local expert

---

## Quick Start

```
/re-neighborhood-research — Carmel 46032, family of 4 relocating from Chicago, schools are top priority
```
```
/re-neighborhood-research — Broad Ripple area, first-time buyer, young professional at Salesforce Tower
```
```
/re-neighborhood-research — Compare Westfield vs Noblesville for a family with a $450K budget
```
```
/re-neighborhood-research — Hendricks County rural property near Brownsburg, first-time buyer, well/septic okay
```

---

## Step-by-Step Workflow

### Step 1: Load Agent Config

Load the following config files before producing any output:

- `~/Skills/real-estate-plugin/config/[slug]/agent-profile.yaml` — voice, tone, brand identity. **Always load first.**
- `~/Skills/real-estate-plugin/config/[slug]/market-areas.yaml` — which areas the agent knows well; flag if the requested area is outside the agent's primary territory
- `~/Skills/real-estate-plugin/config/[slug]/brand-kit.yaml` — colors, tagline, hashtags, compliance disclaimer for branded report header/footer

If the agent config is not found after trying all resolution methods above, you MUST respond with a visible message to the user. Do NOT silently redirect, do NOT produce empty output, and do NOT chain to another command. Instead, respond with:

> I'd be happy to help with that! Before I can run this skill, I need to load your agent profile.
>
> Please provide one of the following:
> - Your **full name** as registered in the Agent Registry
> - Your **email address**
> - Your **config slug** (e.g., `jane-smith-fc-tucker`)
>
> Or if you haven't set up your profile yet, run **/re-agent-setup** to get started (takes about 10 minutes).

Then STOP and wait for the user to respond. Do not proceed to subsequent steps.

---

### Step 2: Identify the Area and Buyer Profile

**Area identification:**
- Accept neighborhood name, city, zip code, or address-level input
- If city or zip provided: confirm the specific part of the area (e.g., "Westfield 46074" covers both established neighborhoods and new construction corridors — which is the buyer looking at?)
- If comparison requested: confirm both areas before proceeding

**Buyer profile:**
Establish buyer priorities before building the report. Ask if not provided:

| Buyer Type | Lead With |
|---|---|
| Family with school-age children | School district, district boundaries, elementary assignment |
| Young professional | Commute, walkability, Monon/trail access, nightlife/dining |
| Relocation buyer | Full overview — unfamiliar with Indianapolis geography |
| Downsizer | HOA amenities, maintenance-free options, tax context |
| Investor | Rental demand, tenant profile, HOA rental restrictions, tax rates |
| Rural/land buyer | Well/septic, acreage zoning, commute reality check |

---

### Step 3: School Research

**Process:**
1. Identify the school district that serves the specific address or zip. Do NOT assume city name = district name.
2. Name the elementary, middle, and high school(s) for that location.
3. Note GreatSchools rating if available — include the required caveat (see below).
4. Include district contact info for enrollment verification.

**Required caveat for GreatSchools ratings:**
> "GreatSchools ratings provide a directional sense of a school's academic profile and are one data point among many. Ratings shift over time and do not capture teaching culture, extracurriculars, or fit for a specific child. We recommend touring schools and speaking with current parents. Contact the district enrollment office to confirm your specific address falls in the district."

**Key district lookup rule:** School districts in Central Indiana do NOT follow city boundary lines. A home in "the City of Carmel" could be in Carmel Clay Schools, Hamilton Southeastern Schools, or Westfield-Washington Schools depending on its precise location. Always verify via the district's address lookup tool or the county assessor.

**Reference:** `~/Skills/real-estate-plugin/re-neighborhood-research/references/central-indiana-school-districts.md`

---

### Step 4: Property Tax Research

**Indiana property tax mechanics:**
- Assessed value is set approximately at market value (reassessed annually)
- Homestead exemption significantly reduces the effective tax bill for owner-occupants
- County tax rates vary; Marion County is generally highest, Boone County lowest in the core metro
- Provide estimated annual tax range for the subject price point; always add the verify-with-county caveat

**Calculation example to provide:**
```
Example: $450,000 home in Hamilton County
Assessed Value: ~$450,000
Standard Homestead Deduction: $45,000
Supplemental Homestead Deduction: 35% of remaining AV
Estimated net taxable value after deductions: ~$263,250
Estimated annual tax at 1.5% effective rate: ~$3,950
(Verify with Hamilton County Auditor — rates vary by exact location and taxing district)
```

**Reference:** `~/Skills/real-estate-plugin/re-neighborhood-research/references/indiana-tax-system.md`

**Township note:** Indiana has township assessors in some counties and county assessors in others. Some services (fire protection, poor relief, cemeteries) are funded at the township level — this can affect total tax rate in unincorporated areas. Explain this when relevant (rural Hendricks, Johnson, or Shelby County properties).

**TIF districts:** Tax Increment Financing districts exist in many redevelopment areas. Property taxes in a TIF district are structured differently — the increment above the base assessment goes to the TIF fund, not general county/school levies. This can affect schools' share of the tax base. Mention when researching urban redevelopment areas or new commercial corridors.

**Annexation:** Active annexation zones exist around growing cities (Westfield, Avon, Noblesville). A property currently in unincorporated Hamilton County adjacent to Westfield may be annexed within 5-10 years, potentially changing tax rates and service levels. Note when relevant.

---

### Step 5: Commute Research

**Standard employer reference points:**
- Downtown Indianapolis (Salesforce Tower, State Capitol, IU Health): use I-465/downtown as the hub
- Eli Lilly campus: 893 Delaware St, Indianapolis (near I-65/downtown)
- IU Health North Hospital: 11700 N Meridian St, Carmel
- Cummins HQ (Columbus): SR-46 corridor, 45 min south of Greenwood
- Honda Manufacturing (Greensburg): US-421 S, Decatur County — note this is a 55-min commute from southeast suburbs
- Subaru (Lafayette): US-52 NW, ~60 min from northwest suburbs; relevant for Boone/Tippecanoe commuters
- Amazon Plainfield fulfillment centers: I-70/Reagan Pkwy interchange

**Highway corridor context:**
- I-465 is the outer loop — all radial highways connect to it
- US-31 (Carmel/Westfield to downtown): historically congested; partially improved with grade separations between SR-32 and I-465
- I-69 (Fishers/Noblesville to downtown): congested at morning peak, especially SR-37 merge
- I-74 (Brownsburg/Avon to downtown): generally better travel times than north corridors at equivalent distance
- I-65 S (Greenwood/Franklin to downtown): moderate; US-31 S is an alternative
- SR-37 (Noblesville to Fishers): being upgraded to I-69; ongoing construction

**IndyGo:** Bus service only; no commuter rail in Indianapolis. Red Line (rapid transit) serves US-31 corridor from Broad Ripple to Greenwood. Limited utility for suburban commuters. Note this honestly.

---

### Step 6: HOA Research

**How to find HOA information:**
1. MLS/BLC listing notes — agent remarks often include HOA name, monthly fee, and management company
2. County Recorder's office — Declaration of Covenants, Conditions & Restrictions (CC&Rs) are recorded documents; search by subdivision name
3. Indiana Secretary of State — HOA corporation registration (most are Indiana nonprofit corporations)
4. Ask the listing agent directly for HOA documents (seller must typically provide these)
5. HOA management company — many Central Indiana HOAs use companies like Associa, FirstService, or local managers

**Key documents to review:**
| Document | What to Look For |
|---|---|
| CC&Rs | Use restrictions, architectural standards, rental restrictions, pet rules |
| Bylaws | Board structure, meeting requirements, enforcement process |
| Current budget | Annual budget, reserve fund balance, reserve study date |
| Last 12 months meeting minutes | Ongoing disputes, deferred maintenance, special assessments discussed |
| Rules and Regulations | Day-to-day rules that CC&Rs delegate to the board |

**Red flags to flag for buyers:**
- Reserve fund below 10% of annual budget (underfunded — risk of special assessment)
- Pending or recent special assessments
- Litigation involving the HOA
- Rental restrictions that would prevent future renting of the property
- No reserve study in the last 5 years

**Note:** Indiana HOA law (IC 32-25.5) provides buyer the right to receive HOA documents. The seller is required to disclose HOA information on the Seller's Disclosure form.

---

### Step 7: Flood Zone Research

**How to look up a specific address:**
- FEMA Flood Map Service Center: msc.fema.gov
- Enter the property address to pull the Flood Insurance Rate Map (FIRM)
- Report the flood zone designation to the buyer

**Zone key:**
| Zone | Meaning | Insurance Impact |
|---|---|---|
| Zone X (unshaded) | Minimal flood hazard | No flood insurance required by lenders |
| Zone X (shaded) | Moderate flood hazard | No requirement, but consider voluntary coverage |
| Zone AE | 1% annual chance flood (100-year floodplain) | Flood insurance REQUIRED for federally-backed mortgages |
| Zone A | 1% annual chance; no base flood elevation determined | Required; higher rates due to uncertainty |
| Zone VE | Coastal — not applicable in Indiana | N/A |

**Central Indiana context:**
- White River, Fall Creek, Eagle Creek, and Buck Creek corridors have documented floodplain areas
- Properties near Geist Reservoir, Morse Reservoir, Eagle Creek Reservoir: waterfront may be Zone AE
- Floodplain maps are updated periodically — Letters of Map Amendment (LOMA) can change a property's designation
- If Zone AE: refer buyer to their lender and insurance agent for flood insurance quote before making an offer

---

### Step 8: Utilities and Municipal Services

**Utility providers by area (approximate — verify with listing or municipality):**

| Area | Electric | Gas | Water/Sewer |
|---|---|---|---|
| Indianapolis (Marion) | AES Indiana (Indianapolis Power & Light) | Citizens Energy / Vectren (south) | Citizens Water |
| Carmel / Hamilton County | Duke Energy | Citizens Energy | Carmel Utilities / Hamilton County Regional |
| Fishers | Duke Energy | Citizens Energy | Fishers Utilities |
| Noblesville | Duke Energy | Citizens Energy | Noblesville City Utilities |
| Westfield | Duke Energy | Citizens Energy | Westfield Water & Sewer |
| Hendricks County | Duke Energy | Vectren | Varies — Avon, Brownsburg, Plainfield each have municipal utilities; rural = well/septic |
| Johnson County | AES Indiana | Citizens Energy / Vectren | Greenwood City Utilities; rural Johnson County = well/septic common |
| Boone County | Duke Energy | Citizens Energy | Lebanon utilities; Zionsville city water; rural Boone = well/septic common |

**Well and septic note (critical for rural buyers):**
Properties on well and septic (common in rural Hendricks, Johnson, Shelby, Morgan, Boone counties) have no municipal utility bill for water/sewer — but require:
- Well water testing before closing (strongly recommended; include in offer)
- Septic inspection (in Indiana: seller is not required to perform a septic inspection unless agreed in contract — recommend buyer negotiate this)
- Future maintenance costs are buyer's responsibility
- Well yield/recovery rate matters for larger households

---

### Step 9: Local Context and Amenities

Draw from `~/Skills/real-estate-plugin/config/[slug]/market-areas.yaml` and `~/Skills/real-estate-plugin/references/central-indiana-market-context.md` to add authentic local color.

**Standard amenity categories:**
- Trails and parks: Monon Trail (runs through Carmel/Westfield/Broad Ripple), Nickel Plate Trail (Noblesville/Fishers), White River Greenway, Eagle Creek Park, Morse Reservoir, Geist Reservoir
- Dining/entertainment districts: Carmel Arts and Design District, Carmel Midtown, Fishers Nickel Plate District, Broad Ripple Village, Fountain Square, Mass Ave, Downtown Indy
- Shopping: Hamilton Town Center (Noblesville), Clay Terrace (Carmel), Metropolis (Plainfield), Greenwood Park Mall, The Fashion Mall at Keystone
- Health systems: IU Health North (Carmel), Ascension St. Vincent (Carmel/Indy), Community Health (multiple)

**Add what makes the specific area distinctive.** If the agent has farm area notes in market-areas.yaml for this neighborhood, include them as local insight.

---

### Step 10: Compile and Format the Report

**Report structure** (lead with buyer's top priority):

```
[AGENT NAME] | NEIGHBORHOOD RESEARCH REPORT
[AGENT TAGLINE] | [DATE]

AREA OVERVIEW
[2-3 sentences: what makes this area what it is]

[BUYER'S #1 PRIORITY SECTION — e.g., SCHOOLS, COMMUTE, etc.]
[Remaining sections in order of buyer priority]

IMPORTANT NOTES
[Caveat on data currency, verify-with-source reminders]

[AGENT DISCLAIMER FROM brand-kit.yaml]
```

**Three output formats:**

**Full Written Report** (default — shareable, PDF-ready)
Complete narrative with all sections. Professional tone. Agent name and branding in header/footer. Recommended for relocation buyers and serious consultation prep.

**Bullet Summary** (agent reference)
One-page quick-reference version. Bullet points only. For agent to use verbally in showing conversations. Not branded.

**Social Media Version**
Instagram/Facebook teaser. 150-200 words. Lead with one compelling local fact. End with CTA + agent hashtags from brand-kit.yaml. Do not include tax rate specifics or data that needs caveat verification — keep social content to the "feel" of the neighborhood.

---

## Fair Housing Compliance — Critical

**NEVER include in any report or communication:**
- Commentary on neighborhood racial or ethnic composition
- References to the demographic makeup of schools or student populations as a proxy for neighborhood quality
- Religious institutions as neighborhood descriptors
- Language implying that some neighborhoods are "safer" based on implied demographic characteristics
- Country of origin or national origin references
- Any framing of school quality that implies demographic desirability

**WHAT IS FINE:**
- School academic ratings (GreatSchools, state accountability grades) with the required caveat
- Test score data published by school districts
- Commute times, walkability, trail access, park proximity
- Tax rates, HOA fees, utility providers
- Named amenities (Monon Trail, Grand Park, Clay Terrace)
- Price range data from MLS
- General character descriptors tied to physical features ("historic bungalows," "new construction," "walkable to downtown")

**Reference:** `~/Skills/real-estate-plugin/references/real-estate-vocabulary.md` for approved language.

If a buyer directly asks about neighborhood demographics, respond: "Fair housing laws require that I focus on property features and neighborhood amenities rather than demographic data. I'd encourage you to visit the area at different times of day to get a feel for it. I'm happy to share school performance data, commute information, or local amenities."

---

## What NOT to Do

- **Never guarantee a tax rate** without the caveat to verify with the county auditor — rates change annually and vary by exact taxing district
- **Never state a school district assignment** without noting it must be verified — city name does not equal school district
- **Never use GreatSchools ratings as the sole measure of a school** — include the required directional caveat
- **Never characterize neighborhood demographics** — see Fair Housing section above
- **Never use school ratings as a proxy for neighborhood demographic desirability** — this is a fair housing violation
- **Never omit the flood zone check** for properties near water bodies, low-lying areas, or areas with known flooding history
- **Never advise a buyer to skip a septic inspection** on a property served by a private septic system
- **Never present a CMA or neighborhood report as an appraisal** — these are informational; buyer should get a licensed appraisal as part of the transaction
- **Never skip the legal disclaimer** on the full written report

---

## Integration Points

### Config Files Used
- `agent-profile.yaml` — agent voice, tone, name, credentials for report byline
- `brand-kit.yaml` — colors, tagline, hashtags, compliance disclaimer text
- `market-areas.yaml` — local knowledge, farm area notes

### Reference Files Used
- `~/Skills/real-estate-plugin/re-neighborhood-research/references/central-indiana-school-districts.md`
- `~/Skills/real-estate-plugin/re-neighborhood-research/references/indiana-tax-system.md`
- `~/Skills/real-estate-plugin/references/central-indiana-market-context.md`
- `~/Skills/real-estate-plugin/references/real-estate-vocabulary.md`

### Related Skills
- `/re-buyer-consultation` — feeds buyer profile and priority list into this skill
- `/re-cma` — pairs with this report (market data + neighborhood context = full buyer prep package)
- `/re-client-communication` — use to email the finished report to the buyer
- `/re-offer-writer` — neighborhood report becomes supporting context when writing the offer

### Example Prompts
See `~/Skills/real-estate-plugin/re-neighborhood-research/examples/example-prompts.md`

---

## Legal Disclaimer

*This output is for guidance and informational purposes only. It does not constitute legal advice. School, tax, flood zone, utility, and HOA data are provided for informational purposes and must be independently verified by the buyer prior to closing. Tax rates, school district assignments, flood zone designations, and HOA terms can change. Agents should direct buyers to verify all data with the relevant county auditor, school district, FEMA, and HOA directly. This report does not constitute an appraisal. Always comply with Indiana Real Estate Commission rules, your brokerage's policies, and federal Fair Housing Act requirements.*

# re-buyer-consultation — Example Prompts

Six realistic buyer consultation scenarios covering the most common buyer profiles in Central Indiana.

---

## Example 1: First-Time Buyers — Hamilton County

**Scenario:** Young couple buying their first home. Pre-approved, targeting Westfield
or Noblesville, school district is important (they plan to start a family). Agent
wants discovery questions, buyer presentation, and search criteria setup.

**Prompt:**
```
/re-buyer-consultation

Buyers: Sarah and Tom Kellerman, first-time buyers
Slug: sarah-jones-fc-tucker
Budget: $300,000–$350,000
Pre-approved: Yes — First Internet Bank, conventional loan, $350K pre-approval
Target area: Hamilton County — Westfield or Noblesville
School district: Important (planning family); Westfield or Noblesville schools preferred
Timeline: Flexible, want to close by summer
Needs: 3BR min, 2-car garage, some yard for a dog, move-in ready preferred
```

**What the skill should produce:**
- Branded discovery questionnaire adapted for first-time buyers (include school district
  question prominently given stated priority)
- Note that Westfield Washington schools vs Noblesville schools carry different price
  premiums — ask agent if buyer understands the boundary distinction
- Buyer presentation populated with Sarah Jones' name, brokerage, and methodology
- MLS search criteria summary: Hamilton County, Westfield + Noblesville zip codes,
  Westfield Washington + Noblesville school districts, $300K–$350K, 3BR+, 2-car garage
- Buyer agency agreement talking points (this is their first appointment — normalize the
  form, don't surprise them with it at the end)
- No lender referral needed since buyer is already pre-approved; note their lender name
  in the summary

---

## Example 2: Move-Up Buyer — Has a Home to Sell

**Scenario:** Current homeowner in Greenwood wants to move up to Carmel area.
Has approximately $200K equity in current home. Needs to sell first — or does she?
Agent needs to walk through the contingency conversation and financing options.

**Prompt:**
```
/re-buyer-consultation

Buyer: Jennifer Walsh, move-up buyer
Slug: lisa-chen-kw
Current home: Greenwood (Center Grove schools) — approx value $340K, payoff ~$140K
Target: Carmel area, $550K–$650K budget
Pre-approved: No — hasn't started financing yet
Needs: 4BR, 3BA, primary on main floor, 3-car garage, Carmel Clay schools
Timeline: Wants to close this spring; is nervous about bridge timing
```

**What the skill should produce:**
- Discovery questionnaire with move-up-specific additions: current home sale timeline,
  willingness to carry two mortgages briefly, rent-back or bridge loan knowledge
- Financing education section covering: home sale contingency mechanics, bridge loans
  (how they work, cost range), simultaneous close vs sale-first strategy
- Decision framework: Jennifer has ~$200K equity — she may qualify to buy without selling
  first if income supports two payments; flag this for lender conversation
- Lender referral from lisa-chen-kw vendor-network.yaml with note that bridge loan
  experience is preferred
- Realistic timeline worksheet: if she lists in March, closes in May, that gives ~30-45
  days to find and close on Carmel home
- Talking points for the "do I have to sell first?" conversation

---

## Example 3: VA Buyer — Relocation from Out of State

**Scenario:** Retired Army sergeant relocating from Kentucky. Not familiar with
Indianapolis geography. VA eligible, no Indiana home to sell. Relocation timeline
is 60–90 days. Has VA loan experience but not in Indiana.

**Prompt:**
```
/re-buyer-consultation

Buyer: Marcus Williams, retired military relocating from Elizabethtown KY
Slug: dan-riley-remax
VA eligible: Yes — confirmed by buyer; no current active VA loan
Pre-approved: Not yet — needs Indiana VA lender
Target: Not sure — wants good schools, < 30 min commute to Fort Benjamin Harrison area
Budget: $350K–$425K
Timeline: PCS orders for August 1 move-in; firm deadline
COE: Buyer thinks he has it from previous loan; needs to verify
```

**What the skill should produce:**
- Discovery questions emphasizing geography (buyer has no Indiana knowledge)
- Recommend running re-neighborhood-research for: Lawrence, Fishers, Noblesville,
  and Castleton areas — all within 30 min of Fort Ben Harrison
- VA loan education summary: Indiana-specific notes, VA MPR considerations, funding fee
  info (ask about any disability rating for potential waiver)
- COE guidance: instruct buyer to retrieve VA.gov eBenefits portal or have lender pull it
- VA-experienced lender referral from vendor-network.yaml with NMLS #
- Pre-approval checklist: VA-specific additions (DD-214, COE, service history if Guard/Reserve)
- Buyer agency agreement note: property-specific agreement suggested for first remote
  virtual showing if buyer can't travel to sign before first tour
- Timeline warning: 60-90 days is tight for VA loans — appraisal takes 1-2 weeks,
  VA MPR repairs can add time; set expectations accordingly

---

## Example 4: Investor — Multi-Family or Rental Property

**Scenario:** Current homeowner expanding into investment real estate. Wants a
rental property — either single-family or small multi-family (2-4 units). First
investment purchase. Agent needs to explain the different financing rules and
shift the consultation to investment-focused discovery.

**Prompt:**
```
/re-buyer-consultation

Buyer: David Park, existing FC Tucker client, first investment purchase
Slug: sarah-jones-fc-tucker
Target: SFR or duplex/small multi-family for rental income
Budget: $200K–$280K
Pre-approved: Yes for SFR at $280K; has NOT asked about investment/multi-family financing yet
Target areas: Not sure — wants best rental yield in Hamilton or Marion County
Timeline: No rush, 3-6 months
Current situation: Owns primary in Carmel (no plans to sell)
```

**What the skill should produce:**
- Discovery questionnaire adapted for investors: target cap rate, desired cash flow
  (positive cash flow from day 1 vs appreciation play), property management plan
  (self-manage vs PM company), renovation tolerance, tenant profile preference
- Financing education: investment property financing rules differ from primary:
  - Conventional investment loans: typically 15–25% down required; higher rates
  - 2-4 unit properties: if buyer occupies one unit, FHA (3.5% down) or conventional
    owner-occupied rates apply; clarify David's intention
  - DSCR loans: debt-service coverage ratio loans that underwrite on rental income;
    higher rates but more flexible qualifying
- Note: David's existing pre-approval is likely for primary SFR; a new pre-approval
  for investment property will have different terms
- Market context: Marion County (Lawrence, Warren Township, Perry Township) vs
  Hamilton County (Noblesville, Anderson adjacent) for rental yield — rough context
  based on market-areas.yaml
- Lender referral with note to ask about investment property and 2-4 unit programs
- Legal note: self-managing landlords in Indiana must comply with Indiana Code 32-31
  (landlord-tenant law); recommend agent note this without giving legal advice

---

## Example 5: Downsizer — Emotional Transition

**Scenario:** Widow selling the family home of 30 years to downsize to something
smaller and easier to maintain. This is an emotionally charged situation. Agent
needs sensitive discovery, realistic expectations about downsizing tradeoffs, and
help navigating the home-sale-first vs buy-first decision.

**Prompt:**
```
/re-buyer-consultation

Buyer: Margaret Thornton, 68 years old, downsizing after husband passed
Slug: sarah-jones-fc-tucker
Selling: 3,800 sqft home in Carmel Clay (worth approximately $575K, no mortgage)
Buying: 1,500–2,000 sqft, ideally one-story, low maintenance, possibly a condo or villa
Budget: Can pay cash with home sale proceeds; up to $400K
Preferences: No stairs, no big yard, close to St. Vincent Hospital (medical reasons),
  possibly Meridian Hills or Carmel area, amenities/activities for retirement
Timeline: Has time; wants to be settled before winter
```

**What the skill should produce:**
- Discovery approach note: this situation requires empathetic pacing — don't rush through
  questions; acknowledge the emotional weight of leaving a family home
- Adapted discovery: accessibility needs, medical proximity requirements, condo vs villa
  community preference, HOA amenity preferences, proximity to family
- Selling-first strategy: all-cash purchase means no contingency financing, but she still
  needs home sale proceeds — leaseback option on selling side may give time to find new home
- Property type education: SFR (easy, low HOA), villa community (low maintenance, private
  feel), condo (potentially higher HOA, amenities); pros/cons for her situation
- Search criteria: main-floor primary, no-step entry or minimal steps, 1,500–2,000 sqft,
  near St. Vincent (86th and Meridian area), low-maintenance exterior, accessible garage
- Buyer agency agreement: use simple, clear language; explain it protects her exclusively
  as the buyer with no competing interests
- Communication cadence: recommend agent note to move at Margaret's pace; don't pressure
  with urgency unless deadline exists

---

## Example 6: Buyer Objecting to Agency Agreement

**Scenario:** Agent has a prospect who wants to "just look at a few homes first"
before signing anything. They're skeptical of the new buyer agreement requirement.
Agent needs talking points and objection handling.

**Prompt:**
```
/re-buyer-consultation agency agreement objection handling

Buyer scenario: Couple in their 40s, not first-time buyers, skeptical about the new
buyer agreement requirement. Have worked with agents before "without all this paperwork."
They're motivated (want to buy in 60 days) but are pushing back on signing before seeing
homes. Slug: sarah-jones-fc-tucker
```

**What the skill should produce:**
- Acknowledge the objection first: the industry change is real and buyers have a right to
  feel it's a new hoop
- Core response script: explain this is now industry-wide, not agent-specific; it exists
  to establish clear professional representation; it protects them
- Escalation path: if they refuse standard form, offer a property-specific agreement for
  first showing — limits commitment to a single address while still complying with requirements
- Explain what happens WITHOUT an agreement: agent cannot represent them; they'd be going
  to showings without professional representation
- Compensation transparency: explain how their agent gets paid (seller typically pays; what
  happens if seller doesn't offer enough; options available)
- Close: "I understand this feels like a lot of paperwork before you've even seen a house.
  Let me do this — I'll put your name on this one-page agreement for just the home we're
  going to see today. After that showing, if it feels like the right fit, we'll do the full
  agreement. Does that work?"
- Follow-up email template if they want to "think about it"

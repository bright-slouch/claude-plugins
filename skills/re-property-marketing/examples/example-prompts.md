# Example Prompts — re-property-marketing

These scenarios show realistic agent inputs and describe what the skill should produce.

---

## Example 1: Just Listed Campaign — Standard Fishers Family Home

**Agent prompt:**
> "Need the full marketing package for a new listing: 4218 Buttonwood Dr, Fishers, 46037.
> 4BR/3BA, 2,200 sqft, attached 2-car garage, built 2008. Kitchen updated in 2022 —
> quartz counters, white shaker cabinets. Finished basement with wet bar. Fenced backyard
> with deck. HSE school district. Listed at $425,000, MLS #21812345.
> Slug: sarah-jones-fc-tucker"

**Context:**
- Standard family home in Fishers, Hamilton County
- Strong school district (HSE) — major value driver in this submarket
- Kitchen update and finished basement are the key differentiators
- Fresh listing — full campaign needed

**Expected output:**
- Load sarah-jones-fc-tucker config; confirm agent name, brokerage, tagline, hashtags
- **Just Listed post (Instagram/Facebook):** Hook leading with the kitchen or school district,
  4 bullet features (kitchen, basement, fenced backyard, HSE schools), price if agent opts in,
  CTA, branded hashtags + #Fishers #HSEschools #HamiltonCountyRealEstate + property tags
- **Feature spotlight series (4 posts over 2 weeks):** Post 1 = kitchen (visual angle,
  quartz/shaker details), Post 2 = finished basement/wet bar (entertainment angle),
  Post 3 = fenced backyard/deck (outdoor lifestyle, no demographic language), Post 4 = HSE
  schools mention by name with community context
- **Email blast:** A/B subject lines; 200-word body with 4 feature bullets, CTA to call/reply
  for a showing, agent signature from email-templates.yaml, brokerage disclaimer
- **Print flyer text:** Headline "White Kitchen. Finished Basement. HSE Schools." full
  feature list, price, MLS#, agent contact block with license number, Equal Housing note
- **30-second reel script:** Hook: "If you've been waiting for a Fishers home with an
  updated kitchen and finished basement under $450K…" → 3 feature callouts → CTA
- **Legal disclaimer on all pieces**

---

## Example 2: Luxury Campaign — Carmel ($1.1M)

**Agent prompt:**
> "Luxury listing: 11204 Springmill Rd, Carmel, 46032. 5BR/4.5BA, 5,400 sqft,
> custom build 2018. Chef's kitchen with Sub-Zero and Wolf. Primary suite with
> spa bath. Gunite pool, outdoor kitchen, 3-car garage. Carmel Clay schools.
> Listed at $1,100,000, MLS #21822001. This one needs elevated, lifestyle-first copy.
> Slug: mike-wright-compass"

**Context:**
- Luxury tier; Carmel's most competitive price band
- Carmel Clay schools — top-rated in Indiana, major buyer motivator
- Custom finishes, pool, outdoor kitchen are the luxury differentiators
- Buyer is likely move-up/luxury buyer or executive relocation

**Expected output:**
- Load mike-wright-compass config; confirm elevated brand tone if set in agent-profile.yaml
- **Just Listed post:** Lifestyle-first headline ("This is what Carmel living looks like."),
  understated luxury copy — no specs in the first sentence, draw them in with the pool/outdoor
  kitchen image direction, price as confirmation not the hook
- **Feature spotlight series (5 posts):** Sub-Zero kitchen spread, primary spa bath, pool +
  outdoor kitchen, great room architectural detail, Carmel City Center proximity (lifestyle)
- **Email blast:** Elevated tone; subject line "A rare find on Springmill Road"; preview text
  teases the pool; 200-word body written for a buyer who values craft and privacy
- **Broker open invitation:** Agent-to-agent tone; notes buyer pool as move-up or executive
  relo; lists competitive advantages vs. current Carmel inventory; confirms lockbox/access
- **60-second walkthrough teaser script:** Cinematic pacing; opens on exterior/pool, closes
  on chef's kitchen; agent narration or caption-driven
- **Legal disclaimer on all pieces**

---

## Example 3: Price Reduction Announcement — Sensitive Reframe

**Agent prompt:**
> "Price reduction for 3218 Oak Creek Lane, Greenwood, 46143. Was $369,000,
> now $349,000. 3BR/2BA, 1,750 sqft, cul-de-sac lot, attached garage, Johnson
> County schools. Been on market 38 days. Need social post and sphere email that
> don't make it sound bad. Slug: lisa-chen-kw"

**Context:**
- 38 DOM — above average for current market; reduction needed to reset activity
- Agent wants to avoid language that signals distress or urgency
- Seller is likely watching; copy should maintain confidence

**Expected output:**
- **Social post:** Lead with "Updated Price — Now $349,000" NOT "PRICE DROP"
  or "DRASTICALLY REDUCED"; open with a property strength ("This Greenwood cul-de-sac
  home is one of the few under $350K with a garage AND updated kitchen…"); 2-sentence
  acknowledgment that the price reflects today's market; strong CTA; no apology, no
  emphasis on how long it's been on market
- **Sphere email:** Subject line "We've updated the price on this Greenwood home"
  (factual, no alarm); body reinforces property quality first, then notes the adjusted
  price as an opportunity; CTA is "If you know someone who's been on the fence, now
  is a great time to reach out"
- Skill notes: remind agent to update ShowingTime notes and MLS remarks for re-activation
  energy; consider re-running open house to reset buyer awareness
- **Legal disclaimer**

---

## Example 4: Open House Promo Series — 2-Week Countdown

**Agent prompt:**
> "Open house for 5501 Orchard Blvd, Noblesville, 46062. Sunday the 13th, 1:00–3:00pm.
> 4BR/2.5BA, 2,050 sqft, main-floor primary suite, large lot (.38 acres), 3-car garage.
> Noblesville schools. Listed at $389,000. I want a full 2-week promo series plus the
> sphere email invite and a broker open too (Thursday the 10th, 11am–1pm).
> Slug: sarah-jones-fc-tucker"

**Context:**
- Main-floor primary suite is a differentiator that appeals to a wide buyer range
- Large lot + 3-car garage = above average for the $389K price point in Noblesville
- Two events: broker open (Thursday) and public open (Sunday)

**Expected output:**
- **2-week social promo calendar:**
  - Day 1 (2 weeks out): "Coming up — open house on [date]" teaser with best photo
  - Day 5 (10 days out): Feature spotlight — main-floor primary suite angle
  - Day 9 (5 days out): "This Sunday — join us" full property post with OH details
  - Day 11 (3 days out): Reminder reel/story script: "3 days away — here's what you'll see"
  - Day 12 (2 days): Final push post + story: "Tomorrow, 1–3pm"
  - Day 13 (day of, morning): "Today! 1–3pm — I'll be there to answer every question"
- **Sphere email invite:** Sent Day 8 (5 days out); subject "You're invited — open house
  this Sunday in Noblesville"; warm body copy with top 3 features + OH logistics
- **Broker open invitation email:** Sent Day 7; agent-to-agent tone; Thursday 11am–1pm;
  notes main-floor primary as broad buyer appeal; light refreshments; access details
- **Legal disclaimer**

---

## Example 5: Under Contract / Just Sold Celebration

**Agent prompt:**
> "Just got under contract on 872 Westfield Blvd, Broad Ripple, Indianapolis — listed
> and sold in 9 days, multiple offers. $298,500. Now need a social post and an email to
> my database to generate new seller leads. Slug: dan-riley-remax"

**Context:**
- Fast sale (9 days) with multiple offers — marketable outcome for the agent
- Broad Ripple is a distinctive Indianapolis neighborhood — lifestyle angle
- Agent wants to convert the momentum into new seller inquiries

**Expected output:**
- **Under contract social post:** Celebration energy; "UNDER CONTRACT — 9 Days, Multiple
  Offers, Broad Ripple"; brief property nod ("This [area] home attracted incredible attention");
  CTA for sellers: "If your home could benefit from this kind of activity, let's talk.
  I have buyers who didn't get this one."
- **Just Sold social post (for after close):** Clean celebration graphic direction; stats
  front and center (9 days, multiple offers); genuine gratitude angle; seller CTA:
  "Curious what your home would sell for in today's market? I run CMAs — no obligation."
- **Sphere email:** Subject "We sold this Broad Ripple home in 9 days — here's what I
  learned about the market"; body uses the sale as a market proof point; ends with CTA
  to reach out for a CMA; agent signature from email-templates.yaml
- **Legal disclaimer**

---

## Example 6: Seasonal Campaign — Spring Listing

**Agent prompt:**
> "Need some spring-flavored marketing for 1447 Clover Hill Rd, Zionsville, 46077.
> 3BR/2BA, 1,900 sqft, built 1995, large screened porch, mature trees, new furnace 2024.
> Zionsville schools. Listed at $379,000. Just hitting the market April 1.
> Slug: dan-riley-remax"

**Context:**
- Spring timing — peak selling season in Central Indiana; can lean into it
- Screened porch + mature trees = spring/summer lifestyle appeal
- Zionsville is a premium small-town market in Boone County

**Expected output:**
- **Just Listed post with spring hook:** "Spring has arrived in Zionsville — and so has
  this listing." Leads with screened porch photo direction (blooming trees visible);
  seasonal language used for setting/lifestyle, not demographics
- **Feature spotlight — screened porch:** Written as a spring/summer lifestyle piece;
  "Imagine your mornings here all summer" framing; image direction: shoot from inside
  porch looking out to trees with spring light
- **Email blast with spring timing hook:** Subject "Spring is the best time to buy in
  Zionsville — and here's why"; preview: "A screened porch, mature trees, and a home
  that checks every box"; body ties spring market context to urgency (inventory is moving)
- **30-second reel script:** Opens on screened porch exterior shot in spring light;
  narration "This is what spring in Zionsville looks like from your own porch…"
- **Legal disclaimer**

---

## Example 7: Investment Property Campaign

**Agent prompt:**
> "Marketing for an investment property: 2244 E 30th St, Indianapolis 46218.
> 3BR/1BA, 1,100 sqft SFR, tenant-occupied at $1,150/month, current lease through
> October. Good condition. Listed at $139,000. Target is investor buyers.
> Slug: lisa-chen-kw"

**Context:**
- Investment property — different buyer audience (landlords, house hackers, portfolio buyers)
- Tenant-occupied: privacy considerations for the tenant
- Cap rate and cash-on-cash return are the primary marketing angles

**Expected output:**
- **Investor-focused social post:** Lead with the income story ("$1,150/month in place, lease
  through October — this one cash flows day one"); present cap rate range based on purchase
  price and gross rent; note tenant situation and showing limitations (tenant privacy)
- **Investment email blast:** Subject "Cash-flowing Indianapolis SFR — $139,000"; body
  focuses on income, lease status, and ease of acquisition; audience is landlords and
  portfolio investors; note that agent can provide rent comps for the area
- **Print flyer text:** Lead with income figures, then property specs; no lifestyle angle;
  include lease terms, showing restrictions note, and agent contact
- Skill notes: remind agent that tenant-occupied showings require proper notice (24-48 hours
  typically per Indiana landlord-tenant law, IC 32-31-3); do not publish interior photos
  without tenant consent and agent verification
- **Legal disclaimer**

---

## Example 8: Condo with HOA — Community Amenities as the Selling Point

**Agent prompt:**
> "Condo listing: 8901 River Crossing Blvd, Unit 204, Indianapolis 46240.
> 2BR/2BA, 1,300 sqft, 9th floor, city views, HOA includes pool, fitness center,
> covered parking, water/trash. HOA $345/month. Listed at $249,000. MLS #21819988.
> Slug: mike-wright-compass"

**Context:**
- Urban condo — 9th floor city views are the lead visual
- HOA covers significant items (pool, parking, water) — the monthly fee has context
- Located in the River Crossing area of Indianapolis (near IUPUI, downtown access)

**Expected output:**
- **Just Listed post:** Lead with the view ("Indianapolis from the 9th floor — every single
  morning."); HOA amenities presented as lifestyle benefits, not obligations; price inclusive
  framing ("$249,000 includes parking, pool access, and covered water/trash")
- **Feature spotlight — city view:** View from the balcony or large windows; copy is about
  the daily experience, not the specs
- **Feature spotlight — amenities:** Pool, fitness center, covered parking as lifestyle bundle;
  "The building does the work — you enjoy the city"
- **Email blast:** Subject "Low-maintenance Indianapolis living under $250K — with a view";
  body positions the HOA as a value package; CTA to schedule a private tour
- **Print flyer text:** Lead with "City Views. Lock and Leave. $249,000."; bullet the HOA
  inclusions; agent contact block; MLS# and brokerage disclaimer
- **Legal disclaimer**

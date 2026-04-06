# re-listing-prep — Example Prompts

Six real-world scenarios showing how agents invoke this skill and what output
to expect in each situation.

---

## Scenario 1: Move-In Ready Home — Light Prep, Photo-Ready in 1 Week

**Agent prompt:**
```
/re-listing-prep jane-smith-fc-tucker
Property: 4BR/2.5BA colonial, Fishers IN, built 2012, 2,400 sqft
          Updated kitchen 2021, new carpet throughout 2023, freshly painted
Timeline: 1 week (sellers want to list fast)
Situation: Occupied, two adults, no pets, extremely clean
Budget: $500
```

**Expected output highlights:**
- Tier 1 recommendations reduced to: professional deep clean ($300–400),
  curb appeal touch-up (mulch refresh, edge lawn)
- Staging guidance focuses on decluttering personal items and countertops —
  not replacement or refresh
- Shot list includes kitchen as feature shot, flags updated finishes as
  highlight detail shots
- Vendor task list: photographer (7 days out), cleaning service (1 day before)
- Timeline: 7-day accelerated schedule
- Note: "This home is in excellent condition. Primary focus is presentation,
  not repair. Decluttering personal items and a single deep clean are the
  highest-leverage moves available."

---

## Scenario 2: Home That Needs Work — Repair Triage

**Agent prompt:**
```
/re-listing-prep john-carter-kw
Property: 3BR/1.5BA ranch, Indianapolis 46227, built 1978, 1,200 sqft
          Original kitchen and baths, carpet worn in living areas,
          exterior paint peeling, gutters need cleaning
Timeline: 4 weeks
Situation: Occupied, seller is estate sale (inherited property)
Budget: $6,000
```

**Expected output highlights:**
- Pre-1978 flag: lead paint disclosure required — Seller's Residential Real
  Estate Sales Disclosure and Lead-Based Paint Addendum required at listing
- Tier 1 (within budget): exterior paint touch-up or full repaint, carpet
  replacement in living areas, professional deep clean, gutter cleaning + curb
  appeal
- Tier 2 (if budget allows): bathroom refresh (faucet, light, caulk)
- Explicit "price it in" recommendation for kitchen: "A full kitchen update is
  not a good investment at this price point. Price the list to reflect the
  dated kitchen rather than renovating."
- 4-week standard schedule with phased contractor assignments
- Note on estate sale: "Sellers often have emotional attachment to items that
  buyers find cluttered. Be prepared to have a direct conversation about what
  stays and what gets donated or staged to storage."

---

## Scenario 3: Vacant Property — Virtual Staging Recommendation

**Agent prompt:**
```
/re-listing-prep sarah-henderson-compass
Property: 3BR/2BA contemporary, Noblesville, 1,950 sqft, built 2019
          Fully vacant — sellers already relocated to new home
          Good condition, neutral finishes, empty rooms
Timeline: 2 weeks
Situation: Vacant
Budget: $1,500
```

**Expected output highlights:**
- Virtual staging recommended for all main living areas, primary bedroom,
  and kitchen nook — empty rooms photograph poorly and make buyers
  struggle to understand scale
- MIBOR compliance reminder: all virtually staged photos must carry the
  "Virtually Staged" label on the image
- Physical prep: deep clean (still needed even in vacant homes — dust,
  cobwebs, fingerprints accumulate), replace any burned-out bulbs, ensure
  all utilities on for photography
- Void space guidance: style the entry with one plant; add a single door
  mat to anchor the entry — inexpensive physical touches that ground the
  vacant home
- Shot list emphasizes architectural features and finishes since furniture
  is virtual: coffered ceilings, kitchen island, built-ins, etc.
- Drone recommended if lot or neighborhood is a feature
- Vendor: virtual staging service (external, if not in vendor-network.yaml,
  recommend agent add one — common services: BoxBrownie, roOomy)

---

## Scenario 4: Occupied with Pets and Kids — Special Staging Challenges

**Agent prompt:**
```
/re-listing-prep mike-torres-remax
Property: 4BR/3BA two-story, Greenwood, 2,800 sqft, built 2006
          Good condition overall; sellers have 3 kids and 2 dogs
          Carpet has pet odors in master, toy accumulation throughout,
          dog door in back door
Timeline: 3 weeks
Situation: Occupied, active family household
Budget: $2,500
```

**Expected output highlights:**
- Odor remediation as Tier 1 priority: carpet cleaning with enzyme treatment
  (not just deodorizer), HVAC filter replacement and duct spray, pet
  bedding and bowls removed for showings
- Practical staging plan that acknowledges lived-in reality: designated
  "launch pad" closet or bin for quick toy pickup before showings
- ShowingTime setup with minimum 2-hour notice window to allow family to
  clear out pets
- Explicit guidance: "Pets should not be present during showings. Arrange
  crating, a friend's home, or professional daycare during the listing period."
- Dog door: note it in showing prep — some buyers will ask about security;
  suggest a draft stopper panel if removable
- Staging priority list: odor first, clutter second, styling third
- Special photo-day checklist: pets removed from property, dog bowls/beds
  packed away, toys stored, backyard cleared of pet waste and toys

---

## Scenario 5: Luxury Staging — $600K+ Home, Professional Stager Warranted

**Agent prompt:**
```
/re-listing-prep jane-smith-fc-tucker
Property: 5BR/4.5BA executive home, Carmel IN, 4,200 sqft, built 2016
          Seller has contemporary taste but home is partially empty
          (moved some furniture to new lake house)
Timeline: 4 weeks
Situation: Partially occupied (some rooms furnished, some empty)
Budget: $8,000–12,000
```

**Expected output highlights:**
- Professional stager consultation recommended as the first action: "At
  this price point, staging ROI typically 3x–5x the cost. A professional
  stager who specializes in luxury Central Indiana homes is not optional —
  it's a marketing investment."
- Pull stager from vendor-network.yaml; if not listed, flag as a gap to fill
- Luxury-specific staging guidance: fresh flowers (not fake), consistent
  linen/towel color palette throughout bathrooms, wine/coffee bar styling in
  kitchen, outdoor furniture styled for entertaining
- Photography: minimum 40 photos, twilight exterior mandatory, drone
  recommended for lot and neighborhood, detail shots of every upgraded
  finish (ceiling treatments, custom millwork, appliances)
- Virtual staging for any fully empty rooms that stager doesn't physically
  furnish
- Checklist of luxury buyer expectations: smart home features documented,
  appliance brands noted, HVAC serviced and documented, recent improvements
  summarized for disclosures

---

## Scenario 6: Budget-Conscious Seller — DIY Staging, Low-Cost High-Impact

**Agent prompt:**
```
/re-listing-prep john-carter-kw
Property: 3BR/2BA ranch, Beech Grove, 1,350 sqft, built 1988
          Dated but clean; seller is cost-sensitive, recently widowed,
          fixed income
Timeline: 2 weeks
Situation: Occupied
Budget: $800 hard limit
```

**Expected output highlights:**
- Empathetic framing: acknowledge the constraint and work within it rather
  than providing a wishlist the seller can't execute
- DIY staging guide: YouTube tutorial for touching up scuffed walls with
  matching paint vs. full repaint, specific product recommendations
  (Rust-Oleum Cabinet Transformations for dated oak cabinets, costs ~$120),
  low-cost light fixture swaps from Home Depot ($40–80 each)
- Budget allocation suggestion within $800:
  - Deep clean (DIY or $250 professional): $250
  - Paint touch-up supplies: $75
  - New cabinet hardware: $80
  - Curb appeal (mulch, one flat of flowers): $120
  - Professional photos (non-negotiable): $275
- Agent coaching note: "Photography is the one place not to cut corners.
  Professional real estate photography is worth every dollar even at this
  price point — buyers are filtering on photos before they ever call."
- Remind agent: if staging limitations affect perceived value, price should
  reflect that — set correct expectations with seller on list price vs.
  competition

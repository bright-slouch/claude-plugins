---
name: re-listing-prep
description: >-
  Property preparation guidance for Central Indiana listings. Generates an
  ROI-ranked repair checklist, room-by-room staging instructions, a
  photography shot list, virtual staging recommendations, vendor coordination
  notes, and a prep timeline — all personalized to the agent's vendor network
  and the seller's specific property.
  Triggers: "prep the listing", "get the house ready", "staging advice",
  "what repairs should the seller do", "photography shot list", "listing prep",
  "property prep", "prepare the home", "pre-listing checklist", "what to fix before listing",
  "staging tips", "home prep timeline", "get ready to list".
argument-hint: "[agent slug or property address + brief property description]"
---

# re-listing-prep

## Overview

`re-listing-prep` helps agents guide sellers through every step of getting a
property photo-ready and market-ready. It produces four core deliverables:

1. ROI-ranked repair/improvement checklist (Tier 1–3)
2. Room-by-room staging guidance
3. Photography shot list (including drone and twilight recommendations)
4. Vendor task list pulled from the agent's vendor-network config

Output is personalized to the property, the seller's timeline, and the agent's
preferred vendors. Nothing is generic — every recommendation references the
Central Indiana market and the agent's brand.

---

## Persona and Mental Model

Think like an experienced listing agent who has prepared 200+ Central Indiana
homes for market. You know what sells in Fishers vs. Broad Ripple vs. Greenwood.
You are honest with sellers about what needs fixing, diplomatic about what
doesn't, and firm about what will cost them at the offer table. Your job is to
maximize net proceeds and minimize days on market — not to make sellers feel
good about every corner they want to ignore.

---

## When to Use This Skill

- Seller has agreed to list and a listing appointment is complete
- Agent needs a written prep plan to hand to the seller
- Seller is asking "what do I need to do before photos?"
- Agent is doing a pre-listing walkthrough and needs a checklist
- Property is vacant and virtual staging is being considered
- Agent needs to coordinate vendors before the go-live date

---

## Quick Start

```
/re-listing-prep [agent-slug]
Property: [address or brief description]
Timeline: [2 weeks / 4 weeks / flexible]
Situation: [occupied / vacant / needs work / move-in ready]
Budget: [seller's stated prep budget, if known]
```

Example:
```
/re-listing-prep jane-smith-fc-tucker
Property: 3BR/2BA ranch, 1,450 sqft, Hamilton County, built 1998
          Original fixtures, good bones, lived-in condition
Timeline: 4 weeks
Situation: Occupied, sellers downsizing, motivated
Budget: $3,000
```

---

## Step-by-Step Workflow

### Step 1: Load Agent Config

Load `~/Skills/real-estate-plugin/config/[slug]/agent-profile.yaml` to
establish agent identity, voice, and brokerage. Load
`vendor-network.yaml` for photographers, stagers, painters, carpet vendors,
cleaning services, and landscapers.

If the agent config is not found after trying all resolution methods above, you MUST respond with a visible message to the user. Do NOT silently redirect, do NOT produce empty output, and do NOT chain to another command. Instead, respond with:

> I'd be happy to help with that! Before I can run this skill, I need to load your agent profile.
>
> Please provide one of the following:
> - Your **full name** as it appears in your agent profile
> - Your **email address**
> - Your **config slug** (e.g., `jane-smith-fc-tucker`)
>
> Or if you haven't set up your profile yet, run **/re-agent-setup** to get started (takes about 10 minutes).

Then STOP and wait for the user to respond. Do not proceed to subsequent steps.

### Step 2: Assess the Property

Capture or confirm:
- Property type (single family / condo / multi-family / vacant land)
- Bedrooms, bathrooms, approximate square footage
- Year built (pre-1978 triggers lead paint disclosure — flag it)
- Current condition: move-in ready / cosmetic work needed / deferred maintenance
- Occupied or vacant
- Seller's prep timeline (2-week / 4-week)
- Seller's stated prep budget
- Known issues: roof age, HVAC age, foundation, water intrusion history
- Special features worth highlighting: pool, deck, finished basement, views, acreage

### Step 3: Generate ROI-Ranked Repair Checklist

Rank every recommended improvement by return on investment for the Central
Indiana market. Present in three tiers:

**Tier 1 — Do These (High ROI, always recommend):**
- Fresh neutral paint (interior): $2,000–$5,000 cost → $5,000–$10,000 return or
  measurably faster sale. Covers dated colors, scuffs, pet odors embedded in walls.
- Professional deep clean (full property + carpets): $300–$600 cost.
  Non-negotiable. Buyers notice smell before anything else.
- Carpet cleaning or replacement: $200–$500 for cleaning; $800–$2,000 for
  replacement of heavily worn areas. Worn carpet destroys perceived value.
- Curb appeal basics: mulch, trimmed shrubs, power-washed driveway, repaired
  gutters — $500–$1,500. First impression sets the entire showing tone.
- Lighting improvements: replace dated fixtures, add higher-lumen bulbs in dark
  rooms, repair non-functioning switches — $200–$800.

**Tier 2 — Often Worth It (assess case-by-case):**
- Minor kitchen updates: hardware swap, new faucet, painted or refaced cabinets
  if visibly dated — $500–$2,000.
- Bathroom refresh: new vanity light, faucet, toilet seat, fresh caulk/grout —
  $300–$800.
- Hardwood floor refinishing (if scratched, not just dull): $2,000–$4,000.
  Assess whether refinish is visible enough to affect perception.
- Garage door replacement (broken or severely dated): $1,200–$2,500. Garage
  door is a significant visual element in curb appeal.
- Interior door hardware: replace mismatched or builder-grade knobs —
  $100–$400.

**Tier 3 — Situational (do not default-recommend):**
- Full kitchen remodel: rarely recoups full cost in Central Indiana residential
  market. Price it into the list price instead.
- Roof replacement: only if buyer's lender will require it, roof is actively
  failing, or inspector will flag it on every transaction. Otherwise, price in
  or offer a credit.
- HVAC replacement: only if system is non-functional. For aging systems (12+
  years), offer a home warranty or adjust price rather than replacing proactively.
- Finished basement improvements: if already finished and functional, stage it.
  Do not start a basement finish project for listing.

**Critical guardrail:** Never over-improve for the neighborhood price point.
A $20,000 kitchen in a $225,000 neighborhood doesn't move the needle.

### Step 4: Room-by-Room Staging Guidance

Generate specific, actionable staging notes for each applicable room:

**Entry / Foyer:**
Clean front door (paint if peeling), replace worn welcome mat, add a single
potted plant or wreath, ensure good overhead lighting, remove coats/shoes from
visible entry area, clear entry table of personal items.

**Living / Family Room:**
Remove 30–40% of furniture to increase perceived spaciousness. Arrange
remaining furniture conversationally facing a focal point (fireplace, TV, view).
Neutral throw pillows and blanket on sofa. Hang a mirror to amplify natural
light. Remove all family photos, diplomas, and personal collections.

**Kitchen:**
Completely clear countertops — one small styled grouping only (e.g., a wooden
cutting board and a plant). Deep clean all appliances inside and out. Replace
dated hardware if budget allows. Organize visible pantry. Clean grout.

**Primary Bedroom:**
Crisp, hotel-style bedding (neutral duvet or comforter). Bedside lamps on for
photos. Remove personal items, medications, and clutter from nightstands and
dresser tops. Clear and organize master closet — buyers will open it.

**Secondary Bedrooms:**
Remove excess furniture. Ensure each room has a clear, singular purpose
(bedroom, not bedroom + storage dumping ground). Neutral bedding.

**Bathrooms:**
Folded towels displayed (not used towels). Toilet lid down. Remove all personal
products from countertop — one small display item maximum. Re-caulk if grout is
discolored. Clean mirrors. Replace cracked toilet seat.

**Finished Basement:**
Style as a functional living space — not storage. Organize any utility/storage
area. If dehumidifier is present, ensure it's running and emptied for photos.

**Garage:**
Completely cleared of clutter. Floor swept. Remove vehicles for photos and
showings. Organized wall storage is a positive.

**Exterior / Yard:**
Freshly mowed and edged lawn. Power-washed driveway, front walk, and porch.
Seasonal color at entry (potted flowers). Remove toys, equipment, garbage cans,
garden hoses from visible areas. Pool cover removed for summer photos if pool
is in good condition.

### Step 5: Photography Shot List

Generate a property-specific shot list:

**Exterior (always required):**
- Front elevation: multiple angles, include landscaping and street number
- Street/curb view: shows neighborhood character
- Backyard: full view plus patio/deck detail
- Side yards if notable
- Twilight exterior: strongly recommend if home photographs well at dusk — adds
  significant listing appeal. Coordinate timing with photographer.

**Interior — Room Coverage:**
- Each room gets at least one wide-angle shot; two for larger spaces
- Emphasize natural light — schedule photos mid-morning or early afternoon
- Kitchen: wide angle + detail of backsplash or appliances if updated
- Primary bedroom + bath together
- Living room from multiple angles if open floor plan

**Feature/Detail Shots:**
- Fireplace (mantel styled)
- Built-in shelving or cabinetry
- Architectural details: coffered ceilings, crown molding, exposed beams
- Updated bath fixtures
- Statement light fixtures

**Special Features:**
- Pool / hot tub (water cleaned, cover removed)
- Deck or patio (styled with outdoor furniture)
- Workshop, finished garage, sport court
- Finished basement (styled)
- Acreage or notable lot features

**Drone/Aerial:**
Recommend if any of the following apply:
- Lot size > 0.3 acres
- Wooded or water lot
- Neighborhood location is a selling point (golf course, lake community)
- Rural or unique topography
- Property is hard to understand from ground level

**Photo count target:** 25–40 for standard MIBOR BLC listings. 40–60 for
luxury ($600K+). Discuss with photographer.

### Step 6: Virtual Staging Guidance

**When to recommend virtual staging:**
- Vacant property (empty rooms are very difficult to photograph compellingly)
- Dated or mismatched furniture that cannot be removed
- New construction where model staging isn't available

**Virtual staging requirements per MIBOR rules:**
- All virtually staged photos must be labeled "Virtually Staged" directly on
  the image or in the photo caption field in the BLC.
- Cannot virtually stage out existing features (popcorn ceilings, dated
  fixtures) — only add furnishings to empty spaces.
- Not a substitute for decluttering an occupied home.

### Step 7: Vendor Coordination

Pull from `vendor-network.yaml` and generate a task list:

| Task | Vendor | Contact | Timeline |
|------|--------|---------|----------|
| Photography | [name from config] | [contact] | [days before list] |
| Staging consultation | [stager from config] | [contact] | [days before photos] |
| Deep clean | [cleaning vendor] | [contact] | [1 day before photos] |
| Paint | [painter from config] | [contact] | [2 weeks before photos] |
| Carpet | [carpet vendor] | [contact] | [1 week before photos] |
| Landscaping | [landscaper] | [contact] | [1 day before photos] |

If a vendor category is not in `vendor-network.yaml`, note the gap and
recommend the agent add one or allow the seller to source.

### Step 8: Output Prep Timeline

Generate one of two schedules based on the seller's timeline:

**2-Week Prep Schedule (fast track):**
- Days 1–3: Deep clean, declutter, donate/store excess items
- Days 3–7: Paint touch-ups or full interior repaint
- Days 5–9: Carpet cleaning or replacement
- Days 7–10: Curb appeal (mulch, power wash, landscaping)
- Day 12: Staging walkthrough with agent
- Day 13: Final deep clean
- Day 14: Photography

**4-Week Prep Schedule (standard):**
- Week 1: Declutter, donate, organize; begin paint project; order any fixtures
- Week 2: Complete paint; replace hardware, fixtures, lighting
- Week 3: Carpet; landscaping; curb appeal; repairs completed
- Week 4: Staging walkthrough; professional clean; photography; list

---

## What NOT to Do

- Do not recommend renovations that exceed the neighborhood price ceiling.
- Do not tell a seller their home "doesn't need anything" to avoid
  uncomfortable conversations — honest prep advice serves their net proceeds.
- Do not schedule photography before staging is complete.
- Do not use virtually staged photos without labeling them per MIBOR rules.
- Do not recommend roof or HVAC replacement as a default — price strategy or
  credit is usually better.
- Do not advise concealing known defects — this is a disclosure violation and
  potential fraud.
- Do not skip the vendor coordination step — agents who hand sellers a written
  vendor list convert prep conversations to action.

---

## Integration Points

### Reads From
- `config/[slug]/agent-profile.yaml` — agent identity and voice
- `config/[slug]/vendor-network.yaml` — preferred vendors
- `references/staging-checklist.md` — detailed room checklist
- `references/indiana-disclosure-requirements.md` — flag pre-1978 properties

### Works With
- `re-cma` — pricing context informs which tier of repairs pencil out
- `re-seller-consultation` — prep plan is often the natural follow-up to the
  listing presentation
- `re-listing-creation` — photography and prep feed directly into listing copy

---

## Example Prompts

- "Prep plan for a 4BR/3BA in Fishers, 2004 build, good condition, 4 weeks"
- "Seller has $2,000 budget and 2 weeks — what do they absolutely have to do?"
- "Vacant home in Noblesville, needs virtual staging recs and shot list"
- "Luxury listing in Carmel, $850K, what staging level is appropriate?"
- "Occupied home with 2 dogs — special staging and odor guidance please"
- "Pre-1978 bungalow in Broad Ripple — flag disclosure requirements and prep"

---

## Legal Disclaimer

*This output is for guidance and informational purposes only. It does not
constitute legal advice. Agents should consult their managing broker and/or a
licensed Indiana real estate attorney for situation-specific guidance. Always
comply with Indiana Real Estate Commission rules and your brokerage's policies.*

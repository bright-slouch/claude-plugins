---
name: re-listing-creation
description: >-
  Generates all MLS listing content for Central Indiana properties: BLC remarks
  (500-character limit), extended marketing description (1,000–1,500 words),
  Instagram and Facebook social captions, and a fair housing compliance check.
  Content is written in the agent's brand voice using their brand-kit config and
  follows all MIBOR BLC rules and HUD Fair Housing guidelines.
  Triggers: "write the listing", "MLS description", "BLC remarks", "listing description",
  "write remarks", "property description", "create the listing", "listing copy",
  "MLS content", "social captions for listing", "write up the listing".
argument-hint: "[agent slug] + property details (beds, baths, sqft, year, features, price range)"
---

# re-listing-creation

## Overview

`re-listing-creation` produces four deliverables for every listing:

1. **BLC Remarks** — 500 characters max, punchy, feature-first, MIBOR-compliant
2. **Extended Marketing Description** — 1,000–1,500 word prose narrative for
   Zillow, Realtor.com, and listing presentations
3. **Social Media Captions** — Instagram (with hashtags) and Facebook versions
4. **Fair Housing Compliance Review** — flags any language that violates the
   Fair Housing Act or HUD guidelines before it goes live

All content is written in the agent's voice using their brand-kit, references
Indiana-specific MLS standards, and never substitutes for the agent's own
final review before submission.

---

## Persona and Mental Model

Think like a listing copywriter who deeply understands the Central Indiana
market — from a Fishers new-construction community to a 1920s Broad Ripple
bungalow to a Carmel executive estate. You know that BLC remarks are a
headline: every character counts. You know that extended descriptions sell
a lifestyle, not a square footage. You know that fair housing violations
aren't just embarrassing — they are federal law violations, and protecting
the agent from inadvertent violations is as important as writing good copy.

---

## When to Use This Skill

- Photos are complete and agent is ready to write listing copy
- Agent has property details and wants BLC remarks drafted before MLS entry
- Social media content is needed for a new listing launch
- Agent wants to double-check remarks or descriptions for fair housing issues
- Relisting a property that needs fresh, updated copy

---

## Quick Start

```
/re-listing-creation [agent-slug]
Address: [property address]
Property: [beds / baths / sqft / year built / type / notable features]
List price: [list price or approximate range]
Highlights: [top 3–5 features you want emphasized]
Neighborhood: [city, school district, proximity context]
```

Example:
```
/re-listing-creation jane-smith-fc-tucker
Address: 12345 Maple Creek Dr, Fishers IN 46037
Property: 4BR / 2.5BA / 2,850 sqft / 2018 / two-story / updated kitchen,
          quartz countertops, LVP throughout main level, 3-car garage,
          finished basement, HSE school district
List price: $549,000
Highlights: Kitchen remodel 2022, screened porch, walkout basement,
            cul-de-sac lot
Neighborhood: Fishers, HSE schools, 5 min to I-69, Flat Fork Creek Park nearby
```

---

## Step-by-Step Workflow

### Step 1: Load Agent Config

Load `~/Skills/real-estate-plugin/config/[slug]/agent-profile.yaml` for
agent identity and voice. Load `brand-kit.yaml` for hashtags, tagline,
brand colors (for social formatting guidance), and compliance disclaimers.

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

### Step 2: Gather Property Details

Confirm or request the following inputs before writing:

**Required:**
- Bedrooms, bathrooms (full and half)
- Gross Living Area (sqft) — ANSI standard; do NOT include finished basement
- Year built
- Property type (single family / condo / townhome)
- City, county, school district
- List price

**Important (affects copy significantly):**
- Top 3–5 features to lead with
- Recent updates with approximate years (kitchen remodel, roof, HVAC, etc.)
- Outdoor features: garage count/type, lot size, deck/patio, pool, acreage
- Basement: finished sqft, features (separate from GLA)
- HOA community name and amenities if applicable
- Proximity context: commute corridors, parks, shopping, schools by name
- Architectural style: ranch, two-story, colonial, craftsman, mid-century, etc.

**Flags:**
- Is any area virtually staged? (Required disclosure in remarks/captions)
- Is any square footage from a finished basement? (Must be listed separately)
- Pre-1978? (Lead paint disclosure required — flag it but do not include
  in copy)

### Step 3: Write BLC Remarks (500 characters max)

**Rules — non-negotiable:**
- Hard 500-character limit including spaces
- No phone numbers in remarks
- No agent or brokerage names in remarks
- No website URLs in remarks
- No ALL CAPS words (abbreviations are fine: BR, BA, SF, LVP, SS, W/D, HW,
  FP, FROG, DR, LR, FR, HOA, 2-car gar, HSE)
- No fair housing violations (see Step 5)
- Must not describe features not included in the sale

**Writing approach:**
- Lead with the single strongest selling point (location, updates, finishes,
  lot, lifestyle)
- Pack in quantifiable facts: bedroom count, bath count, sqft (GLA only),
  garage count
- Use approved abbreviations aggressively to hit the character limit
- End with a forward-leaning phrase: "Schedule your showing today." or
  "Won't last."
- Count every character before finalizing — BLC will reject over-limit
  remarks

**Format output as:**
```
[DRAFT BLC REMARKS]
[remarks text]
Character count: [X]/500
```

### Step 4: Write Extended Marketing Description (1,000–1,500 words)

Structure the description as flowing prose — not a bulleted list.

**Lead paragraph (hook):**
Open with the lifestyle angle and location context. Avoid "Welcome to your
dream home" — it's cliché and wastes the lead. Instead: place the reader
in the experience. Name the neighborhood or community, lead with the
best feature or setting, and create forward momentum.

**Main body — room narrative:**
Walk through the home in a logical showing order (entry → main living →
kitchen → primary suite → secondary bedrooms → basement → outdoor spaces).
Write about each space in 2–4 sentences that convey feel and function, not
just dimensions. Reference specific finishes, materials, and updates with
approximate dates where known.

**Neighborhood/location section:**
Name the school district (elementary, middle, high school if known). Name
nearby commute corridors (I-69, US-31, 465, SR-37, etc.). Reference nearby
parks, shopping corridors, and lifestyle anchors (Flat Fork Creek Park,
Hamilton Town Center, Monon Trail, Mass Ave, etc.). Be specific to Central
Indiana — not generic.

**Closing paragraph:**
Summarize the lifestyle the home enables. Invite the reader to schedule a
showing. Do not include contact info per MIBOR rules — that is in the
listing's contact fields.

**Voice guidance:**
- Use the agent's brand voice from `agent-profile.yaml` — formal vs.
  conversational, energy level, vocabulary preferences
- Avoid overused listing phrases: "must see," "won't last long," "gem,"
  "cozy" (implies small), "charming" (implies old/small), "spacious"
  without specific dimensions, "motivated seller"
- Use specific details over adjectives: "quartz countertops with waterfall
  island" beats "gorgeous kitchen"

### Step 5: Fair Housing Compliance Review

Every output receives an automatic compliance scan before delivery.

**Protected classes under federal Fair Housing Act:**
Race, color, national origin, religion, sex, disability, familial status.

**Additional Indiana protected class:**
Age, ancestry (Indiana Civil Rights Law).

**Language that must be flagged or removed:**

| Phrase Type | Example | Issue |
|---|---|---|
| Familial status | "Perfect for families," "great for couples," "ideal for empty nesters" | Implies preference based on family composition |
| Religion | "Near [church name]" as a selling point | Implies religious preference |
| National origin/race | Any reference to neighborhood demographics | Direct violation |
| Disability | "Accessible," "no stairs" used as lifestyle selling point tied to disability | Can imply preference; describe features factually instead |
| Exclusion language | "Exclusive," "private enclave," "executive community" | May imply exclusion if used to signal demographic homogeneity |
| Familial status (indirect) | "Quiet, peaceful street" | Can be acceptable; flag if context implies discouraging certain buyers |
| Ancestry/origin (indirect) | References to ethnic neighborhoods, cultural centers as selling points | Must be framed neutrally; cannot be used to market to a specific group |

**Compliant rewrites:**
- "Perfect for families" → describe the yard size, school district, bedroom
  count factually
- "Near [church name]" → "minutes from Westfield's vibrant community
  centers and amenities"
- "Accessible first-floor master" → "primary suite on the main level" (factual
  description of physical feature — this is compliant)
- "Executive neighborhood" → name the neighborhood by its actual name

**Output format for compliance review:**
```
[FAIR HOUSING REVIEW]
Status: PASS / NEEDS REVISION
Flagged items: [list any flags with line references and suggested rewrites]
```

### Step 6: Social Media Captions

**Instagram caption (150–200 characters + hashtags):**
- Lead with the most visual, aspirational feature
- Punchy, hook-first, emoji optional (follow agent's brand-kit preference)
- 3–5 lines maximum before hashtags
- Hashtags: pull from `brand-kit.yaml`; add property-specific tags:
  #[City]RealEstate #[SchoolDistrict] #[NeighborhoodName] #INdiana

**Facebook caption (200–300 words):**
- Storytelling format — slightly longer, warmer tone
- Lead with a question or observation that draws the reader in
- Include key features (3–5) in natural prose, not a bullet list
- End with a call to action: link to listing, "DM for details," or
  "comment below if you'd like a private tour"
- No phone number or URL required in the post body if the listing link is
  in the Facebook post's link preview

**LinkedIn caption (optional — investor/corporate relo):**
- Professional, value-focused tone
- Lead with investment angle, location metrics, school district ranking
  (if strong), or corporate relocation context
- Keep to 150–200 words
- Generate only if agent requests it or if property profile warrants it

### Step 7: SEO Optimization Notes

Provide brief guidance on keywords for Zillow/Realtor.com syndication:
- "[City] homes for sale" naturally embedded in extended description
- School district name used at least twice
- Neighborhood name used in both BLC remarks and extended description
- Year of key updates included (buyers search "updated kitchen," etc.)

---

## What NOT to Do

- Do not exceed 500 characters in BLC remarks — count carefully.
- Do not include agent name, phone number, or website in BLC remarks.
- Do not include basement square footage in the GLA field — list separately.
- Do not describe features that are not included in the sale (personal property,
  fixtures that will be removed).
- Do not use virtually staged photo language without the disclosure.
- Do not use fair housing-violating language under any circumstances, even if
  the seller requests it.
- Do not write "motivated seller" in any listing copy — it signals desperation
  and weakens the seller's negotiating position.
- Do not claim a CMA is equivalent to an appraisal. Never reference pricing
  rationale in the listing copy itself.
- Do not invent facts about the property — square footage, school district,
  year built must be confirmed, not assumed.

---

## Integration Points

### Reads From
- `config/[slug]/agent-profile.yaml` — agent voice, methodology
- `config/[slug]/brand-kit.yaml` — hashtags, tagline, disclaimer text, colors
- `references/mls-field-guide.md` — BLC field rules, character limits
- `references/real-estate-vocabulary.md` — approved terminology, fair housing
  language standards

### Works With
- `re-listing-prep` — prep and photography inform which features to lead with
- `re-property-marketing` — social captions here feed into the broader
  marketing campaign workflow
- `re-cma` — pricing context informs where in the market narrative to position
  the property

---

## Example Prompts

- "Write BLC remarks for a 4BR/2.5BA in Fishers, $549K, updated kitchen, HSE"
- "Extended description for a Carmel luxury estate, 5,200 sqft, $1.1M"
- "Instagram and Facebook captions for a new Westfield listing launching Monday"
- "Fair housing check on these BLC remarks: [paste remarks]"
- "Write listing copy for a downtown Indy condo, urban lifestyle angle"
- "Relist copy for a property that expired — fresh language, same home"

---

## Legal Disclaimer

*This output is for guidance and informational purposes only. It does not
constitute legal advice. Agents should consult their managing broker and/or a
licensed Indiana real estate attorney for situation-specific guidance. Always
comply with Indiana Real Estate Commission rules and your brokerage's policies.
All listing content must be reviewed by the agent before submission to the BLC.
Fair housing compliance is the agent's and brokerage's legal responsibility.*

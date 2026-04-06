# Neighborhood Research: 5-Minute Quick Start Guide

## What This Skill Does

`re-neighborhood-research` generates a buyer-ready local area report for any Central Indiana neighborhood, city, or zip code. You give it a location and a buyer profile; it produces a polished, on-brand report that positions you as the local expert.

The report covers:
- **Schools** — district, school names, GreatSchools directional context, enrollment contacts
- **Property taxes** — Indiana homestead system, county rate estimates, how to verify
- **Commute** — drive times to key employers, highway corridor notes, IndyGo options
- **HOA** — what to look for, red flags, where to find documents
- **Flood zones** — FEMA designation, insurance implications
- **Utilities** — electric, gas, water/sewer providers; well/septic context for rural
- **Amenities** — trails, parks, dining/entertainment, shopping
- **Indiana-specific** — township structure, TIF districts, annexation context

---

## The Most Important Input: Buyer Profile

The report adapts based on who the buyer is. The more you tell the skill about the buyer's priorities, the better the output.

**Tell the skill:**
1. Location (neighborhood, city, or zip code)
2. Buyer type and priorities
3. Budget range (helps contextualize tax estimates and what they'll find in that area)
4. Employer or commute destination (if commute matters)
5. Household type (family with kids, young professional, downsizer, investor)

**Minimal input:**
```
/re-neighborhood-research — Fishers 46037
```
This works, but the report will be generic.

**Better input:**
```
/re-neighborhood-research — Fishers 46037, family with 2 kids moving from out of state,
budget $475K, schools and commute to downtown Indy are top priorities
```
This produces a tailored report that leads with what matters most.

---

## Three Output Formats

| Format | Best For | Length |
|---|---|---|
| **Full Written Report** (default) | Emailing to buyer; relocation clients; consultation prep | 3-5 pages |
| **Bullet Summary** | Your own verbal reference during showings | 1 page |
| **Social Media Version** | Instagram/Facebook — teaser positioning you as local expert | 150-200 words |

Request the format in your prompt:
```
/re-neighborhood-research — Carmel 46032 ... [full report]
/re-neighborhood-research — Carmel 46032 ... [bullet summary for my own reference]
/re-neighborhood-research — Carmel 46032 ... [social media version for Instagram]
```

If you don't specify, you get the full written report.

---

## What Comes From Web Search vs. Local Knowledge

| Data Type | Source |
|---|---|
| School names and district info | Reference file + web search for current details |
| GreatSchools ratings | Web search (directional only — caveat always included) |
| FEMA flood zone for a specific address | Web search (msc.fema.gov lookup) |
| Current tax bill for a specific parcel | Web search (DLGF Gateway or county auditor) |
| HOA documents | Agent inquiry / county recorder (research guidance provided; actual docs must come from seller/agent) |
| Utility providers | Reference file + web search to confirm |
| Commute times | Web search (Google Maps current travel times) |
| Neighborhood amenities | Reference files + web search |
| Current listing/price context | Agent's MLS knowledge + web search |

---

## What the Skill Cannot Do

- **Cannot pull actual MLS data.** The skill knows Central Indiana market context deeply, but for specific active listings and current price-per-square-foot, use the BLC directly.
- **Cannot retrieve actual HOA documents.** It tells you where to find them and what to look for. You'll need to request the actual documents from the listing agent or county recorder.
- **Cannot give legal or tax advice.** All tax estimates include a verify-with-county-auditor caveat. All legal questions (HOA disputes, flood insurance requirements) reference appropriate professionals.
- **Cannot speak to demographic composition of neighborhoods.** This is intentional — Fair Housing compliance is built in. If a buyer asks about this, the skill provides a scripted, compliant response.

---

## Fair Housing — What's Built In

The skill is calibrated to avoid Fair Housing violations automatically:

- School data is presented with academic metrics only — never framed as a proxy for neighborhood demographics
- The skill will not characterize neighborhood composition by race, ethnicity, religion, or national origin
- If a buyer asks directly about demographics, the skill provides a compliant redirect script for you to use
- All language is reviewed against `references/real-estate-vocabulary.md`

You don't need to think about this during a busy buyer consultation — the skill handles it.

---

## Quick Examples

**Relocation family (school focus):**
```
/re-neighborhood-research — Carmel 46032, relocating family from Chicago,
2 kids ages 8 and 11, budget $600K, schools are #1 priority,
one parent commutes to Eli Lilly campus
```

**Young professional (walkability/commute focus):**
```
/re-neighborhood-research — Broad Ripple area, first-time buyer,
works at Salesforce Tower 2 days/week, budget $300K,
wants walkability and Monon Trail access
```

**Area comparison:**
```
/re-neighborhood-research — Compare Westfield vs Noblesville,
family with kids, budget $440K, need Hamilton County schools,
one parent commutes downtown, other to Fishers tech corridor
```

**Rural buyer:**
```
/re-neighborhood-research — Rural Hendricks County near Brownsburg,
buyer wants 2+ acres, okay with well/septic, first-time rural buyer,
commutes to Indianapolis airport area
```

---

## After the Report: What's Next

| Action | Skill |
|---|---|
| Send the report to the buyer | `/re-client-communication` |
| Do a full CMA for the area | `/re-cma` |
| Prep for the buyer consultation | `/re-buyer-consultation` |
| Write an offer on a property in this area | `/re-offer-writer` |

The neighborhood research report is a natural opener for buyer consultation prep. Run it before you meet with any buyer who's new to an area — it takes 5 minutes and makes you look like you've lived in that zip code for 20 years.

# Example Prompts — re-listing-creation

Six scenarios showing realistic agent inputs and expected skill output.

---

## Example 1: Family Home — Fishers, HSE Schools, Updated Kitchen

**Agent prompt:**
> "/re-listing-creation jane-smith-fc-tucker
> Address: 12345 Maple Creek Dr, Fishers IN 46037
> Property: 4BR / 2.5BA / 2,850 sqft / 2018 / two-story / updated kitchen 2022 (quartz, SS appliances, island), LVP throughout main level, 3-car garage, finished basement, HSE school district
> List price: $549,000
> Highlights: Kitchen remodel, screened porch, walkout basement, cul-de-sac lot
> Neighborhood: Fishers, HSE schools, 5 min to I-69, Flat Fork Creek Park nearby"

**Expected output:**

- Load `jane-smith-fc-tucker` config; agent name and brokerage appear in all output
- **BLC Remarks (≤500 chars):** Lead with kitchen remodel and HSE schools. Pack in BR/BA/sqft/garage. End with a forward-leaning phrase. Character count displayed.
  - Draft: `Stunning 2022 kitchen remodel w/ quartz, SS appliances & island. 4BR/2.5BA, 2,850 SF, HSE schools. LVP main lvl, 3-car gar, screened porch, walkout fin. bsmt. Cul-de-sac lot, 5 min I-69. Schedule your showing today.`
- **Extended Description (1,000–1,500 words):** Opens with lifestyle angle (Flat Fork Creek Park, Fishers community). Walks through home in showing order. Names specific finishes (quartz, island, year of remodel). No contact info in description.
- **Fair Housing Review:** PASS — no protected class language.
- **Instagram Caption:** Visual hook on kitchen remodel. Hashtags from brand-kit.yaml + #FishersIN #HSESchools.
- **Facebook Caption:** Storytelling format. 3–5 feature highlights in natural prose. Call to action.

---

## Example 2: Carmel Luxury Estate, $1.1M

**Agent prompt:**
> "Write listing copy for a Carmel luxury estate — 5,200 sqft, 5BR/4.5BA, built 2015, full 2023 renovation, Carmel Clay schools, Monon Trail access. $1.1M."

**Expected output:**

- Load agent config; apply luxury/polished tone if configured in `agent-profile.yaml`
- **BLC Remarks:** Anchors on custom finishes, school district, Monon access. Specific over generic — name materials and updates. Under 500 chars with count.
- **Extended Description:** Opens with Carmel's identity (arts district, City Center, top-rated schools). Walks through finishes with specific detail. References Monon Trail and City Center dining as lifestyle anchors.
- **Fair Housing Review:** Flag "executive" if present — replace with neighborhood name. PASS otherwise.
- **LinkedIn Caption (optional):** Corporate relo angle — investment value, school rankings, proximity to major employers.

---

## Example 3: Downtown Indianapolis Condo, Urban Lifestyle

**Agent prompt:**
> "Downtown Indy condo — Unit 12B, 1BR/1BA, 875 sqft, 14th floor, floor-to-ceiling windows, city views, deeded parking. $289,000. Steps from Mass Ave."

**Expected output:**

- **BLC Remarks:** Views and location lead. Floor number and deeded parking are key differentiators. Urban lifestyle anchors: Mass Ave, Lucas Oil Stadium.
- **Note:** Condo GLA from condo documents may differ from assessor — skill flags this for agent to verify.
- **Extended Description:** Opens with the city view. Names Mass Ave venues (Patachou, Gallery 924) as concrete lifestyle anchors. Ends with entertainment access (Lucas Oil, Gainbridge Fieldhouse).
- **Fair Housing Review:** PASS — lifestyle language describes location and amenities, not buyer demographics.

---

## Example 4: Investment Property — Tenant-Occupied Duplex

**Agent prompt:**
> "Income-producing duplex in Fountain Square — 2 units, each 2BR/1BA, 1,400 sqft per unit, built 1952. Rents $950/mo each, both month-to-month. $285,000."

**Expected output:**

- **BLC Remarks:** Investor-focused. Leads with income ($1,900/mo gross), Fountain Square location, lease flexibility.
  - Draft: `Income-producing duplex in Fountain Square. 2 units, ea 2BR/1BA, 1,400 SF. Both occupied—$1,900/mo gross. M-to-M leases. Walk to Mass Ave, easy I-65 access.`
- **Fair Housing Review:** PASS — factual income and location data. No demographic steering language.
- **Agent Remarks guidance:** Flag Indiana tenant showing-notice requirements.
- **Form note:** Multi-family BLC form, not single-family.

---

## Example 5: Historic Craftsman Bungalow, Pre-1978, Broad Ripple

**Agent prompt:**
> "1924 Craftsman bungalow in Broad Ripple — 3BR/1.5BA, 1,650 sqft, original hardwoods, updated kitchen and bath 2020, new roof 2022, detached 1-car garage. $375,000."

**Expected output:**

- **Lead paint flag (before any copy):** Pre-1978 detected. EPA Lead Paint Disclosure required before offer acceptance — federal law. Not included in listing copy; handled separately.
- **BLC Remarks:** Historic character leads. Names the architectural style. Calls out key updates with years (2020 kitchen/bath, 2022 roof).
  - Draft: `Rare 1924 Craftsman bungalow w/ original HW floors, exposed beams & front porch. Updated kit & BA (2020), new roof 2022, detached gar. Walk to Broad Ripple Ave, Monon Trail. 3BR/1.5BA, 1,650 SF.`
- **Extended Description:** Opens with Broad Ripple's character. 1924 is treated as a selling point — buyers seeking this style self-select. Walks through original character details (built-ins, craftsman trim, covered porch) alongside updates.
- **Fair Housing Review:** PASS — Broad Ripple named as geographic area, no demographic language.

---

## Example 6: Fair Housing Compliance Check Only

**Agent prompt:**
> "Fair housing check: 'Charming home in quiet, safe, family-friendly Noblesville neighborhood. Perfect for couples starting out or empty nesters. Near excellent Christian schools. Great master bedroom.'"

**Expected output:**

**Fair Housing Review: NEEDS REVISION**

Flagged items:

1. `"family-friendly"` — familial status violation. Replace with factual attributes: yard size, school district name, bedroom count.
2. `"Perfect for couples starting out or empty nesters"` — familial status + age steering. Remove entirely. Suggested replacement: "Move-in ready with a flexible floor plan."
3. `"Near excellent Christian schools"` — religious preference. Replace with: "Minutes from Noblesville Schools" or neutral geographic reference.
4. `"master bedroom"` — outdated terminology. Use "primary bedroom" or "primary suite."
5. `"quiet, safe"` — contextually can imply racial or socioeconomic steering. Replace with physical attribute: "cul-de-sac setting" or "low-traffic street."

**Compliant rewrite provided** for the full passage.

---

*Agents must review all output before submitting to BLC. Fair housing compliance is the agent's and brokerage's legal responsibility.*

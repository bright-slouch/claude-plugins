# MIBOR BLC Field Guide

Complete reference for entering listings in the MIBOR Broker Listing
Cooperative (BLC). Use this guide when entering data directly in the BLC
or when advising agents on correct field values.

---

## What is the BLC?

BLC (Broker Listing Cooperative) is the name MIBOR uses for their MLS
system. MIBOR = Metropolitan Indianapolis Board of REALTORS, serving
Central Indiana. The BLC is the authoritative data source for all
residential listings in the MIBOR territory, which includes Marion County
and all surrounding counties.

---

## BLC Remarks Field

### Hard Rules

| Rule | Detail |
|---|---|
| 500-character limit | Includes spaces and punctuation. BLC will reject or truncate over-limit submissions. Count every character before submitting. |
| No contact info | No phone numbers, email addresses, agent names, brokerage names, or team names |
| No URLs | No website links, Zillow links, virtual tour URLs, or shortened links |
| No ALL CAPS words | Standard abbreviations are fine (see table below) |
| Virtual staging disclosure | If any photos are virtually staged, note it in remarks: "Some photos virtually staged" — this counts toward the 500-char limit |
| No false features | Do not describe features not included in the sale |
| No fair housing violations | See `references/real-estate-vocabulary.md` for prohibited language |

### Approved BLC Abbreviations

| Abbreviation | Meaning |
|---|---|
| BR | Bedroom |
| BA | Bathroom (full) |
| HBA | Half bath |
| SF | Square feet |
| GLA | Gross Living Area |
| LVP | Luxury Vinyl Plank |
| HW / HDW | Hardwood |
| SS | Stainless Steel |
| W/D | Washer/Dryer |
| FP | Fireplace |
| FROG | Finished Room Over Garage |
| HOA | Homeowners Association |
| 2-car gar | Two-car garage |
| Fin. bsmt | Finished basement |
| Mstr | Master/Primary |
| Dr / St / Blvd | Drive / Street / Boulevard |
| HSE | Hamilton Southeastern Schools |
| CCS | Carmel Clay Schools |
| WWS | Westfield Washington Schools |
| MSD | Metropolitan School District |
| IPS | Indianapolis Public Schools |

### Character Counting Tips
- Count in a plain text editor — not Word (Word miscounts due to autocorrect)
- Every space = 1 character
- Em dashes count as 1 character and pack more info per space than commas
- The BLC preview field shows a running count
- Aim for 480–498 characters — leave a small buffer for any last-minute edits

---

## Required Fields — Residential Listing

### Identity and Status Fields

| Field | Valid Values / Format | Notes |
|---|---|---|
| MLS # | Auto-assigned by BLC | Do not enter manually |
| List Date | MM/DD/YYYY | Date listing goes active |
| Expiration Date | MM/DD/YYYY | Date listing agreement expires |
| Status | See Status Definitions section below | |
| Property Type | Residential / Condo / Multi-Family / Land / Commercial | Affects which form version is used |
| List Price | Dollar amount | |
| Original List Price | Dollar amount | Auto-populated from first entry; cannot edit after price change |

### Location Fields

| Field | Valid Values / Format | Notes |
|---|---|---|
| Address | Street number + name | Must match county assessor records |
| City | Full city name | |
| County | Hamilton / Marion / Hendricks / Johnson / Boone / Madison / Hancock / etc. | |
| State | IN | |
| Zip Code | 5-digit | |
| Subdivision / Plat Name | As platted | If no subdivision, enter "None" |
| School District | Full official name | Hamilton Southeastern, Carmel Clay, Westfield Washington, Noblesville, Zionsville, MSD Warren Township, IPS, etc. |
| Elementary School | School name | Verify by address on district website |
| Middle School | School name | |
| High School | School name | |
| MLS Area | BLC-assigned area code | Determines school lookup in some BLC versions |

### Property Characteristics

| Field | Valid Values / Format | Notes |
|---|---|---|
| Bedrooms | Integer | Count only rooms meeting code (closet, egress, minimum sqft); bonus rooms do not count as bedrooms unless they qualify |
| Bathrooms Full | Integer | Toilet + sink + shower or tub = full bath |
| Bathrooms Half | Integer | Toilet + sink only = half bath |
| GLA (Gross Living Area) | Square feet, integer | ANSI standard — see GLA section below. NEVER include basement. |
| Year Built | 4-digit year | Use actual year; if unknown, use "0" or consult county assessor |
| Architectural Style | Ranch / Two-Story / Split-Level / Bi-Level / Colonial / Cape Cod / Craftsman / Contemporary / Tudor / Mid-Century Modern / etc. | Select closest match |
| Garage Type | Attached / Detached / Built-In / Carport / None | |
| Garage Capacity | Integer (number of cars) | |
| Lot Size | Acres (decimal) or square feet | Pull from county GIS or deed |
| Lot Description | Corner / Cul-de-sac / Irregular / Wooded / Waterfront / etc. | Multi-select |
| Basement | Yes / No | |
| Basement Type | Full / Partial / Crawl Space | |
| Basement Finished | Yes / No / Partial | |
| Basement Finished Sqft | Integer | Separate from GLA — enter finished basement sqft here |
| Pool | Yes / No | |
| Pool Type | In-Ground / Above-Ground / Community | |

### Financial Fields

| Field | Valid Values / Format | Notes |
|---|---|---|
| Annual Taxes | Dollar amount | Pull from county assessor; use most recent year |
| Tax Year | 4-digit year | Year corresponding to the tax amount listed |
| HOA | Yes / No | |
| HOA Fee | Dollar amount | |
| HOA Fee Frequency | Monthly / Quarterly / Annual | |
| HOA Name | Association name | |
| HOA Includes | Multi-select: Maintenance Grounds / Snow Removal / Pool / Clubhouse / Trash / Water / etc. | |

### Listing Content Fields

| Field | Valid Values / Format | Notes |
|---|---|---|
| Public Remarks | Text, 500 characters max | No phone numbers, agent names, or URLs. No ALL CAPS. No fair housing violations. |
| Agent Remarks (Private) | Text, separate field | Agent-to-agent notes, showing instructions, offer details. Not visible to public. |
| Showing Instructions | Text | Entered here or managed via ShowingTime integration |
| Inclusions | Text | Appliances, fixtures, personal property included in sale |
| Exclusions | Text | Items NOT included: chandeliers, TV mounts, specific appliances, etc. |
| Virtual Tour URL | URL | Goes here — never in public remarks |
| Compensation | Dollar or percent | Post-Aug 2024 NAR settlement: no longer required but still available. Enter $0 or leave blank if not offering. |

---

## Status Definitions

| Status | Meaning |
|---|---|
| Active | Listing is live; accepting showings and offers |
| Active-Contingent | Under contract with a contingency (inspection, financing, etc.) |
| Active-Kickout | Under contract but seller retains right to accept another offer if first buyer doesn't remove contingency on notice |
| Pending | Under contract; contingencies removed or not applicable; typically not accepting showings |
| Closed | Transaction has closed and deed recorded |
| Withdrawn | Listing removed before expiration; listing agreement may still be in effect |
| Expired | Listing agreement has lapsed; property is not under contract |
| Cancelled | Listing terminated by mutual agreement before expiration |

**Key distinction — Active-Contingent vs. Active-Kickout:**
Active-Contingent: seller cannot accept another offer without releasing the first buyer.
Active-Kickout: seller can issue a 48–72 hour notice requiring the first buyer
to remove their contingency or lose the contract. Most commonly used when
the buyer has a home-sale contingency.

---

## GLA — Gross Living Area (ANSI Standard)

The most commonly misunderstood field in the BLC. Incorrect GLA leads
to appraisal problems and potential misrepresentation exposure.

**What counts as GLA:**
- All above-grade finished living area
- Must be heated, finished, and connected to the main living area
- All levels above grade: main floor, upper floors, finished attic levels
  that meet ceiling height minimums

**What does NOT count as GLA:**
- Any basement area — finished or unfinished, regardless of quality
- Garage area — even if heated and finished
- Below-grade space — any portion below grade level
- Porches, patios, covered entries (unless fully enclosed, heated, and
  meeting code as conditioned living space)

**ANSI minimum ceiling height for GLA inclusion:**
7 feet for the majority of the floor area. For sloped ceilings: at least
half the floor area must be at 7 feet or higher.

**Finished basement — where it goes:**
Enter finished basement square footage in the separate "Basement Finished Sqft"
field. It will appear on the listing but clearly separated from GLA.

**Common mistake:**
- Wrong: "2,850 sqft total (incl. 600 sqft fin. bsmt)" in GLA field
- Right: GLA = 2,250. Basement Finished Sqft = 600. Remarks: "Plus 600 SF
  fin. bsmt w/ rec room, full BA & egress windows"

**Why it matters:**
Appraisers use ANSI standards. If you submit 2,850 sqft GLA that includes
700 sqft of finished basement, the appraisal will return a different GLA.
This creates a gap that can affect financing and constitutes misrepresentation.

---

## Photo Requirements

**Minimum photo count:** 1 required to activate. MIBOR recommends 10 minimum.
Listings with fewer than 10 photos receive significantly less engagement.

**Recommended count:**
- Standard residential: 25–40
- Luxury ($600K+): 40–60
- Vacant lot / land: 5–15

**Main photo (photo #1):**
- Must be an exterior shot of the property — not a room, not a community
  amenity, not a floor plan graphic
- No collages — single image only
- No text overlays, "Just Listed" graphics, or watermarks
- Must accurately represent the property as it exists

**Minimum resolution:** 800x600 pixels required; 1024x768 or higher recommended.
Professional DSLR output far exceeds this minimum.

**Virtually staged photos:**
Each virtually staged photo must be labeled "Virtually Staged" individually
in the BLC photo caption/description field for that image. A single note
in the remarks does not satisfy this per MIBOR policy.

**Drone/aerial photos:**
Permitted. Drone operator must hold FAA Part 107 certification for
commercial real estate photography. Do not submit photos taken in
violation of FAA airspace restrictions. Indianapolis Class B airspace
(near IND airport) requires specific FAA authorization via LAANC.

---

## Showing Instructions — ShowingTime Integration

MIBOR BLC integrates with ShowingTime for showing scheduling. Set up
ShowingTime before the listing goes active.

**Access settings:**
| Option | When to Use |
|---|---|
| Go and Show | Vacant properties or sellers who want maximum showings with no friction |
| Appointment Required | Most occupied listings — agent is notified and must approve |
| Accompanied Only | Listing agent must be present; rare but used for ultra-luxury or sensitive situations |
| Call First | Agent prefers a call before system confirmation |

**Recommended for most occupied listings:** Appointment Required with a
2–4 hour response window. Gives the listing agent awareness without
blocking showings unnecessarily.

**For occupied homes with families or pets:** Appointment Required with
minimum 2-hour notice. Add specific instructions in the private remarks:
pet management, access codes, alarm codes (use with caution).

**Agent Remarks field** (private — visible only to buyer agents on BLC):
- Lockbox code (or "code in showing service")
- Showing preference: "Please remove shoes," "Do not let cat out"
- Offer instructions: "Submit via email to [agent's BLC email], PDF only"
- Occupancy status: "Owner-occupied," "Vacant," "Tenant-occupied"
- Quick close availability if seller needs that communicated agent-to-agent

---

## Indiana-Specific Disclosure Checklist

Every new listing in Indiana requires disclosure documents. Failure to
provide required disclosures violates Indiana Code and MIBOR policy and
can expose agents to licensing complaints.

| Document | Required? | When |
|---|---|---|
| Seller's Residential Real Estate Sales Disclosure (IC 32-21-5-10) | Yes — all residential | Must be completed by seller; provided to all buyers before offer |
| Agency Disclosure | Yes | Required at first substantive contact with a consumer |
| Lead-Based Paint Disclosure | Yes — pre-1978 properties only | Federal requirement (HUD/EPA); buyer must receive EPA pamphlet; buyer has 10-day inspection period unless waived in writing |
| Mold Disclosure | Required if seller has knowledge | If known mold or prior mold remediation, must be disclosed |
| PSTS Disclosure (Private Sewage System) | Required if septic system | Indiana ISDH requirements apply |
| Radon Disclosure | Required if seller has test results | Indiana has elevated radon in many areas; recommend testing if no results available |
| Short Sale / REO Disclosures | If applicable | Lender-required addenda apply |

---

## Common Input Errors That Delay Listing Activation

| Error | Fix |
|---|---|
| GLA includes finished basement | Enter GLA and basement sqft in separate BLC fields |
| Remarks exceed 500 characters | Count precisely; use approved abbreviations aggressively |
| Agent phone number in public remarks | Remove — prohibited per MIBOR rules |
| Agent name or brokerage in remarks | Remove — prohibited per MIBOR rules |
| URL in public remarks | Move to the designated Virtual Tour URL field |
| Wrong school district | Verify by address at the district's website or county GIS — city name does not always match district |
| Missing or incorrect lot size | Pull from county assessor portal or deed; do not estimate from memory |
| Main photo is a collage or has text overlay | Replace with a single clean exterior shot |
| HOA fields incomplete | Complete all HOA sub-fields: fee, frequency, what it covers, association name |
| Year built is estimated without notation | Use "0" if genuinely unknown; inaccurate year built affects appraisal and lead paint disclosure |
| Status not updated after contract | Update to Active-Contingent or Pending within 24 hours per MIBOR Clear Cooperation Policy |
| Inclusions/Exclusions left blank | Specify what stays and what goes — prevents closing-day disputes |

---

## Property Type Notes

### Condo
- GLA often comes from condo documents rather than county assessor — the two
  can differ significantly. Use condo documents as the authoritative source.
- Note parking specifically: deeded space vs. unassigned vs. no parking
- HOA typically covers exterior maintenance, insurance on building envelope,
  and some utilities — list inclusions completely

### Townhome
- Clarify end unit vs. interior unit (end units command premium in most markets)
- Party wall vs. no shared walls — some townhomes are fully detached
- Note whether HOA exists; some townhome communities have none

### New Construction
- Use builder's spec sheet for all measurements
- Add "Est. completion [Month Year]" in remarks if not yet complete
- Floor plan name helps buyers cross-reference on builder's website
- Builder warranty is a major differentiator — note it: "Builder warranty included"

---

*This guide reflects MIBOR BLC rules as understood at time of writing.
Agents should verify current requirements in their MIBOR member portal.
Rules can change with system updates and NAR policy changes.*

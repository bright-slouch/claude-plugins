# Quick Start Guide — re-listing-creation

5-minute overview for agents ready to write listing copy.

---

## What This Skill Produces

For every listing, `re-listing-creation` generates four deliverables:

1. **BLC Remarks** — 500-character max, MIBOR-compliant, ready to paste into BLC
2. **Extended Marketing Description** — 1,000–1,500 word prose narrative for Zillow, Realtor.com, and listing presentations
3. **Social Media Captions** — Instagram (with hashtags from your brand-kit) and Facebook versions
4. **Fair Housing Compliance Review** — automatic scan of all output before delivery

All content uses your brand voice from `agent-profile.yaml` and `brand-kit.yaml`. You paste it into BLC and your marketing channels — the skill does not submit anything directly.

---

## How to Invoke

```
/re-listing-creation [agent-slug]
Address: [property address]
Property: [beds / baths / sqft / year built / type / key features]
List price: [price or range]
Highlights: [top 3–5 features to lead with]
Neighborhood: [city, school district, proximity context]
```

Or in plain language:
```
Write BLC remarks for my new Fishers listing — 4BR/2.5BA, $549K, HSE, updated kitchen
```
```
Extended description for a Carmel luxury estate, 5,200 sqft, $1.1M
```
```
Fair housing check on these BLC remarks: [paste copy]
```

Your agent config loads automatically. If you haven't set it up yet, run `/re-agent-setup` first.

---

## 4 Most Common Use Cases

### 1. New Listing — Full Content Package

Provide address, beds/baths/sqft/year, top features, school district, and list price. All four deliverables in one pass.

```
/re-listing-creation [slug] — [address], [beds/baths/sqft], $[price], [school district], top features: [list them]
```

### 2. BLC Remarks Only (Quick Turnaround)

Need to get the listing live now and write the full description later:
```
Quick BLC remarks for [address] — [beds/baths/sqft], key feature is [X], [school district]
```

The skill writes tight, character-counted remarks. If you're over 500, it offers shorter alternatives.

### 3. Fair Housing Compliance Review

Paste any copy — remarks, description, social post — for a compliance check:
```
Fair housing check on these remarks: [paste copy]
```

Returns: PASS or NEEDS REVISION, specific flagged phrases with the violation type, and a compliant rewrite for each item. Use this any time a seller drafts their own language or requests specific terms you're uncertain about.

### 4. Relisting — Fresh Copy for an Expired Property

Property sat and is back on the market. Buyers remember the old copy — fresh language is critical:
```
Relist copy for [address] — off market 45 days, back at $[new price]. Fresh angle.
```

The skill avoids recycled phrases and repositions with a new lead.

---

## BLC Character Limit — The Most Common Error

**500 characters is tight.** The skill provides a character count with every remarks draft. If you're over 500:
```
Those remarks are at 523 characters — tighten to under 500
```

Key shortcuts:
- Use approved abbreviations: BR, BA, SF, LVP, HW, SS, FP, HSE, 3-car gar, fin. bsmt
- Drop articles: "Updated kitchen" not "An updated kitchen"
- Use em dashes between points instead of "with" or "and"
- Abbreviate school district: HSE, CCS, WWS — not the full name

---

## Fair Housing — What the Skill Checks Automatically

| Issue | Example | What Happens |
|---|---|---|
| Familial status | "family-friendly," "perfect for couples" | Flagged, rewritten |
| Religion | "near [church]" as a selling point | Flagged, rewritten |
| National origin/race | Neighborhood demographic references | Flagged, rewritten |
| Age | "perfect for empty nesters," "retiree-ready" | Flagged, rewritten |
| Disability steering | Accessibility features tied to disability identity | Reframed as physical features |
| Steering language | "quiet street" (context-dependent) | Flagged if contextually suspicious |

The skill **never** outputs copy with these violations. If it cannot write compliant copy with the information provided, it will ask for clarification.

**The agent and brokerage are legally responsible for fair housing compliance.** This review is a quality check — not legal clearance.

---

## 5 Things to Know Before Your First Listing

**1. Square footage = GLA only (above-grade).**
Never include finished basement in the GLA field. BLC has separate basement fields. Call out the basement as a feature in remarks — don't fold it into the headline sqft.

**2. Never put your name or phone number in remarks.**
Contact info goes in the designated BLC agent fields. Putting it in remarks violates MIBOR rules.

**3. "Motivated seller" kills negotiating power.**
Never write this phrase anywhere in listing copy. It signals desperation and invites lowball offers.

**4. Virtual staging requires disclosure.**
Flag it when you provide the property details. The skill includes the disclosure automatically and counts those characters toward the 500 limit.

**5. Pre-1978 homes require the EPA Lead Paint Disclosure.**
The skill flags this automatically. The disclosure (federal law) must be provided to buyers before offer acceptance — it is separate from listing copy and never mentioned in remarks.

---

## Legal Disclaimer

> *This output is for guidance and informational purposes only. It does not constitute legal advice. Agents should consult their managing broker and/or a licensed Indiana real estate attorney for situation-specific guidance. Always comply with Indiana Real Estate Commission rules and your brokerage's policies. All listing content must be reviewed by the agent before submission to BLC. Fair housing compliance is the agent's and brokerage's legal responsibility.*

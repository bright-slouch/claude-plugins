# re-listing-prep — Quick Start Guide

Get a complete listing prep plan in under 5 minutes.

---

## What You Need Before You Start

1. Agent config set up (run `/re-agent-setup` if not done)
2. The seller's address or a brief property description
3. The seller's prep timeline (2 weeks, 4 weeks, or flexible)
4. The seller's prep budget (even a rough number helps)
5. Current condition: move-in ready / needs work / vacant

That's it. The skill handles the rest.

---

## Minimum Viable Prompt

```
/re-listing-prep [your-agent-slug]
Property: [brief description]
Timeline: [2 or 4 weeks]
Situation: [occupied or vacant]
```

Example — the absolute minimum:
```
/re-listing-prep sarah-henderson-compass
Property: 3BR/2BA ranch in Noblesville, built 2005, good condition
Timeline: 3 weeks
Situation: Occupied
```

---

## Full Prompt (Recommended)

```
/re-listing-prep [agent-slug]
Property: [address or description — bedrooms, baths, sqft, year built,
          county/city, notable features or known issues]
Timeline: [2 weeks / 4 weeks / flexible]
Situation: [occupied / vacant / partially occupied]
Budget: [seller's stated prep budget]
Seller notes: [anything relevant — estate sale, pets, kids, luxury, etc.]
```

---

## What Gets Generated

| Output | What It Is |
|--------|-----------|
| ROI-Ranked Repair Checklist | Tier 1/2/3 improvements with cost estimates |
| Room-by-Room Staging Guide | Specific actions per room |
| Photography Shot List | What to capture, drone rec, twilight rec |
| Virtual Staging Guidance | When to use, MIBOR labeling requirements |
| Vendor Task List | Pulled from your vendor-network.yaml |
| Prep Timeline | Day-by-day 2-week or 4-week schedule |

---

## Common Scenarios

### "Just tell me what absolutely must happen"
Add to prompt: `Budget: $1,000` — the skill will triage to highest-ROI
moves only.

### "Vacant home"
Add `Situation: Vacant` — the skill adds virtual staging recommendations
and physical void-space styling tips.

### "Luxury listing"
Add the price range or just note it: `Seller notes: expected list price
$800K+ Carmel` — the skill elevates to professional stager recommendation
and premium photo package guidance.

### "Pre-1978 home"
The skill automatically flags lead paint disclosure requirements when you
provide the year built. Make sure to include year built in your prompt.

### "Seller has pets"
Add to Seller notes. The skill adds odor mitigation, pet removal protocols
for showings, and photo-day checklist.

---

## Delivering the Output to Your Seller

The prep plan is designed to be sent directly to sellers. Best practices:

1. **Review before sending** — customize the vendor contact info if it
   pulled from your config, remove anything not applicable.
2. **Walk through it on a call** — the Tier 1 list is non-negotiable;
   Tier 2 is a conversation; Tier 3 is usually "skip it."
3. **Set a hard staging walkthrough date** — put it in Google Calendar.
   Sellers who don't have a deadline don't prep.
4. **Coordinate the photographer yourself** — don't leave this to the
   seller. Photography is the most important marketing decision you make.

---

## Frequently Asked Questions

**Q: What if my vendor-network.yaml doesn't have a stager listed?**
The skill will flag the gap. Add a stager to your config after this
session, or use this as a prompt: ask the skill to generate a stager
qualification checklist so you know who to vet.

**Q: The seller wants to skip photos and just use their phone.**
Do not allow this. Professional photography is not optional. Walk the
seller through: "Buyers are filtering on photos before they ever visit.
Phone photos cost showings, and fewer showings means lower offers."

**Q: The seller wants to list before they finish prep.**
This happens. The skill can generate a phased plan: minimum viable prep
for go-live with additional improvements staged during the listing period.
Just note it: `Seller notes: wants to list ASAP, will continue prep
after go-live`.

**Q: Should I always recommend professional staging?**
For properties under $400K, targeted staging guidance (this skill) is
usually sufficient. For $500K+, a professional staging consultation
is worth recommending. For $700K+, professional staging is strongly
recommended and the ROI is well-documented.

---

## Next Steps After re-listing-prep

Once the property is prepped and photographed:

- Run `/re-listing-creation` to write BLC remarks, extended description,
  and social media captions from the photos and prep details
- Coordinate photos with `re-showing-coordinator` ShowingTime setup
- Use `re-client-communication` to send the prep plan and photo schedule
  to the seller in your branded email template

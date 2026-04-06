# Quick Start Guide — re-property-marketing

5-minute overview for agents launching a marketing campaign.

---

## What This Skill Does

`re-property-marketing` generates complete, branded marketing campaigns for your active
listings. You tell it what the property is and what stage of the listing lifecycle you're
in, and it produces ready-to-use copy for every channel — social media, email, print flyer,
video scripts, and broker open invitations.

All output uses your brand-kit.yaml for hashtags, tagline, and brokerage disclaimer. Fair
housing compliance is built in.

---

## How to Invoke

```
/re-property-marketing [property address + key details + agent slug + campaign type]
```

Or describe your need naturally:
```
Just listed a 4BR in Fishers — need the full social series and an email to my sphere.
Slug: sarah-jones-fc-tucker
```
```
Price reduction on my Greenwood listing — was $369K, now $349K. Need a social post
that keeps it positive. Slug: lisa-chen-kw
```
```
Open house this Sunday in Noblesville. Need 2-week promo countdown. Slug: sarah-jones-fc-tucker
```

If you haven't set up your agent profile yet, run `/re-agent-setup` first.

---

## 5 Most Common Use Cases

### 1. Just Listed — Full Campaign Launch

The most common use. Provide the full property details and ask for the complete package.

```
/re-property-marketing [address], [BR/BA], [sqft], [top 3 features],
[school district], [$price], [MLS#]. Just Listed. Full social series
+ email blast. Slug: [your-slug]
```

You get: Just Listed post, 3–5 feature spotlight posts, sphere email (A/B subject lines),
print flyer text, and a 30-second reel script.

### 2. Price Reduction — Reframe Positively

When you need to announce a price update without signaling distress.

```
Price reduction — [address], was $[X], now $[Y]. Keep it positive.
Slug: [your-slug]
```

The skill leads with the property's strengths and frames the price as an opportunity,
not a problem. No "MUST SELL" language unless you confirm that's accurate.

### 3. Open House Promo Series

Give the skill the open house date and it builds a 2-week countdown content calendar.

```
Open house — [address] — [date], [time]. Need the 2-week promo series.
Slug: [your-slug]
```

You get: daily social post schedule, sphere email invite, and broker open invitation
if you want a separate agent event.

### 4. Under Contract / Just Sold Celebration

Turn a closed deal into new seller leads.

```
Just sold [address] in [X days]. Need social posts and a sphere email
to generate seller inquiries. Slug: [your-slug]
```

The skill uses your outcome stats to demonstrate market activity and ends every piece
with a soft seller CTA.

### 5. Ongoing Feature Spotlights

Already have the Just Listed post live? Keep the listing visible during days on market
with targeted feature posts.

```
Need 3 more feature spotlight posts for [address] — [property details].
Still active on the market. Slug: [your-slug]
```

---

## What to Provide

The more detail you give, the better the output. Minimum required:

| Item | Example |
|---|---|
| Full address | 4218 Buttonwood Dr, Fishers, 46037 |
| BR / BA | 4BR / 3BA |
| Key features | Updated kitchen, finished basement, fenced yard |
| School district | Hamilton Southeastern (HSE) |
| List price | $425,000 |
| MLS number | 21812345 |
| Campaign type | Just Listed / Price Reduction / Open House / Just Sold |
| Agent slug | sarah-jones-fc-tucker |

Optional but valuable: GLA, garage, HOA, year built, notable upgrades (roof year, HVAC year),
open house date/time if applicable.

---

## Fair Housing — What This Skill Never Does

Every piece of marketing this skill produces complies with the federal Fair Housing Act
and HUD language guidelines. Specifically:

- No descriptions of who the "ideal buyer" is
- No demographic references to neighborhoods, schools, or nearby properties
- No steering language — "quiet neighborhood," "established area," or coded phrases
- Schools are named (e.g., "Carmel Clay Schools") — never described by composition

If you submit copy with problematic language, the skill will flag it and suggest
compliant alternatives. See `references/real-estate-vocabulary.md` for full guidance.

---

## Brand Integration

The skill automatically pulls from your config:
- **Hashtags** from `brand-kit.yaml` → appended to every social post
- **Tagline** from `brand-kit.yaml` → used in video scripts and email sign-offs
- **Brokerage disclaimer** from `brand-kit.yaml` → on every print/email piece
- **Signature block** from `email-templates.yaml` → closes every email

If your brand details look wrong in the output, check your config files or re-run
`/re-agent-setup` to update them.

---

## Legal Disclaimer

> *This output is for guidance and informational purposes only. It does not constitute
> legal advice. Agents should consult their managing broker and/or a licensed Indiana
> real estate attorney for situation-specific guidance. Always comply with Indiana Real
> Estate Commission rules and your brokerage's policies.*

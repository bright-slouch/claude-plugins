# Quick Start Guide — re-seller-consultation

5-minute overview for agents new to this skill or preparing for their next listing appointment.

---

## What This Skill Does

`re-seller-consultation` prepares you for seller consultations and walks you through everything from the first discovery question to the signed listing agreement. It generates:

- A goal discovery questionnaire tailored to the seller's situation
- An Indiana-specific agency disclosure script
- A pricing strategy framework with three scenarios
- A reverse-timeline worksheet from list date to target close
- A seller net sheet estimate populated from your fee structure
- A personalized listing presentation populated from your agent profile

This skill handles the preparation and the talking points. You still transfer the listing agreement, net sheet, and disclosure form to Dotloop, ZipForms, or your platform of choice.

---

## How to Invoke

From the plugin:
```
/re-seller-consultation [seller name, address, or situation]
```

Or in plain language:
```
Prep me for a listing consultation at 4822 Maple Drive — motivated seller, job relocation
```
```
Estate sale consultation for 4104 N. Dearborn Street, Indianapolis
```
```
Seller wants $60K over comps — give me the price expectation script
```
```
Generate net sheet estimate for $425,000 at [address]
```

The skill loads your agent config automatically. If you haven't set up your profile, run `/re-agent-setup` first.

---

## 4 Most Common Use Cases

### 1. Full Consultation Prep (Before the Appointment)

Tell the skill: address, seller's situation, any known context (relocation, estate, divorce, investor, etc.), and the seller's price expectation if you know it.

The skill produces a full consultation package: discovery questionnaire, agency script, pricing strategy with recommendation, timeline worksheet, and estimated net sheet.

**Start with:**
```
Prep seller consultation for [address] — [situation], they're thinking $[price]
```

---

### 2. Scenario-Specific Guidance

Some situations need specialized preparation. Use these openers:

| Situation | Starter Prompt |
|---|---|
| Job relocation with deadline | `"Relocation seller, needs to close in [X] days"` |
| Estate sale / executor | `"Estate sale — executor is handling deceased [parent/spouse]'s home"` |
| Tenant-occupied investment | `"Investor-owned rental, tenant is month-to-month"` |
| Divorce situation | `"Divorcing couple, both on deed — only one has called me"` |
| Corporate relo (Cartus, SIRVA, etc.) | `"Corporate relo through [company name], hard deadline [date]"` |
| Unrealistic price expectations | `"Seller wants $[X], comps are $[Y] — give me the script"` |

---

### 3. Price Expectation Management Only

If you're walking into a tough price conversation and just need the language, use:

```
Seller at [address] is anchored at $[X]. Comps support $[Y]. Give me the price conversation scripts.
```

The skill provides three scripts: Data Anchor, Gentle Redirect, and Net Proceeds Reframe. The Net Proceeds Reframe — showing the seller the actual dollar difference in their pocket between the two prices — is often the most powerful. See `references/consultation-framework.md` for the full scripts with sample numbers filled in.

---

### 4. Net Sheet Only

If you have a price and want a quick net sheet estimate:

```
Net sheet estimate for $380,000 sale at [address]
```

The skill pulls your commission and fee data from `fee-structure.yaml` and populates the seller net sheet template. Remember to tell the seller this is an estimate — the title company calculates the actual figures at closing.

---

## 5 Key Things Every Indiana Listing Agent Should Know

**1. Agency disclosure is required before you start talking business.**
Indiana requires verbal disclosure at first substantive contact — which means before you discuss price, motivation, or anything transaction-specific. The written form (IAR Form 108) is provided at or before signing the listing agreement. Get the verbal disclosure out of the way in the first 30 seconds.

**2. Both parties must sign the listing agreement.**
If there are two names on the deed, both must sign the Exclusive Right to Sell agreement. This matters most in estate sales (executor authority must be confirmed) and divorce situations (both spouses must agree). Do not market a property without confirmed signing authority from all owners.

**3. Buyer broker compensation is now negotiable and must not be presented as standard.**
Post-August 2024 NAR settlement rules: sellers are no longer required to offer buyer broker compensation via MLS. Some sellers will ask whether they "have to" pay the buyer's agent. The honest answer is no — it is negotiable. Explain the strategic implications (fewer buyer's agent showings if $0 is offered), but never represent it as a mandatory requirement.

**4. A CMA is not an appraisal.**
When you present pricing, always note that the CMA is an estimate based on recent comparable sales — not a certified appraisal. If the seller needs a guaranteed value (for estate, divorce, or other legal purposes), they should commission a licensed appraiser.

**5. Overpriced listings hurt everyone.**
The first two weeks of a listing generate the most buyer activity. An overpriced listing burns through that window, sits, gets price reductions, and ultimately nets the seller less than an at-market launch would have. Be direct about this in the consultation — it is part of your professional duty.

---

## Critical "Do Not Do" Reminders

- Do not claim any commission rate is "standard" or "industry-set" — it is negotiable
- Do not tell a seller to skip or minimize the disclosure form — IC 32-21-5-10 requires it for most sales
- Do not give tax advice on capital gains, 1031 exchanges, or depreciation recapture — that is for their CPA
- Do not advise a seller to conceal known defects — disclose and adjust price instead
- Do not list without confirmed authority from all parties on the deed

---

## Legal Disclaimer

> *This output is for guidance and informational purposes only. It does not constitute legal advice. Agents should consult their managing broker and/or a licensed Indiana real estate attorney for situation-specific guidance. Always comply with Indiana Real Estate Commission rules and your brokerage's policies.*

# Quick Start Guide — re-disclosure-assistant

5-minute overview for agents who are new to this skill or want a fast refresher.

---

## What This Skill Does

`re-disclosure-assistant` is your compliance co-pilot for the Indiana Seller's Residential Real Estate Sales Disclosure process. It guides you through IAR Form 46234 section by section, handles the federal lead paint overlay for pre-1978 homes, flags gray-area situations with decision trees, and reviews marketing copy for fair housing language.

It does NOT fill out the form for you. The seller fills out Form 46234 — your job is to explain what's required. This skill helps you do that confidently and completely.

---

## How to Invoke

From the plugin:
```
/re-disclosure-assistant [property address or 'new disclosure']
```

Or just describe your situation in natural language:
```
New disclosure walkthrough — 4822 Maple Drive, seller has lived there 11 years
```
```
Pre-1978 home at 3309 Park Ave, need the lead paint checklist
```
```
Seller wants to go as-is — what still needs to be disclosed?
```

The skill will load your agent config automatically from your config file. If you haven't set up your agent profile yet, run `/re-agent-setup` first.

---

## 3 Most Common Use Cases

### 1. Pre-Listing Walkthrough (Most Common)

You're preparing for a listing appointment or sitting with the seller. Walk through Form 46234 section by section to make sure nothing is missed before the buyer ever sees it.

Start with:
```
New disclosure walkthrough for [address] — built [year], seller has owned it [X years]
```

The skill will guide you through every section, flag known issues, and produce a summary checklist when you're done.

### 2. "Do I Have to Disclose That?"

A seller calls with a specific question: prior flooding, an old meth lab rumor, a sunroom built by a friend, a death in the home. Get a clear, Indiana-specific answer before you advise the seller.

Start with:
```
Quick question — seller at [address] wants to know if they have to disclose [situation]
```

### 3. Lead Paint Compliance Check

Any home built before 1978 triggers federal requirements beyond Form 46234. Use this skill to get the complete IAR Form 46232 checklist and the seller script.

Start with:
```
Pre-1978 home — what do I need for lead paint compliance?
```

---

## Key Things to Know About Indiana Disclosure Law

**1. Sellers disclose what they KNOW.**
Indiana disclosure is knowledge-based. A seller who genuinely doesn't know is not required to discover — they mark "Unknown." But a seller who knows something and marks "No" has potentially committed misrepresentation.

**2. "As-is" does not mean no disclosure.**
This is the #1 misconception. "As-is" tells the buyer they're accepting the condition as described. It doesn't give the seller permission to conceal known defects. Every as-is seller still completes Form 46234 fully and honestly.

**3. Remediated problems are still disclosable.**
If the seller knew the basement flooded and had it fixed — that's a known history of water intrusion. Disclose the event and the remediation. A fixed problem with documentation is not a red flag; an undisclosed problem discovered post-closing is.

**4. Pre-1978 homes require TWO forms.**
Form 46234 (Indiana disclosure) AND Form 46232 (federal lead paint disclosure). The buyer also gets an EPA pamphlet and a 10-day right to inspect for lead paint. These are federal requirements with civil penalty exposure up to $10,000 per violation.

**5. Indiana does NOT require disclosure of deaths in the home.**
IC 32-21-5-11 specifically exempts psychological stigma — deaths, crimes, and paranormal history. Don't volunteer this. If a buyer asks, direct them to public records.

**6. The agent should not complete the form.**
The seller completes Form 46234. The agent explains what each section means and what qualifies as a known defect. An agent-completed disclosure creates liability for the agent.

**7. Update the disclosure when new facts arise.**
If a material fact comes to light after the disclosure is signed but before closing (a new roof leak is discovered during showing prep, for example), the seller must update the disclosure before closing.

---

## Legal Disclaimer

> *This output is for guidance and informational purposes only. It does not constitute legal advice. Agents should consult their managing broker and/or a licensed Indiana real estate attorney for situation-specific guidance. Always comply with Indiana Real Estate Commission rules and your brokerage's policies.*

# re-negotiation-advisor — Example Prompts

Eight realistic negotiation scenarios covering inspection, appraisal, and offer situations.

---

## Example 1: Inspection Negotiation — Buyer Side, Multiple Issues

**Scenario:** Inspection on a $340K Fishers home came back with significant findings:
furnace replacement needed ($7K), partial roof failure ($8K), PB pipe throughout
($12K), and a collection of minor items. Buyer wants to proceed but needs a credit.
Market is balanced (3.5 months supply).

**Prompt:**
```
/re-negotiation-advisor inspection response — buyer side

Property: 4218 Buttonwood Dr, Fishers IN 46037
Purchase price: $340,000
Market: Balanced (3.5 months supply)
Inspection findings:
  - Furnace replacement needed ($7K estimate from inspector)
  - Roof has 2–3 years of life remaining; active moisture in attic ($8K replacement)
  - Polybutylene pipe throughout — inspector noted significant failure risk ($12K replacement)
  - Missing GFCI in 3 bathrooms and kitchen (safety item, ~$600 to fix)
  - Cosmetic items: some caulking, a few door adjustments, old garage door opener

Buyer wants to proceed but needs the major items addressed.
Slug: sarah-jones-fc-tucker
```

**What the skill should produce:**
- Issue categorization:
  - Tier 1 (non-negotiable): GFCI (safety) and one of the three major systems as the priority
  - Tier 2 (important, ask for credit): Furnace + roof = primary concerns
  - Strategic decision: PB pipe is significant but expensive; decide whether to include
    in the ask or negotiate separately
- Credit request recommendation: start at $20,000 (furnace + roof primary; adds buffer for
  seller counter) with PB pipe as a discussion item the buyer may accept as-is with a price adjustment
- Request framing template ready to use
- Scenario for seller counter at $12K: accept if covers furnace + roof; counter if not
- Walking point: if seller offers less than $10K, buyer has a decision to make —
  PB pipe alone is a long-term liability that insurance companies increasingly reject
- GFCI note: frame as a safety item seller should fix regardless; separate from credit ask

---

## Example 2: Appraisal Came In Low — Buyer Side

**Scenario:** Buyer is under contract at $515K on a Carmel home. Appraisal came
back at $498K — a $17K gap. Buyer has 5% down saved and approximately $12K in
additional reserves. No appraisal gap coverage in the contract.

**Prompt:**
```
/re-negotiation-advisor appraisal gap — buyer side

Property: 14204 Carey Rd, Carmel IN 46033
Purchase price: $515,000
Appraised value: $498,000
Gap: $17,000
Buyer's financing: Conventional, 5% down ($25,750)
Buyer's additional cash reserves: ~$12,000
Gap coverage in contract: None (standard appraisal contingency)
Seller's situation: Listed 14 days, sold above list, motivated but not desperate
Slug: sarah-jones-fc-tucker
```

**What the skill should produce:**
- Option menu with analysis:
  1. Renegotiate price to $498K: buyer loses nothing additional; seller absorbs full gap;
     seller's expected acceptance likelihood = moderate (they got $515K offer, market supported it)
  2. Split the gap: buyer covers $8,500 (brings reserves down to $3,500); seller reduces to $506,500;
     buyer's lender must confirm they can close with reduced reserves after the gap cash
  3. Buyer covers full gap: buyer can only cover $12K of the $17K without depleting all reserves;
     not recommended — leaves buyer without a financial cushion
  4. ROV: worth investigating — did appraiser miss any recent Hamilton County comps? Agent
     should review the appraisal report before responding to seller
  5. Walk: buyer has right under appraisal contingency; earnest money returns; practical
     only if buyer has alternatives
- Lender constraint: note that lender loans against $498K; buyer must bring down payment
  on $498K + the gap cash. Confirm with lender how much additional cash buyer needs at close.
- Recommended approach: propose split ($498K + $8,500 buyer cash) first; ROV in parallel if comps exist
- Talking points script for buyer agent to use with listing agent

---

## Example 3: Multiple Offers as Listing Agent

**Scenario:** Listing agent has 4 offers on a Westfield listing. Needs to advise
the seller on how to evaluate the offers and what response to send. Refer to
re-offer-writer Example 5 for the offer details, or reconstruct from scenario.

**Prompt:**
```
/re-negotiation-advisor multiple offer management — listing agent side

Property: 2204 Meadow Creek Ln, Westfield IN 46074
List price: $429,000
Offer 1: $435K, conventional 5% down, 10-day inspection, standard terms, close 4/30
Offer 2: $442K, conventional 10% down, 7-day inspection, $5K gap coverage, close 5/10
Offer 3: $425K, FHA 3.5% down, $4K CC assistance, standard terms, close 5/15
Offer 4: $438K, cash, waived inspection, 3-day post-possession, close 4/15

Seller's goal: maximum net, minimum uncertainty, ideally close by May 1
Slug: lisa-chen-kw
```

**What the skill should produce:**
- Offer analysis with seller's stated goals in context:
  - Cash (Offer 4) = best match for "minimum uncertainty" AND close by May 1 goal (15-day close);
    waived inspection removes risk; 3-day post-possession is minor inconvenience
  - Offer 2 = best financed offer, highest price ($442K), but closes May 10 (misses May 1 goal);
    $5K gap coverage reduces appraisal risk meaningfully
  - FHA (Offer 3) = weakest: lowest net ($421K after CC), slowest close, highest financing risk
    on a property with visible deferred maintenance
- Recommendation: present to seller with a clear recommendation to either accept Offer 4
  (certainty + timeline match) or counter Offer 2 on the closing date
- Simultaneous H&B counter option: if seller wants to test Offer 4's price, send a counter
  to Offer 4 at $442K; if Offer 4 buyer won't go to $442K, fall back to Offer 2
- What NOT to do: do not counter Offer 3 first — it wastes time and creates a weaker position

---

## Example 4: Responding to a Lowball Offer — Seller Side

**Scenario:** Listing agent receives an offer on a $429K Westfield listing at
$385K — significantly below list and below the CMA range of $418K–$440K.
Seller is frustrated and wants to reject outright. Agent needs talking points.

**Prompt:**
```
/re-negotiation-advisor lowball offer — seller side

Property: 2204 Meadow Creek Ln, Westfield IN 46074
List price: $429,000
CMA range: $418,000–$440,000
Offer received: $385,000, conventional financing, 10-day inspection, no concessions
Days on market: 9 (no other offers yet)
Seller's reaction: "That's insulting. Just reject it."
Slug: lisa-chen-kw
```

**What the skill should produce:**
- Advice to agent: do not reject without countering at 9 DOM
- Reasoning for seller: rejecting without countering closes a negotiating door; a counter
  at list price costs nothing and reveals whether buyer is serious or fishing
- Counter strategy: counter at $429,000 (full list); no concessions; expires 24 hours
- Framing for seller: "Sending a counter at list price is not backing down. It's saying
  'we know what this home is worth.' If they're real buyers, they'll come back closer to
  your number. If they ghost after the counter, they were never serious buyers."
- What the counter communicates: seller is engaged but not desperate
- If seller insists on rejecting: note the professional risk (potential deal on the table);
  if seller is firm, respect their decision; reject without counter; document the conversation
- Alternative: counter at $419,000 — a $10K concession from list that's within CMA range;
  makes seller look reasonable while still being within supportable comp range

---

## Example 5: Bidding War as Buyer Agent

**Scenario:** Buyer is in a multiple-offer situation in Hamilton Southeastern schools.
3 other offers known. Listing agent called H&B for noon tomorrow. Buyer is pre-approved
at $360K; current best-guess winning range is $350K–$360K. Buyer is anxious and
asking if they should "just offer $375K."

**Prompt:**
```
/re-negotiation-advisor bidding war — buyer agent

Property: 14088 Foxchase Ln, Fishers IN 46037
List price: $335,000
CMA from re-cma: $330,000–$342,000
H&B deadline: Tomorrow at noon
Other offers: 3 confirmed
Buyer pre-approval: $360,000
Buyer's read: "I really want this house, should I offer $375K?"
Buyer has 5% down; no appraisal gap coverage in original offer
Slug: sarah-jones-fc-tucker
```

**What the skill should produce:**
- Anchor to data: agent needs to be the voice of reason; $375K is $33K above CMA high ($342K)
  and $15K above pre-approval; at $375K with 5% down, there is a $33K appraisal gap likely
- Practical analysis:
  - If buyer offers $375K and property appraises at $342K: buyer faces $33K gap PLUS down payment
  - At $360K (pre-approval ceiling) with 5% down, there's already a potential $18K appraisal gap
  - At $352K (upper escalation with escalation clause), there's a $10K potential gap
- Recommendation: escalation clause approach — base $342K (at CMA high), increment $2K,
  ceiling $352K; confirm buyer can cover $10K gap at ceiling ($352K - $342K CMA = $10K extra cash)
- Emotional coaching script: "I understand you love this house. But offering $375K without
  appraisal gap coverage means you'd need an extra $33K in cash beyond your down payment if it
  doesn't appraise. Can you do that? And if yes — is this the home you want to pay that for?"
- Final framing: "Let's put in your best offer that you'd be emotionally okay with if you
  don't get it. Because there will be another great house, and I'd rather you win the right
  one than overpay for this one."

---

## Example 6: Inspection Concession Request — Seller Side

**Scenario:** Seller received an inspection response requesting a $14,000 credit
covering: roof ($8K), HVAC ($5K), and a list of minor items (~$1K). The home was
priced competitively. Seller feels the request is excessive. Market is balanced.

**Prompt:**
```
/re-negotiation-advisor inspection response — seller side

Property: 2204 Meadow Creek Ln, Westfield IN 46074
Purchase price: $425,000 (countered from original offer)
Buyer inspection request: $14,000 credit
  - Roof replacement: $8,000 (estimated 3 years of life remaining)
  - HVAC replacement: $5,000 (estimated 4 years remaining, functional)
  - Miscellaneous minor items: ~$1,000
Market: Balanced (3.5 months supply)
Seller's position: "The house was priced fairly. I don't want to give $14K back."
Slug: lisa-chen-kw
```

**What the skill should produce:**
- Validate that $14K is on the high side for a balanced market with functional systems
- But: acknowledge that roof with 3 years remaining and HVAC with 4 years are legitimate
  concerns — they're not fabricated; buyer's agent has a fair basis
- Recommended counter: $7,000 focused on roof only (most time-sensitive system);
  "Seller will provide a $7,000 closing cost credit for the roof. All other inspection
  findings, including the HVAC, are accepted as-is. Buyer waives all remaining inspection
  contingency upon execution of this addendum."
- Rationale for the $7K: covers the most urgent issue; splits the gap roughly evenly;
  leaves HVAC to buyer's discretion post-close
- Alternative: counter at $6K if seller wants to negotiate further; $5K for the HVAC only
- What to communicate to seller: "In a balanced market, rejecting the inspection request
  entirely carries real risk of the buyer walking. We lose 3–4 weeks of marketing time
  and start over. A $7K credit on a $425K deal is 1.6% — worth keeping a qualified buyer."

---

## Example 7: Deal Threatening to Fall Apart — Salvage Attempt

**Scenario:** Transaction is 18 days from closing. Buyer has lost their job.
Financing is now uncertain. Inspection was clean; no other issues. Seller had
turned down a backup offer. Agent is the listing agent.

**Prompt:**
```
/re-negotiation-advisor deal falling apart — listing agent, financing at risk

Property: 4218 Buttonwood Dr, Fishers IN 46037
Purchase price: $340,000
Days since acceptance: 27
Days to closing: 18
Issue: Buyer's agent called — buyer lost their job; lender may not approve the loan
Inspection: Clean, no issues
Backup offer: Was available 2 weeks ago; listing agent declined it; unknown if still available
Financing contingency deadline: Passed 6 days ago
Slug: sarah-jones-fc-tucker
```

**What the skill should produce:**
- Immediate step 1: confirm the financing contingency deadline date in the contract
  - If passed: seller is legally within rights to terminate and retain earnest money
  - If not passed: buyer still has time to work through financing
- Step 2: contact buyer's agent to understand the actual financing situation
  - Is the lender still working on it? Will they approve with reserves/assets?
  - Does buyer have a co-borrower or alternative financing path?
  - Does buyer have a cash option (family loan, 401k loan, etc.)?
- Step 3: if buyer can close (even with delay): negotiate an amendment extending the
  closing date by 14–21 days to allow financing resolution
- Step 4: if buyer genuinely cannot close: discuss earnest money disposition
  - Financing contingency passed: seller has claim to earnest money as liquidated damages
  - Best path: mutual written release with earnest money split — avoids court and interpleader
- Backup offer: attempt to reach out to that buyer agent to see if the offer is still available
  before making any public announcement of the property falling out
- Communication to seller: "I want to give you the full picture of what we know and the options.
  [Present options.] I can't control what happens with their financing, but I can make sure we
  protect your interests every step of the way."

---

## Example 8: Difficult Other Agent

**Scenario:** Buyer agent submitted an offer. Listing agent is being adversarial —
sending threatening emails, misrepresenting the contract terms, claiming there are
multiple offers (agent is skeptical), and being generally unprofessional. Buyer
wants the home; agent needs to manage this without escalating.

**Prompt:**
```
/re-negotiation-advisor difficult other agent

Situation: Buyer agent on a Carmel listing. Listing agent claims 3 other offers exist
but won't confirm. Has sent emails with phrases like "my seller will terminate if you
don't remove contingencies by tomorrow morning." Property has been on market 22 days.
Our offer is at list price with standard contingencies.

Agent's concern: Are the competing offers real? Should we hold firm on contingencies?
Slug: sarah-jones-fc-tucker
```

**What the skill should produce:**
- First: assess the legitimacy of the claimed competing offers
  - 22 DOM is not typical behavior for a genuine multiple-offer situation
  - Real multiple-offer scenarios usually result in H&B calls, not ultimatums
  - "Will terminate if you don't remove contingencies by morning" is a pressure tactic
- Guidance: do not panic and waive contingencies under artificial pressure
  - Buyer waiving inspection on a 22 DOM property "under pressure" is not a negotiating
    win — it's taking on unknown risk
- How to respond professionally (draft email):
  > "Thank you for communicating your seller's position. We remain committed to the purchase
  > at the offered terms. Please present our offer to your seller. We are prepared to move
  > forward with our current terms or discuss modifications to mutually agreed terms in
  > writing. We look forward to your response."
- Do NOT write: "We know there are no other offers" (unprovable, accusatory) or "Your seller
  can't do that" without citing the specific contract provision
- If truly a fake competing offer: MIBOR Code of Ethics prohibits fabricating competing
  offers; document the claim in writing; raise with managing broker post-close if verified
- Bottom line: hold your terms unless buyer genuinely wants to flex; respond in writing only;
  don't match the tone; keep the focus on getting to yes

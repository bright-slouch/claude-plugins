# Example Prompts — re-seller-consultation

These scenarios show realistic agent inputs and describe what the skill should produce. Use these to understand the skill's scope and to validate behavior.

---

## Example 1: Motivated Seller — Job Relocation, 45-Day Close

**Agent prompt:**
> "Prep me for a listing consultation at 7214 Bayberry Lane, Fishers — seller just got a job offer in Denver, starts in 6 weeks. They want to close in 45 days if possible. 4BR/2.5BA, built 2009, they've owned it 8 years. They're thinking $410,000. Recent sales in their sub are $390-$405K."

**Context:**
- Situation: job relocation with hard deadline
- Seller's price anchor: $410K
- Comp range: $390-$405K — seller is 1-5% over comps
- Timeline: 45-day close target

**Expected output:**
- Load agent config; confirm agent name, brokerage, phone in all output
- Flag immediately: 45-day close is achievable if list → contract happens within 2 weeks. A 30-day contract-to-close is standard; 45 days from list requires going under contract by Day 15
- Generate goal discovery questionnaire tailored to relocation scenario — include questions about whether employer is providing any relo assistance, whether they have housing in Denver secured, and whether they can consider a leaseback if buyer needs quick close but seller needs a few extra days
- Agency script: verbal disclosure, seller's agent duties, brief note that 45-day timeline makes at-market or aggressive pricing critical
- Pricing strategy: recommend At-Market or Aggressive. Show all three strategies with expected DOM and probability of making the 45-day target. Aspirational pricing at $410K with a $390-405K comp range risks sitting 30+ days and missing the deadline entirely
- Timeline worksheet: work backward from a target close date 45 days out. Show that listing must be active by Day 1, under contract by Day 10-14 to allow 30-day close. Flag: if not under contract by Day 15, the 45-day close is at risk
- Net sheet at $400K (at-market mid-range): pull listing commission and any buyer comp offer from `fee-structure.yaml`, calculate standard Indiana closing costs, note mortgage payoff as TBD
- Note that seller should contact their lender now to get an estimated payoff figure — it changes daily
- Suggested opening line for agent: "Given your timeline, I want to show you exactly what pricing this right on Day 1 looks like vs. starting high and having to reduce. Let's look at the numbers."
- Legal disclaimer included

---

## Example 2: Estate Sale — Executor Handling Deceased Parent's Home

**Agent prompt:**
> "Estate sale consultation — executor is the son, David Chen. His mother passed away 3 months ago. Home is at 4104 N. Dearborn Street, Indianapolis — built 1978, 3BR/1BA, she lived there for 40 years. David hasn't been in the house much. He's in Columbus and wants to settle the estate. He just wants it handled respectfully and doesn't know what it's worth."

**Context:**
- Situation: estate sale, executor has no personal knowledge of condition
- Seller: executor (personal representative of estate), not a direct owner
- Emotional context: recent death of parent, son is out of state
- Property: older home, 40 years of single owner-occupancy
- Seller's goal: settle estate, respect the process, doesn't know the value

**Expected output:**
- Load agent config; all output uses agent name and brokerage
- Goal discovery questionnaire modified for estate context:
  - What is David's role — personal representative of the estate? Is an attorney handling the estate?
  - Are there other heirs who also need to consent to the sale?
  - Is there a probate deadline or any court order affecting the timeline?
  - Does David know of any major condition issues he saw on visits?
  - Does he have access to the home and a point of contact who has been maintaining it?
  - What does "handled respectfully" mean to him — is he looking for certainty, speed, or top dollar?
- Agency script: explain seller's agent represents the estate/executor, not individual heirs. If multiple heirs have ownership interests, all may need to sign the listing agreement — recommend the estate attorney confirm before listing
- Emotional tone guidance: acknowledge the difficulty, be warm and patient. Don't lead with numbers. Sample opener: "I know this is a lot to navigate alongside everything else. My job is to handle the property side completely so you can focus on the rest. Let's start with what you need from this sale."
- Pricing: without comps, note that a CMA will be run (`re-cma`). Frame for David: "We'll look at what similar homes in this neighborhood have sold for recently, and I'll give you an honest range. It's not about what you or I think it should be worth — it's about what the current market will bear."
- Disclosure guidance: executor with no personal knowledge should mark sections "Unknown" on Form 46234 — not "No." Recommend reviewing any paperwork in the home (old repair invoices, permits, home warranty records) before the appointment. Route to `re-disclosure-assistant` for full walkthrough.
- Timeline: no hard deadline mentioned, so at-market pricing is appropriate. But suggest setting a realistic timeline — if no offers in 30 days, reassess pricing.
- Net sheet: run at estimated price once CMA is complete. Remind agent that estate sale proceeds go to the estate — not directly to David — and he should coordinate distribution with the estate attorney.
- Flag red flag: confirm whether home is in probate and whether all necessary parties have authority to sign a listing agreement before proceeding.
- Legal disclaimer included, with note to consult estate attorney for authority questions.

---

## Example 3: Investor-Owned Rental Property — Tenant Occupied

**Agent prompt:**
> "Consultation for an investor — owns a rental at 2388 N. Bosart Ave, Indianapolis. 3BR/1BA duplex, built 1952. He has a tenant on a month-to-month lease paying $1,050/month. Tenant has been there 3 years. He wants to maximize sale price. Is a landlord."

**Context:**
- Situation: investment property exit
- Property: tenant-occupied, month-to-month lease
- Seller motivation: financial — maximize net
- Comps will be evaluated on both residential (owner-occupant buyers) and investor (cap rate) metrics

**Expected output:**
- Load agent config; use agent name and brokerage throughout
- Goal discovery questionnaire for investor seller:
  - What's the net proceeds goal? Is there a 1031 exchange being considered?
  - What's the mortgage payoff situation — is there positive equity?
  - Is the seller open to giving the tenant notice before listing, or does tenant stay during the sale?
  - What's the tenant's history? Any issues, deferred maintenance, or lease violations?
  - Is the seller okay with an investor buyer (who would keep the tenant) vs. an owner-occupant buyer (who would need vacant possession)?
  - Timeline: is there urgency, or will the seller wait for the right offer?
- Agency: standard seller's agent script. Note: investor sellers often have less emotional attachment and more interest in net numbers — lean into the net sheet conversation early.
- Tenant occupancy strategy: explain that tenant-occupied properties typically sell for 5-15% less than vacant comparable homes when targeting owner-occupant buyers — because the buyer cannot occupy immediately. Options:
  1. **Give 30-day notice now, sell vacant** — maximizes owner-occupant buyer pool; risk is carrying costs without rent income during vacancy
  2. **List tenant-occupied at investor price** — targets landlord buyers; narrows buyer pool but tenant provides income offset during marketing period
  3. **Negotiate tenant departure with incentive** — offer tenant relocation assistance in exchange for vacating early; costs money but may recapture more in sale price
  - Recommend option based on seller's stated goals and current rental market
- Disclosure: rental history, condition of systems (older 1952 home), any known deferred maintenance. Tenant may have information about condition issues the landlord doesn't know — suggest the agent schedule a pre-listing walkthrough with tenant present.
- Cap rate context: if targeting investor buyers, calculate implied cap rate at the asking price ($1,050 x 12 = $12,600 gross annual rent). At a 7% cap rate, the property's investor value is approximately $180,000. At 6%, approximately $210,000. Use this as a secondary pricing anchor.
- Post-NAR settlement note: if buyer is an investor with no buyer's agent, compensation discussion is different — cover as needed.
- 1031 exchange: if seller mentions a 1031, note that timing is strict (45-day identification, 180-day close). Confirm with their tax advisor — this is beyond agent scope.
- Net sheet at investor's target price.
- Legal disclaimer included, with note to consult CPA about tax implications of investment property sale.

---

## Example 4: Seller with Unrealistic Price Expectations

**Agent prompt:**
> "Need help with a tough price conversation. Seller at 9330 Harvest Moon Drive, Zionsville wants $575,000. I've run the comps — best comps are $505-$520K. The house is nice but it's not $575K. They bought in 2020 for $490K and think the market has gone way up. How do I handle this?"

**Context:**
- Seller's anchor: $575K
- Comp-supported range: $505-$520K
- Gap: $55-70K over comps (11-13%)
- Seller's logic: bought in 2020 at $490K, assumes large appreciation

**Expected output:**
- Load agent config
- Note: this is primarily a price expectation management conversation — the skill provides scripts, not just data
- Do not simply tell agent to "show them the comps." Give the agent the actual language to use.

**Data anchor script (primary approach):**
> "[Seller name], I want to show you exactly what the market is telling us. Here are the four homes most similar to yours that sold in the past 90 days in [neighborhood/zip]. [Review comps.] When we look at price per square foot — which is how buyers and appraisers evaluate homes — your home's comp-supported value is in the $505-$520K range. A $575,000 price isn't something I could defend to an appraiser, and that matters because most buyers are financing."

**Gentle redirect script:**
> "I understand where $575,000 came from, and if the right buyer walked in tomorrow and paid it, I'd be thrilled for you. But here's the risk: if we list at $575,000, we're likely to sit on the market for 60-90 days with no offers, then reduce. Homes that sit develop a stigma — buyers start asking 'what's wrong with it.' By the time we get to $520K, we've lost the new-listing excitement that drives the highest-value offers. I'd rather get you $520K in 14 days than $510K in 90 days after two price reductions."

**Net proceeds reframe script (most powerful if seller has financial goals):**
> "Let's look at what you actually walk away with, because the list price is just the starting number. At $575K, after commissions, closing costs, and your mortgage payoff — here's your estimated net. At $520K — here's your net. The difference in your pocket is [X], not $55,000. Sometimes people are surprised by how much of the gap gets absorbed by closing costs and commission on both ends."

- Generate net sheet comparison at $575K vs. $520K side-by-side to show the actual net difference — this often reframes the conversation
- Flag: if seller insists on $575K, the agent must decide whether to take the listing. An overpriced listing at 11-13% over comps is likely to sit, require price reductions, and damage the agent's brand. Offer the agent language for declining if appropriate: "I can only take this listing at a price I can justify to a buyer and an appraiser. If we're not aligned on pricing, it may not be the right time for us to work together."
- Legal disclaimer included

---

## Example 5: Divorce Situation — Both Spouses Must Agree

**Agent prompt:**
> "Potential listing — divorcing couple at 5517 Cold Springs Road, Greenwood. Both names on the deed. The wife called me — she's motivated to sell. I haven't met the husband yet. She says he's 'not being cooperative.' What do I need to know?"

**Context:**
- Situation: divorce with potential for conflict between co-owners
- Both spouses on deed — both must sign the listing agreement
- Only one spouse has contacted agent so far
- Potential for disagreement on price, timing, or choice of agent

**Expected output:**
- Load agent config
- Flag immediately: both owners on the deed means BOTH must sign the listing agreement (IAR Form 103) for it to be valid. Agent cannot proceed with a listing that only one party has authorized.
- Goal discovery: before the full consultation, agent needs to assess:
  - Is there a divorce decree or court order that addresses the real property? If there is a signed divorce decree ordering the sale, agent should ask to see it — this can clarify each party's obligations and rights.
  - Are they legally separated or is the divorce in progress? An active divorce proceeding may require court approval of the sale or appointment of a special master.
  - Is there an attorney involved? If so, coordinate through counsel — this protects the agent.
  - What is the husband's objection? Financial (price, timing), personal (doesn't want to move), or strategic (using the home as leverage in the divorce settlement)?
- Consultation structure: agent should ideally meet with BOTH parties — even if separately. Meeting only with the wife creates the perception of taking sides, which can derail the transaction and create liability.
- Pricing: get both parties to agree on price in writing before listing. If they disagree on price, the listing cannot proceed without court intervention or agreement. Agent is not a mediator — if the parties cannot agree, recommend they resolve it through their attorneys before the agent can list.
- Agency explanation: as seller's agents, the agent represents BOTH spouses as co-sellers. The agent cannot favor one over the other. If one spouse attempts to get the agent to share the other's negotiating position or motivation, decline — that is a confidentiality violation regardless of the marital situation.
- Red flags to name:
  - One spouse attempting to hide the sale from the other — agent cannot proceed
  - One spouse threatening to block the sale — agent needs written authorization from both before marketing
  - Restraining orders or domestic violence history — agent's safety and protocol considerations apply
  - Pending litigation involving the property — this can affect title
- Follow-up email suggestion: send a meeting request to both spouses jointly. Never communicate about the listing with only one party unless specifically authorized by a court order.
- Legal disclaimer included, with strong note to consult managing broker before proceeding in contentious divorce situations.

---

## Example 6: Corporate Relocation — Employer-Assisted Relocation

**Agent prompt:**
> "Seller at 14302 Williams Creek Drive, Carmel — corporate relo. She works for Salesforce, just got transferred to Chicago. Her employer is using Cartus for the relo. She has to be out by July 15 and Salesforce is doing a guaranteed buyout if the home doesn't sell. She wants a real agent though, not just Cartus. What should I know?"

**Context:**
- Situation: corporate relocation with employer-provided assistance
- Relo company: Cartus (relocation management company)
- Hard deadline: July 15
- Guaranteed buyout option exists if the home doesn't sell through the open market
- Seller wants direct agent representation, not just the relo company process

**Expected output:**
- Load agent config
- Key context for agent: Cartus and other relocation management companies (RMCs) typically charge a referral fee to the listing agent — often 30-40% of gross commission — as a condition of being assigned the listing through the relo program. The seller may want to work with their own agent, but the RMC may have contractual rights to manage the sale. Agent should clarify the relo company's role before accepting the listing.
- Goal discovery questions for relo situation:
  - Has she signed the Cartus relocation agreement yet? What does it say about agent selection?
  - Does Cartus have the right to approve or assign the listing agent, or is she free to choose?
  - What is the guaranteed buyout (GBO) price? Is there a marketing period before the GBO kicks in?
  - Does Cartus require two appraisals to set the GBO value, and when are those scheduled?
  - Are there any allowances for repairs, painting, or staging provided by the employer?
  - What are Cartus's requirements for the listing — price, DOM before reduction, open house requirements?
- Agency: standard seller's agent, but note that Cartus may have overlapping advisory role. Agent represents the seller's interests — if Cartus's recommendations conflict with the seller's interests, agent should advocate for the seller and document all communications.
- Timeline: with a July 15 deadline, work backward. If today is late March, that is approximately 15 weeks. That is enough time for a full-price market process — but only if listed promptly and priced right from Day 1. Any pricing error wastes weeks the seller doesn't have.
- Net sheet: the relo company may pay some closing costs as part of the benefit package. Ask seller what Cartus covers. Also note that the seller likely does not pay capital gains on relo-related home sales if employer provides a GBO and buyer — verify with their CPA.
- Referral fee consideration: if the agent is working directly with the seller (not assigned by Cartus), confirm whether any referral fee applies to the brokerage. This is a business decision between agent and broker — do not represent to the seller that a Cartus referral fee is or isn't in play without checking with the managing broker.
- Legal disclaimer included, with note to consult managing broker about relo company referral agreements and to recommend seller review all Cartus documentation with an attorney before signing.

# Example Prompts — re-disclosure-assistant

These scenarios show realistic agent inputs and describe what the skill should produce. Use these to understand the skill's scope and to validate behavior.

---

## Example 1: New Listing, Standard Occupied Home — Full Form Walkthrough

**Agent prompt:**
> "New disclosure walkthrough for 4822 Maple Drive, Indianapolis — seller has lived there 11 years, it's their primary residence, built in 1998. I know the roof was replaced about 5 years ago and they mentioned the basement had some moisture about 8 years ago but they had it waterproofed."

**Context:**
- Year built: 1998 (post-1978 — no lead paint requirement)
- Ownership type: Owner-occupied, 11 years
- Known issues agent has flagged: roof replacement (~5 years ago), prior basement moisture (8 years ago, remediated)

**Expected output:**
- Load agent config; confirm agent and brokerage
- Note that 1998 build year means no federal lead paint form required
- Begin Section 1 walkthrough: ask about title status, any liens or encumbrances
- Work through Section 2 (Systems): roof replacement → confirm seller discloses date of replacement, contractor if known, whether any warranty transferred; basement moisture → confirm seller discloses the history of water intrusion AND the remediation performed; ask about all other systems (electrical, plumbing, HVAC)
- Continue Sections 3-7 conversationally, pausing at each section to confirm with agent whether there are any known issues
- Produce a summary checklist with: disclosed items (roof replacement date, prior basement water intrusion + waterproofing), items to clarify (any other system age/condition questions), and a clean "no items flagged for attorney review" if everything is straightforward
- Include mandatory legal disclaimer

---

## Example 2: Pre-1978 Home — Lead Paint Requirements

**Agent prompt:**
> "Working on a listing at 3309 Park Avenue, Speedway — built in 1962. Seller has owned it for 22 years. Never had a lead paint test done. What do I need?"

**Context:**
- Year built: 1962 (pre-1978 — federal lead paint disclosure required)
- Lead paint testing: never done
- Seller knowledge: none disclosed yet

**Expected output:**
- Immediately flag: "This home was built in 1962 — federal law requires IAR Form 46232 in addition to Form 46234."
- Explain the four federal requirements under 42 U.S.C. § 4852d:
  1. Seller must disclose any known lead paint hazards on Form 46232
  2. Seller must provide any available records (none here, since never tested)
  3. Agent must provide EPA pamphlet "Protect Your Family from Lead in Your Home" to buyer
  4. Buyer has a 10-day right to inspect for lead paint (can waive in writing)
- Provide script to use with the seller explaining what Form 46232 requires
- Note that since seller has no prior testing results, they disclose "no known lead paint hazards and no records or reports available"
- Remind agent: retain signed Form 46232 in transaction file for minimum 3 years
- Note civil penalty exposure ($10,000 per violation) to underscore importance
- Continue to Form 46234 walkthrough for remaining sections
- Include mandatory legal disclaimer

---

## Example 3: "As-Is" Sale — What Still Must Be Disclosed

**Agent prompt:**
> "Seller wants to sell as-is. They have a list of things wrong with the house — old roof, one bathroom that doesn't work, a garage door that's off the track. They're pricing for condition and don't want to deal with negotiating repairs. Do they still need to fill out the disclosure?"

**Context:**
- Sale type: "As-is" intended
- Known issues: aged roof, non-functioning bathroom, broken garage door
- Seller's (incorrect) belief: as-is = no disclosure needed

**Expected output:**
- Clearly explain: "As-is" does not exempt sellers from Form 46234 under Indiana law
- Cite the IC 32-21-5-3 context: the as-is exemption that sellers often assume simply does not exist in Indiana disclosure law
- Explain the distinction: "As-is" affects the buyer's remedies after closing; it does not affect the seller's obligation to disclose before closing
- All three known issues (roof condition, non-functioning bathroom, broken garage door) must be disclosed on Form 46234
- Frame it positively for the seller: disclosing everything on a priced-for-condition as-is sale actually protects them — it limits post-closing disputes because the buyer accepted the disclosed condition
- Walk through the sections of Form 46234 that apply to the known issues: Section 2 (Systems — roof, plumbing, appliances/garage)
- Produce summary with all three items in the "Disclosed Items" list and a note that proper as-is disclosures reduce seller liability
- Include mandatory legal disclaimer

---

## Example 4: Estate Sale — Executor Doesn't Know the Property

**Agent prompt:**
> "Estate sale at 7741 Elm Street, Carmel. Executor is the deceased's daughter — she lives in Ohio, never lived in the house, hasn't seen it in about 10 years. She's asking how to handle the disclosure form since she doesn't know the condition. We do have the old owner's home warranty records and some contractor invoices in a box she brought."

**Context:**
- Sale type: Estate
- Seller: Executor (personal representative) with no personal knowledge
- Records available: home warranty records, some contractor invoices

**Expected output:**
- Confirm this is a legitimate situation with a clear path forward
- Explain: executor marks "Unknown" for sections where she has no personal knowledge — that is legally correct and appropriate
- Critical point: she must NOT mark sections "No" when she simply doesn't know — "Unknown" is the right answer
- Prompt to review the box of records: home warranty records and contractor invoices may show prior repairs or known issues that constitute constructive knowledge of the estate
- Walk through how to read warranty claims history: any repairs made under warranty represent conditions the estate now knows about and should disclose
- Advise: attach relevant records to the disclosure if they document repaired conditions — this builds good faith and limits future disputes
- Suggest executor ask any neighbors or family members who visited regularly if they recall any property issues (furnace problems, leaks, etc.) — while not required, it demonstrates good faith
- Produce output checklist with: sections to mark "Unknown," items identified from the records that should be disclosed, and a recommendation to consult with the estate attorney given the estate context
- Include mandatory legal disclaimer and note that estate transactions may warrant additional legal oversight

---

## Example 5: Prior Basement Flooding That Was Remediated

**Agent prompt:**
> "Seller at 2288 Birchwood Lane, Fishers is asking whether they have to disclose that their basement flooded twice in 2018 during back-to-back heavy rain events. They had a French drain and sump pump installed right after and haven't had any water since. They don't want it to scare buyers off."

**Context:**
- Known issue: basement flooded twice in 2018 (6-7 years ago)
- Remediation: French drain + sump pump installed immediately after
- No recurrence since remediation
- Seller preference: would rather not disclose

**Expected output:**
- Clear answer: yes, this must be disclosed — prior water intrusion is a known material defect even when remediated
- Explain: the disclosure question asks whether the seller is AWARE of water intrusion history, not whether the problem currently exists
- Reframe for the seller: disclosing the flooding AND the remediation is actually protective. The French drain and sump pump are visible — any inspector will find them and wonder why they were installed. An undisclosed known flood history discovered post-closing is far more damaging than a disclosed one.
- Note: sellers who try to hide prior flooding events and then the basement floods again face fraud claims, not just breach of contract claims
- Script for the seller: "In 2018 the basement experienced water intrusion during two significant rain events. Immediately following, we had a French drain system and sump pump installed professionally. There has been no water intrusion since. Documentation of the remediation work is available."
- Identify this on Form 46234: Section 4 (Water), water intrusion section
- Produce summary with item in "Disclosed Items" list, note to attach any remediation documentation, and no items requiring attorney review
- Include mandatory legal disclaimer

---

## Example 6: Unpermitted Addition — Sunroom Added Without Permit

**Agent prompt:**
> "Seller at 5503 Driftwood Court, Noblesville added a sunroom in 2019. About 400 square feet off the back of the house. Looks great — hardwood floors, insulated windows, ceiling fans. But when I asked, they admitted they never pulled a permit. The work was done by a friend who does construction. Do we have to disclose this?"

**Context:**
- Addition: 400 sq ft sunroom, 2019
- Permit status: no permit pulled
- Work quality: appears well-done but unlicensed contractor (friend)
- Seller awareness: confirmed they knew no permit was obtained

**Expected output:**
- Clear answer: yes — unpermitted work is a known material defect and must be disclosed on Form 46234, Section 5 (Structural/Additions)
- The seller knew the work was done without a permit — this is not an "unknown" situation
- Practical implications to explain to the seller and agent:
  - The county assessor may not have this square footage on record — it could affect assessed value discrepancies
  - A buyer's lender appraiser will measure the property and may flag the non-permitted addition
  - Some lenders and insurance companies require permits to include additions in coverage/valuation
  - The buyer could require the seller to obtain a retroactive permit or price adjustment
- What the disclosure should say: "Approximately 400 sq ft sunroom addition constructed in 2019. Work was performed without a building permit."
- What the seller should consider: contacting the Noblesville Building Department about a retroactive permit now, before listing — resolving it proactively is better than having it surface mid-transaction
- Note: even if they decide not to pursue retroactive permitting, the disclosure obligation does not change
- Produce summary with item in "Disclosed Items" and a note under "Items Flagged for Clarification" about the retroactive permit option and potential appraisal/lender implications
- Include mandatory legal disclaimer and note that seller should consult with their attorney about the retroactive permitting question

# Example Prompts — re-showing-coordinator

Eight scenarios covering both listing-side and buyer-side showing coordination.

---

## Example 1: Listing Agent — ShowingTime Setup for Occupied Home

**Agent prompt:**
> "Set up ShowingTime instructions for 12345 Maple Creek Dr, Fishers 46037 — owner-occupied, 4BR house, they have a dog (small, will be in a crate). Need at least 1-hour notice. No showings before 9am or after 7pm. Lockbox on front door handle. Lights on please, garage door closed."

**Expected output:**

- Load agent config; confirm agent name appears in output
- **ShowingTime instruction sheet:**
  ```
  SHOWING INSTRUCTIONS — 12345 Maple Creek Dr, Fishers 46037
  Access: Lockbox on front door handle
  Notice: Minimum 1-hour advance notice required
  Hours: 9:00 AM – 7:00 PM daily
  Pets: Dog on premises — secured in crate
  Special notes: Please leave lights on and garage door closed upon departure
  Feedback: Automatic feedback request sent via ShowingTime after each showing
  ```
- **Agent remarks guidance:** What to put in BLC agent-only remarks vs. ShowingTime (alarm code hint, if any, goes in ShowingTime agent notes only — never in public remarks)
- **Tip:** Suggest auto-feedback request enabled so the agent doesn't have to manually follow up after every showing

---

## Example 2: Five-Home Buyer Tour in Carmel — Tour Prep

**Agent prompt:**
> "Buyer tour prep for Sarah and Michael Chen — first-time buyers looking for 4BR, $450-550K range, HSE or Carmel Clay schools preferred, want a big kitchen and main-floor primary if possible. Seeing 5 homes tomorrow in Carmel. Here are the addresses and basic info: [list of 5 properties with beds/baths/price/year]."

**Expected output:**

- Load agent config
- **Per-property prep sheet for each of the 5 homes:**
  - Address, price, beds/baths/sqft/year
  - Features that align with Sarah and Michael's criteria (big kitchen, main-floor primary, school district)
  - Things to evaluate in person (kitchen size/layout, primary bedroom location, road noise, neighborhood feel)
  - Questions to ask/note (seller's timeline, HOA fees, any known issues)
- **Tour logistics:**
  - Recommended showing order by geography (minimize drive time)
  - Estimated time per showing (20–30 min standard; allow 45 for larger homes)
  - Buffer time for travel and debrief between showings
- **Buyer briefing:** Short 2-paragraph note to send to Sarah and Michael the night before — what to bring (pre-approval letter in case they want to make an offer), what to wear, what to look for

---

## Example 3: Weekly Showing Report — Negative Feedback Pattern

**Agent prompt:**
> "Weekly showing report for seller at 4218 Buttonwood Dr, Fishers, $389,000. Listed 14 days. 9 showings, 5 feedback responses. Feedback summary: 2 said price is high for the area, 1 said the kitchen needs updating, 2 said they liked it but are still looking. No offers yet."

**Expected output:**

- Load agent config; all output uses agent name and brokerage
- **Seller-facing weekly report:**
  - Activity summary: 9 showings, 5 feedback responses (56% response rate), 0 offers
  - Feedback themes: Price concern (2 of 5), condition/kitchen (1 of 5), interested but still shopping (2 of 5)
  - Market context: Compare 9 showings in 14 days to typical Fishers absorption rate and DOM at $389K
  - **Agent's read:** "Two separate buyers independently cited price. Combined with zero offers at 9 showings, this is data worth discussing."
  - **Recommended next step:** Price reduction conversation — not a directive, but a clear recommendation with context. Provide the agent with talking points for the call.
- **Do NOT sugarcoat the feedback.** The seller deserves accurate data.

---

## Example 4: Buyer Can't Decide Between Two Homes

**Agent prompt:**
> "Help me work through this with my buyers Tom and Janet — they saw 6 homes Saturday. They loved two of them: 7814 Oak Hill Ct in Noblesville ($415K, 4BR, HSE, needs some cosmetic work) and 3301 Willow Bend Dr in Fishers ($439K, 4BR, HSE, move-in ready). They can't decide. Both are still active."

**Expected output:**

- **Side-by-side comparison worksheet:**
  - Price, location, beds/baths, year, condition for each
  - Pros and cons for each property based on what Tom and Janet stated they want
  - Price difference: $24K — what does the move-in ready premium mean in monthly payment terms?
  - Gut reaction question: "If the Noblesville one went under contract tonight, would you regret not offering? What about the Fishers one?"
- **Decision framework:**
  - Identify any dealbreakers in the concern column
  - Quantify the cosmetic work estimate on the Noblesville home (agent should ask them what they observed; help frame it against the $24K price difference)
  - Urgency check: days on market for each, showing volume if known
- **Suggested agent script** for the decision conversation — guiding without pushing

---

## Example 5: Low Showing Volume — Troubleshooting

**Agent prompt:**
> "I've got 10 Lincoln Court in Westfield priced at $529K. Only 3 showings in 3 weeks. Property is in great shape, well-staged, good photos. What's going on and what should I do?"

**Expected output:**

- **Diagnostic framework:** Walk through the most likely causes of low showing volume:
  1. **Price point** — Is $529K above the typical buyer pool activity level for this area/size? Compare to active competition.
  2. **Online presence** — Is the listing syndicated to Zillow, Realtor.com, Homes.com? Check for listing errors (wrong school district, missing photos).
  3. **Showing access friction** — Is the notice requirement too restrictive? 24-hour notice on an occupied home significantly reduces spontaneous showings.
  4. **Marketing reach** — Has the listing been promoted socially? Broker open held? Email blast sent to buyer-side agents?
  5. **Market conditions** — Is this a price range with known inventory surplus? Use market context from `references/central-indiana-market-context.md`.
- **Recommended actions with priority:**
  1. Reduce notice requirement to 1-hour if possible
  2. Run a broker open this week — incentivize agent attendance
  3. Send a personal email to buyer agents in your network who work this price range
  4. If no traction in 7 more days: price reduction conversation
- **Seller communication script** for discussing low activity

---

## Example 6: Out-of-Town Buyer — Virtual Showing Prep

**Agent prompt:**
> "I'm working with out-of-town buyers relocating from Chicago. They can't come in person until they're under contract. I'm doing FaceTime showings with them this weekend — 3 properties in Carmel. Help me prep for these virtual tours."

**Expected output:**

- **Virtual tour prep checklist per property:**
  - Key features to demonstrate on camera (kitchen layout, primary suite size, backyard)
  - What to narrate vs. what to show visually (road noise is audio; ceiling height is visual)
  - Walk-through sequence (entry → main level → upstairs → basement → exterior)
  - Specific items to inspect for/narrate on behalf of absent buyers (crawl space access, sump pump, basement moisture indicators, HVAC age, roof visible from outside)
- **Buyer prep:** What to ask the buyers to pay attention to during the virtual tour. What questions they should have ready.
- **Documentation:** Recommend taking video of each property and sending a clip compilation so they can review later
- **Post-tour workflow:** Same comparison worksheet and decision framework as an in-person tour — buyers still need to evaluate from the recorded footage

---

## Example 7: Investor Showing Checklist

**Agent prompt:**
> "Showing an investment property (3BR SFH, tenant-occupied, Fountain Square) to an investor buyer. Help me prep for this showing."

**Expected output:**

- **Pre-showing checklist for agent:**
  - Confirm tenant has received proper notice (Indiana: generally 24 hours minimum)
  - Confirm showing window is agreed to by tenant
  - Have current lease terms available: rent amount, lease expiration, any renewal options
  - Note any visible condition issues for investor's repair cost estimate
- **Investor evaluation framework (what the buyer should be assessing):**
  - Gross rent vs. purchase price → gross rent multiplier
  - Estimated repairs/deferred maintenance
  - Property management cost if they won't self-manage
  - Tenant quality signals (observable condition, length of tenancy)
  - Exit strategy: hold and rent vs. renovate and sell
- **Post-showing investor debriefe questions:**
  1. "Does the rent-to-price ratio work for your target return?"
  2. "What did you observe about the tenant's treatment of the property?"
  3. "What's your estimate for immediate repairs vs. deferred maintenance?"
  4. "Are you interested in keeping the current tenant or transitioning to a new occupant?"
- **Legal note:** Agent should never make representations about tenant's character — describe observable condition only.

---

## Example 8: Buyer with Accessibility Needs

**Agent prompt:**
> "My buyer uses a power wheelchair. She's looking for a single-story or ranch with main-floor everything. Touring 3 homes tomorrow — help me prep."

**Expected output:**

- **Per-property evaluation checklist focused on physical accessibility (factual features, not fair housing language):**
  - Doorway widths (32" minimum for standard wheelchair; 36" recommended for power chair)
  - Entry access: step-free, ramp, or step count and height
  - Main floor layout: bedroom, full bathroom, laundry all on main level
  - Bathroom doorway width and layout (room to maneuver a turning radius)
  - Kitchen layout: aisle widths, counter heights (note these are typically not ADA-height in residential builds)
  - Garage: step-free entry from garage to home interior
  - Exterior: driveway and walkway grading/slope
- **Framing note for agent:** These are factual physical features of the home, not fair housing issues. Describing them accurately for a buyer is compliant and necessary.
- **Realistic expectations:** Most residential resale homes are not designed for power wheelchair access. Set expectations about frequency of suitable inventory at this buyer's price point, and whether new construction (with ADA-optional features) should be on the search list.

---

*These examples cover common listing and buyer-side showing scenarios in Central Indiana. Actual showing scheduling is handled in ShowingTime or your brokerage's showing platform — this skill generates the preparation and follow-up content.*

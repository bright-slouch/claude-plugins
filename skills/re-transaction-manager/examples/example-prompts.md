# re-transaction-manager — Example Prompts

Eight realistic transaction management scenarios covering setup, updates, and mid-transaction issues.

---

## Example 1: Standard 30-Day Close — New Transaction Setup

**Scenario:** Agent just accepted an offer. 30-day close, conventional financing, standard
contingencies. Need to set up the full transaction file and create calendar events.

**Prompt:**
```
/re-transaction-manager new transaction setup

Property: 4218 Buttonwood Dr, Fishers IN 46037
Accepted: April 2
Close date: May 2 (30 days)
Earnest money: $7,000 — due April 5 (3 business days)
Inspection period: 10 calendar days (deadline April 12)
Financing contingency: 21 days (deadline April 23)
Appraisal contingency: 21 days (deadline April 23)
Buyer: Conventional financing, 5% down, pre-approved with Ruoff Mortgage
Lender contact: Mike Dawson, Ruoff — 317-555-1234 / mdawson@ruoff.com
Title: Stewart Title, Julie Park — 317-555-5678 / jpark@stewart.com
Other agent: Tom Bradley, RE/MAX — 317-555-9012 / tbradley@remax.com
Buyer: Chris and Emily Sutton
Seller: Robert Davies
Slug: sarah-jones-fc-tucker
```

**What the skill should produce:**
- Complete deadline calendar table with all dates computed from April 2 acceptance
- 11 Google Calendar events created (one per critical deadline), each with 1-day and 1-hour reminders
- Three coordination emails ready to send:
  1. To lender Mike Dawson — accepted contract, inspection/financing deadlines, request appraisal timeline
  2. To title Julie Park — new transaction, parties, target close date, document delivery
  3. To other agent Tom Bradley — executed contract, earnest money logistics, coordination intro
- Flag that inspection deadline (April 12) falls on a Sunday — note buyer must submit IAR Form 162 by end of day Sunday
- Calendar event for inspection deadline marked ⚠ HIGH PRIORITY

---

## Example 2: 45-Day Close With Home Sale Contingency

**Scenario:** Buyer has a home to sell. 45-day close with a home sale contingency and
kick-out clause. More complex timeline with two parallel transaction tracks.

**Prompt:**
```
/re-transaction-manager new transaction setup

Property: 8814 Eagle Creek Pkwy, Indianapolis IN 46254
Accepted: April 1
Close date: May 16 (45 days)
Earnest money: $5,000 — due April 4
Inspection: 10 days (deadline April 11)
Financing contingency: 30 days (deadline May 1) — FHA loan
Appraisal contingency: 30 days (deadline May 1)
Home sale contingency: Buyer's home at 5501 Trowbridge Dr, Lawrence must close by May 12
Kick-out clause: Seller can continue marketing; if new offer, buyer has 48 hours to
  remove home sale contingency or release
Buyer: FHA financing, 3.5% down
Other agent: Raj Patel, Century 21 — 317-555-3456
Title: Old National Title, Derek Wu — 317-555-7890
Slug: sarah-jones-fc-tucker
```

**What the skill should produce:**
- Dual-track deadline calendar:
  - Track A: buyer's transaction on 8814 Eagle Creek (primary contract deadlines)
  - Track B: parallel watch on buyer's home sale (5501 Trowbridge must close May 12)
- Note FHA timeline risk: 45 days is standard for FHA but tight if appraisal is flagged
- Kick-out clause event created: "Seller can trigger 48-hour removal window at any time — monitor actively"
- Coordination email to other agent includes kick-out clause acknowledgment
- Calendar alert on May 9 (3 days before buyer's home must close): "Confirm buyer's Trowbridge sale on track"
- Note: if kick-out triggered, buyer has 48 hours — agent needs to know buyer's current home sale status immediately

---

## Example 3: Inspection Issue — Extension Needed

**Scenario:** Inspection found possible structural issues. Buyer wants a structural
engineer to inspect. Inspection period expires in 2 days. Need an extension.

**Prompt:**
```
/re-transaction-manager inspection extension needed

Property: 4218 Buttonwood Dr, Fishers IN 46037
Current inspection deadline: April 12
Today's date: April 10
Issue: Home inspector flagged possible foundation movement in basement.
  Buyer wants a structural engineer to inspect before deciding.
  Structural engineer's earliest availability: April 15.
Need: 5-day extension to April 17.
Slug: sarah-jones-fc-tucker
```

**What the skill should produce:**
- Draft extension request email to listing agent Tom Bradley:
  > "Tom — our inspection flagged a potential foundation concern that warranted a structural
  > engineer's evaluation. The engineer's earliest availability is April 15. We're requesting
  > a 5-day extension to the inspection period through April 17. Nothing more sinister than
  > wanting to do our due diligence properly. Can we get seller's agreement on a quick IAR
  > 157 amendment? I can turn that around immediately."
- IAR Form 157 amendment language ready to paste into Dotloop:
  > "Inspection Period is hereby extended from April 12, 2026 to April 17, 2026. All other terms
  > and conditions of the Purchase Agreement remain unchanged."
- `gcal_update_event` call to update the existing inspection deadline calendar event to April 17
- New calendar event created: April 17 — "EXTENDED Inspection Deadline — Structural Engineer Report Due"
- Warning: if seller refuses the extension, buyer must submit inspection response by April 12 or contingency waives; advise buyer on options immediately

---

## Example 4: Appraisal Delay — Closing at Risk

**Scenario:** Appraisal was ordered 2 weeks ago but still hasn't been completed.
Closing is in 14 days. Financing contingency is in 5 days.

**Prompt:**
```
/re-transaction-manager appraisal delay — closing at risk

Property: 4218 Buttonwood Dr, Fishers IN 46037
Accepted: April 2
Close date: May 2
Financing contingency deadline: April 23 (5 days from today, April 18)
Appraisal ordered: April 10 by lender
Today: April 18 — appraisal not yet completed; no report received
Lender update: AMC says appraiser scheduled for April 20
Slug: sarah-jones-fc-tucker
```

**What the skill should produce:**
- Immediate action plan:
  1. Contact lender Mike Dawson today — confirm appraisal is actually scheduled April 20
  2. After April 20 inspection, ask lender for expected report delivery (typically 5–7 days = April 27)
  3. April 27 + lender review = CTC by April 29 at earliest — May 2 closing is TIGHT
- Appraisal contingency warning: deadline is April 23, but appraisal won't be done by then
  - Draft contingency extension request: extend appraisal and financing contingency to May 1
  - "We need to extend the financing and appraisal contingencies. Appraisal is scheduled April 20.
    Report expected April 27. We need to extend both deadlines to May 1 to allow the lender to
    review and confirm value. Please confirm seller's agreement to the extension."
- IAR Form 157 language for appraisal + financing contingency extension
- Two gcal_update_event calls for the financing and appraisal deadline events
- Risk flag: if seller refuses extension and appraisal isn't done by April 23, buyer may waive
  the contingency unintentionally — agent must not let this date pass without written extension or active response

---

## Example 5: Title Issue — Unreleased Mortgage

**Scenario:** Title company discovered an unreleased mortgage from a prior refinance 8 years ago.
The lender is now defunct. Title cannot close until the issue is resolved.

**Prompt:**
```
/re-transaction-manager title issue — unreleased mortgage

Property: 4218 Buttonwood Dr, Fishers IN 46037
Close date: May 2 (14 days away)
Issue: Stewart Title found an unreleased mortgage from a 2018 refi with First Meridian Bank,
  which was acquired by another bank in 2021. Title needs a release from the current
  holding institution before issuing a clear commitment.
Title estimate: 10–15 days to obtain the release.
Slug: sarah-jones-fc-tucker
```

**What the skill should produce:**
- Immediate communication to all parties:
  1. To buyer (via agent): "Title has discovered an unreleased lien from a prior refinance.
     The title company is working to obtain a release. The May 2 closing date will need to be
     extended. This is a resolvable issue — it does not affect your ability to purchase the home."
  2. To other agent: "Title found an unreleased mortgage from a 2018 refi. Stewart Title is
     working the release. They estimate 10–15 days. We'll need to extend the closing date to
     approximately May 19. Can you get seller's agreement to an extension?"
  3. To title company: "Please provide a written timeline for the release. We'll be drafting
     a closing date extension. What is the specific date you need to have the release in hand?"
- Draft IAR Form 157 amendment for closing date extension to May 19 (with 5-day buffer beyond 15-day estimate)
- gcal_update_event to update closing date event
- Note: buyer's rate lock may expire if close date extends more than 7 days — alert buyer to contact lender immediately
- Note: buyer's Closing Disclosure 3-day delivery window resets with the new closing date

---

## Example 6: Financing Falls Through Post-Contingency

**Scenario:** Buyer's financing has collapsed. The financing contingency expired 6 days ago.
Buyer cannot close. This is a difficult conversation for all parties.

**Prompt:**
```
/re-transaction-manager financing fell through — post-contingency

Property: 4218 Buttonwood Dr, Fishers IN 46037
Financing contingency expired: April 23
Today: April 29 (6 days after contingency expired)
Issue: Buyer lost their job on April 26. Lender cannot approve without current employment.
Earnest money: $7,000
Other offers: Listing had a backup offer 3 weeks ago — unknown if still available.
Slug: sarah-jones-fc-tucker
```

**What the skill should produce:**
- Timeline analysis:
  - Financing contingency expired April 23 — buyer is outside the protected window
  - Buyer cannot terminate with earnest money return based on financing at this point
  - Seller likely has a claim to the $7,000 earnest money as liquidated damages
- Immediate steps:
  1. **Do not advise client to make any decisions without talking to managing broker first**
  2. Notify listing agent immediately — professional courtesy; deal needs to be unwound
  3. Do NOT promise seller the earnest money — earnest money disposition requires mutual release or court order
- Earnest money options:
  1. Mutual release with EM to seller — fastest; avoids litigation
  2. Mutual release with EM split — possible if both parties agree
  3. Seller pursues as liquidated damages in court — slow; usually not worth it for $7K
  4. Interpleader by holding brokerage/title — court decides; months to resolve
- Communication to other agent (buyer's agent drafts):
  > "Tom — I need to share some difficult news. Our buyers experienced an unexpected job loss
  > on April 26 and can no longer obtain financing. We are working through this with our broker.
  > I'll be in contact about next steps on the earnest money and releasing the property.
  > I'm sorry for the inconvenience and any impact this has on your sellers."
- Backup offer note: reach out to the previous buyer's agent (if agent remembers who it was)
  **before** making the listing publicly available again — professional courtesy and could save 2+ weeks
- Mandatory disclaimer: consult managing broker before taking any formal action on earnest money

---

## Example 7: Amendment Tracking — Mid-Transaction Price Change

**Scenario:** After inspection, the parties agreed to a $9,500 closing cost credit.
Need to update the transaction record and send the amendment to all parties.

**Prompt:**
```
/re-transaction-manager amendment — inspection credit agreed

Property: 4218 Buttonwood Dr, Fishers IN 46037
Amendment: Seller to provide $9,500 closing cost credit to buyer at closing
  in lieu of repairs (roof and HVAC). All other terms unchanged.
Amendment date: April 16
Amendment number: Amendment #1
Slug: sarah-jones-fc-tucker
```

**What the skill should produce:**
- Amendment tracking entry:
  ```
  AMENDMENT LOG — 4218 Buttonwood Dr, Fishers
  Amendment #1 — April 16, 2026
  Change: Seller to provide $9,500 closing cost credit at closing for roof and HVAC
  Status: Executed
  Impact: No deadline changes; updates Closing Disclosure (lender must be notified)
  ```
- Immediate action: send the executed amendment to:
  1. Buyer's lender (credit affects the CD — lender needs this immediately)
  2. Title company (affects settlement statement)
  3. Both agents (for their files)
- Draft email to lender:
  > "Mike — Amendment #1 is attached. Parties agreed to a $9,500 closing cost credit to buyer
  > for inspection items. Please note this for the Closing Disclosure. The credit is within
  > conventional lending limits for this transaction. Let us know if you need anything else."
- No Google Calendar updates needed (no deadline changes)
- Note: confirm the $9,500 credit is within the buyer's lender limits for the loan type and LTV
  (conventional < 10% down: up to 3% = $10,155 on $338,500 net price — $9,500 is within limit)

---

## Example 8: Cash Deal — Fast Close (15 Days)

**Scenario:** Cash buyer, 15-day close. Fewer contingencies but still needs coordination.
No financing contingency; no appraisal. Inspection and title only.

**Prompt:**
```
/re-transaction-manager new transaction setup — cash deal, fast close

Property: 3302 Oak Hill Rd, Carmel IN 46033
Accepted: April 3
Close date: April 18 (15 days)
Earnest money: $15,000 — due April 5 (2 business days)
Inspection: 5 calendar days (deadline April 8) — buyer negotiated shorter period
No financing contingency (cash)
No appraisal contingency (cash)
Title commitment needed by: April 14 (4 days before close)
Buyer: Cash purchaser — confirmed proof of funds at offer
Other agent: David Kim, Compass — 317-555-2222 / dkim@compass.com
Title: Attorneys Title Group, Mike Solano — 317-555-4444 / msolano@atg.com
Slug: lisa-chen-kw
```

**What the skill should produce:**
- Compressed deadline calendar:
  ```
  Day  | Date    | Deadline                       | Owner
   0   | Apr 3   | Contract accepted               |
  1–2  | Apr 5   | ⚠ Earnest money due ($15K)      | Buyer
  1–5  | Apr 3–8 | Inspection period               | Buyer
   5   | Apr 8   | ⚠ INSPECTION DEADLINE (5 days)  | Buyer's Agent
   6   | Apr 9   | Inspection response due         | Buyer's Agent
  10–14| Apr 13–14| Title commitment expected       | Title Company
   14  | Apr 17  | Final walkthrough               | Buyer
   15  | Apr 18  | 🔑 CLOSING DAY                   | All parties
  ```
- Note compressed inspection window — buyer's inspector must be scheduled April 4 or 5
- Cash deal advantages: no lender to coordinate, no appraisal, faster close
- Cash deal still requires: title search, title commitment, title policy
- Coordination emails to title (expedited request — 15-day timeline) and other agent
- 4 Google Calendar events (fewer, because no financing/appraisal events)
- Flag: if title finds an issue by April 14, there's only 4 days to resolve before close
  — title company needs to expedite their search and start it immediately

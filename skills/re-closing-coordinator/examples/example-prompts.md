# re-closing-coordinator — Example Prompts

Six realistic closing scenarios covering pre-closing prep, common complications, and post-closing sequences.

---

## Example 1: Smooth Standard Closing — Full Sequence

**Scenario:** Clear to Close received. Standard 30-day close on a Fishers home. First-time
buyer couple. Agent needs the complete pre-closing prep package.

**Prompt:**
```
/re-closing-coordinator clear to close — full pre-closing prep

Property: 4218 Buttonwood Dr, Fishers IN 46037
Closing: May 5, 10:00am at Stewart Title
Buyer: Chris and Emily Sutton — first-time buyers
Financing: Conventional, 5% down
Loan amount: $321,750
CD delivered: May 1 (3 business days clears by May 5)
Agreed repairs: None — $9,500 credit at closing
Title: Stewart Title, Julie Park — 317-555-5678
Other agent: Tom Bradley, RE/MAX
Sellers: Robert Davies
Slug: sarah-jones-fc-tucker
```

**What the skill should produce:**
- Pre-closing checklist organized by: agent to-do, buyer to-do, seller to-do
- Utility transfer list for Fishers (Hamilton County):
  - AES Indiana (electric): aesindiana.com / 317-261-8222
  - Citizens Gas: citizensenergygroup.com / 317-924-3311
  - City of Fishers Utilities (water): fishers.in.us/utilities
  - Republic Services or city trash (confirm Fishers city service)
  - Options for internet: AT&T Fiber, Spectrum, Metronet (available in Fishers)
- Wire fraud warning: verbal confirmation reminder for buyer re: Stewart Title wire instructions
- Buyer closing day guide: what to bring, what to expect, timing, cash to close amount
- Seller closing day guide: what to bring, keys/openers, proceeds wire instructions
- Final walkthrough scheduled for May 3 or 4 (24–48 hours before close)
- Post-closing sequence preview: gift, review request, 30-day check-in
- Calendar events created: May 5 closing day, May 12–15 review request reminder, June 5 30-day check-in

---

## Example 2: Closing With a Last-Minute Walkthrough Issue

**Scenario:** Final walkthrough reveals the washer/dryer (included in the sale per the
purchase agreement) has been removed by the seller. Closing is tomorrow morning.

**Prompt:**
```
/re-closing-coordinator walkthrough issue — missing personal property

Property: 4218 Buttonwood Dr, Fishers IN 46037
Closing: Tomorrow, May 5 at 10:00am
Issue: Washer and dryer listed as included in purchase agreement (Line 5, Personal Property)
  are not present at the walkthrough. Seller's agent says "seller took them by mistake."
Current time: May 4, 3:00pm
Slug: sarah-jones-fc-tucker
```

**What the skill should produce:**
- Immediate action plan:
  1. Document with photos — timestamp photos of empty laundry area
  2. Text and email listing agent immediately with photo evidence
  3. Present three resolution options in order of preference:
     **Option A:** Seller delivers the washer/dryer before closing tomorrow morning (seller "took them by mistake" — they should bring them back)
     **Option B:** Closing holdback — title company holds seller's proceeds equal to the replacement value ($1,500–$3,000 for a mid-range set) until seller delivers the units within X days
     **Option C:** Credit at closing — reduce seller proceeds by the agreed replacement value; buyer purchases new set
  4. Agent should not threaten to blow up the deal over this — it is resolvable — but must advocate for the buyer
- Draft text to listing agent:
  > "Tom — the washer and dryer included in the PA per Line 5 Personal Property are not present at
  > the walkthrough. Photos attached. We need to resolve this before close tomorrow. Three options:
  > seller delivers by 9am; we agree on a credit at closing; or title does a $2,500 holdback.
  > Call me ASAP."
- If seller refuses to address: consult managing broker; buyer has the right to delay closing
- Closing can still proceed if parties agree on a written resolution before signing

---

## Example 3: Remote (Mail-Away) Closing

**Scenario:** Buyers are relocating from Seattle and cannot attend the Indiana closing in person.
Closing is May 5. Agent needs to set up a remote closing.

**Prompt:**
```
/re-closing-coordinator remote closing setup

Property: 8814 Eagle Creek Pkwy, Indianapolis IN 46254
Closing: May 5
Buyers: Michael and Sandra Kim — currently in Seattle, WA
Buyer's agent: Sarah Jones (closing as buyer agent for remote buyers)
Financing: Conventional
Title: Old National Title, Derek Wu — 317-555-7890
Timeline: Today is April 24 — 11 days before close
Slug: sarah-jones-fc-tucker
```

**What the skill should produce:**
- Remote closing setup checklist:
  1. Contact Old National Title TODAY — confirm remote closing capability (RON or mail-away)
  2. Indiana RON (Remote Online Notarization) enacted 2019 — ask title if they support it
  3. Mail-away alternative: FedEx signing package 7 days before close (April 28) for return by May 4
  4. Buyers must have a notary available wherever they are (bank, UPS Store, notary service)
  5. Wire instructions still require verbal confirmation — buyers call Derek Wu directly at an independently obtained number
  6. Buyer's photo ID: clear photo of driver's license or passport must be provided to title in advance for remote notarization
- Final walkthrough note: buyers are in Seattle — agent or TC should conduct walkthrough on their behalf and send video walkthrough to buyers
- Closing Disclosure review: agent walks buyers through the CD on a video call (not email alone)
- Key handoff: arrange for lockbox code or TC to accept keys and mail/FedEx to buyers if they're not arriving immediately

---

## Example 4: New Construction Closing

**Scenario:** Agent is closing a buyer on a new build in Westfield (Drees Homes). Different
from a resale — needs the new construction closing checklist.

**Prompt:**
```
/re-closing-coordinator new construction closing

Property: 3458 Clearwater Blvd, Westfield IN 46074 (Drees Homes, Springfield subdivision)
Closing: May 10, estimated
Buyer: Lisa and David Park
Financing: Conventional — buyer used Drees's preferred lender (Homeowners Financial Group)
Builder warranty: 1-year workmanship / 2-year mechanical / 10-year structural
Certificate of Occupancy: Expected May 7
Final builder walkthrough (punch list): Scheduled May 8
Slug: sarah-jones-fc-tucker
```

**What the skill should produce:**
- New construction pre-closing checklist with builder-specific items:
  1. CO must be issued (May 7) before buyer can occupy — closing date must be after CO issuance
  2. Final punch list walkthrough on May 8 — document ALL items in writing; get Drees to acknowledge in writing
  3. Confirm punch list items are either: completed by May 10, OR placed on a written warranty repair list with completion dates
  4. Builder's warranty package: must receive all warranty documentation at closing — 1/2/10 structure explained
  5. Survey of the lot — builder should provide
  6. HOA documents: Springfield CC&Rs, budget, HOA contact info — review before signing
- Property tax note: first year property taxes will likely be land-only (house not on tax rolls yet). Year 2 assessment will include the structure — taxes may increase significantly. Prepare buyers for this.
- Utility setup: Westfield, IN utilities:
  - AES Indiana (electric): aesindiana.com
  - Citizens Gas (likely, depending on area): citizensenergygroup.com
  - City of Westfield Water: westfield.in.gov/utilities
  - Internet: AT&T Fiber or Metronet (available in parts of Westfield)
- Punch list follow-up: put a 60-day calendar reminder to verify punch list items are completed

---

## Example 5: Cash Closing — Fast Close

**Scenario:** Cash buyer, 15-day close. Closing tomorrow. Different process without lender involvement.

**Prompt:**
```
/re-closing-coordinator closing day prep — cash buyer, closing tomorrow

Property: 3302 Oak Hill Rd, Carmel IN 46033
Closing: Tomorrow, April 18 at 1:00pm at Attorneys Title Group
Buyer: James Whitfield — cash buyer, no financing
Sale price: $685,000
Seller: Patricia Harding
Final walkthrough: Completed this morning — no issues
Title: Attorneys Title Group, Mike Solano — 317-555-4444
Slug: lisa-chen-kw
```

**What the skill should produce:**
- Cash buyer closing day guide:
  - What to bring: photo ID; cashier's check or wire confirmation for $685,000 (per settlement statement)
  - Wire fraud warning: call Mike Solano at Attorneys Title Group directly (317-555-4444) to verbally confirm wire routing number and account number — do not wire based on email alone
  - Cash deals close faster: no lender funding, no VOE — process is typically 30–45 minutes
  - Deed records same day; buyer takes possession after recording
  - Cash buyer note: no title insurance lender policy needed (no lender); buyer is purchasing owner's policy only
- Seller guide: bring ID, all keys/access devices, bank info for wire proceeds
- Post-closing note: no lender means no IRS reporting requirement for the loan — but the deed transfer may still generate a 1099-S (sale of real property). Advise buyer and seller to consult their CPA regarding capital gains and cost basis.
- Post-closing sequence:
  - Congratulations email to both buyer and seller within 2 hours of recording
  - Gift for buyer: James Whitfield is an investor-type buyer at $685K — premium gift (quality bottle, experience, or Indiana-made goods basket)
  - Google Calendar: 30-day check-in, 1-year anniversary

---

## Example 6: Closing With Post-Possession Agreement

**Scenario:** Seller's new construction isn't ready — seller needs to stay for 30 days after close.
Need to set up a post-possession agreement before closing.

**Prompt:**
```
/re-closing-coordinator post-possession setup

Property: 4218 Buttonwood Dr, Fishers IN 46037
Closing: May 5
Post-possession needed: Seller needs 30 days (through June 4) while new build completes
Daily rent agreed: $75/day (aligned with mortgage per-diem)
Security deposit: $2,000
Move-out deadline: June 4, 5:00pm
Agreement form: IAR Form 196
Buyer: Chris and Emily Sutton
Seller: Robert Davies
Slug: sarah-jones-fc-tucker
```

**What the skill should produce:**
- Post-possession checklist:
  1. IAR Form 196 must be signed by all parties BEFORE closing — not after
  2. Security deposit ($2,000) held by buyer's agent or title company (confirm holding arrangement)
  3. Buyer must notify homeowners insurance that property has a "tenant" for 30 days — coverage implications
  4. Utility protocol during possession: seller continues paying utilities and remains responsible for the home during their occupancy
  5. Move-out deadline is hard: June 4 at 5:00pm. If seller doesn't vacate, buyer must pursue Indiana eviction process (even though it's the "seller")
  6. Hard move-out walkthrough: schedule for June 4 (or June 5 to allow seller to fully vacate)
- Critical warning to buyer:
  > "Once you close, Robert Davies becomes your tenant under IAR Form 196. Your homeowners insurance
  > may not fully cover the property during his occupancy. Call your insurance agent today to notify
  > them and understand your coverage during the 30-day possession period."
- Draft closing day note to title:
  > "Please confirm IAR Form 196 (Post-Closing Occupancy Agreement) is included in the closing packet.
  > All parties must sign before close of escrow."
- Calendar events:
  - June 4: "[Seller] Post-Possession Expires — Move-Out Walkthrough"
  - June 4: Return security deposit if no damages documented

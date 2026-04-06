# re-client-communication: Example Prompts

---

## Scenario 1: Just Listed — Email to Sphere (New Brokerage)

**Context:** Marcus Williams just listed 14207 Allisonville Rd, Fishers — a 4BR/2.5BA home at $429,000. He recently moved to Keller Williams Indy Metro North from F.C. Tucker and this is his first listing under his new brokerage. He wants to announce the listing to his sphere while subtly reinforcing his new brokerage affiliation. His `tone_preset` is `professional-friendly`, `formality_scale` is 6, `emoji_usage: minimal`.

**Prompt:**
```
Write a just-listed email to my sphere for 14207 Allisonville Rd, Fishers — 4 bed, 2.5 bath, 2,800 sqft, listed at $429,000. This is my first listing at KW. I want to mention the new brokerage but keep it natural.
```

**What happens:**
The skill loads Marcus's agent-profile.yaml and email-templates.yaml. It uses the `just_listed_announcement` base template, then personalizes to his professional-friendly voice at formality 6. The email opens with his greeting style ("Hi [First Name],"), mentions the new brokerage naturally in the body ("...under my new home at Keller Williams Indy Metro North..."), includes one line of property highlights, a referral soft ask, and closes with his signature block. One emoji if Marcus's config allows minimal. Subject line follows the base template format.

**Expected output shape:**
```
Subject: Just Listed: 14207 Allisonville Rd, Fishers | 4 Bed / 2.5 Bath | $429,000

Hi [First Name],

Exciting news — I just listed a beautiful home in Fishers and wanted you to hear it from me first.

14207 Allisonville Rd, Fishers
4 beds | 2.5 baths | 2,800 sq ft | $429,000

[Property highlight in 1-2 sentences]

This is my first listing with my new brokerage, Keller Williams Indy Metro North — and I couldn't be happier with how it's going.

If you know anyone who's been looking in Fishers, I'd love an introduction. And if you'd like to see the home yourself, just say the word.

Thanks,
Marcus Williams
Keller Williams Indy Metro North | [Office]
[Phone] | [Email]
[Website]
Licensed in Indiana | REALTOR® | Equal Housing Opportunity
```

---

## Scenario 2: Text to a Buyer Who Went Silent After Offer Rejection

**Context:** Jennifer Hartley (CENTURY 21 Scheetz) is working with a buyer, Chris Navarro, who made an offer on a Westfield home at 8832 Sunridge Dr. The offer was rejected — the seller wanted $15k more than Chris was willing to pay. That was 5 days ago. Chris hasn't responded to Jennifer's last two calls. Jennifer's `tone_preset` is `casual-warm`, `formality_scale` is 4, `emoji_usage: moderate`.

**Prompt:**
```
Write a text to Chris — he's been quiet since his offer on 8832 Sunridge Dr didn't work out, 5 days ago. I want to check in and see if he's still in the game. His name is Chris Navarro.
```

**What happens:**
The skill identifies this as a lapsed-lead reactivation text. Casual-warm at formality 4 means this reads like a genuine friend checking in, not a sales push. Short. No pressure. Opens with his name. Ends with a low-commitment ask. Character count provided.

**Expected output shape:**
```
Hi Chris — thinking about you after the Sunridge situation. Totally get it if you need a beat. When you're ready to look again, I've got a couple things I want to show you. No rush. 😊

[Character count: 187 / 300]
```

*Note: Emoji included because Jennifer's config allows moderate. Adjusted down to one because the situation is empathetic, not celebratory.*

---

## Scenario 3: Phone Call Talking Points — Seller with No Offers After 3 Weeks

**Context:** Sarah Chen (F.C. Tucker Carmel) is listing 11204 Whispering Creek Dr, Carmel — listed at $575,000, has been on market 22 days, 8 showings, no offers. Feedback themes: "feels dated," "kitchen needs updating," two agents mentioned price. Comparable homes have been selling in 9–14 days. Sarah's `tone_preset` is `professional-friendly`, `negotiation_style` is `data-driven`.

**Prompt:**
```
I need talking points for a call with my seller at 11204 Whispering Creek Dr in Carmel. We've had 8 showings in 22 days and zero offers. Feedback keeps coming back as "dated" and "price." Comparable homes are selling in 9–14 days. I need to have the price reduction conversation.
```

**What happens:**
The skill generates structured call talking points (not a script). Data-driven tone per Sarah's negotiation style. Opens with the purpose of the call. Uses market data as the framing device — not Sarah's opinion, but the numbers. Presents options at the end with a concrete closing ask.

**Expected output shape:**
```
Opening line: "I want to walk through the showing feedback and some market data with you — do you have about 15 minutes?"

Key points:
- Summary: 8 showings in 22 days is decent traffic. Zero offers means the feedback is worth listening to.
- The pattern: Two separate agents mentioned price independently. That's not noise — that's a trend.
- Market context: Comparable 4BR homes in this part of Carmel have been selling in 9–14 days. We're at 22. The gap between our days-on-market and the market average is the clearest signal we have.
- What the "dated / kitchen" feedback means: Buyers are mentally calculating renovation costs and adjusting their offer ceiling down. At this price point, they expect move-in condition.
- The options:
  - Price reduction to $549,000–$555,000 to get back into competitive range
  - Cosmetic updates (paint, fixtures) before recommitting at current price — adds 2–3 weeks
  - Hold firm and continue waiting

Closing ask: "I'd like your go-ahead to put together a specific price reduction analysis by [date]. Can we agree to reconvene Thursday to make a decision?"
```

---

## Scenario 4: Under Contract Email to Buyers

**Context:** David Park (CENTURY 21 Scheetz) just got his buyers — the Okonkwo family — under contract on 2847 Prairie Wind Dr, Noblesville, at $387,500. Close date is May 15. Inspection period ends April 12. David's `tone_preset` is `casual-warm`, `formality_scale` is 5, `emoji_usage: moderate`.

**Prompt:**
```
Write an under-contract email to my buyers, the Okonkwo family. They're under contract at 2847 Prairie Wind Dr, Noblesville. $387,500, close date May 15, inspection ends April 12.
```

**What happens:**
The skill pulls the `under_contract_listing_notification` base template and adapts it for the buyer side (separate from the seller-facing template). Casual-warm tone with milestone energy. Signature block appended. Character count not needed — this is an email.

**Expected output shape:**
```
Subject: You're Under Contract! 2847 Prairie Wind Dr, Noblesville

Hi [Family Name / First Name],

We did it — you're officially under contract on 2847 Prairie Wind Dr! 🎉

Here's your roadmap to closing day:

- Inspection Period Ends: April 12
- Appraisal: We'll hear back approximately 10 business days after ordered
- Target Close Date: May 15

Your next step is the home inspection. I've already reached out to [inspector name] to get it scheduled — I'll confirm the date and time within the next 24 hours.

I'll keep you updated at every milestone. If you have questions at any point, just text or call me.

Congratulations — this is a big deal and you earned it!

David
David Park | CENTURY 21 Scheetz
[Phone] | [Email]
[Website]
Licensed in Indiana | REALTOR® | Equal Housing Opportunity
```

---

## Scenario 5: Appraisal Gap Email to Buyer Client ($15K Low)

**Context:** Lisa Morales (F.C. Tucker) is representing buyers on 5512 Copperleaf Ln, Zionsville. Contract price: $612,000. Appraisal came back at $597,000 — $15,000 below contract. Lisa's buyers have the cash to cover it but haven't said so explicitly. Lisa's `tone_preset` is `professional-friendly`, `formality_scale` is 7.

**Prompt:**
```
Draft the appraisal gap email to my buyers on 5512 Copperleaf Ln, Zionsville. Contract price was $612,000 and the appraisal came in at $597,000 — $15k short. I want to explain their options clearly.
```

**What happens:**
This is a difficult conversation scenario. The skill uses the appraisal gap framework from `references/communication-scenarios.md`. Professional-friendly at formality 7 means clear, measured, no panic. The email presents three options with the math spelled out. It ends with a call-to-action to talk through it rather than asking them to reply in writing.

**Expected output shape:**
```
Subject: Appraisal Update: 5512 Copperleaf Ln, Zionsville

Hi [First Name],

I have the appraisal results for Copperleaf and wanted to get this to you right away.

The property appraised at $597,000, which is $15,000 below your contract price of $612,000.

Here's what that means in practical terms, and the options available to you:

Option 1 — Cover the difference out of pocket
You'd bring an additional $15,000 to closing above your loan amount. Your mortgage stays the same; this is an additional cash requirement.

Option 2 — Renegotiate with the seller
We can ask the seller to reduce to the appraised value, split the difference, or meet you partway. This requires seller agreement and isn't guaranteed, but it's worth presenting.

Option 3 — Walk away
Your contract includes an appraisal contingency. If you choose not to proceed, you would receive your earnest money back. I'll confirm the specific language before you make any decisions.

I'd like to talk through this with you — can you call me today? I'm available between [time] and [time]. I'll have the full appraisal report to share.

Best,
Lisa Morales
F.C. Tucker Company | [Office]
[Phone] | [Email]
[Website]
Licensed in Indiana | REALTOR® | Equal Housing Opportunity
```

---

## Scenario 6: Annual Home Anniversary Email

**Context:** Marcus Williams (KW Indy Metro North) helped the Patel family close on their Carmel home — 9301 Fairview Woods Dr — exactly one year ago. Marcus's `tone_preset` is `professional-friendly`, `emoji_usage: minimal`.

**Prompt:**
```
Write the one-year anniversary email for the Patel family — they closed on 9301 Fairview Woods Dr in Carmel a year ago today.
```

**What happens:**
The skill uses the `anniversary_check_in` base template from `email-templates.yaml`, personalized to Marcus's voice. Professional-friendly at his formality level. Brief. Genuine. Soft home value mention and soft referral ask — not pushy.

**Expected output shape:**
```
Subject: One Year — Happy Home Anniversary, Patel Family!

Hi [First Name],

Hard to believe it's already been a year since you closed on 9301 Fairview Woods Dr!

I hope Carmel has been treating you well and that the home has become everything you hoped it would be.

If you're ever curious what your home is worth in today's market, I'm happy to put together a quick estimate — no obligation, just good to know. And if you know anyone who's thinking about buying or selling, I'd be grateful for the introduction.

Enjoy the anniversary — and thank you again for trusting me with such an important decision.

Thanks,
Marcus Williams
Keller Williams Indy Metro North | [Office]
[Phone] | [Email]
[Website]
Licensed in Indiana | REALTOR® | Equal Housing Opportunity
```

---

## Scenario 7: Google Review Request — Post-Close

**Context:** Jennifer Hartley (CENTURY 21 Scheetz) helped the Torres family buy a home in Fishers. They closed 10 days ago and responded enthusiastically to her "how's the new home?" text. Jennifer's `tone_preset` is `casual-warm`, `emoji_usage: moderate`, `formality_scale: 4`.

**Prompt:**
```
Write a Google review request email for the Torres family — they just bought in Fishers 10 days ago and they loved working with me.
```

**What happens:**
Casual-warm means this reads warm and personal, not like a corporate survey request. It uses the `review_request` base template. Brief, heartfelt, no-pressure. Link placeholder included. One sentence opt-out so it doesn't feel transactional.

**Expected output shape:**
```
Subject: Would You Share Your Experience?

Hi [First Name],

Congratulations again on the new home — I hope you're settling in and loving every minute of it! 🏡

If you had a good experience working with me, I'd genuinely appreciate it if you'd take a couple of minutes to share a review online. It means a lot, and it helps other families in the same spot you were in not too long ago.

[Google Review Link]

No pressure at all — and if there's anything I could have done better, I'd love to hear that too.

Thank you for letting me be part of this. It was truly a joy!

Jennifer
Jennifer Hartley | CENTURY 21 Scheetz
[Phone] | [Email]
[Website]
Licensed in Indiana | REALTOR® | Equal Housing Opportunity
```

---

## Scenario 8: Price Reduction Prep Email — Agent to Seller

**Context:** Sarah Chen (F.C. Tucker Carmel) needs to bring the seller at 11204 Whispering Creek Dr, Carmel into a price reduction conversation. She's planning to call them but wants to send a market data summary beforehand so they can review it before the call. The listing has been active 22 days with no offers. Comparable homes have sold between $539,000–$558,000. The current list price is $575,000. Sarah's `tone_preset` is `professional-friendly`, `formality_scale: 6`.

**Prompt:**
```
Write a pre-call email to my seller at 11204 Whispering Creek Dr, Carmel. I want to send the market data before we talk so they're not blindsided. Listed at $575k, no offers in 22 days. Comparable sales are $539k–$558k.
```

**What happens:**
This is the "price reduction — internal prep" scenario. The skill writes an agent-to-seller email that leads with data, not opinion. Professional-friendly at formality 6 keeps it warm but direct. The email sets up the call without delivering the full recommendation in writing — it ends with an invitation to talk, not a demand to reduce.

**Expected output shape:**
```
Subject: Market Update for 11204 Whispering Creek Dr — Let's Connect

Hi [First Name],

I want to share some market context with you before we talk, so you have time to look it over.

Here's where we stand:

- Days on Market: 22 (market average for comparable homes: 9–14 days)
- Showings: 8 total
- Offers received: 0
- Recent comparable sales in this part of Carmel: $539,000–$558,000

The showing feedback has pointed consistently toward two things: the dated finishes in the kitchen and the price. When multiple buyer agents mention the same thing independently, it's worth taking seriously.

I have some specific thoughts on where we might be able to get more traction — I'd like to walk you through it on a call. Does [day/time] or [day/time] work for you?

Thanks,
Sarah Chen
F.C. Tucker Company | Carmel Office
[Phone] | [Email]
[Website]
Licensed in Indiana | REALTOR® | Equal Housing Opportunity
```

*Note: This email intentionally does not state a specific recommended price reduction — that conversation should happen on the call where the agent can respond to the seller's reaction in real time.*

# re-closing-coordinator — Quick Start Guide

## What This Skill Does

`re-closing-coordinator` handles the final mile of a transaction — from Clear to Close through
post-closing follow-up. It generates:

- Pre-closing checklists for buyer, seller, and agent
- Central Indiana utility transfer lists with correct providers by county
- Closing Disclosure review guide
- Final walkthrough checklist
- Closing day prep guides (what to bring, what to expect)
- Post-closing sequence: gift, review request, anniversary reminders

---

## When to Invoke This Skill

| Trigger | Command |
|---|---|
| Lender issues Clear to Close | `/re-closing-coordinator clear to close — [property, closing date, buyer type]` |
| Buyer needs utility list | `/re-closing-coordinator utilities — [property address]` |
| Buyer wants to review the CD | `/re-closing-coordinator CD review — [property, buyer financing type]` |
| Final walkthrough tomorrow | `/re-closing-coordinator final walkthrough — [property, any known repair items]` |
| Closing is tomorrow | `/re-closing-coordinator closing day prep — [buyer or seller side, title company, time]` |
| Transaction just closed | `/re-closing-coordinator post-closing — [property, buyer type (first-time/move-up/investor)]` |
| Walkthrough problem | `/re-closing-coordinator walkthrough issue — [what was found]` |
| Remote closing needed | `/re-closing-coordinator remote closing — [property, buyer location, timeline]` |

---

## The Handoff From re-transaction-manager

This skill picks up exactly where `re-transaction-manager` leaves off — at CTC:

```
/re-closing-coordinator clear to close — 4218 Buttonwood Dr, Fishers.
Closing May 5. First-time buyers. Conventional. Slug: sarah-jones-fc-tucker
```

At this point `re-transaction-manager` has already tracked the deadlines. This skill
now handles everything from CD review through post-closing.

---

## Indiana Utility Providers — Quick Reference

| County | Electric | Gas | Water |
|---|---|---|---|
| Marion (Indianapolis) | IPL or Duke Energy | Citizens Gas | Citizens Water |
| Hamilton (Carmel, Fishers, Noblesville, Westfield) | AES Indiana or Duke Energy | Citizens Gas or CenterPoint | City/town utilities |
| Hendricks (Avon, Plainfield, Brownsburg) | Duke Energy | CenterPoint | City/town |
| Johnson (Greenwood, Franklin) | Duke Energy | Citizens Gas or CenterPoint | City/town |
| Boone (Zionsville, Lebanon) | Duke Energy | CenterPoint | City/town or Rural Water |

For internet: AT&T Fiber (metro-wide), Spectrum (metro-wide), Metronet (Hamilton County expansion).

---

## Wire Fraud Prevention — Never Skip This

Every closing day prep includes a wire fraud warning. Your job:

1. Tell the buyer to call the title company using a phone number **they looked up independently** — not from the email containing wire instructions
2. Confirm routing number and account number verbally
3. Only then wire or bring cashier's check

Real estate wire fraud costs Central Indiana buyers real money every year. This takes 3 minutes and is non-negotiable.

---

## Post-Closing Sequence

The skill generates a 4-touch post-closing plan:

| When | Touch | Action |
|---|---|---|
| Day of close | Congratulations email | Within 2 hours of recording |
| Day 7–10 | Review request | Google + Zillow |
| Day 30 | Check-in | + homestead exemption reminder |
| Month 6 | Seasonal check-in | Maintenance tips |
| Year 1 | Anniversary | Card + CMA offer |

Google Calendar events are created for the 30-day, 6-month, and 1-year touches so they don't fall through the cracks.

---

## Indiana Homestead Exemption — Always Remind Buyers

Buyers who live in the home as their primary residence must file for the **homestead exemption**
by **December 31 of the purchase year**. This is the most commonly missed Indiana buyer benefit.

- Savings: typically $200–$500+ per year in reduced property taxes
- File with the county assessor's office (online or in person)
- Include this reminder in the 30-day post-closing check-in

---

## Critical Rules

- **3-day CD rule:** Closing cannot happen until 3 business days after the Closing Disclosure is delivered to the buyer. Confirm the CD delivery date before confirming the closing can proceed.
- **Deed records first:** In Indiana, buyer does not get keys until the deed records with the county recorder. Closing ≠ immediate occupancy for funded loans.
- **Post-possession in writing:** If seller stays after close, IAR Form 196 must be signed **before** closing — never after.
- **New construction:** Closing cannot happen without a Certificate of Occupancy.

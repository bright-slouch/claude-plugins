---
name: re-open-house
description: >-
  Full open house lifecycle management for Central Indiana listings. Pre-event:
  2-week promotion schedule, social posts, email blast, signage text, and
  property-specific talking points. During: sign-in sheet, conversation starters,
  and security reminders. Post-event: same-day thank-you through 1-week follow-up
  sequence, feedback collection, and seller report.
argument-hint: "[property address + open house date/time + agent slug]"
---

# re-open-house

## Overview

`re-open-house` manages the complete open house lifecycle — from first promotion post to post-event follow-up sequence. Whether it's a standard weekend open house, a broker-only preview, or a mega open house event with multiple agents, this skill generates the content agents need at every stage.

This skill produces promotion copy, sign-in sheet setup, conversation guides, and follow-up sequences. Agents run the actual event and execute in their CRM and showing platform.

---

## Persona and Mental Model

Think like a listing agent who has run 300+ open houses and knows that the event itself is only 20% of the value — the remaining 80% lives in the follow-up. You know that most visitors won't volunteer their real buyer timeline or agent status unless you ask the right questions naturally. You know that security at an open house is a real concern and that sellers need a pre-event briefing to protect their home and identity.

Every piece of content you generate is ready to use. Agents copy it into their channels — they don't rewrite it.

---

## When to Use This Skill

- 2 weeks before a new open house: generate the full promotion schedule
- 1–3 days before: final promo push and property-specific talking points
- Day of: sign-in sheet setup, conversation guide, security checklist
- Day of / same evening: post-event thank-you messages
- 2 days after: follow-up check-in for interested visitors
- 1 week after: final follow-up and seller report

---

## Quick Start

```
Plan open house for 12345 Maple Creek Dr, Fishers — Saturday [date], 1-3pm
```
```
Generate open house promotion schedule for my Carmel listing, open house is next Sunday
```
```
Write post-open-house follow-up sequence for 8 visitors who signed in
```
```
Broker open house invitation for 3301 Willow Bend Dr, Fishers — Thursday [date] 11am-1pm
```

---

## Step-by-Step Workflow

### Step 1: Load Agent Config

Load `agent-profile.yaml` and `brand-kit.yaml` from `config/[slug]/`. If no slug is provided, ask for agent identification and look up in the Monday.com "Real Estate Agent Registry" board.

If no config found: "I don't have your agent profile set up yet. Run `/re-agent-setup` first."

Also load:
- `email-templates.yaml` — for follow-up sequence base templates
- `market-areas.yaml` — for neighborhood context in talking points

### Step 2: Identify Stage and Type

**Stage options:**
- Pre-event (2 weeks out, 1 week out, final push)
- Event day (sign-in, talking points, security)
- Post-event (follow-up sequence, seller report)
- Full lifecycle (generate everything for an upcoming open house)

**Open house types:**
- Standard consumer open house (most common)
- Broker open house (agent-only preview)
- Mega open house (multi-agent event, extended hours, additional promotion)
- Virtual open house (live-streamed or video-based)
- Price-reduced listing open house (repositioning messaging)

---

## Pre-Event: Promotion Schedule

### 2 Weeks Before

**Social media (2 posts):**

*Post 1 — Announcement (Instagram + Facebook):*
- Lead with a feature of the property (not just "open house!")
- Include date, time, address
- Hashtags from `brand-kit.yaml` + #OpenHouse #[City]OpenHouse #[SchoolDistrict]
- Instagram: keep caption brief; let the property photo carry the visual
- Facebook: 2–3 sentences of narrative + date/time/address

*Post 2 — Neighborhood spotlight (day after Post 1):*
- Lead with a reason to visit this neighborhood or area
- Mention nearby amenities (Flat Fork Creek Park, Hamilton Town Center, Monon Trail, downtown Indy, etc.)
- Soft call to action toward the open house

**Email blast:**
- Send to agent's buyer-side list and sphere
- Subject line: "Open House Preview — [address], [day], [time]"
- Include top 3 property features, date/time, RSVP link or agent contact
- Signature from `email-templates.yaml`

### 1 Week Before

**Social media (2 posts):**

*Post 3 — Feature spotlight:*
- One standout feature — the kitchen, the outdoor space, the primary suite
- "One week until you can see this in person" framing
- Date/time/address reminder

*Post 4 — Countdown:*
- Lighter, conversational tone: "7 days until the doors open at [address]"
- Can include a detail or fun fact about the property or neighborhood
- Repeat hashtags

**Text blast (if agent uses text marketing):**
- Short: "Heads up — open house at [address] this [day], [time]. Details: [link]"

### Final Push (Day Before / Morning Of)

**Social (1 post):**
- "Tomorrow / Today" urgency
- Time, address, one hook feature
- Highlight "No appointment needed — just come by"

**Stories (Instagram/Facebook):**
- Behind-the-scenes: walk-through preview, exterior shot, feature close-up
- "See you there" CTA

**Day-of social post (live or scheduled):**
- "Doors open in 1 hour" or "We're live at [address]"
- Address and hours

---

## Event Day: Sign-In Sheet and Conversation Guide

### Sign-In Sheet Setup

Use template `~/Skills/real-estate-plugin/templates/open-house-sign-in.md`.

Customize for the property:
- Property address and date/time pre-filled at the top
- Collect: name, email, phone, currently working with an agent (Y/N), pre-approved (Y/N), timeline to buy, how they heard about this open house

**Sign-in approach (verbal):**
The agent should ask visitors to sign in with a welcoming, low-pressure opener:
> "Hi, I'm [Name] — welcome! Would you mind grabbing a name tag and signing in? It helps me send you the listing details after today."

Never make sign-in feel like a data-collection exercise. It's a courtesy follow-up offer.

### Property-Specific Talking Points

Generate 5–7 talking points specific to the property's features. Format for quick reference during the event.

**Structure per talking point:**
- Feature name
- What to say (1–2 natural sentences)
- Supporting fact if relevant

**Example talking points (Fishers 4BR, updated kitchen, HSE):**
1. *Kitchen:* "The owners redid the kitchen in 2022 — all new quartz countertops, that island with seating for four, and the stainless appliances are all staying."
2. *School district:* "This is in HSE — the elementary school for this address is [name]. It's literally a 5-minute drive."
3. *Commute:* "You're 5 minutes to I-69 from here. Downtown Indy is 25–30 minutes, and Keystone at the Crossing is about 15."
4. *Basement:* "The finished basement has [features]. It's above grade on the back side because of the walkout, so it gets great light."
5. *Neighborhood:* "This is a cul-de-sac — [X] houses only share the street. Flat Fork Creek Park is a 3-minute walk down the trail."

### Conversation Starters

Provide the agent with natural openers for different visitor types:

**Buyer exploring the area:**
> "Have you been looking in Fishers long, or is this a new area for you? What's bringing you to this part of town?"

**Buyer with an agent already:**
> "Are you working with someone? Happy to share listing details and anything your agent needs."

**Buyer who seems very interested:**
> "What's your take so far — any rooms you want to take another look at? I'm happy to walk through with you."

**Neighbor / curious visitor:**
> "Did you see the open house sign out front? Great — even just stopping by helps spread the word. Are you or anyone you know thinking about moving to the area?"

### Security Reminders (Pre-Event Seller Briefing)

Provide agents with a seller briefing checklist before the open house:

- Secure or remove: jewelry, cash, prescription medications, financial documents, passports, spare keys, small electronics
- Lock away or remove: family photos (optional, but limits personal information visible to strangers)
- Lock interior rooms that will not be part of the tour (e.g., a cluttered storage room, office with sensitive documents)
- Advise seller not to be present during the open house — buyers speak more freely when the owner is not there
- Advise seller to be available by phone in case agent has questions
- After the event: do a walkthrough to confirm nothing is missing or out of place

---

## Post-Event: Follow-Up Sequence

### Touch 1 — Same Day (Text or Email to All Signed-In Visitors)

**Timing:** Within 2 hours of the open house closing.

**Channel:** Text is higher open rate; email if no phone was provided.

**Message goal:** Thank you + low-pressure next step.

> "Hi [Name] — thanks for stopping by [address] today! If you have any questions about the property or would like to schedule a private showing, I'm happy to help. — [Agent Name], [Phone]"

Short. No pressure. Easy reply path.

### Touch 2 — 2 Days After (Email to All Visitors)

**Timing:** Monday or Tuesday following a weekend open house.

**Message goal:** Provide one piece of value + surface interest.

> Subject: Following up — [address] open house
>
> Hi [Name],
>
> I wanted to follow up from the open house Saturday. We had great traffic and the seller is moving forward with [appropriate context — accepting offers, still available, etc.].
>
> I've attached/linked the property brochure with full details, disclosures, and the seller's preferred timeline. If you'd like to schedule a private showing before decisions are made, let me know and I'll get you in.
>
> [Agent Name] | [Brokerage] | [Phone]

**For visitors marked "working with agent":** Add: "Feel free to forward this to your agent — happy to work with them directly."

### Touch 3 — 1 Week After (Email or Phone Call)

**For high-interest visitors only** (gut reaction / body language / direct interest expressed):

**Phone script:**
> "Hi [Name], this is [Agent Name] from [Brokerage]. I just wanted to touch base — you seemed really interested in [address] at the open house last weekend. The property is still available / we've had some activity on it, and I wanted to make sure you had a chance to ask any questions or revisit before anything changes. Would you like to schedule a private showing?"

**Email version:**
> Subject: Still thinking about [address]?
>
> Hi [Name] — just wanted to check in on [address]. It's still available and the sellers are [motivated / flexible on timing / etc. — use appropriate honest context]. If you'd like a second look or have questions, I'm here.
>
> [Signature]

### Post-Event Seller Report

Provide the seller with a post-open-house summary the same evening or next morning.

**Report contents:**
1. **Traffic:** Number of visitors, number who signed in
2. **Visitor profile:** How many were working with an agent, how many pre-approved, timeline breakdown
3. **Standout comments:** Any specific positive feedback heard during the event
4. **Concerns raised:** Any recurring questions or objections (parking, HVAC age, basement, etc.)
5. **Agent's read:** Honest assessment — was interest strong? Were visitors serious buyers?
6. **Next steps:** Follow-up contacts in progress, any showings scheduled from open house leads

---

## What NOT to Do

- **Never fabricate competing interest.** Do not tell follow-up leads "we have multiple offers coming in" unless that is factually true and the agent has confirmed it with the seller.
- **Never share a visitor's personal information** (name, contact, pre-approval status) with anyone other than the listing agent's seller client in the context of reporting. Open house leads are not to be shared with other agents without consent.
- **Never skip the seller security briefing.** Open houses create legitimate security risks. Remind the seller to secure valuables every time.
- **Never pressure visitors to sign in.** It's a courtesy. Aggressive sign-in practices create bad brand impressions.
- **Never represent the property as something it is not** in talking points. Talking points should be accurate, specific, and based on real features — not invented or exaggerated.
- **Never make fair housing violations in open house conversation.** Do not describe neighborhoods, schools, or buyer demographics in protected class terms. See `references/real-estate-vocabulary.md`.

---

## Integration Points

### Reads From
- `config/[slug]/agent-profile.yaml` — agent voice, methodology, open house preference
- `config/[slug]/brand-kit.yaml` — hashtags, tagline, compliance disclaimers
- `config/[slug]/email-templates.yaml` — follow-up email base templates
- `config/[slug]/market-areas.yaml` — neighborhood context for talking points
- `~/Skills/real-estate-plugin/templates/open-house-sign-in.md`
- `~/Skills/real-estate-plugin/templates/weekly-status-update.md`
- `~/Skills/real-estate-plugin/references/real-estate-vocabulary.md`

### Works With
- **`re-property-marketing`** — social content here is a subset of the broader marketing campaign; open house promo posts can be generated here or there
- **`re-showing-coordinator`** — private showings often result from open house leads; hand off to showing coordinator workflow
- **`re-client-communication`** — seller open house report is a type of client communication; agent voice applies
- **`re-listing-creation`** — property features and talking points source from the listing content

---

## Example Prompts

See `examples/example-prompts.md` for 6 detailed scenarios including: standard first open house, mega open house event, broker open house, low-traffic open house follow-up, price-reduced listing open house, and virtual open house.

---

## Legal Disclaimer

> *This output is for guidance and informational purposes only. It does not constitute legal advice. Agents should consult their managing broker and/or a licensed Indiana real estate attorney for situation-specific guidance. Always comply with Indiana Real Estate Commission rules and your brokerage's policies.*

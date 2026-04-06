# Example Prompts — re-open-house

Six scenarios covering the full open house lifecycle.

---

## Example 1: Standard First Open House — New Listing Launch

**Agent prompt:**
> "Plan the open house for my new listing at 12345 Maple Creek Dr, Fishers — 4BR/2.5BA, $549K, HSE schools, updated kitchen, screened porch. Open house is Saturday [date], 1–3pm. Generate the full 2-week promotion schedule."

**Expected output:**

- Load agent config; all content uses agent name, brokerage, tagline, and hashtags from brand-kit.yaml
- **2-week promotion schedule with ready-to-post content:**
  - Week 2 out: Announcement social post (Instagram + Facebook) leading with kitchen update and school district. Email blast to sphere with date/time/top features.
  - Week 1 out: Feature spotlight post (screened porch or kitchen visual). Countdown post.
  - Day before: Final push story + "Tomorrow" urgency post.
  - Day of: "Doors open at 1pm today" post.
- **All social posts fair-housing compliant:** No familial status language. Lead with property features and location.
- **Event day package:**
  - Sign-in sheet customized for 12345 Maple Creek Dr with date/time
  - 5 property-specific talking points (kitchen remodel year, HSE school name, commute to I-69, screened porch lifestyle, Flat Fork Creek Park proximity)
  - Conversation starters for buyer, neighbor, and "already working with agent" visitor types
  - Seller security briefing checklist
- **Post-event follow-up sequence:**
  - Touch 1 (same day): Thank you text template
  - Touch 2 (Monday): Email with listing details and private showing offer
  - Touch 3 (1 week): High-interest visitor follow-up script (phone and email versions)
  - Seller report template populated with placeholders for traffic and feedback

---

## Example 2: Mega Open House Event — Multi-Agent Brokers Open

**Agent prompt:**
> "Mega open house for my Carmel luxury listing — 3301 Willow Bend Dr, 5BR/4.5BA, $1.1M, Carmel Clay schools. Bringing in 3 agents to help. Saturday [date], 12–4pm extended hours. Need extra promotion including broker network outreach."

**Expected output:**

- Load agent config; luxury tone applied if configured in `agent-profile.yaml`
- **Extended promotion schedule (3 weeks):**
  - Additional Week 3 post: Teaser / "Coming to the market" luxury angle
  - Week 2: Full announcement plus broker email blast (target buyer's agents who work $800K+ in Hamilton County)
  - Week 1: Feature spotlight series (primary suite, outdoor living, chef's kitchen) across 3 posts
  - Days before: Countdown, Stories, final email to sphere
- **Broker open invitation (separate):** Formal, professional tone. Targeted to MIBOR buyer agents. Include light incentive if agent offers one (catered lunch, gift card drawing, etc.)
- **Event day package with multi-agent coordination:**
  - Room assignments or station assignments for 3 agents
  - Unified talking points so all agents tell the same story
  - Team greeting protocol: who greets at the door, who handles sign-in, who tours
- **Post-event seller report:** Reflects premium event; higher expectations for traffic and follow-up conversion rate.

---

## Example 3: Broker Open House — Agent-to-Agent Preview

**Agent prompt:**
> "Write a broker open house invitation for 7814 Oak Hill Ct, Noblesville — 4BR/3BA, $415K, HSE, needs cosmetic updates. Broker open Thursday [date] 11am–1pm. Agents only."

**Expected output:**

- Load agent config; tone is professional peer-to-peer (not consumer marketing)
- **Broker open invitation:**
  - Subject: "Broker Preview — 7814 Oak Hill Ct, Noblesville — Thu [date] 11am–1pm"
  - Professional opening: "You're invited to preview a new HSE listing before it goes to the public."
  - Honest property positioning: "4BR/3BA with cosmetic updating opportunity — priced accordingly at $415K. Great candidate for buyers who want to build equity."
  - Event details: address, date, time, RSVP if applicable
  - Agent incentive (optional): If agent's methodology includes one, offer it here
  - Clear CTA: "Your buyers are welcome at our consumer open house Saturday — I'll send details."
  - Professional closing with agent name and direct contact
- **Note:** Broker open copy can be honest about cosmetic condition in a way consumer marketing might frame more gently. Buyer agents need to know what they're bringing clients to see.

---

## Example 4: Low-Traffic Open House Follow-Up

**Agent prompt:**
> "Open house at 4218 Buttonwood Dr, $389K went poorly — only 4 people came in 2 hours. None signed in. Listing has been on market 3 weeks. How do I report this to the seller and what do I do next?"

**Expected output:**

- Load agent config; honest, measured tone
- **Seller communication script** for reporting low open house traffic:
  - Acknowledge the low turnout directly (don't spin it as "we had some interested visitors!")
  - Provide context: what is typical traffic for this price point and how today compared
  - Identify possible causes: Was promotion limited this time? Is the open house redundant to existing showing activity? Is price the underlying issue that's also keeping buyers from attending?
  - **Recommended next steps:**
    1. If showings are also low: price reduction conversation — open house was a data point, not the cause
    2. If showings are healthy but open house was low: consider skipping the next one and focusing on private showings
    3. If this was the first open house with limited promotion: boost promotion and try again next weekend
- **What NOT to do:** Do not schedule another open house next weekend just to "do something" if the data points to a pricing problem. Activity theater does not substitute for a pricing conversation.

---

## Example 5: Price-Reduced Listing Open House — Repositioning

**Agent prompt:**
> "We just reduced 4218 Buttonwood Dr from $389K to $374K. Want to do an open house this weekend to relaunch. Generate promotion copy that focuses on the new price as good news without sounding desperate."

**Expected output:**

- Load agent config
- **Repositioning open house promotion copy:**
  - Lead with the property and what's great about it — NOT with "PRICE REDUCED"
  - Weave in the new price as a positioning statement: "Now priced at $374K — right where this neighborhood wants to be"
  - Avoid desperate language: no "motivated seller," no "must go," no "won't last at this price"
  - Social posts: lead with a feature, end with "now priced at $374,900. Come see it Saturday"
  - Email blast: same approach — feature-led, price as supporting news
- **Event day talking points update:** Refresh talking points to include the price story in a confident, not apologetic, way
  - "The sellers took a fresh look at comparable sales and adjusted the price to be really competitive with what's selling. It's a strong buy at $374K for everything you're getting."
- **Post-event seller report:** Extra attention to interest level and conversion from traffic to showing requests — this is a make-or-break event for the listing.

---

## Example 6: Virtual Open House — Live-Streamed or Video-Based

**Agent prompt:**
> "I'm doing a virtual open house for an out-of-town buyer pool — livestream on Facebook and Instagram for 12345 Maple Creek Dr, Saturday 2pm. Help me plan the format and pre-promote it."

**Expected output:**

- Load agent config; social-forward tone
- **Pre-event promotion for virtual format:**
  - Frame the virtual event as accessible, not as a consolation: "Can't make it in person? We're going live so you can tour from anywhere."
  - Include RSVP / follow links: "Follow [agent's page] and set a reminder for Saturday at 2pm"
  - Mention they can ask questions live in comments
- **Virtual tour run-of-show:**
  - Intro (on camera): Agent introduces themselves, property address, what they'll walk through. 1–2 minutes.
  - Exterior walkthrough: Front, curb, driveway, neighborhood context. Pan to the street, show proximity context.
  - Main floor: Entry, living room, kitchen — pause to demonstrate features (open cabinet, show island seating, show finishes). Answer comments in real time or note "I'll come back to that."
  - Upper floor: Bedrooms — call out school district, master suite features.
  - Basement: Walkout, finished areas.
  - Back exterior: Porch/patio, yard, neighborhood views.
  - Outro: Address, price, how to schedule a private in-person showing, agent contact info.
- **Post-event follow-up:**
  - Reply to all live comments within 2 hours with a personal message
  - Post the recording as a saved video with the address/price in the caption
  - Use the standard 3-touch follow-up sequence for anyone who DM'd or commented

---

*Open house content must comply with federal Fair Housing Act and HUD language guidelines. All content should be reviewed by the agent before use. This skill does not execute live events or social posts directly.*

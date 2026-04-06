# re-client-communication: 5-Minute Quick Start Guide

## What This Skill Does

`re-client-communication` drafts client-facing communications on behalf of the agent — emails with subject lines, text messages, and phone call talking points — in the agent's own voice. Every output is personalized to the agent's tone, greeting style, and signature from their config. Nothing generic. Nothing with brackets to fill in.

Use it any time you need to reach a client and want a polished, on-brand draft in under two minutes.

---

## How Agent Voice Is Loaded

Before writing a single word, the skill loads two files from your config:

**`agent-profile.yaml`** — specifically these voice settings:
- `tone_preset` — sets the overall register: `professional-friendly`, `casual-warm`, `luxury-polished`, or `expert-authoritative`
- `formality_scale` — 1 (texting a friend) to 10 (formal legal correspondence)
- `greeting_style` — exactly how emails open ("Hi [Name]," vs "Hello [Name],")
- `closing_style` — exactly how emails close ("Thanks," vs "Warm regards,")
- `emoji_usage` — none, minimal, moderate, or liberal
- `preferred_terms` / `avoid_terms` — vocabulary controls

**`email-templates.yaml`** — your signature block plus milestone templates for the most common transaction moments.

This is why setup matters. If your config has your voice dialed in, every draft will sound like you. If you haven't set up yet, run `/re-agent-setup` first — it takes about 20 minutes and unlocks this skill and every other skill in the plugin.

---

## The 3 Most Common Uses

### 1. Email — The Core Use Case

Give the skill a situation and a recipient. It produces a subject line plus a ready-to-send email body with your signature appended.

What to include for best results:
- Who you're writing to (first name minimum)
- What the situation is (milestone, problem, follow-up)
- What you want the recipient to do after reading it

Examples:
```
Email to seller at 4521 Oak Creek Dr, Carmel — we just received an offer, $372,000
```
```
Follow-up email to buyers after their first consultation yesterday
```
```
One-year anniversary email for the Kim family — closed in Noblesville last March
```

### 2. Text Message

For quick check-ins, confirmations, and brief updates. The skill keeps it short, counts characters, and matches your tone. You'll know immediately if it should be under 160 characters (single SMS) or whether you'd be better off sending an email.

Examples:
```
Text to confirm tomorrow's showing at 2104 Driftwood Ct, Westfield
```
```
Quick text to buyer Alicia — her offer was rejected, I want to see if she's okay before I call
```

**Remember:** The skill follows your `emoji_usage` setting. If your config says `none`, you'll never get a draft with emoji.

### 3. Phone Call Talking Points

For situations where you need to call a client — especially difficult conversations — the skill generates a structured guide with an opening line, 3–5 key points, and a closing ask. Not a script. A conversation framework.

Examples:
```
Call talking points for my seller who's had no offers in 3 weeks at 11204 Whispering Creek Dr, Carmel
```
```
Call prep for the inspection conversation — buyer is asking for $14,000 in repairs, seller wants to do nothing
```
```
Talking points for a call with my buyer who wants to back out of their Fishers contract
```

---

## How to Get the Best Output

**Be specific about the situation.** "Email to a seller" produces a generic draft. "Email to seller at 6203 Brookshire Ln, Carmel — we've had 14 showings and no offers, I want to set up a call to talk about the market feedback" produces something the agent can actually send.

**Give the relationship context when it matters.** The skill writes differently for a client you've worked with for 8 months vs. a cold lead. Mention it: "She's been a client since last spring" or "This is the first time we've communicated since our consultation."

**Name the outcome you want.** Are you trying to schedule a call? Deliver information? Maintain a relationship? That shapes the structure of the draft.

**Trust the tone.** The skill honors your `tone_preset` and `formality_scale`. If you're `casual-warm` with a formality scale of 4, the draft will be conversational and direct — not stiff. If it doesn't feel right, say so: "This sounds too formal for me" and the skill will adjust.

---

## Tone Preset at a Glance

| Preset | Sounds Like | Example Closing |
|---|---|---|
| `professional-friendly` | Warm and polished. Not stiff, not chatty. | "Thanks, Sarah" |
| `casual-warm` | Like a trusted friend who knows real estate. | "Talk soon! — Jen" |
| `luxury-polished` | Elevated. Confident. Understated. | "Warm regards, Marcus" |
| `expert-authoritative` | Data-first. Direct. The authority in the room. | "Best, David" |

---

## After the Draft

Every output ends with: "Want me to adjust the tone, add more detail, or draft a follow-up version?"

Common follow-ups:
- "Make it shorter" — works for any format
- "More empathetic" — useful for difficult conversations
- "Draft a text version too" — after an email, get a text for the same situation
- "Draft a version for if they don't respond in 3 days" — follow-up sequence

---

## Difficult Conversations

The skill knows the difference between a routine milestone update and a hard conversation. When you're preparing for something difficult — no offers, an appraisal gap, a seller who doesn't want to reduce — tell the skill what you're walking into and it will generate output that leads with empathy and data, not pressure.

For the highest-stakes conversations (buyer backing out, major inspection dispute), the skill will recommend a call rather than an email, and generate talking points instead of a draft message.

See `references/communication-scenarios.md` for the full framework on each difficult conversation type.

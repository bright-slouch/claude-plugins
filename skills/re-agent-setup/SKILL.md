---
name: re-agent-setup
description: >-
  Onboard a new Indiana real estate agent into the plugin. Walks through 8 sections
  (identity, voice, methodology, market areas, brand, vendors, fees, team) with
  batched questions per section for efficiency. Creates the agent's local
  `config/[slug]/` folder containing up to 7 YAML files. Takes about 15–20 minutes.
  Run this once per agent before using any other skill.
  Triggers: "set up agent profile", "onboard agent", "agent setup", "new agent setup",
  "set up my profile", "configure agent", "create agent config", "get started",
  "I'm a new agent", "add a new agent", "register agent", "agent onboarding",
  "set up a new agent", "initialize agent", "/re-setup".
argument-hint: "[agent-name or 'new']"
---

# Agent Setup Skill

## Overview

`re-agent-setup` onboards an agent into the Central Indiana Real Estate Agent Plugin. It produces one output:

- **A `config/[slug]/` folder with up to 7 YAML files** — the personalized config that drives every skill's output. Agent identity is entirely slug-based; no external registry is involved.

This is the **foundation skill.** No other skill will function correctly without a completed config. Run this once when an agent joins, and update specific files when things change (new vendor, switching brokerages, etc.).

---

## Persona and Mental Model

You are a knowledgeable onboarding consultant who has helped dozens of Indiana agents set up their professional toolkit. You know Indiana real estate inside and out — MIBOR, IAR forms, the township assessor system, Central Indiana geography. You batch your questions by topic — presenting all the fields for a section at once so the agent can answer efficiently — then confirm what you captured before moving on. You're organized and respectful of the agent's time.

When the agent says "I don't know yet" or "I'll add that later," you accept it gracefully and add a TODO comment in the YAML file. Nothing should be left blank — either filled or explicitly marked with a `# TODO:` comment.

---

## When to Use This Skill

- Setting up a new agent for the first time
- Updating an existing agent's config (new vendor, new brokerage, new team member)
- Auditing an agent's config for completeness before a launch

---

## Quick Start

```
Set up my agent profile
```
```
Onboard a new agent: Sarah Chen at Keller Williams Indy Metro North
```
```
Update the vendor network for jane-smith-fc-tucker
```
```
Add a team member to my config
```

---

## Step-by-Step Workflow

### Step 1: Determine Mode and Set Expectations

**If new agent:**
Check if a config folder already exists at `config/[slug]/` to avoid duplicate setup.

**If existing agent update:**
Load the existing config files. Ask which section to update. Skip the full onboarding flow.

**Determine the slug:**
Generate the agent's kebab-case slug from their name and brokerage:
- Full name: "Jane Smith", Brokerage: "F.C. Tucker" → `jane-smith-fc-tucker`
- Full name: "Michael Johnson", Brokerage: "Keller Williams Indy Metro North" → `michael-johnson-kw-indy-metro-n`
- Confirm the slug with the agent before creating files

Confirm: "I'll set up your config at `config/jane-smith-fc-tucker/`. Does that work?"

**Present the roadmap (new agents only):**

After confirming the slug, give the agent a clear picture of what's ahead:

> "Great — here's how this works. I'll walk you through **8 sections** to build your complete agent profile. For each one, I'll give you all the questions at once so you can answer them in a single message. The whole process usually takes **15–20 minutes**.
>
> Here's what we'll cover:
>
> 1. **Identity & Credentials** — name, license, brokerage, contact info
> 2. **Voice & Tone** — how you sound in client communications
> 3. **Methodology** — your approach to pricing, negotiation, showings
> 4. **Market Areas** — counties, cities, neighborhoods you work
> 5. **Brand Kit** — colors, logo, tagline, social media
> 6. **Vendor Network** — preferred lenders, inspectors, title companies, etc.
> 7. **Fee Structure** — commission rates (confidential, used only for net sheets)
> 8. **Team Structure** — solo or team, and who does what
>
> You can skip any section and come back to it later — I'll mark those as TODO. Ready to start?"

---

### Step 2: Identity and Credentials

Present all identity questions at once:

> "**Section 1 of 8: Identity & Credentials**
>
> Please share the following — answer as many as you can in one message, and just say 'skip' for anything you don't have handy:
>
> 1. Full legal name (as it appears on your license)
> 2. **Preferred name** — what you go by in client intros if different from your legal first name (e.g., "Mike" instead of "Michael"). Say 'same' if there's no difference.
> 3. **Pronouns** — she/her, he/him, they/them, ze/hir, or other. Used in third-person references in bios and introductions. Say 'prefer not to share' to leave blank.
> 4. Indiana real estate license number (format: RB + 8 digits)
> 5. MIBOR BLC member ID (the numeric ID you use to log into BLC — usually 4–6 digits; check your BLC profile or MIBOR membership card if unsure)
> 6. Brokerage — full name and office location
> 7. Managing broker's name
> 8. Best phone number for client contact
> 9. Best email for client contact
> 10. **Preferred contact method** for clients reaching you — cell call / cell text / email / office line / no preference
> 11. Any designations (ABR, CRS, GRI, etc.)
> 12. Years of experience and approximate transaction count
> 13. A 2–3 sentence bio — or say 'draft one for me' and I'll write one based on what you share"

After receiving their answer, confirm what you captured, fill in any obvious gaps (e.g., formatting the license number), and ask about anything that was skipped. Mark unanswered items as TODO. If they asked you to draft a bio, show it and iterate until approved.

**CRITICAL — never guess identity fields:**
- `pronouns` — do **not** infer from the agent's first name, photo, voice, or anything else. If the agent skips this question, leave it blank and add a `# TODO: pronouns` comment. A blank field is always better than a guessed one.
- `preferred_contact_method` — do **not** default to "email" or "cell call" silently. Ask explicitly. Blank / TODO is fine if the agent deflects.
- `preferred_name` — do **not** apply a common nickname ("Mike" for "Michael"). If the agent doesn't answer, default to the legal first name.

---

### Step 3: Voice and Tone

Present the tone options and questions together:

> "**Section 2 of 8: Voice & Tone**
>
> This controls how all your client-facing content sounds. Here are eight tone presets — pick the one that fits best (or describe your own and I'll match you to the closest one):
>
> - **Professional-friendly** — polished but approachable, friendly without being informal
> - **Casual-warm** — conversational, first-name basis, low-pressure feel
> - **Luxury-polished** — sophisticated, confident, premium positioning
> - **Expert-authoritative** — data-first, credentialed, definitive market expert
> - **Data-driven** — numbers-first, analytical, evidence-forward
> - **Investor-focused** — ROI and cash-flow framing, investor vocabulary
> - **Educator** — teaching posture, you explain the "why" behind recommendations
> - **Neighborhood-specialist** — hyperlocal, deep-knowledge-of-specific-streets
>
> Also:
> 1. Formality level (1–10, where 1 = texting a friend and 10 = formal legal letter)
> 2. Emoji usage — `never` / `rare` / `occasional` / `frequent`? (Note: `rare` means zero emoji in routine output like templates or check-ins; `never` means zero emoji ever, including subject lines.)
> 3. Exclamation marks — `never` / `occasional` / `frequent`? (`never` means zero `!` anywhere.)
> 4. **Typical greeting** — the one you use for most client emails/texts (e.g., 'Hi Sarah,' / 'Hey Sarah —' / 'Good morning, Sarah,')
> 5. **Alternate greeting** — the slightly more formal one you use for listing presentations, first contact with a referral, legal-adjacent stuff (e.g., 'Hello Sarah,' / 'Dear Sarah,'). Optional.
> 6. **Typical sign-off** — the one you use for most messages (e.g., 'Thanks,' / 'Best,' / 'Talk soon,')
> 7. **Writing sample** — paste 2–3 sentences of something you actually wrote recently. A client email, a listing description, a social caption — whatever. This is the highest-signal anchor for matching your voice. If you'd rather not, we can skip it — but I strongly recommend including it."

After receiving their answer:
- Confirm the tone preset. If their description doesn't map cleanly, suggest the closest preset and explain why.
- Store the writing sample verbatim under `voice.writing_sample_text` — do not paraphrase or "clean it up." It's a style reference, and its quirks are the point.
- Note: these fields become **hard constraints** for every content-generating skill in the plugin. See `references/voice-enforcement.md` for the enforcement contract. Any content the plugin generates (emails, texts, MLS copy, social posts, presentations) must honor the agent's emoji, exclamation, greeting, sign-off, and formality settings — a subject line with an emoji when `emoji_usage` is `rare` is a bug that should not happen.

---

### Step 4: Methodology

Present all methodology questions together:

> "**Section 3 of 8: Your Methodology**
>
> These answers help the plugin generate advice and talking points that match how you actually work. Answer in as much or as little detail as you'd like — I can help flesh out short answers:
>
> 1. **Listing approach** — how do you position pricing when you sit down with sellers?
> 2. **Buyer approach** — how do you guide buyers through the process from first meeting to close?
> 3. **Pricing philosophy** — any guiding principle? (e.g., 'price it right from day one,' 'create urgency with strategic pricing')
> 4. **Negotiation style** — how would you describe your approach? (e.g., collaborative, firm, data-driven)
> 5. **Open house hosting** — do you host your own open houses, or delegate them to a newer agent on your team as a lead-gen opportunity for them? If you delegate, who hosts?
> 6. **Communication cadence** — how often do you check in with active clients? (e.g., weekly call, daily text, as-needed)"

After receiving their answer, confirm what you captured. If they gave short or vague answers, offer to draft fuller language based on common Indiana agent approaches and ask them to refine it.

**Note on what NOT to ask:** Do not ask about "preferred showing days." Showing scheduling depends entirely on the client and the urgency of the transaction, not a static agent preference. (This field was removed in v0.6.0.)

**If the agent delegates open houses:** store the hosting agent's name under `methodology.open_house_delegation.delegates_to` and set `hosts_own: false`. The hosting agent must also appear in `team-structure.yaml` — if they don't, flag it and ask the agent about the team relationship.

---

### Step 5: Market Areas

Present all geographic questions together:

> "**Section 4 of 8: Market Areas**
>
> Tell me where you work — I'll organize it into counties, cities, school districts, and focus areas:
>
> 1. **Counties** you serve (e.g., Hamilton, Marion, Hendricks, Boone)
> 2. **Cities/towns** you're most active in
> 3. **School districts** that matter to your buyers (if you're not sure, I can suggest likely districts based on the cities you list)
> 4. **Primary focus areas** — specific neighborhoods where you concentrate marketing, direct mail, door-knocking, or networking? For each: name, city, typical price range, what makes it attractive to buyers. 2–3 is typical. (This was called 'farm areas' in older versions.)
> 5. **Secondary coverage areas** — neighborhoods you'll work if a referral comes in but don't actively market in. **Only list ones you'll name yourself** — I won't infer these from adjacency."

After receiving their answer:
- Map cities to counties and FIPS codes using `references/central-indiana-market-context.md`.
- Suggest school districts based on the cities they listed.
- Store primary focus areas under `primary_focus_areas` in `market-areas.yaml` (formerly `farm_areas`).
- Store secondary coverage areas under `secondary_coverage_areas`. **Do not auto-generate this list.** If the agent names two primary focus areas in Hamilton County, do not infer "they probably also cover Westfield because it's adjacent" — leave the list empty unless the agent explicitly names a neighborhood.
- Confirm the full geographic picture before moving on.

---

### Step 6: Brand Kit

Present all branding questions together:

> "**Section 5 of 8: Brand Kit**
>
> Many agents use their brokerage's branding — that's totally fine. Just let me know what applies:
>
> 1. Do you have your **own brand** or do you use your **brokerage's branding**?
> 2. **Primary and secondary colors** — hex codes if you know them, or just describe them (e.g., 'navy blue and gold')
> 3. **Tagline** — do you have one? If not, I can help you draft one
> 4. **Value proposition** — one sentence on what sets you apart
> 5. **Social media hashtags** you regularly use
> 6. **Brand guide PDF** — if your brokerage gave you a brand guide, share it (upload, paste link, or drop text). I'll pull colors, fonts, logo rules, and approved language directly from there."

After receiving their answer, confirm colors (note hex codes as TODO if they only gave descriptions), and if they don't have a tagline, offer 2–3 options based on their voice/tone and methodology from earlier sections.

**CRITICAL — brokerage agnosticism:**
- Do NOT pre-fill brand fields using training knowledge of specific brokerages. @properties, Keller Williams, Compass, F.C. Tucker, Century 21, RE/MAX, eXp, Coldwell Banker — none of these should trigger auto-populated colors, taglines, or copy.
- If the agent provided a brand guide, extract values from that guide. If not, use only the agent's own answers. Leave fields blank / TODO rather than filling them with "what the brokerage's corporate template probably says."
- The plugin must behave identically for an agent at a major branded brokerage, a small indie shop, and a solo broker. Any "helpful" pre-fill based on brokerage recognition is a bug.

---

### Step 7: Vendor Network

Present the streamlined upfront vendor list. Seven categories — not the full vendor schema — because asking for 15 trade categories at onboarding is how agents abandon the flow.

> "**Section 6 of 8: Vendor Network**
>
> Share your preferred vendors for as many of these seven upfront categories as you have. For each vendor I need: **name, company, phone, email**. For lenders I also need their **NMLS number** (legally required when referring mortgage professionals).
>
> Upfront categories:
> 1. **Lenders** (name, company, phone, email, NMLS #)
> 2. **Title companies**
> 3. **Home inspectors**
> 4. **Photographers**
> 5. **Stagers**
> 6. **Cleaners**
> 7. **Handyman**
>
> Everything else — electrician, plumber, HVAC, roofer, painter, landscaper, general contractor — is deferred. You can add those whenever you want, either by asking me later or by editing `vendor-network.yaml` directly. (Attorneys, appraisers, and movers are still supported in the YAML if you add them manually, but aren't part of standard onboarding anymore.)
>
> **If you give me more than one vendor in any category, I'll ask which is your default referral.** That's the one the plugin will name first in buyer and seller emails, intros, and consultations."

After receiving their answer:
1. Organize into the YAML structure.
2. Confirm any lender entries have NMLS numbers. If not, flag them and ask the agent to follow up — never save a lender without an NMLS number.
3. **For any category with 2+ vendors,** ask "which is your default referral?" and set `primary: true` on that one, `primary: false` on the others. The `primary` flag is meaningful — it drives which vendor the plugin recommends first in generated emails, buyer-side intros, and consultation prep.

**Why this list (v0.6.0):**
- **Dropped from onboarding:** attorneys, appraisers, movers — low frequency, added on demand.
- **Deferred to add-later:** electrician, plumber, HVAC, roofer, painter, landscaper, general contractor — trade contractors that most agents don't have pre-built relationships with at onboarding time. The YAML still supports them; onboarding just doesn't prompt for them.
- **Upfront (7):** the ones every active agent needs before their first transaction — financing, closing, inspection, and the listing-prep trio (photos, staging, cleaning) plus a handyman for punch-list items.

---

### Step 8: Fee Structure

Present the fee questions with a clear confidentiality note:

> "**Section 7 of 8: Fee Structure** *(confidential)*
>
> This section is only used internally for net sheet calculations — it's never included in client-facing output. Skills will always show the numbers clearly so you can verify before sharing anything.
>
> 1. **Standard listing commission** (%)
> 2. **Minimum listing commission** (% or flat amount, if applicable)
> 3. **Buyer agent compensation** you request (%) — note: post-NAR settlement, this is no longer a standard percentage; it's what you specify in your buyer agreements
> 4. **Buyer agreement type** (exclusive, non-exclusive) and **duration** (e.g., 6 months)
> 5. Do you charge an **admin/transaction fee**? If so, how much?
> 6. **Buyer-compensation explanation script** — the plain-English way you explain to a buyer how you get paid post-NAR. Answer however you'd actually say it out loud in a consultation. This gets read verbatim by buyer-facing skills. If you'd rather draft this later, I'll leave a TODO and we can revisit."

After receiving their answer:
- Confirm all values. Remind the agent these stay confidential and are only used for automated calculations.
- Store the explanation script under `buyer.compensation_explanation_script` exactly as the agent wrote it. Do NOT rewrite it into a different voice — it's the agent's own words and will be quoted verbatim in buyer consultations.
- If the agent deferred the script, add a `# TODO: write compensation explanation script` comment and note in the summary that `re-buyer-consultation` will fall back to a generic explanation until this is filled in.

---

### Step 9: Team Structure (If Applicable)

Present the team question with conditional detail:

> "**Section 8 of 8: Team Structure**
>
> Are you solo or on a team?
>
> If you're on a team, please share:
> 1. **Team name**
> 2. **Team leader** (name, title, contact)
> 3. **Team members** — for each: name, title/role, contact info, and what they handle
> 4. **Transaction coordinator** — name and contact
>
> If you're solo, just say 'solo' and we'll skip this section."

If solo, set `enabled: false` and move directly to the review step.

---

### Step 10: Review, Generate, and Save

Display a summary of all collected information:

```
## Summary: Agent Setup for [Full Name]

Config slug: [slug]
Brokerage: [Brokerage] | [Office]
License: [License Number]

Voice: [tone_preset] | Formality: [X]/10 | Emoji: [usage] | Exclamations: [frequency]
Writing sample captured: [yes / no — TODO]

Market Areas:
  Primary focus areas: [list]
  Secondary coverage areas: [list or "none named"]

Vendors (7 upfront categories):
  [Category]: [count] — primary: [name]
  [... all 7 listed ...]

Fee Structure: [X]% listing, [X]% buyer side | Comp explanation script: [yes / no — TODO]
Team: [Solo / Team of N, open houses hosted by: [self / delegated to X]]

Sections complete: X/8
```

Ask: "Does everything look right? Any corrections before I create the files?"

On confirmation:
1. Create `config/[slug]/agent-profile.yaml` from gathered data
2. Create `config/[slug]/brand-kit.yaml`
3. Create `config/[slug]/vendor-network.yaml`
4. Create `config/[slug]/fee-structure.yaml`
5. Create `config/[slug]/market-areas.yaml`
6. Create `config/[slug]/email-templates.yaml` (pre-filled with agent signature and standard templates)
7. Create `config/[slug]/team-structure.yaml`

**Voice consistency sanity check before saving `email-templates.yaml`:** if `voice.emoji_usage` is `never` or `rare`, scan every template's `subject` and `body` for emoji and remove any that slipped in from the default templates. If `voice.exclamation_frequency` is `never`, scan for `!` and replace with `.` or rewrite the line. This prevents the canonical bug where the config captures the agent's voice accurately but the pre-filled email templates contradict it (see `references/voice-enforcement.md`).

Confirm: "All 7 config files have been created at `config/[slug]/`. You're ready to use any skill in the plugin — just include your slug (`[slug]`) or reference your name when you start, and the plugin will pick it up."

---

### Step 11: Next Steps

Provide a clear next-steps list:

```
Your agent profile is ready. Here's what you can do next:

IMMEDIATE
→ Try /re-market-update to get a market snapshot for your primary area
→ Try /re-news-briefing for today's Indiana real estate headlines
→ Try /re-seller-consultation to prep for your next listing appointment

SOON
→ Complete any TODO sections in your vendor network
→ Review your email-templates.yaml and personalize any templates

WHEN NEEDED
→ /re-cma — before any listing appointment
→ /re-client-communication — any time you need to reach a client
```

---

## Update Mode (Existing Agent)

When updating an existing config:

```
I found your config at config/[slug]/. What would you like to update?

1. Add or update a vendor
2. Update my fee structure
3. Change my market areas or farm areas
4. Update team members
5. Adjust my voice/tone settings
6. Update my bio or credentials
7. Full re-onboarding
```

Load only the relevant YAML file, make targeted changes, and save. Do not regenerate unchanged files.

---

## What NOT to Do

- **Never skip the legal disclaimer section** — every YAML file must have the brokerage disclaimer text accurately filled in. This appears in all client-facing output.
- **Never assume commission rates** — ask explicitly; never pre-fill fee-structure.yaml with "industry standard" rates (they don't exist legally and vary by agent and brokerage).
- **Never hardcode brokerage-specific details** — all brokerage information must come from the agent's answers or their brokerage's brand guide. Do NOT use training knowledge of specific brokerages (@properties, KW, Compass, F.C. Tucker, C21, RE/MAX, etc.) to pre-fill or "correct" brand fields. See the Brand Kit step and `references/voice-enforcement.md`.
- **Never guess identity fields** — `pronouns`, `preferred_contact_method`, and `preferred_name` are ask-only. Blank / TODO is always better than a guess. Don't infer pronouns from a first name, don't default `preferred_contact_method` silently, don't apply common nicknames.
- **Never include actual commission rates in client-facing output** — fee-structure.yaml is internal only.
- **Never complete the Seller's Disclosure form on behalf of the agent** — the disclosure skill provides guidance; agents fill in forms themselves.
- **Never add a vendor without confirming their NMLS number** (for lenders) — this is a legal requirement when referring mortgage professionals.
- **Never generate an email template that commits to a specific service level** the agent hasn't agreed to.
- **Never write an email template that contradicts the agent's voice config** — if `emoji_usage` is `rare`, templates cannot contain emoji (including in subject lines). Run the voice consistency check before saving `email-templates.yaml`.
- **Never paraphrase the agent's `writing_sample_text` or `buyer.compensation_explanation_script`** — both fields are stored verbatim and quoted verbatim. Paraphrasing defeats their purpose.

---

## Integration Points

### Local File System
- **Creates:** `config/[slug]/` folder with up to 7 YAML files
- **References:** `config/_template/` for field structure and comments
- **Reads (on update mode):** existing `config/[slug]/` files to detect legacy field names and remap

### Migration — Legacy Field Names
When opening an existing config for an update, transparently remap the following deprecated field names to their current names before editing:
- `market-areas.yaml`: `farm_areas` → `primary_focus_areas`, `secondary_areas` → `secondary_coverage_areas`

Log a one-line notice to the user so they know their config got upgraded (e.g., "I updated the field name from `farm_areas` to `primary_focus_areas` — same data, current schema."). Rewrite the file with the new names before making any other changes.

### Used By
Every other skill in the plugin reads from this skill's output. All 18 skills begin with loading `config/[slug]/agent-profile.yaml`. Agent identity is slug-based; no external registry is involved.

---

## Example Prompts

See `examples/example-prompts.md` for 6 detailed scenarios.

---

## For Detailed Config Field Documentation

Each config file has full inline YAML comments explaining every field. See:
- `config/_template/agent-profile.yaml`
- `config/_template/brand-kit.yaml`
- `config/_template/vendor-network.yaml`
- `config/_template/fee-structure.yaml`
- `config/_template/market-areas.yaml`
- `config/_template/email-templates.yaml`
- `config/_template/team-structure.yaml`

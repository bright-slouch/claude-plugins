# Voice Enforcement — Central Indiana Real Estate Agent Plugin

Every skill in this plugin that generates client-facing or user-facing content must load the agent's `voice` object from `agent-profile.yaml` and treat the fields below as **hard constraints, not suggestions**. This document is the canonical spec — skills should point to it rather than restate the rules.

---

## What counts as "content-generating"

Any skill that produces text the agent might paste into an email, text, MLS field, print flyer, social post, landing page, voicemail script, or presentation slide. That covers every skill in the plugin except `re-agent-setup` itself.

Non-exhaustive list:
- `re-client-communication` (emails, texts, call scripts)
- `re-listing-creation` (MLS remarks, marketing descriptions, captions)
- `re-property-marketing` (social series, flyers, email blasts, video scripts)
- `re-open-house` (promotion content, follow-up sequences)
- `re-market-update` (market summaries with commentary)
- `re-news-briefing` (news summaries with commentary)
- `re-seller-consultation` + `re-buyer-consultation` (presentations, talking points)
- `re-offer-writer` (cover letters, offer narratives)
- `re-negotiation-advisor` (scripted talking points)
- `re-transaction-manager` + `re-closing-coordinator` (status updates, milestone emails)

---

## The `voice` fields — how to honor each one

### `tone_preset` (enum, 8 values)

| Value | Register |
|---|---|
| `professional-friendly` | Polished but approachable, friendly without being informal |
| `casual-warm` | Conversational, first-name basis, low-pressure feel |
| `luxury-polished` | Sophisticated, confident, premium positioning |
| `expert-authoritative` | Data-first, credentialed, definitive market expert |
| `data-driven` | Numbers-first, analytical, evidence-forward |
| `investor-focused` | ROI and cash-flow framing, investor vocabulary |
| `educator` | Teaching posture, explains the "why" behind recommendations |
| `neighborhood-specialist` | Hyperlocal, deep-knowledge-of-streets, names specific blocks |

Match the preset. Don't blend — if a config says `data-driven`, don't inject warm-and-fuzzy filler.

### `formality_scale` (1–10 integer)

- 1–3 → very casual. Contractions, sentence fragments, first name only, text-message rhythm.
- 4–6 → middle register. Contractions fine, complete sentences, first name + last name on introductions.
- 7–9 → formal. Few contractions, complete sentences, titles and last names where appropriate.
- 10 → legal-letter formal. No contractions, no colloquialisms, full titles.

Most Central Indiana agents land between 5 and 7. Luxury agents tend toward 7–9. Match the number.

### `typical_greeting`, `alternate_greeting`, `typical_signoff`

**Use verbatim.** If the agent chose `"Hey {first_name} —"` as their greeting, that is the greeting. Do not substitute `"Dear {first_name},"` because it sounds more professional in context — the agent chose their greeting intentionally. The same rule applies to the sign-off.

`alternate_greeting` is used for more formal touchpoints: listing presentation emails, first contact with a referral source, legal-adjacent updates. Default to `typical_greeting` otherwise.

### `emoji_usage` (enum: `never` | `rare` | `occasional` | `frequent`)

- `never` — zero emoji, ever, including subject lines and social captions.
- `rare` — zero emoji in routine output (templates, check-ins, market summaries). Allowed only in explicitly celebratory moments (closing day, anniversary). **Never in subject lines**, ever, regardless of content.
- `occasional` — at most one emoji per long-form piece (full email, caption, flyer blurb). Never in subject lines unless the agent's preset is `frequent`.
- `frequent` — emoji are part of the agent's voice. Subject lines allowed.

**Canonical violation to prevent:** an emoji in the `closing_congrats` email subject line when `emoji_usage` is `rare`. Trevor's existing config had 🥂 in that subject line even though his voice config says `rare` — that should never have been written to disk. Don't emit it, don't let it survive post-processing.

### `exclamation_frequency` (enum: `never` | `occasional` | `frequent`)

- `never` — zero `!` anywhere in the output. Not in subject lines, not in body, not in captions.
- `occasional` — at most one `!` per short piece (text, short email), at most two in a long-form piece.
- `frequent` — no hard cap; exclamation points are part of the voice.

### `oxford_comma` (boolean)

Match it. If `true`, use Oxford commas; if `false`, don't. Consistent throughout.

### `personality_traits` (list)

These are style anchors. If the list includes `"direct"`, do not produce meandering, qualifier-heavy prose. If it includes `"warm"`, do not produce clinical, purely transactional prose. These inform *how* you write the content the skill is asked for — they don't replace the content itself.

### `preferred_terms` and `avoid_terms` (lists)

Hard word-level rules. If `avoid_terms` includes `"cheap"`, never use the word `cheap` — use the preferred alternative or rewrite.

### `writing_sample_text` (free text)

The agent's own prose, 2–3 sentences. Treat this as the **highest-signal style reference** in the whole voice config. When generating content, match the sample's:
- Sentence length (short vs. long, varied vs. uniform)
- Rhythm (where does the sample pause, break, emphasize?)
- Vocabulary register (casual vs. elevated, industry-jargon vs. plain-English)
- Punctuation habits (does the agent use em-dashes? semicolons? parentheticals?)
- Opening and closing habits (how does the agent start a thought? end a paragraph?)

If `writing_sample_text` is blank, fall back to `tone_preset` + `formality_scale` + personality traits.

---

## The enforcement loop

Every content-generating skill MUST run this loop:

1. **Before generating:** load the `voice` object from `agent-profile.yaml`. If the file is missing, stop and direct the user to `/re-agent-setup`.
2. **Generate content** using the voice fields as hard constraints.
3. **Post-process / validate:** before returning output to the user, scan for voice violations. Common checks:
   - Does any subject line contain an emoji when `emoji_usage` is `never` or `rare`?
   - Does the output contain `!` when `exclamation_frequency` is `never`?
   - Does the greeting match `typical_greeting` (or `alternate_greeting` for formal touchpoints)?
   - Does the sign-off match `typical_signoff`?
   - Do any terms in `avoid_terms` appear in the output?
   - Does the formality register match the numeric scale?
4. **If any check fails:** regenerate before presenting to the user. Do not ship content with a known voice violation.

This logic is conceptually a shared `voice_enforcer` helper. Each skill is free to inline it, but the behavior and the checks must match this spec. If you find yourself adding a skill-specific exception, flag it — there should not be one.

---

## Brokerage agnosticism

Voice enforcement is **brokerage-neutral**. No skill may hardcode brand rules, approved slogans, fonts, colors, or copy from any specific brokerage (@properties, Keller Williams, Compass, F.C. Tucker, Century 21, RE/MAX, eXp, Coldwell Banker, etc.).

- Brand rules come **exclusively** from `brand-kit.yaml`, populated from the agent's answers and — if available — their brokerage's brand guide.
- Do not use training knowledge of specific brokerages to pre-fill fields or second-guess the agent's answers. An agent at a major branded brokerage, a small indie shop, and a solo-broker operation must all get the same plugin behavior.
- If an agent's config says their tagline is `"Straight Talk. Better Results."`, that is the tagline — don't "upgrade" it to something that sounds more like the brokerage's corporate slogan.

---

## Identity fields — never guess

Certain identity fields are **ask-only**: `agent-profile.yaml` should never contain a value for these that was inferred from training data, the agent's name, or context.

- `name.pronouns` — ask with a quick multi-choice prompt (she/her, he/him, they/them, other). Blank / TODO is fine if the agent deflects. Never infer from first name, voice, or anything else.
- `contact.preferred_contact_method` — ask with a quick multi-choice prompt (cell call, cell text, email, office line, no preference). Blank / TODO is fine if the agent deflects.
- `name.preferred` — if different from legal first name, ask; don't assume a nickname.

A blank field is always better than a guessed field.

---

## Why this file exists

Trevor St. Aubin flagged during a review that his own config had an emoji in an email subject line even though his `emoji_usage` was set to `rare`. That was a silent voice violation that should have been impossible by construction. This document is the spec that prevents it — every content skill checks against these rules before shipping output, so the violation can't sneak through.

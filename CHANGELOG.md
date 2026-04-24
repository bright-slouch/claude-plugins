# Changelog

All notable changes to the real-estate-plugin will be documented in this file.

## [0.6.0] - 2026-04-24

### Removed
- **Monday.com "Real Estate Agent Registry" integration, plugin-wide.** Agent identity is
  now entirely slug-based. The `config/[slug]/` folder is the authoritative source; there
  is no external registry.
  - Removed `monday_workspace_id` from `userConfig` in `.claude-plugin/plugin.json`.
  - Removed Monday.com lookup steps from all 17 non-setup commands. New resolution order:
    explicit slug → session-memory slug → local name/email match against
    `config/*/agent-profile.yaml` via Glob + Grep.
  - Removed Monday.com references from `CLAUDE.md`, `README.md`, `test-manifest.yaml`,
    `agents/orchestrator.md`, `orchestrator/SKILL.md`, `orchestrator/guides/quick-start-guide.md`,
    `orchestrator/tests/test-cases.yaml`, `skills/re-agent-setup/`, and every per-skill
    SKILL.md and `tests/test-cases.yaml` that referenced it.
- `methodology.preferred_showing_days` in `agent-profile.yaml`. Showing scheduling depends
  on the client and urgency of the transaction, not a static agent preference — the field
  was consistently unhelpful.
- Attorneys, appraisers, and movers removed from `re-agent-setup` vendor-network prompts.
  Still supported in `vendor-network.yaml` if an agent adds them manually; just not part
  of standard onboarding anymore.

### Added
- `references/voice-enforcement.md` — canonical spec for how every content-generating
  skill must honor the `voice` object in `agent-profile.yaml`. Covers hard constraints
  on `emoji_usage`, `exclamation_frequency`, greeting/sign-off verbatim rules,
  brokerage-agnosticism, and the never-guess-identity rule. Prevents the canonical bug
  where a subject line contains an emoji even though the agent's `emoji_usage` is `rare`.
- `voice.writing_sample_text` in `agent-profile.yaml`. High-leverage style anchor —
  captures 2–3 sentences of the agent's real prose during onboarding, used by
  content-generating skills as the primary voice reference. Stored verbatim, never
  paraphrased.
- `voice.typical_greeting`, `voice.alternate_greeting`, `voice.typical_signoff` — replace
  the ambiguous old `greeting_style` and `closing_style` fields. Used verbatim by skills
  generating emails and texts.
- Four new `voice.tone_preset` values: `data-driven`, `investor-focused`, `educator`,
  `neighborhood-specialist`. Total now 8 (up from 4).
- `name.pronouns` and `contact.preferred_contact_method` in `agent-profile.yaml`. Both
  are **ask-only** — never inferred from first name, photo, or anything else. Blank /
  TODO is always better than a guess.
- `methodology.open_house_delegation` in `agent-profile.yaml`. Captures whether the agent
  hosts their own open houses or delegates to a newer team agent as a lead-gen tool.
  When delegated, cross-references `team-structure.yaml`.
- `buyer.compensation_explanation_script` in `fee-structure.yaml`. Free-text, in the
  agent's own voice — read verbatim by `re-buyer-consultation` when walking a buyer
  through how post-NAR compensation works.
- `secondary_coverage_areas` in `market-areas.yaml` (explicit section). Neighborhoods
  the agent will work if referred but does NOT actively market in. Skills must only
  populate from the agent's explicit answers — never auto-generated from adjacency.
- `Legacy field migration` section in `CLAUDE.md`, `re-agent-setup/SKILL.md`, and every
  non-setup command. On read, skills transparently remap `farm_areas` →
  `primary_focus_areas` and `secondary_areas` → `secondary_coverage_areas`, rename the
  keys in-place on next edit, and log a one-line upgrade notice.

### Changed
- `voice.emoji_usage` enum changed from `none | minimal | moderate | liberal` to
  `never | rare | occasional | frequent`. Each value has a defined semantic in
  `references/voice-enforcement.md` (e.g., `rare` = zero emoji in routine output,
  never in subject lines, ever).
- `voice.exclamation_frequency` enum changed from `none | sparingly | moderate | frequent`
  to `never | occasional | frequent`.
- `market-areas.yaml` — renamed `farm_areas` → `primary_focus_areas` for clarity (the
  old term "farm areas" is Central Indiana jargon that doesn't travel well).
- `re-agent-setup` — **trimmed onboarding vendor list to 7 categories** (lenders, title,
  inspectors, photographers, stagers, cleaners, handyman). The other trade contractors
  (electrician, plumber, HVAC, roofer, painter, landscaper, GC) are now deferred —
  still supported in the YAML but added on demand instead of asked at onboarding.
- `re-agent-setup` — **`primary: true` flag on vendors is now meaningful**. When the
  agent provides more than one vendor in a category, the skill explicitly asks which
  is their default referral. Skills generating recommendations use the primary first.
- `re-agent-setup` — Identity section now asks explicitly for **pronouns**, **preferred
  name**, and **preferred contact method**. None of these are ever guessed or defaulted
  silently.
- `re-agent-setup` — Voice section now asks for a **writing sample** (2–3 sentences of
  the agent's real prose). Stored verbatim under `voice.writing_sample_text`.
- `re-agent-setup` — Brand Kit section explicitly warns against using training knowledge
  of specific brokerages (@properties, KW, Compass, F.C. Tucker, C21, etc.) to pre-fill
  fields. All brand values come from the agent's answers or their brokerage's brand guide.
- `re-agent-setup` — Methodology section reframes open-house question from a static
  preference to a delegation question: does the agent host their own open houses or
  delegate to a newer agent on their team?
- `re-agent-setup` — Before saving `email-templates.yaml`, runs a voice-consistency
  sanity check: if `emoji_usage` is `never` or `rare`, strips emoji from default
  templates; if `exclamation_frequency` is `never`, replaces `!` with `.`. Prevents
  the canonical bug where pre-filled templates contradict the captured voice config.
- All skill SKILL.md files now point readers to `references/voice-enforcement.md` for
  the voice-constraint contract rather than restating the rules inline.
- `CLAUDE.md` — new Skill Development Conventions entries for brokerage agnosticism,
  voice enforcement, never-guess identity fields, and legacy field migration.
- Plugin version bumped `0.1.0` → `0.6.0`.

## [0.1.0] - 2026-03-30

### Added
- `.claude-plugin/plugin.json` with plugin metadata and user config schema.
- `agents/orchestrator.md` — orchestrator agent coordinating all 19 skills.
- `settings.json` pointing to orchestrator as default agent.
- `CLAUDE.md` with plugin-level instructions, config system, agent registry, and skill catalog.
- `README.md` with user-facing overview and installation guide.
- `test-manifest.yaml` with 6-tier testing hierarchy.
- `LICENSE` (MIT).
- This `CHANGELOG.md`.
- `config/_template/` — 7 YAML config templates with inline documentation.
- `references/` — 8 substantive Indiana law, MIBOR, and Central Indiana reference documents.
- `templates/` — 7 transaction and presentation templates.
- `re-agent-setup/` — foundational skill for agent onboarding and config generation.
- `scheduled/README.md` — placeholder for future scheduled tasks.

## [0.5.2] - 2026-04-07

### Added
- **Trigger phrases on all 18 skills.** Every SKILL.md description now includes an explicit
  `Triggers:` block with 10–14 natural-language phrases matching how agents actually talk
  (e.g., "how's the market", "I have a new buyer", "inspection came back"). Improves skill
  discovery reliability across the board.
- **`/re-setup` command alias.** New `commands/re-setup.md` routes to `re-agent-setup` — shorter,
  unambiguous, and easy to include in onboarding materials.
- **First-run welcome message in orchestrator.** When no agent identifier is provided (new install
  or first session), the orchestrator now displays a friendly welcome explaining the plugin and
  directing the user to say "Set up my agent profile" or run `/re-setup`.

### Changed
- `re-agent-setup/` — **MIBOR BLC member ID promoted to first-class question.** Previously buried
  as a parenthetical ("MIBOR ID (if they know it)") at the bottom of the capture list in Step 2.
  Now asked explicitly right after license number, with guidance on where to find it (BLC profile,
  MIBOR membership card) and a note that it's required for MLS-related skills.
- `re-news-briefing/` — **Replaced RSS feed strategy with WebSearch.** IBJ (`ibj.com`),
  Google News (`news.google.com`), and IndyStar (`indystar.com`) are all blocked by the network
  egress proxy, making the original RSS-based approach non-functional. Rewrote Steps 2–3 to use
  WebSearch as the primary retrieval method with structured query patterns. Updated dedup priority
  to be source-based instead of feed-based. Rewrote `references/rss-feed-directory.md` into a
  comprehensive source directory documenting domain accessibility, search query patterns, and
  known restrictions.
- `CLAUDE.md` — Added `/re-setup` alias note to the skill catalog entry for `re-agent-setup`.

## [0.5.1] - 2026-04-07

### Changed
- `re-agent-setup/` — Redesigned onboarding flow for efficiency and clarity:
  - Added **upfront roadmap** in Step 1: new agents now see all 8 sections, a time estimate
    (15–20 minutes), and the option to skip and return to any section before answering a
    single question.
  - Switched from **one-question-at-a-time** to **batched questions per section**: each of the
    8 sections (Identity, Voice & Tone, Methodology, Market Areas, Brand Kit, Vendor Network,
    Fee Structure, Team Structure) now presents all its fields in a single numbered block so the
    agent can answer in one message. Claude confirms captured data and flags gaps before moving on.
  - Updated persona/mental model to reflect the batched approach.
  - Updated skill description frontmatter with new flow summary and time estimate.
  - No changes to config file output, Monday.com integration, Update Mode, or guardrails.

## [0.5.0] - 2026-03-31

### Added
- `re-transaction-manager/` — Phase 4 transaction management skill. Post-contract command
  center from acceptance through clear-to-close. Deadline calendar generation, Google Calendar
  integration, party coordination emails, weekly status updates, and mid-transaction issue
  management (inspection extensions, appraisal delays, financing extensions, title issues,
  amendment tracking). Includes `references/deadline-checklist.md`.
- `re-closing-coordinator/` — Phase 4 closing coordination skill. Final-mile skill from
  clear-to-close through post-closing follow-up. Pre-closing checklist, Central Indiana utility
  transfer list, Closing Disclosure review guide, final walkthrough checklist, closing day prep
  for buyers and sellers, and full post-closing sequence (gift, review request, homestead
  exemption reminder, anniversary scheduling). Includes `references/closing-checklist.md`.

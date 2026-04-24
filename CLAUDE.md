# Central Indiana Real Estate Agent Plugin

## What This Plugin Does

This plugin provides a comprehensive AI skill suite for residential real estate agents operating in Central Indiana within the MIBOR/BLC territory. It covers the full buying and selling lifecycle — from initial client consultations through closing — and is designed to serve multiple agents via personalized config files.

**18 skills + orchestrator — all phases complete (Phase 0–5).** Plugin follows standard Claude Code plugin conventions:
- **Skills** live in `skills/` (e.g., `skills/re-cma/SKILL.md`)
- **Commands** (slash commands) live in `commands/` (e.g., `commands/re-cma.md`)
- **Agents** live in `agents/` (e.g., `agents/orchestrator.md`)
- A SKILL.md stub for the orchestrator lives at `orchestrator/SKILL.md`.

---

## Config System

Every agent-specific detail lives in YAML config files — never hardcoded. The same skills serve any agent.

### Config Location
```
~/Skills/real-estate-plugin/config/[agent-slug]/
```

Each agent has up to 7 config files:
| File | Purpose |
|---|---|
| `agent-profile.yaml` | Identity, license, brokerage, voice/tone, methodology |
| `brand-kit.yaml` | Colors, fonts, logos, tagline, hashtags, compliance disclaimers |
| `vendor-network.yaml` | Preferred lenders, inspectors, title companies, contractors, etc. |
| `fee-structure.yaml` | Commission rates, fees, buyer agreement terms — SENSITIVE |
| `market-areas.yaml` | Counties, cities, neighborhoods, zip codes, farm areas |
| `email-templates.yaml` | Signature block, per-milestone email templates |
| `team-structure.yaml` | Team members, roles, TC contact, showing assistant |

Templates for all 7 files are in `~/Skills/real-estate-plugin/config/_template/`.

### Agent Identification Pattern

Agent identity is **entirely slug-based** (as of v0.6.0). There is no external registry. The slug is the kebab-case folder name under `config/` (e.g., `jane-smith-fc-tucker`).

**Resolution order for every skill:**

1. If the user provided a slug explicitly (e.g., `jane-smith-fc-tucker`), use it directly.
2. If a prior turn in this session already resolved a slug, reuse it.
3. If the user provided a name or email, list the existing `config/*/` folders and try to match by:
   - Kebab-casing the name and checking for an exact folder match.
   - Reading the `name.full` field in each `agent-profile.yaml` and fuzzy-matching.
   - Reading the `contact.email_primary` field in each `agent-profile.yaml` for email lookup.
4. If no match, direct the user to `/re-agent-setup` to create their config.

**Once the slug is resolved, load config files from `config/[slug]/`:**

```
config/jane-smith-fc-tucker/
├── agent-profile.yaml    # Always load first — establishes identity and voice
├── brand-kit.yaml        # Load for any output with branding
├── vendor-network.yaml   # Load when recommending vendors
├── fee-structure.yaml    # Load for net sheets, agreement discussions
├── market-areas.yaml     # Load for geographic context
├── email-templates.yaml  # Load for any client communication
└── team-structure.yaml   # Load when routing to team members
```

**Legacy field migration (v0.6.0):**
- When reading `market-areas.yaml`, if you encounter `farm_areas:`, treat it as `primary_focus_areas:`. If you encounter `secondary_areas:`, treat it as `secondary_coverage_areas:`. When next editing the file, rename the keys in-place and mention the upgrade to the user in one line.

**If agent not found:** Ask the user to run `/re-agent-setup` to create the agent config.

---

## Reference System

Shared Indiana-specific legal, market, and practice references live in:
```
~/Skills/real-estate-plugin/references/
```

| File | Contains |
|---|---|
| `indiana-agency-law.md` | IC 25-34.1-9-11, agency types, duties, limited agency rules |
| `indiana-disclosure-requirements.md` | IC 32-21-5-10, disclosure form requirements, what to disclose |
| `mibor-forms-checklist.md` | Complete MIBOR/IAR forms list with when each is used |
| `indiana-purchase-agreement-guide.md` | Clause-by-clause PA walkthrough, Indiana-specific norms |
| `central-indiana-market-context.md` | County breakdown, school districts, employers, commute patterns |
| `buyer-agreement-requirements.md` | Post-July 2024 written buyer agreement requirements |
| `real-estate-vocabulary.md` | Approved terminology, fair housing language, Indiana terms |
| `transaction-timeline-template.md` | Standard 30-45 day close timeline, common delays |
| `voice-enforcement.md` | Hard constraints every content skill must honor from `voice` config — emoji/exclamation rules, greeting/signoff verbatim, brokerage agnosticism, never-guess identity fields |

All skills should reference these files for Indiana-specific content rather than inventing general guidance. Any skill that generates client-facing content must point readers to `voice-enforcement.md` and implement the enforcement loop described there.

---

## Shared Templates

Presentation and document templates live in:
```
~/Skills/real-estate-plugin/templates/
```

| File | Used By |
|---|---|
| `seller-net-sheet.md` | re-cma, re-seller-consultation |
| `buyer-cost-estimate.md` | re-buyer-consultation |
| `listing-presentation.md` | re-seller-consultation |
| `buyer-presentation.md` | re-buyer-consultation |
| `open-house-sign-in.md` | re-open-house |
| `weekly-status-update.md` | re-transaction-manager, re-client-communication |
| `closing-gift-tracker.md` | re-closing-coordinator |
| `iar-form-150-purchase-agreement-2026.pdf` | re-offer-writer (Form 150 PDF generation) |

---

## Skill Catalog (18 Skills)

### Foundation
| Skill | Description |
|---|---|
| `re-agent-setup` | Onboard a new agent — creates all 7 local YAML config files at `config/[slug]/`. Alias: `/re-setup` |

### Core (Phase 1)
| Skill | Description |
|---|---|
| `re-disclosure-assistant` | Indiana disclosure compliance advisor — walks through IC 32-21-5-10 section by section |
| `re-client-communication` | On-brand email, text, call scripts, and status updates for any transaction stage |
| `re-neighborhood-research` | Local area expert report — schools, taxes, commutes, amenities for buyers |
| `re-market-update` | Monthly/quarterly market snapshots — median price, DOM, inventory, absorption rate |
| `re-news-briefing` | Personalized real estate news briefing from IBJ, Google News, and Indiana-specific feeds |

### Selling Process (Phase 2)
| Skill | Description |
|---|---|
| `re-seller-consultation` | Prepare seller consultations — goals discovery, listing presentation, pricing framework |
| `re-cma` | Comparative market analysis — comps, adjustments, pricing strategy, net sheet |
| `re-listing-prep` | Property prep guidance — staging, repairs (ROI-ranked), photography shot list |
| `re-listing-creation` | MLS listing content — BLC remarks (500-char), marketing description, social captions |
| `re-property-marketing` | Marketing materials — social series, email blast, print flyer, video scripts |
| `re-showing-coordinator` | Showing management — ShowingTime setup, feedback templates, buyer comparison worksheets |
| `re-open-house` | Open house lifecycle — promotion, sign-in, conversation starters, follow-up sequences |

### Buying Process (Phase 3)
| Skill | Description |
|---|---|
| `re-buyer-consultation` | Buyer consultations — needs discovery, agency explanation, buyer presentation |
| `re-offer-writer` | Write offers (buyer side) and review/present offers (seller side) |
| `re-negotiation-advisor` | Negotiation strategy and talking points for both buyer and seller situations |

### Transaction (Phase 4)
| Skill | Description |
|---|---|
| `re-transaction-manager` | Transaction coordination — deadlines, task checklists, Google Calendar integration |
| `re-closing-coordinator` | Closing preparation — final walkthrough, closing day checklist, post-closing follow-up |

---

## Orchestrator

The orchestrator lives at `agents/orchestrator.md` and is available via `/orchestrator` (see `commands/orchestrator.md`). It is **not** the default entry point — individual slash commands work independently without the orchestrator. Use the orchestrator when starting a new client engagement, running multi-skill workflows, or when the user doesn't know which skill to invoke.

A SKILL.md stub at `orchestrator/SKILL.md` provides a reference index of all workflows and skills for discovery purposes. Full orchestrator logic is in `agents/orchestrator.md` only.

The orchestrator uses the `real-estate-plugin:skill-name` prefix format in its frontmatter `skills:` list (e.g., `real-estate-plugin:re-cma`). All 18 skills are listed. `re-agent-setup` is included for new agent onboarding.

---

## Legal Disclaimer (MANDATORY)

**Every skill touching contracts, disclosures, fiduciary duties, or legal rights must include this disclaimer:**

> *This output is for guidance and informational purposes only. It does not constitute legal advice. Agents should consult their managing broker and/or a licensed Indiana real estate attorney for situation-specific guidance. Always comply with Indiana Real Estate Commission rules and your brokerage's policies.*

**Never:**
- Advise a client to conceal known material defects
- Recommend not getting pre-approval before offering
- Suggest skipping inspection on any purchase
- Give tax or legal advice beyond "consult a professional"
- Claim a CMA is equivalent to a licensed appraisal

---

## Plugin Directory Layout

```
real-estate-plugin/
├── .claude-plugin/plugin.json   # Plugin manifest
├── settings.json                # Plugin settings (no default agent)
├── skills/                      # All 18 skills (auto-discovered by plugin system)
│   ├── re-agent-setup/SKILL.md
│   ├── re-cma/SKILL.md
│   ├── re-buyer-consultation/SKILL.md
│   └── ... (18 total)
├── commands/                    # Slash commands (one per skill)
│   ├── re-agent-setup.md
│   ├── re-cma.md
│   └── ... (18 total)
├── agents/                      # Agent definitions
│   └── orchestrator.md
├── orchestrator/                # Orchestrator SKILL.md stub
│   └── SKILL.md
├── config/                      # Per-agent config files
│   ├── _template/
│   └── [agent-slug]/
├── references/                  # Shared Indiana-specific references
└── templates/                   # Shared document templates
```

---

## Skill Development Conventions

- **Step 1 of every skill:** "Load Agent Config" — read `agent-profile.yaml` + any other needed configs. If not found, direct to `re-agent-setup`. On read, transparently remap legacy field names (`farm_areas` → `primary_focus_areas`, `secondary_areas` → `secondary_coverage_areas`) and log a one-line notice to the user.
- **SKILL.md line limit:** 500 lines maximum. Extract heavy content to each skill's own `references/` subdirectory and link.
- **Skill location:** All skills live in `skills/[skill-name]/SKILL.md`
- **Command location:** All slash commands live in `commands/[skill-name].md`
- **Config paths:** Always use `~/Skills/real-estate-plugin/config/[slug]/[file].yaml`
- **Reference paths:** Always use `~/Skills/real-estate-plugin/references/[file].md`
- **Template paths:** Always use `~/Skills/real-estate-plugin/templates/[file].md`
- **Branding:** All output must use the agent's name, tagline, colors, and signature from config — never generic placeholders.
- **Brokerage agnosticism:** No skill may hardcode brokerage-specific rules, colors, fonts, slogans, or copy (@properties, KW, Compass, F.C. Tucker, C21, etc.). Brand values come exclusively from `brand-kit.yaml`. Training-knowledge pre-fills based on brokerage recognition are bugs.
- **Voice enforcement:** Any skill that generates client-facing or user-facing content must load `voice` from `agent-profile.yaml` and treat its fields as hard constraints. See `references/voice-enforcement.md` for the full contract (emoji/exclamation rules, greeting/sign-off verbatim, writing-sample anchor). Run a voice consistency check before shipping output; regenerate if any check fails.
- **Never-guess identity fields:** `name.pronouns`, `name.preferred`, and `contact.preferred_contact_method` are ask-only. Never infer them from other data. Blank / TODO is always better than a guess.
- **Fair housing:** All content must comply with federal Fair Housing Act and HUD language guidelines. See `references/real-estate-vocabulary.md`.

---

## Build Status

All phases complete as of 2026-03-31:

| Phase | Content | Status |
|---|---|---|
| Phase 0 | Plugin scaffold, config templates, references, templates, orchestrator stub | Complete |
| Phase 1 | re-disclosure-assistant, re-client-communication, re-neighborhood-research, re-market-update, re-news-briefing | Complete |
| Phase 2 | re-seller-consultation, re-cma, re-listing-prep, re-listing-creation, re-property-marketing, re-showing-coordinator, re-open-house | Complete |
| Phase 3 | re-buyer-consultation, re-offer-writer, re-negotiation-advisor | Complete |
| Phase 4 | re-transaction-manager, re-closing-coordinator | Complete |
| Phase 5 | Orchestrator finalization — agents/orchestrator.md, orchestrator/SKILL.md, examples, guide, tests | Complete |

---

## Scheduled Tasks (v2 Roadmap)

Scheduled tasks (weekly market pulls, daily deadline reminders, monthly anniversary alerts) are planned for v2. See `scheduled/README.md`.

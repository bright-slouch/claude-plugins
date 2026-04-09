# Central Indiana Real Estate Agent Plugin

A comprehensive AI skill suite for residential real estate agents in Central Indiana (MIBOR/BLC territory). Covers the full buying and selling lifecycle — from first client contact through closing — with full personalization for each agent.

---

## What This Plugin Does

18 skills covering every stage of a real estate transaction:

- **Set up your profile** — one-time config that personalizes every skill to your voice, brand, market areas, and vendor network
- **Win listings** — seller consultation prep, CMA, pricing strategy, net sheets
- **Prepare and market listings** — staging guidance, MLS content, social media campaigns, open house management
- **Serve buyers** — buyer consultations, neighborhood research, offer writing, comparison worksheets
- **Negotiate** — strategy memos, counter-offer talking points, multiple-offer analysis
- **Manage transactions** — deadline tracking, task checklists, weekly status updates
- **Close and beyond** — closing prep, post-closing follow-up, anniversary check-ins
- **Stay informed** — daily news briefings, monthly market reports, neighborhood research

Everything is calibrated to Indiana law, MIBOR forms, and Central Indiana geography.

---

## Who This Is For

Residential real estate agents who:
- Are licensed in Indiana and operate in the MIBOR/BLC market
- Want AI assistance that knows their voice, brand, and market areas
- Handle both buyer and seller sides
- Work solo or on a team of up to 5-6 members

---

## Installation

### Option A: Install via Claude Plugin Marketplace (recommended)
```
/plugin marketplace add alecmandla/claude-plugins
/plugin install real-estate-plugin
```

### Option B: Clone from GitHub
```
git clone https://github.com/alecmandla/claude-plugins.git
```
Then add the plugin directory in Claude Desktop → **Settings → Plugins**.

### First-Time Setup

1. **Set up your agent profile** — run the setup command:
   ```
   /re-agent-setup
   ```
   This walks you through creating your personalized config (takes 15-20 minutes for a full setup, less if you skip optional sections).

2. **Start using skills** — invoke any skill by slash command:
   ```
   /re-seller-consultation
   /re-cma
   /re-client-communication
   ```
   Or start the orchestrator and describe what you need in plain language.

3. **(Optional) Connect Monday.com** — if you manage multiple agents or want a centralized registry, set up the "Real Estate Agent Registry" board in Monday.com and add your `MONDAY_API_KEY` to `~/.zshrc`.

---

## Quick Start

**First session:**
```
Set up my agent profile
```
This runs `re-agent-setup` and walks you through every configuration section.

**Prepare for a listing appointment:**
```
Help me prepare for a listing appointment at 4521 Oak Creek Dr, Carmel — 4 bed, 2.5 bath, about 2,400 sq ft
```

**Draft client communication:**
```
Write an email to my buyers confirming we go under contract tomorrow on 8812 Maple Ridge Lane
```

**Get a news briefing:**
```
Give me today's Indiana real estate news briefing
```

**Run a CMA:**
```
I need a CMA for a 3/2 ranch in Plainfield, around 1,600 sq ft, built 2005
```

---

## Skill Reference

### Foundation
| Skill | What It Does |
|---|---|
| `re-agent-setup` | One-time setup — creates your agent profile, brand kit, vendor network, fee structure, market areas, email templates, and team structure |

### Core Skills
| Skill | What It Does |
|---|---|
| `re-disclosure-assistant` | Indiana disclosure compliance advisor — walks through Form 46234 section by section, flags lead paint requirements, explains what must and cannot be disclosed |
| `re-client-communication` | On-brand emails, texts, call scripts, and status updates in your voice — for any transaction stage |
| `re-neighborhood-research` | Buyer-ready local area report — schools, taxes, commutes, employers, HOAs, flood zones, amenities |
| `re-market-update` | Monthly/quarterly market snapshots — median price, days on market, inventory, absorption rate, YoY changes |
| `re-news-briefing` | Personalized daily/weekly news briefing from IBJ, IndyStar (via Google News), and local business sources |

### Selling Process
| Skill | What It Does |
|---|---|
| `re-seller-consultation` | Consultation prep — seller discovery questionnaire, listing presentation, agency explanation, pricing framework, timeline planning |
| `re-cma` | Comparative market analysis — comparable selection, adjustments, three pricing strategies, absorption rate, seller net sheet |
| `re-listing-prep` | Property preparation — room-by-room staging, ROI-ranked repairs, photography shot list, vendor coordination |
| `re-listing-creation` | MLS listing content — BLC remarks (500 char), extended description, social captions, fair housing compliance check |
| `re-property-marketing` | Full marketing package — social post series, email blast, print flyer, broker open invitation, video scripts |
| `re-showing-coordinator` | Showing management — ShowingTime instructions, feedback requests, seller activity reports, buyer tour prep, side-by-side comparisons |
| `re-open-house` | Open house lifecycle — 2-week promotion schedule, sign-in setup, conversation starters, 3-touch follow-up sequence |

### Buying Process
| Skill | What It Does |
|---|---|
| `re-buyer-consultation` | Buyer consultation prep — needs discovery, agency explanation, financing overview, buyer presentation |
| `re-offer-writer` | Write offers for buyers and review/present offers for sellers — includes contingency guidance and Indiana-specific terms |
| `re-negotiation-advisor` | Negotiation strategy and talking points — inspection response, multiple offers, price negotiations |

### Transaction Management
| Skill | What It Does |
|---|---|
| `re-transaction-manager` | Transaction coordination — deadline calendar, task checklists, party contacts, weekly status reports |
| `re-closing-coordinator` | Closing preparation — final walkthrough checklist, closing day agenda, post-closing follow-up plan |

---

## Configuration System

Each agent has a config folder at `config/[agent-slug]/` containing up to 7 YAML files:

| File | What's In It |
|---|---|
| `agent-profile.yaml` | Name, license #, brokerage, contact info, voice/tone settings, methodology |
| `brand-kit.yaml` | Colors, fonts, logo paths, tagline, hashtags, compliance disclaimers |
| `vendor-network.yaml` | Preferred lenders, title companies, inspectors, photographers, contractors |
| `fee-structure.yaml` | Commission rates, buyer agreement terms (sensitive — not shared with clients) |
| `market-areas.yaml` | Counties, cities, neighborhoods, school districts, farm areas |
| `email-templates.yaml` | Signature block, per-milestone email templates |
| `team-structure.yaml` | Team members, roles, TC, showing assistant |

Templates for all 7 files are in `config/_template/`. Run `re-agent-setup` to generate your personal config.

---

## Indiana-Specific References

Shared reference documents in `references/`:

- `indiana-agency-law.md` — IC 25-34.1-9-11, agency relationship types, duties
- `indiana-disclosure-requirements.md` — IC 32-21-5-10, Form 46234, what to disclose
- `mibor-forms-checklist.md` — Complete MIBOR/IAR forms list
- `indiana-purchase-agreement-guide.md` — Clause-by-clause PA walkthrough
- `central-indiana-market-context.md` — County breakdown, school districts, employers
- `buyer-agreement-requirements.md` — Post-July 2024 written buyer agreement rules
- `real-estate-vocabulary.md` — Approved terminology, fair housing language
- `transaction-timeline-template.md` — 30-45 day close timeline

---

## Important Disclaimer

This plugin provides guidance and informational assistance only. It does not constitute legal advice. Agents should consult their managing broker and/or a licensed Indiana real estate attorney for situation-specific guidance. CMAs are not appraisals. Always comply with Indiana Real Estate Commission rules and your brokerage's policies.

---

## Version

Current version: **0.1.0** — See `CHANGELOG.md` for version history.

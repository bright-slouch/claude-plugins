---
name: re-news-briefing
description: >-
  Personalized daily real estate news briefing. Fetches IBJ and Google News
  RSS feeds, de-duplicates headlines, categorizes stories, and formats a
  scannable morning briefing tailored to the agent's market areas. Optional:
  generate a social media post from the top story.
argument-hint: "[optional: focus area or 'full briefing']"
---

# News Briefing Skill

## Overview

`re-news-briefing` is your personalized morning news editor for Central Indiana real estate. It fetches live RSS feeds from IBJ and Google News, de-duplicates stories across sources, categorizes them by relevance type, and formats a scannable briefing tailored to the agent's specific farm areas and counties.

This skill goes beyond headlines — it adds local context, flags what's actionable for the agent's clients, and optionally drafts a social post from the most shareable story.

No browser automation or special MCP tools required. RSS feeds are plain HTTP/XML that any WebFetch call can retrieve.

---

## Persona

You are the agent's morning news editor. You know which stories affect their specific farm areas, which national trends are hitting Indiana, and which headlines their buyers and sellers need to know about. You curate rather than aggregate — cutting noise and surfacing what's actionable. You don't just summarize headlines; you add the local context that makes a story meaningful for a Central Indiana agent. A rate increase story becomes: "This affects buyers rate-locked above 7% — you may want to check in with anyone who went under contract in the last 60 days."

---

## When to Use This Skill

- Morning routine — before calls, appointments, or client outreach
- Preparing for a listing or buyer consultation (know the market narrative)
- Drafting a weekly client newsletter or social post calendar
- Monitoring for news that affects active transactions (rate moves, policy changes)
- Staying current on local development in farm areas

---

## Quick Start

```
Give me my morning briefing
```
```
What's happening in Hamilton County real estate today?
```
```
Full briefing with a social post for the top story
```
```
Week in review — what happened in Central Indiana real estate this week?
```
```
Any news relevant to my buyers who are rate shopping right now?
```

---

## Step-by-Step Workflow

### Step 1: Load Agent Config

Load these config files before fetching any feeds:

- `~/Skills/real-estate-plugin/config/[slug]/agent-profile.yaml` — agent name, tone preset, formality level, emoji preference
- `~/Skills/real-estate-plugin/config/[slug]/market-areas.yaml` — farm areas, counties, cities (used to build custom feed queries)
- `~/Skills/real-estate-plugin/config/[slug]/brand-kit.yaml` — hashtags, tagline (only needed if generating a social post)

If the agent config is not found, direct the user to run `/re-agent-setup` first.

If a slug is provided directly (e.g., `jane-smith-fc-tucker`), skip any registry lookup and load config files directly from `config/[slug]/`.

---

### Step 2: Build Feed List

Always include these four base feeds:

| Feed | URL |
|---|---|
| IBJ Real Estate | `https://www.ibj.com/topics/real-estate/feed` |
| IBJ Main | `https://www.ibj.com/feed` |
| Google News: Indianapolis RE | `https://news.google.com/rss/search?q=Indianapolis+real+estate&hl=en-US&gl=US&ceid=US:en` |
| Google News: Indiana Market | `https://news.google.com/rss/search?q=Indiana+housing+market&hl=en-US&gl=US&ceid=US:en` |

Then add custom Google News queries for the agent's farm areas from `market-areas.yaml`. For each farm area or city, build a query URL:

```
https://news.google.com/rss/search?q={CITY}+Indiana+real+estate&hl=en-US&gl=US&ceid=US:en
```

Examples:
- Farm area: "Carmel" → `https://news.google.com/rss/search?q=Carmel+Indiana+real+estate&hl=en-US&gl=US&ceid=US:en`
- Farm area: "Hamilton County" → `https://news.google.com/rss/search?q=Hamilton+County+Indiana+homes&hl=en-US&gl=US&ceid=US:en`

**Limit:** Add at most 3 custom farm area feeds. If the agent has more than 3 farm areas, prioritize by the order they appear in `market-areas.yaml` (primary farm area first).

Full feed reference with known working/non-working URLs: `~/Skills/real-estate-plugin/re-news-briefing/references/rss-feed-directory.md`

---

### Step 3: Fetch All Feeds

Use WebFetch to retrieve each RSS feed URL. RSS feeds return plain XML over HTTP — no authentication, no browser required.

For each feed, parse the XML to extract these fields per item:

| Field | RSS Tag | Notes |
|---|---|---|
| Title | `<title>` | Strip CDATA wrappers and HTML tags |
| Link | `<link>` | Destination URL |
| Summary | `<description>` | Strip HTML tags; first 2-3 sentences only |
| Published date | `<pubDate>` | RFC 2822 format |
| Source name | `<source>` or feed title | Used for attribution and dedup priority |

**Age filter:**
- Daily briefing: exclude items older than 48 hours
- Weekly digest: include items up to 7 days old

If a feed returns an HTTP error, is unreachable, or returns no parseable items, log the failure ("IBJ feed unavailable — skipping") and continue with remaining feeds. Never abort the entire briefing because one feed is down.

---

### Step 4: De-duplicate

After collecting all items, identify duplicate stories (the same news event covered by multiple sources).

**Dedup rule:** If two headlines share 5 or more consecutive words, treat them as the same story. Keep one item using this priority order:

1. IBJ Real Estate feed (highest authority for local Indiana RE)
2. IBJ Main feed
3. Google News aggregated feeds (any)

When keeping the authoritative item, you may augment its summary with context from the duplicate if the duplicate source added meaningful detail.

---

### Step 5: Categorize

Sort de-duplicated items into these categories. An item can belong to only one category — assign to the best fit:

| Category | What Belongs Here |
|---|---|
| **Market Conditions** | Interest rates, home prices, inventory levels, affordability, days on market, absorption rate |
| **Local Development** | New construction, commercial projects, zoning changes, subdivision announcements, infrastructure |
| **Regulatory / Legal** | NAR policy, CFPB rules, Indiana legislature, MIBOR policy changes, buyer agreement requirements |
| **Mortgage / Finance** | Rate announcements, lending program news, FHA/VA/USDA updates, buyer financing trends |
| **National RE News** | NAR statistics, Zillow/Redfin/CoreLogic data releases, broad national housing trends |
| **General Business** | IBJ business news that directly affects real estate — major employer announcements, economic development, population trends |

If an item doesn't clearly fit any category, use **General Business** as a catch-all or omit it if it has no real estate relevance.

---

### Step 6: Apply Agent Personalization

Before formatting, review each categorized item and:

1. **Tag farm area relevance** — if a story directly mentions the agent's counties, cities, or farm areas, mark it as locally relevant and move it to the top of its category section.
2. **Flag actionable items** — identify stories that suggest a specific outreach action:
   - Rate moves → reach out to rate-locked buyers or pre-approved clients
   - Inventory drops → reach out to waiting buyers about urgency
   - Local development → reach out to sellers in the affected area
   - Regulatory changes → brief active clients on any process changes
3. **Lead with local** — the most locally relevant stories should appear first within each section.

---

### Step 7: Format the Briefing

Use this exact structure. Adjust emoji usage based on the agent's formality level from `agent-profile.yaml` — omit emojis entirely if formality is 7 or higher.

```
## [emoji] Real Estate Briefing — [Day, Month DD, YYYY]
Prepared for [Agent First Name] [Agent Last Name] | [Brokerage Name]

---

### [emoji] Market Conditions

**[Headline]** — [Source], [Month DD]
[1-2 sentence summary]. [Local context sentence — what this means for the agent's buyers, sellers, or farm area specifically.]
[Actionable note if applicable: e.g., "Worth mentioning to buyers who are still shopping rates."]
[Full story: [URL]]

[Additional stories in same format — 2-4 per category max]

---

### [emoji] Local Development
[Stories]

---

### [emoji] Regulatory / Legal
[Stories]

---

### [emoji] Mortgage / Finance
[Stories]

---

### [emoji] National RE News
[Stories]

---

### [emoji] General Business
[Stories]

---

*[count] stories from [count] sources | Feeds fetched [time] | [any feeds that failed]*

---
*News content is sourced from third-party RSS feeds. [Agent Name] does not endorse or verify the accuracy of third-party reporting. Verify important market claims before sharing with clients.*
```

**Category omission rule:** If a category has zero stories after filtering, omit the entire section — do not include empty headers.

**Story count:** Aim for 8-15 total stories across all sections. If feeds return more, prioritize local and actionable stories.

---

### Step 8: Optional Social Post

If the agent requests a social media post (or if the argument is "full briefing with social"), identify the single most shareable story. Shareable criteria:
- Locally relevant to the agent's farm areas
- Positive or timely (not alarming or litigation-heavy)
- Contains a concrete data point or insight that would interest homeowners or buyers

Draft the post using the agent's brand voice from `agent-profile.yaml` and hashtags from `brand-kit.yaml`:

```
---
## Social Post Draft

**Platform:** [LinkedIn / Facebook / Instagram — recommend based on story type]

[Post text in agent's voice, 150-250 words for LinkedIn, 80-120 for Facebook/Instagram]

[Suggested hashtags from brand-kit.yaml, plus story-relevant tags]

[Optional: suggested image prompt if the story warrants a graphic]
```

Do not draft a social post that reproduces more than 15 words from the original article.

---

## Output Format Reference

See the exact structure above in Step 7. Key formatting rules:

- Each story: headline (linked), source + date, 1-2 sentence summary + local context, actionable note if warranted, link
- Emojis: use if agent formality < 7; omit if formality >= 7
- Footer: always include story/source count, fetch time, any feed failures
- Disclaimer: always include the third-party content disclaimer at the bottom

---

## Feed Failure Handling

If any individual feed fails (HTTP error, timeout, empty response, malformed XML):

1. Log the failure inline: `[IBJ Real Estate feed returned 503 — skipped]`
2. Continue fetching remaining feeds without interruption
3. If all Google News feeds succeed but both IBJ feeds fail, note this prominently: "IBJ feeds unavailable — briefing based on Google News aggregation only. For IBJ coverage, visit ibj.com directly."
4. If all feeds fail: inform the agent and suggest trying again in a few minutes. Do not fabricate stories.
5. Partial briefings are valid — 2 stories from one working feed is better than no briefing.

---

## Briefing Frequency Guidance

| Mode | Best For | Age Filter | Feed Set |
|---|---|---|---|
| Daily briefing | Active agents, morning routine | 48 hours | All feeds |
| Focused briefing | Pre-appointment prep | 48 hours | Relevant category + farm area feeds only |
| Weekly digest | Lower-frequency agents, client newsletters | 7 days | All feeds |
| Breaking news check | Reactive — after hearing about a market event | 24 hours | All feeds, fast scan |

For weekly digests, group stories by category and add a brief "week in review" sentence at the top of each section summarizing the theme.

---

## What NOT to Do

- **Never fabricate news stories** — if feeds are empty or all fail, say so. Do not invent headlines or fill gaps with general real estate knowledge presented as current news.
- **Never include stories not from the fetched feeds** — all items must be sourced from a feed retrieved in this session. Do not pull from memory or training data to fill out a thin briefing.
- **Never omit source attribution** — every story must show its source (IBJ, Axios Indianapolis, IndyStar via Google News, etc.) and publication date. Anonymous sourcing is not acceptable.
- **Never reproduce more than 15 words verbatim from any article** — summarize and contextualize; do not quote extensively.
- **Never include stories older than the age filter** — a 3-day-old story is not "news" in a daily briefing.
- **Never use fair-housing-violating language** — even if the source article uses language that describes neighborhoods by protected characteristics, do not reproduce or paraphrase it. Reference `~/Skills/real-estate-plugin/references/real-estate-vocabulary.md` for approved terms.
- **Never present a Google News aggregated story as having a single authoritative source** — Google News pulls from many outlets; acknowledge the aggregated nature when the direct source is unclear.
- **Never generate a social post from a story involving litigation, discrimination complaints, or regulatory violations** — these are not shareable.
- **Never claim a CMA or pricing data from a news article is equivalent to a licensed appraisal** — if referencing price data from Zillow, Redfin, or similar, note it as "reported by [source]" not as authoritative valuation.

---

## Integration Points

### Pairs Well With
- `re-market-update` — for a full morning briefing, run news briefing first (current events), then re-market-update (local stats). Together they give the agent both narrative context and hard numbers.
- `re-client-communication` — social post output from this skill can feed directly into re-client-communication to become a newsletter item or social caption with full agent branding.
- `re-property-marketing` — a relevant local development story can become a marketing hook ("Did you see the new [development] announced for [neighborhood]? Here's what it means for home values...").
- `re-seller-consultation` — use current market condition stories to support pricing conversations with sellers.

### Config Files Used
- `agent-profile.yaml` — agent name, tone, formality, emoji preference
- `market-areas.yaml` — farm areas and counties for personalized feed queries
- `brand-kit.yaml` — hashtags and tagline (social post only)

### Reference Files
- `~/Skills/real-estate-plugin/re-news-briefing/references/rss-feed-directory.md` — full feed directory with working/non-working status and parse notes

---

## Example Prompts

See `~/Skills/real-estate-plugin/re-news-briefing/examples/example-prompts.md` for 6 detailed scenarios.

# Example Prompts — re-news-briefing

Six scenarios showing how different agents use the news briefing skill.

---

## Scenario 1: Daily Morning Briefing — Hamilton County Agent

**Agent:** Tom Garrett, Keller Williams Indy Metro North. Farms Hamilton County broadly (Carmel, Fishers, Noblesville, Westfield). Runs his briefing every weekday morning before his 9am call block.

**Prompt:**
```
Morning briefing
```

**What the skill does:**

1. Loads `agent-profile.yaml` (Tom Garrett, professional-friendly tone, formality 5/10, emojis OK) and `market-areas.yaml` (farm areas: Hamilton County, Carmel, Fishers).
2. Builds feed list: 4 base feeds + 3 custom farm area feeds (Hamilton County, Carmel, Fishers).
3. Fetches all 7 feeds, parses items published within the last 48 hours.
4. De-duplicates across feeds; keeps IBJ items over Google News duplicates.
5. Categorizes: finds 3 Market Conditions stories, 2 Local Development (Carmel mixed-use announcement, Fishers tech campus), 1 Regulatory (MIBOR policy update), 2 Mortgage/Finance.
6. Tags the Carmel and Fishers stories as locally relevant and moves them to the top of their sections.
7. Formats the briefing with emojis (formality 5), leads with local stories.

**Expected output structure:**
```
## 🗞 Real Estate Briefing — Monday, March 30, 2026
Prepared for Tom Garrett | Keller Williams Indy Metro North

### 📊 Market Conditions
**[Rate story headline]** — [Source], March 29
...

### 🏗 Local Development
**[Carmel mixed-use development story]** — IBJ, March 30
[Summary + context: "This is in your Carmel farm area — worth mentioning to sellers..."]
...

### ⚖️ Regulatory / Legal
...

### 💰 Mortgage / Finance
...

---
*11 stories from 5 sources | Feeds fetched 8:47am | All feeds loaded successfully*

*News content is sourced from third-party RSS feeds...*
```

---

## Scenario 2: Hamilton County Focus Briefing

**Agent:** Same Tom Garrett. Has a listing appointment in Noblesville at 2pm and wants only Hamilton County-relevant stories plus anything about rates before he walks in.

**Prompt:**
```
Give me a focused briefing — just Hamilton County news and anything about interest rates. Listing appointment today.
```

**What the skill does:**

1. Loads config as normal.
2. Fetches full feed set but applies a focus filter before formatting.
3. Includes only: items that mention Hamilton County, Carmel, Fishers, Noblesville, or Westfield by name + all Mortgage/Finance category items + all Regulatory items affecting buyers or sellers.
4. Excludes: national RE news with no Indiana angle, General Business items, unrelated local development.
5. Formats a shorter, tighter briefing — likely 5-7 stories instead of the full 10-15.
6. Adds a pre-appointment note: "For your Noblesville appointment: [relevant local context]."

**Expected output:**
A shorter briefing with a section order that puts local Hamilton County stories first, followed by rate/finance news. Clear labeling that this is a focused view, not the full briefing.

---

## Scenario 3: Luxury Market Briefing

**Agent:** Diana Park, Sotheby's International Realty. Farms high-end Carmel (homes $800K+) and Zionsville (homes $1M+). Less interested in first-time buyer affordability news; very interested in luxury market trends, high-end development, and affluent buyer demand signals.

**Prompt:**
```
Luxury market briefing for Carmel and Zionsville
```

**What the skill does:**

1. Loads `agent-profile.yaml` (Diana Park, luxury-polished tone, formality 8/10, no emojis) and `market-areas.yaml` (farm areas: Carmel luxury, Zionsville).
2. Builds feed list with Carmel and Zionsville custom feeds.
3. Applies a luxury filter after categorization:
   - Elevates: stories about $500K+ market segments, luxury inventory, affluent buyer trends, high-end construction, premium neighborhood development
   - De-emphasizes: first-time buyer affordability stories, entry-level rate sensitivity (still included but flagged as lower priority)
4. Formats without emojis (formality 8). Uses more polished language in the local context notes.

**Expected output:**
Formal layout, no emojis. Any rate news framed around the $1M+ cash-heavy buyer segment ("luxury buyers in your price range are less rate-sensitive, but this signals broader market sentiment"). Local development stories about Carmel or Zionsville featured prominently.

---

## Scenario 4: First-Time Buyer News Focus

**Agent:** Marcus Webb, F.C. Tucker. Specializes in first-time buyers across Marion County and southern Hamilton County. Needs to stay on top of rate news and affordability programs.

**Prompt:**
```
What's happening with rates and affordability today? I have three first-time buyer clients who are hesitating.
```

**What the skill does:**

1. Loads Marcus's config (casual-warm tone, formality 4/10, emojis OK).
2. Fetches full feed set.
3. Applies a first-time buyer filter: elevates Mortgage/Finance and Market Conditions stories. Specifically flags:
   - Any rate movement (up or down)
   - FHA/VA/USDA program updates
   - Indiana Housing and Community Development Authority (IHCDA) down payment assistance news
   - Affordability index changes
   - Stories about buyer hesitation or confidence surveys
4. For each rate or affordability story, adds explicit client-facing context: "For hesitating buyers: [specific talking point about why now vs. waiting]."

**Expected output:**
Mortgage/Finance and Market Conditions sections appear first, expanded. Includes a brief "Talking points for hesitating buyers" note at the end of the relevant sections — specific language Marcus can use on his calls today.

---

## Scenario 5: Investment Property News Briefing

**Agent:** Priya Nair, RE/MAX Realty Group. Works with residential investors — buy-and-hold rentals, small multi-family, house hacking. Wants to monitor rental market trends, investor activity, and any commercial crossover news relevant to her clients.

**Prompt:**
```
Investment property news — any rental market or investor activity stories this week?
```

**What the skill does:**

1. Loads Priya's config. Her `market-areas.yaml` includes Marion County and Hendricks County; no specific farm areas for this briefing.
2. Fetches full feed set.
3. Applies investment property filter after categorization:
   - Elevates: rental vacancy rate stories, rent growth/decline data, investor purchase volume, cap rate trends, multi-family construction news, short-term rental regulation
   - Flags as relevant: any zoning or regulatory news that affects rental properties, employer growth/contraction news (affects rental demand), national investor activity data
4. Adds investor-specific context to each story: "For your buy-and-hold clients: [what this means for rental yield / property values]."

**Expected output:**
A briefing organized around investor decision-making. National RE News section may be expanded if it contains investor-relevant data (e.g., CoreLogic investor purchase share data). Local Development section highlights anything affecting rental supply.

---

## Scenario 6: Week-in-Review Digest

**Agent:** Sarah Chen, Carpenter Realtors. Runs a weekly client newsletter every Friday. Needs a week-in-review briefing to source content for the newsletter.

**Prompt:**
```
Week in review — what happened in Central Indiana real estate this week? I'm writing my Friday newsletter.
```

**What the skill does:**

1. Loads Sarah's config (professional-friendly, formality 6/10, emojis OK).
2. Fetches full feed set with 7-day age filter instead of 48-hour filter.
3. Collects more stories than a daily briefing — may surface 20-30 items before dedup.
4. De-duplicates more aggressively: for multi-day stories (e.g., an ongoing development announcement covered over three days), keep the most recent/complete article only.
5. Adds a "Week in Review" summary sentence at the top of each category section: a single sentence synthesizing the category's overall theme for the week.
6. Formats for newsletter sourcing: slightly longer summaries (2-3 sentences) since Sarah is pulling content, not just scanning.
7. Social post option: drafts a Friday wrap-up post for Facebook/Instagram with the week's top theme.

**Expected output:**
```
## 🗞 Real Estate Week in Review — Week of March 24-30, 2026
Prepared for Sarah Chen | Carpenter Realtors

### 📊 Market Conditions
*This week: Interest rate volatility dominated the conversation as the Fed signaled a potential pause on cuts.*

**[Story 1]** — [Source], March 28
...
**[Story 2]** — [Source], March 26
...

[4-5 stories per section]

---
## Social Post Draft (Friday Wrap-Up)

**Platform:** Facebook / Instagram
...
```

**Newsletter sourcing note:** For each story, the summary is slightly longer than the daily briefing to give Sarah enough material to paraphrase for her newsletter without needing to read every article in full.

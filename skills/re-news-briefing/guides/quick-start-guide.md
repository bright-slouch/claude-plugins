# Quick Start Guide — re-news-briefing

**5-minute overview for new users**

---

## What This Skill Does

`re-news-briefing` gives you a personalized morning news briefing for Central Indiana real estate — every weekday in under 2 minutes.

It fetches live headlines from IBJ (Indianapolis Business Journal) and Google News, removes duplicates, categorizes stories, and formats a scannable briefing with local context added. You get headlines that are actually relevant to your farm areas, not a fire hose of generic real estate news.

Optional: generate a ready-to-post social media caption from the top story.

---

## How RSS Fetch Works (No Special Tools Required)

This skill uses RSS feeds — a standard, openly available format that news sites publish for syndication. RSS is just XML delivered over plain HTTP. No authentication, no browser required, no special API keys.

When you run the skill, it fetches each feed URL with a standard web request, parses the XML, and extracts the headlines. This is the same technology that powers podcast apps, email newsletter tools, and news readers. It works reliably and fast.

**What this means for you:** You don't need to set up any integrations or connect any accounts. The skill works immediately after your agent config is set up.

---

## How market-areas.yaml Personalizes Your Feed List

The skill reads your `config/[slug]/market-areas.yaml` file to find your farm areas and counties. It then builds custom Google News search queries for each of your primary farm areas.

**Example:** If your `market-areas.yaml` lists Carmel and Westfield as farm areas, the skill automatically adds:
- `https://news.google.com/rss/search?q=Carmel+Indiana+real+estate&...`
- `https://news.google.com/rss/search?q=Westfield+Indiana+housing&...`

This means you'll automatically see news about your specific neighborhoods and communities — not just generic Indianapolis news.

**Max 3 custom feeds are added** (to keep the briefing focused). If you have more than 3 farm areas, the skill prioritizes them in the order they appear in your config.

To update your farm areas, edit your `market-areas.yaml` or run `/re-agent-setup` in update mode.

---

## Focused Briefing vs. Full Briefing

### Full Briefing (default)
Run with no arguments or say "morning briefing" / "full briefing." You'll get:
- All 6 story categories (Market Conditions, Local Development, Regulatory, Mortgage/Finance, National RE News, General Business)
- 8-15 stories total
- Emojis and formatting adapted to your tone settings

### Focused Briefing
Add context to narrow the scope:
- `"Hamilton County news and rates only"` — just your farm area plus mortgage news
- `"Luxury market news"` — de-prioritizes first-time buyer affordability, elevates premium segment
- `"Investment property news"` — filters for rental market and investor-relevant stories
- `"Anything affecting first-time buyers today"` — elevates rate, affordability, and program news

Focused briefings are shorter but still pull from all feeds — they just filter what appears in the output.

### Weekly Digest
Say "week in review" or "Friday digest." Changes the age filter from 48 hours to 7 days and adds a summary sentence to each category section. Useful for Friday client newsletters.

---

## The Social Post Option

At the end of any briefing, you can ask for a social post draft:

- Include in your original prompt: `"...and draft a social post for the top story"`
- Or after reading the briefing: `"Draft a LinkedIn post from the [category] story"`

The skill picks the most shareable story (locally relevant, positive angle, concrete data point) and writes a post in your brand voice using your hashtags from `brand-kit.yaml`.

**One important rule:** The skill will not draft a social post from stories involving litigation, regulatory violations, or discrimination complaints. For those stories, you'll see a note explaining why.

---

## Five Things to Know

1. **IBJ is the primary source.** When IBJ and Google News both cover the same story, the skill keeps the IBJ version as more authoritative for Indiana coverage.

2. **Stories older than 48 hours are filtered out** in daily briefings. If you run the briefing in the afternoon and don't see a story you heard about in the morning, it may have been cut. Use the weekly digest mode to look back further.

3. **If a feed is down, the briefing still runs.** The skill notes any failed feeds at the bottom and continues with what it can retrieve. A partial briefing from working feeds is always better than no briefing.

4. **IndyStar stories still appear here.** IndyStar blocks direct scraping, but their articles are aggregated through Google News and will surface in your briefing from that path.

5. **The "local context" additions are the value.** You could read headlines yourself. What makes this skill useful is the 1-2 sentences after each headline explaining what the story means for your specific farm area, your buyers, or your sellers.

---

## Typical Output Length

| Mode | Stories | Read time |
|---|---|---|
| Daily full briefing | 8–15 stories | 3–5 minutes |
| Focused briefing | 4–8 stories | 1–3 minutes |
| Weekly digest | 15–25 stories | 8–12 minutes |

---

## Getting Started

1. Make sure your agent config exists — run `/re-agent-setup` if you haven't already.
2. Try: `Give me my morning briefing`
3. For a focused brief before an appointment: `Quick briefing on [city/topic] before my 2pm`
4. For a social post: `Morning briefing with a social post for the top story`

---

## Pairing With Other Skills

- **`re-market-update`** — Run after the news briefing for the statistical side. News briefing gives you narrative context; re-market-update gives you the hard numbers (median price, days on market, inventory). Together they make a complete market picture.
- **`re-client-communication`** — Take a story from the briefing and ask re-client-communication to draft an email or text to specific clients based on it.
- **`re-seller-consultation`** or **`re-buyer-consultation`** — Use current market stories from the briefing to support your talking points at appointments.

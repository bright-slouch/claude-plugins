# RSS Feed Directory — Central Indiana Real Estate News Briefing

Last verified: March 2026

This file is the authoritative reference for all RSS feeds used by `re-news-briefing`. Update this file when feed status changes, new feeds are discovered, or query patterns are refined.

---

## Confirmed Working Feeds

### IBJ Real Estate
- **URL:** `https://www.ibj.com/topics/real-estate/feed`
- **Format:** RSS 2.0
- **Update frequency:** Hourly
- **Content:** Indianapolis Business Journal real estate section. Primary source for local commercial, residential, and development coverage. High signal-to-noise ratio for Central Indiana RE.
- **Best for:** Local development stories, major transaction news, market trend features
- **Notes:** Requires no authentication. Returns standard RSS 2.0 with `<item>` elements. Author field present on bylined articles.

### IBJ Main Feed
- **URL:** `https://www.ibj.com/feed`
- **Format:** RSS 2.0
- **Update frequency:** Hourly
- **Content:** All IBJ sections — broader business news beyond real estate. Filter for RE-relevant items (employer relocations, economic development, infrastructure) when building the briefing.
- **Best for:** General Business category stories; stories about major employers that affect housing demand
- **Notes:** Higher volume than the RE-specific feed. Apply relevance filtering before including items.

### Google News: Indianapolis Real Estate
- **URL:** `https://news.google.com/rss/search?q=Indianapolis+real+estate&hl=en-US&gl=US&ceid=US:en`
- **Format:** RSS 2.0 (Google News format)
- **Update frequency:** Near real-time (reflects Google News indexing)
- **Aggregates from:** IndyStar, Axios Indianapolis, WRTV, WTHR, Realtor.com, Zillow Blog, national outlets covering Indiana stories
- **Best for:** Broad Indianapolis RE coverage; surfaces IndyStar stories that block direct scraping
- **Notes:** Titles may be wrapped in CDATA. The `<source>` tag identifies the originating publication. Descriptions are short summaries, not full article text. URLs are Google redirect URLs — the actual article URL is embedded.

### Google News: Indiana Housing Market
- **URL:** `https://news.google.com/rss/search?q=Indiana+housing+market&hl=en-US&gl=US&ceid=US:en`
- **Format:** RSS 2.0 (Google News format)
- **Update frequency:** Near real-time
- **Aggregates from:** Indiana state-level outlets, national outlets covering Indiana housing data
- **Best for:** State-level inventory, affordability, and market trend stories; distinguishes from hyperlocal Indianapolis stories
- **Notes:** Same parse logic as the Indianapolis RE feed. May overlap with Indianapolis RE feed — apply dedup logic.

---

## Custom Query Pattern (Google News)

To generate a personalized feed for a specific farm area or city, use this URL template:

```
https://news.google.com/rss/search?q={QUERY}&hl=en-US&gl=US&ceid=US:en
```

URL-encode spaces as `+`. Special characters should be percent-encoded.

### Example Queries for Central Indiana Farm Areas

| Farm Area / City | Query Parameter | Full URL |
|---|---|---|
| Carmel | `Carmel+Indiana+real+estate` | `https://news.google.com/rss/search?q=Carmel+Indiana+real+estate&hl=en-US&gl=US&ceid=US:en` |
| Hamilton County | `Hamilton+County+Indiana+homes` | `https://news.google.com/rss/search?q=Hamilton+County+Indiana+homes&hl=en-US&gl=US&ceid=US:en` |
| Westfield | `Westfield+Indiana+housing` | `https://news.google.com/rss/search?q=Westfield+Indiana+housing&hl=en-US&gl=US&ceid=US:en` |
| Noblesville | `Noblesville+Indiana+homes` | `https://news.google.com/rss/search?q=Noblesville+Indiana+homes&hl=en-US&gl=US&ceid=US:en` |
| Fishers | `Fishers+Indiana+real+estate` | `https://news.google.com/rss/search?q=Fishers+Indiana+real+estate&hl=en-US&gl=US&ceid=US:en` |
| Zionsville | `Zionsville+Indiana+homes` | `https://news.google.com/rss/search?q=Zionsville+Indiana+homes&hl=en-US&gl=US&ceid=US:en` |
| Brownsburg | `Brownsburg+Indiana+real+estate` | `https://news.google.com/rss/search?q=Brownsburg+Indiana+real+estate&hl=en-US&gl=US&ceid=US:en` |
| Greenwood | `Greenwood+Indiana+housing` | `https://news.google.com/rss/search?q=Greenwood+Indiana+housing&hl=en-US&gl=US&ceid=US:en` |
| Avon | `Avon+Indiana+homes` | `https://news.google.com/rss/search?q=Avon+Indiana+homes&hl=en-US&gl=US&ceid=US:en` |
| Plainfield | `Plainfield+Indiana+real+estate` | `https://news.google.com/rss/search?q=Plainfield+Indiana+real+estate&hl=en-US&gl=US&ceid=US:en` |
| Geist | `Geist+Indiana+homes` | `https://news.google.com/rss/search?q=Geist+Indiana+homes&hl=en-US&gl=US&ceid=US:en` |
| Lawrence | `Lawrence+Indiana+real+estate` | `https://news.google.com/rss/search?q=Lawrence+Indiana+real+estate&hl=en-US&gl=US&ceid=US:en` |
| Greenfield | `Greenfield+Indiana+housing` | `https://news.google.com/rss/search?q=Greenfield+Indiana+housing&hl=en-US&gl=US&ceid=US:en` |
| Franklin | `Franklin+Indiana+homes` | `https://news.google.com/rss/search?q=Franklin+Indiana+homes&hl=en-US&gl=US&ceid=US:en` |

**Query construction tips:**
- Adding `Indiana` to the query avoids confusion with same-name cities in other states (e.g., "Carmel California")
- Use `homes` or `housing` for residential-focused results; use `real+estate` for broader commercial/residential mix
- Hamilton County as a county-level query captures Carmel, Fishers, Noblesville, and Westfield together

---

## Known Non-Working or Low-Value Feeds

### IndyStar (direct)
- **Status:** Blocks direct RSS/scraping
- **Workaround:** IndyStar stories appear in the Google News Indianapolis RE aggregated feed. Do not attempt to fetch `indystar.com` feeds directly.

### Inman News
- **Status:** 403 Forbidden (paywalled)
- **Notes:** Premium real estate industry trade publication. No free RSS access. Not available for this skill.

### HousingWire
- **Status:** 403 Forbidden (paywalled)
- **Notes:** National mortgage and housing industry trade publication. No free RSS access. Not available for this skill.

### Fox59 (WXIN)
- **Status:** Feed works technically but low RE signal
- **Notes:** General Indianapolis local news TV station. Very low proportion of real estate relevant content. Not included in base feed set due to noise.

### Realtor.com / NAR (direct RSS)
- **Status:** Limited availability; stories appear via Google News aggregation
- **Notes:** National RE content surfaces through Google News feeds. Prefer the aggregated path.

---

## XML Parse Notes

### CDATA Handling
Google News RSS wraps `<title>` and `<description>` in CDATA blocks:
```xml
<title><![CDATA[Home prices rise 4.2% in Indianapolis metro]]></title>
```
Strip the CDATA wrapper before displaying. Extract the inner text only.

### HTML in Descriptions
`<description>` fields often contain embedded HTML tags (`<a>`, `<b>`, `<br>`). Strip all HTML tags and render as plain text for the briefing summary.

### Publication Date Format
All feeds use RFC 2822 date format:
```
Mon, 30 Mar 2026 09:15:00 GMT
```
Parse and display as: `March 30` (for same-year items) or `March 30, 2025` (for prior-year items in weekly digest).

### Google News Source Attribution
The originating publication is available in two places in Google News RSS items:
1. The `<source url="...">` tag: `<source url="https://www.indystar.com">IndyStar</source>`
2. Embedded at the end of the `<title>` field: `"Home prices up 4% — IndyStar"`

Use the `<source>` tag when present. Fall back to parsing the title if not present.

### Google News Redirect URLs
Links in Google News RSS are redirect URLs (beginning with `news.google.com/rss/articles/...`). These redirect to the actual article. Display the redirect URL as-is; readers can follow it to the original article. Do not attempt to resolve redirects programmatically.

### IBJ Article URLs
IBJ links are direct article URLs. No redirect resolution needed.

---

## Feed Priority for Deduplication

When the same story appears in multiple feeds, keep the item from the highest-priority source:

1. IBJ Real Estate (highest — primary local source)
2. IBJ Main
3. Google News Indianapolis RE
4. Google News Indiana Market
5. Custom Google News farm area feeds (lowest — most likely to surface the same stories as the above)

---

## Maintenance Notes

When testing a new RSS feed URL:
1. Fetch the URL with WebFetch
2. Confirm it returns XML with `<rss>` or `<feed>` root element
3. Confirm `<item>` or `<entry>` elements are present with title, link, and pubDate
4. Check that recent items (within 48 hours) are present
5. If confirmed working, add to this directory with status "Confirmed Working"
6. If returning errors, add to "Known Non-Working" section with error code and date tested

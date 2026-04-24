# News Source Directory — Central Indiana Real Estate News Briefing

Last verified: April 2026

This file is the authoritative reference for all news sources used by `re-news-briefing`. The primary retrieval method is **WebSearch**, not RSS feeds. RSS feeds are documented below for reference but are currently blocked by the network egress proxy.

---

## Primary Method: WebSearch

WebSearch is the working method for retrieving news. It can surface articles from IBJ, Axios, WTHR, Zillow, and other sources even when their domains are blocked for direct WebFetch access.

### Base Search Queries (always run)

| Search | Query Template | Allowed Domains |
|---|---|---|
| Indianapolis RE News | `Indianapolis real estate news [month] [year]` | `ibj.com`, `axios.com`, `wthr.com`, `wrtv.com` |
| Indiana Housing Market | `Indiana housing market news [month] [year]` | *(none — cast wide)* |
| Mortgage / Rates | `Indiana mortgage rates housing [month] [year]` | *(none — cast wide)* |

### Farm Area Search Pattern

For each farm area from `market-areas.yaml`:
```
[City/County] Indiana real estate [month] [year]
```

Limit: 3 farm area searches max. Prioritize by order in config.

### Source Quality Tiers (for dedup priority)

| Tier | Sources | Notes |
|---|---|---|
| 1 (highest) | IBJ (ibj.com) | Primary local business/RE authority for Central Indiana |
| 2 | Axios Indianapolis, MIBOR/IAR official | High-quality local or industry sources |
| 3 | IndyStar, WTHR, WRTV | Local news outlets; IndyStar blocked for direct fetch but surfaces in search |
| 4 | Zillow Blog, Realtor.com, Redfin | National platforms with Indiana-specific data |
| 5 (lowest) | Agent blogs, smaller local sites | Use only when no higher-tier source covers the story |

---

## Domain Accessibility Status (April 2026)

### Accessible via WebSearch (articles appear in search results)

| Domain | Content | Notes |
|---|---|---|
| ibj.com | Indianapolis Business Journal | Best local RE source. Full articles may be paywalled, but titles + snippets are rich enough for briefing summaries. |
| axios.com | Axios Indianapolis | Good for local development, economic news |
| wthr.com | WTHR (NBC Indianapolis) | Local TV news; covers major RE stories |
| wrtv.com | WRTV (ABC Indianapolis) | Local TV news |
| zillow.com | Zillow market data/blog | National with Indiana-specific data pages |
| realtor.com | Realtor.com market data | National with Indiana-specific data |
| caraconde.com | Local agent blog | Detailed Central Indiana market analysis |
| indyhomes.com | Local market stats | Good for stats, less for breaking news |

### Blocked or Restricted

| Domain | Status | Workaround |
|---|---|---|
| ibj.com | Blocked by WebFetch egress proxy | Use WebSearch — IBJ articles appear in search results with titles and snippets |
| news.google.com | Blocked by WebFetch egress proxy | Not needed — WebSearch replaces Google News RSS entirely |
| indystar.com | Blocked by web crawler (400 error) | Stories may surface in general WebSearch without domain filter; do not include in `allowed_domains` |
| inman.com | Paywalled (403) | Not available through any method |
| housingwire.com | Paywalled (403) | Not available through any method |

### Low-Value Sources (excluded from base searches)

| Domain | Reason |
|---|---|
| fox59.com | Very low proportion of RE-relevant content |
| wishtv.com | Rarely covers RE-specific stories |

---

## Legacy RSS Feed URLs (Currently Non-Functional)

These RSS feeds were the original data source but are all blocked by the network egress proxy. They are documented here for reference only — do not attempt to use WebFetch with these URLs.

| Feed | URL | Status |
|---|---|---|
| IBJ Real Estate | `https://www.ibj.com/topics/real-estate/feed` | Blocked (egress proxy) |
| IBJ Main | `https://www.ibj.com/feed` | Blocked (egress proxy) |
| Google News: Indianapolis RE | `https://news.google.com/rss/search?q=Indianapolis+real+estate&hl=en-US&gl=US&ceid=US:en` | Blocked (egress proxy) |
| Google News: Indiana Market | `https://news.google.com/rss/search?q=Indiana+housing+market&hl=en-US&gl=US&ceid=US:en` | Blocked (egress proxy) |

If the egress proxy restrictions change in the future, these feeds could be re-enabled as a supplementary source alongside WebSearch.

---

## Maintenance Notes

When testing a new news source:
1. Run a WebSearch query with `allowed_domains` set to the target domain
2. Confirm results appear with titles, URLs, and useful snippets
3. If results appear, add to the "Accessible via WebSearch" table above
4. If no results appear, try without domain filtering to see if the source surfaces organically
5. Update this directory with findings and date tested

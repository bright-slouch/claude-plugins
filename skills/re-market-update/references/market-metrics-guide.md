# Market Metrics Guide

> Reference document for `re-market-update`. Contains metric formulas, data
> source mapping, Central Indiana county market profiles, seasonal patterns, and
> new construction impact notes. Not for direct client output — use as working
> context when building reports.

---

## Metric Formulas

### Months of Supply (Absorption Rate)

```
Months of Supply = Active Listings (end of period) ÷ Average Monthly Closed Sales
```

**Inputs:**
- Active listings: point-in-time count at end of reporting month
- Average monthly closed sales: use 3-month trailing average to smooth
  volatility (e.g., for March report: average of Jan + Feb + Mar closed sales)

**Single-month method (less stable but usable):**
```
Months of Supply = Active Listings ÷ Closed Sales (current month)
```

**Interpretation thresholds:**

| Result | Condition |
|---|---|
| < 2.0 months | Strong seller's market |
| 2.0 – 3.0 months | Seller's market |
| 3.0 – 6.0 months | Balanced market |
| 6.0 – 9.0 months | Buyer's market |
| > 9.0 months | Strong buyer's market |

---

### List-to-Sale Price Ratio

```
L/S Ratio = (Average Sale Price ÷ Average List Price) × 100
```

**Example:** Average list price $425,000, average sale price $432,500
→ L/S Ratio = (432,500 ÷ 425,000) × 100 = 101.8%

**Interpretation:**
- Above 100%: homes selling over asking; multiple offers expected
- 99–100%: homes selling at or just under asking; moderate competition
- 97–99%: typical negotiated discount; balanced to buyer-leaning
- Below 97%: price reductions common; buyer leverage present

**Note:** MIBOR reports this metric directly in monthly press releases as
"sale-to-list price ratio." Redfin also reports it in city-level summaries.

---

### Year-over-Year (YoY) Percentage Change

```
YoY % Change = ((Current Value − Prior Year Same Period Value) ÷ Prior Year Value) × 100
```

**Example:** Median price Feb 2026 = $385,000; Feb 2025 = $362,000
→ YoY = ((385,000 − 362,000) ÷ 362,000) × 100 = +6.4%

Apply YoY calculation to: median sale price, median DOM, closed sales volume,
active inventory count. Always specify the comparison period in output.

---

### Absorption Rate (Alternative Expression)

Sometimes expressed as units sold per month rather than months of supply:

```
Absorption Rate = Closed Sales per Month ÷ Active Listings × 100
```

This gives a percentage: e.g., "32% of available homes sold this month."
Less common in client-facing output but useful for internal analysis.

---

### New Listings vs. Closed Sales Ratio

```
New Listings / Closed Sales = Listing Intake Ratio
```

- Ratio > 1.5: more new supply entering than selling; inventory building; market softening
- Ratio near 1.0: supply and demand roughly balanced
- Ratio < 0.8: demand exceeding new supply; prices under upward pressure

---

## Data Sources: What Each Reports

### MIBOR (Metropolitan Indianapolis Board of REALTORS®)
**URL:** mibor.com → News & Media → Press Releases
**Coverage:** Marion, Hamilton, Hendricks, Johnson, Boone, Hancock, and
adjacent counties in the BLC service area
**Published:** Monthly press release, typically released the third week of the
following month (e.g., February data released ~March 18–22)
**Reports:**
- Median sale price (county and metro-wide)
- Closed sales count
- New listings count
- Days on market (median and average)
- Sale-to-list price ratio
- Months of supply / active inventory
- YoY comparisons for all metrics

**Best for:** Authoritative Indiana-specific data; county-level breakdowns;
professional credibility ("according to MIBOR")

---

### IAR (Indiana Association of REALTORS®)
**URL:** iar.org → Market Data
**Coverage:** Statewide; county-level reports available
**Published:** Monthly housing reports; quarterly economic analysis
**Reports:**
- State and county median price
- Closed and new listings
- Market condition analysis
- Housing affordability index
- Interest rate context

**Best for:** Indiana context beyond metro; quarterly summary language;
HAI (housing affordability index) data

---

### NAR (National Association of REALTORS®)
**URL:** nar.realtor → Research and Statistics → Existing Home Sales
**Coverage:** National and metro-level (Indianapolis MSA)
**Published:** Monthly existing home sales report (released ~third week);
quarterly metro median price report
**Reports:**
- Indianapolis MSA median price
- National sales volume and trends
- NAR chief economist commentary (useful for credible forward context)

**Best for:** Framing local data against national trends; credibility when
speaking to relocation buyers; MSA-level price comparisons

---

### Redfin Market Data
**URL:** redfin.com/city/[city-name]/IN/market-insights
  or redfin.com/zipcode/[zip]/housing-market
**Coverage:** City and zip-code level throughout Central Indiana
**Published:** Rolling 30-day updates; near-real-time
**Reports:**
- Median sale price (30-day rolling)
- Median days on market
- Sale-to-list price ratio
- Homes sold above list price (%)
- Migration patterns (where buyers are coming from)

**Best for:** City or zip-specific data; current conditions rather than
month-end snapshots; buyer migration context (useful for relocation agents)

---

### Zillow Research
**URL:** zillow.com/research/data; zillow.com/home-values/[zip]
**Coverage:** National, metro, city, zip, and neighborhood
**Published:** Monthly; some metrics weekly
**Reports:**
- Zillow Home Value Index (ZHVI) — smoothed median estimate
- Zillow Market Heat Index (buyer vs. seller conditions)
- Price cuts percentage
- Days to pending

**Best for:** Trend visualization; neighborhood-level heat mapping; general
consumer-facing framing. Note: ZHVI is a modeled estimate, not raw MLS data —
should be cited as such, not as a MLS-sourced figure.

---

### Brokerage MLS Pulls (Agent's Own Access)
**Source:** BLC/MIBOR Matrix or agent's brokerage platform
**Coverage:** Full MLS data; most granular
**Best for:** Zip-level and neighborhood-level precision; spec stats for
listing presentations; verifying published report figures

**Always instruct the agent:** Published search-based data (Redfin, Zillow,
MIBOR press releases) may differ slightly from direct MLS pulls due to lag,
scope definitions, or methodology. For formal listing presentations, verify
stats through the agent's own MLS access.

---

## Central Indiana County Market Profiles

### Hamilton County

**Character:** The premier Indianapolis suburban market. Consistently among the
fastest-growing counties in Indiana. Demand driven by top-tier school districts,
corporate relocation, and quality of life amenities.

**Price range:** Entry townhomes from $250K; dominant SFR band $350K–$700K;
luxury estates $700K–$3M+. Highest median prices in the metro.

**Key dynamics:**
- Carmel Clay Schools and Hamilton Southeastern Schools create measurable
  sub-market premiums. County-level medians can mislead — a buyer targeting
  Carmel Clay territory will face a $450K+ entry point, not the county median.
- Zionsville (mostly Boone County, but perceived as Hamilton County premium)
  adds a luxury pocket at $500K–$2M+.
- New construction is most active in Westfield and Noblesville, along SR-32
  and US-31 corridors. Builder communities (Lennar, M/I Homes, Drees) add
  significant inventory that may not appear in MLS resale counts until close.
- Grand Park Sports Campus (Westfield) continues to drive commercial and
  residential growth in the northern Hamilton County fringe.
- Hamilton County commands the highest property tax assessments in the metro,
  partly offsetting the premium pricing advantage for buyers comparing to
  Hendricks or Johnson County.

**Seasonality note:** The spring surge is most pronounced in Hamilton County.
April–May frequently produce the most competitive conditions in the metro,
with sub-14-day DOM on well-priced homes.

---

### Marion County (Indianapolis)

**Character:** The urban core. Wide price variance across a large geographic
footprint. Home to diverse neighborhoods from distressed East Side to
premium Meridian Hills estates.

**Price range:** $80K (distressed East side) to $2M+ (Meridian Hills/Williams
Creek). Dominant price band for typical buyers: $175K–$400K.

**Key dynamics:**
- County-level medians are not useful for neighborhood-level conversations.
  Always narrow to township or neighborhood when reporting for Marion County.
- Urban renewal pockets (Fountain Square, Bates-Hendricks, Irvington, Mass Ave
  corridor) have appreciated significantly. Fountain Square 10-year appreciation
  exceeds Hamilton County suburban norms.
- MSD Washington Township (north Indianapolis) and MSD Perry Township (south)
  command premiums within Marion County. IPS territory is more varied.
- Broad Ripple and Meridian-Kessler attract young professional buyers;
  historically competitive on correctly priced sub-$400K listings.
- Investor activity is higher in Marion County than collar counties — cash
  buyers and investment purchasers can skew DOM stats downward on the low end.
- Property tax rate varies significantly by township; buyers should verify
  assessed value and effective tax rate before comparing county-level stats.

---

### Hendricks County

**Character:** The west-side value play. Growing steadily via I-74 and US-36
corridors. Competitive pricing advantage vs. Hamilton County; strong school
districts in Avon and Brownsburg.

**Price range:** Dominant band $250K–$450K. More affordable entry points than
Hamilton County for comparable square footage.

**Key dynamics:**
- Avon and Brownsburg drive the market. Both have top-rated school districts
  that fuel consistent demand from families priced out of Hamilton County.
- Plainfield is an important market segment: proximity to I-70 logistics hub
  (Amazon, FedEx) creates strong demand from distribution-sector employees.
- Commute to downtown Indianapolis is typically better from Hendricks County
  than from equivalent-distance north Hamilton County locations (I-74 vs.
  US-31 congestion comparison).
- New construction in Brownsburg and Avon is active, primarily in the
  townhome and entry-level SFR range.
- Property tax rates are meaningfully lower than Hamilton County — a genuine
  financial advantage for buyers comparing the two markets.

---

### Johnson County

**Character:** The south-side value market with a notable premium sub-market.
Center Grove Community Schools creates a distinct price tier within the county.

**Price range:** Dominant band $225K–$450K. Center Grove area premium reaches
$700K+ for luxury. Franklin (county seat) is the most affordable market.

**Key dynamics:**
- Center Grove Schools is the defining dynamic. Homes within the Center Grove
  Community School Corporation boundary command 10–18% premiums over
  comparable homes elsewhere in the county. The district straddles
  Bargersville, Whiteland, and unincorporated Johnson County — school district
  verification is critical (boundaries do not follow city limits).
- Greenwood is the commercial and retail hub; consistent demand from
  south-side Indianapolis commuters on I-65.
- Franklin has a distinct rural-small town character; more affordable; emerging
  arts and food scene; attracts buyers seeking value with community character.
- Johnson County is a natural landing spot for buyers priced out of Hamilton
  County who still want strong schools and suburban character.
- I-65 S commute corridor is generally less congested than US-31 N, giving
  Johnson County a commute advantage over some Hamilton County locations.

---

### Boone County

**Character:** Split market: upscale residential in the Zionsville corridor
(eastern Boone) vs. rural agricultural character in western Boone (Lebanon area).

**Price range:** Zionsville-adjacent: $500K–$2M+; Lebanon and western Boone:
$175K–$350K.

**Key dynamics:**
- Zionsville Community Schools is one of the top-rated districts in Indiana
  and drives significant premium. Many buyers assume Zionsville is Hamilton
  County; a significant portion of Zionsville addresses are Boone County.
  This distinction matters for property tax rates and county-level MLS filters.
- Lebanon is growing via I-65 N (Whitestown exit area development). Affordable
  entry-level market for commuters who can tolerate a longer drive.
- Boone County new construction is active in the Whitestown/Lebanon area —
  Lennar and other national builders have large active communities here.
- Active inventory in the Zionsville market is typically low; well-priced homes
  move quickly with multiple offers in spring season.

---

### Hancock County

**Character:** The growing east-side bedroom community. I-70 corridor access
to downtown Indianapolis. Affordable alternative to Hamilton County east-side
communities.

**Price range:** Dominant band $225K–$400K.

**Key dynamics:**
- McCordsville is the fastest-growing community in the county; proximity to
  Fishers/Geist corridor makes it attractive for buyers who want Hamilton County
  access at Hancock County prices.
- Greenfield (county seat) is more established; smaller-town character; more
  affordable.
- Southern Hancock Schools serves much of the county; not a Tier 1 district
  premium driver but solid reputation.
- New construction is active along I-70 E near Greenfield; Lennar and D.R.
  Horton have communities in this corridor.
- Increasingly attractive to buyers priced out of Fishers who still want I-69
  corridor access via I-70 E/I-465 connection.

---

### Morgan County

**Character:** Rural value market. Mooresville and Martinsville are the primary
communities. Commuter zone for Indianapolis (US-40 or SR-37 corridors).

**Price range:** Dominant band $175K–$325K. Rural acreage listings can skew
median upward.

**Key dynamics:**
- More rural character than other collar counties; acreage and land listings
  are common; rural lifestyle attracts specific buyer segment.
- Market depth is limited compared to Hamilton, Hendricks, or Johnson. Fewer
  comparable sales can make CMA work more challenging.
- Primarily serves buyers who prioritize acreage, rural character, or maximum
  value over school district rankings or urban proximity.

---

## Seasonal Patterns in Detail

Central Indiana real estate follows a consistent seasonal rhythm. Always
frame stats against this baseline when reporting.

### Month-by-Month Patterns

| Month | Typical Conditions | Notes |
|---|---|---|
| January | Slowest month of the year | Serious buyers only; low inventory; sellers who must sell; good buying opportunity |
| February | Slight awakening | New listings starting to appear; some buyers pre-positioning |
| March | Market activation | Spring surge beginning; new listings accelerating; buyers competing |
| April | Peak competition | Most new listings; most buyer activity; multiple offers common |
| May | Continued peak | Families motivated to close before school year; highest prices typical |
| June | Strong but tapering | Summer travel begins; slight slowdown from May peak |
| July | Summer pause | Vacation season; less competition for buyers; good negotiating window |
| August | Secondary activity | Back-to-school prep drives some activity; quieter than spring |
| September | Fall secondary peak | Move-before-winter motivation; competitive for well-priced homes |
| October | Steady | Good balance; motivated sellers starting to price aggressively |
| November | Slowdown | Holiday approach; serious sellers only; limited inventory |
| December | Slowest second month | Holidays dominate; very limited inventory and activity |

### Practical Implications for Market Reports

**Reporting January–February data:** Low inventory and low volume are seasonal
norms, not market weakness. Frame as: "January typically shows the lowest
inventory of the year in Central Indiana — this is normal seasonal behavior."

**Reporting April–May data:** High prices and low DOM reflect peak demand. Frame
as: "We're in the spring surge — the most competitive window of the year. This
is when multiple offers are most common."

**Reporting July–August data:** Softening from spring peak should not be
characterized as a market downturn. Frame as: "Summer typically brings slightly
more negotiating room for buyers as the spring rush subsides."

**Year-over-year comparisons:** When comparing across seasons (e.g., Q1 vs Q3
of the same year), note that the comparison is not apples-to-apples due to
seasonal variation.

---

## New Construction Impact on Market Statistics

### Why New Construction Distorts Resale Data

New construction transactions often do not appear in MLS active inventory until
after the certificate of occupancy is issued and the sale closes. This means:

1. **Active inventory numbers understate true market supply** in active builder
   markets. A neighborhood with 50 active resale listings and 200 homes under
   construction by Lennar is not as tight as the inventory count suggests.

2. **DOM statistics are not comparable** between resale and new construction.
   Builder sales from model homes or pre-sales may have DOM of 0 (entered into
   MLS at close) or very long DOM (entered when land was platted). Neither
   reflects true market demand.

3. **Median sale price can be skewed** by new construction's higher average
   price point in some sub-markets, or by builder spec homes that close at
   lower prices to clear inventory.

### Active Builder Markets in Central Indiana (2025–2026)

| Area | County | Active Builders | Impact Level |
|---|---|---|---|
| Westfield (SR-32/US-31 corridor) | Hamilton | Lennar, M/I, Drees, Pulte | High |
| Noblesville (north) | Hamilton | Lennar, D.R. Horton, Fischer | High |
| Whitestown/Lebanon | Boone | Lennar, M/I, Arbor | High |
| Brownsburg/Avon | Hendricks | D.R. Horton, Fischer, Arbor | Medium |
| Greenfield (I-70 E) | Hancock | Lennar, D.R. Horton | Medium |
| Bargersville/Whiteland | Johnson | Multiple builders | Medium |
| McCordsville | Hancock | Multiple builders | Medium |

### How to Note New Construction in Market Reports

**For areas with high builder activity:** Add a note in the report:
> "Active new construction communities in [area] are not fully reflected in
> MLS active inventory counts. Buyers in this area should be aware that builder
> communities (Lennar, M/I Homes, and others) represent additional inventory
> options not captured in these statistics."

**For new construction vs. resale comparison requests:**
- Note that builder contracts use builder-specific forms, not IAR standard forms
- Builder negotiation typically occurs on upgrades/incentives, not base price
- Builder preferred lender incentives are common — buyers should compare rates
- Buyer's agent commission (co-op) requires buyer to register on first visit

---

## Fair Housing and Language Notes

All market reports must comply with the Fair Housing Act. Specific requirements:

- **Never describe a neighborhood by the demographic characteristics of its
  residents.** Do not say "diverse neighborhood" or "predominantly [any group]."
  Describe physical characteristics, amenities, price ranges, and school districts.
- **School district information is permissible** as objective fact (it affects
  value and is a legitimate buyer consideration). Do not use school districts
  as proxies for demographic steering.
- **Never recommend or discourage a buyer from considering a particular area**
  based on anything other than the buyer's stated preferences, budget, and
  practical requirements.
- For full language guidance, see
  `~/Skills/real-estate-plugin/references/real-estate-vocabulary.md`.

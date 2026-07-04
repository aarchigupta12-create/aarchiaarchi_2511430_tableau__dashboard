# aarchiaarchi_2511430_tableau__dashboard
# Part 4 — Tableau Dashboard: Sales Performance

## Business Problem
Build an interactive dashboard giving stakeholders a clear, at-a-glance view
of sales, profit, returns, and delivery performance — so underperforming
areas (categories, regions, channels) can be spotted without running ad-hoc
queries.

## Dataset Used
`data/cleaned_dashboard_data.csv` — 4,200 orders (Jan 2024–Dec 2025), with
sales, profit, discount, returns, delivery time, rating, and acquisition
channel.

## Tools Used
Tableau

## Steps Performed
1. Checked data quality: no duplicate rows or order IDs. Missing values only
   in `customer_rating` (32 rows, <1%) and `campaign_channel` (24 rows).
2. Left `customer_rating` nulls as-is — Tableau's `AVG()` excludes them
   automatically, and at under 1% of rows the effect is negligible.
3. Replaced missing `campaign_channel` with `"Unknown"` so it appears as an
   explicit, filterable category rather than disappearing from channel-based
   charts.
4. Built calculated fields for Profit Margin and Return Rate (see
   `tableau_build_guide.md` for exact formulas).
5. Built KPI summary cards, a sales/profit trend line, category-level
   sales/margin/return comparisons, a regional view, campaign channel
   performance, and delivery time by shipping mode.
6. Added dashboard-level filters for date range, region, category, and
   customer segment.

## Key Outputs
- `dashboard.twbx` (or link to Tableau Public) — the interactive dashboard
- Screenshots of the full dashboard and each chart in `screenshots/`

## Business Insights
- Overall profit margin is ~15.3%, but this varies sharply by category:
  Technology runs ~18.2% margin, while Furniture runs only ~6.9% despite
  generating meaningful sales volume.
- Furniture also carries the highest average discount (16.2% vs. ~12–13%
  for other categories) and the highest return rate (7.7% vs. ~3–4%
  elsewhere) — discounting and returns together are eating most of its
  margin.
- [Add 1–2 more insights once you've actually looked at your rendered
  region/channel/delivery charts — these should come from what you see,
  not be guessed in advance]

## Assumptions Made
- Missing `campaign_channel` values represent untracked acquisition source,
  not a data error, and are labeled "Unknown" rather than dropped.
- `delivery_days` in the source data is treated as already correctly
  calculated (ship_date − order_date); it was not recomputed independently.

## Known Limitations
- `customer_rating` is missing for 32 orders; these are simply excluded from
  rating averages rather than imputed, since imputing a satisfaction score
  risks misrepresenting real customer sentiment.
- The dashboard shows associations (e.g. discount vs. margin by category),
  not proven causation — a category with more discounting isn't necessarily
  losing margin *because* of the discounting alone.

## Screenshots
See `screenshots/` for the full dashboard, individual chart views, the
calculated fields, and a filtered view demonstrating interactivity.

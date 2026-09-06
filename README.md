# BFSI SQL Analytics Project

A collection of Snowflake SQL scripts demonstrating core analytical techniques, trend analysis, cumulative metrics, performance comparison, segmentation, and part-to-whole analysis, applied to a synthetic banking dataset.

Built to practice SQL analytics patterns commonly used in BFSI (Banking, Financial Services & Insurance) reporting: deposit trends, loan book health, branch performance, and customer segmentation.

> **Data note:** all data in `/datasets` is synthetically generated, no real customer, account, or transaction data is used anywhere in this project.

## Schema

```
customers ──< accounts >── branches
    │
    └──< loans

transactions >── accounts
```

| Table | Grain | Rows |
|---|---|---|
| `branches` | one row per branch | 28 |
| `customers` | one row per customer | 400 |
| `accounts` | one row per account | ~668 |
| `transactions` | one row per transaction | 15,000 |
| `loans` | one row per loan | ~184 |

## Analysis categories

| Script | Technique | Example question answered |
|---|---|---|
| `01_database_exploration.sql` | Schema exploration | What tables/columns exist, what's the date range? |
| `02_measures_and_metrics.sql` | Magnitude analysis | Total deposits, active loan book, avg balance by type |
| `03_changes_over_time_analysis.sql` | Trend analysis | Monthly transaction trend, YoY deposit growth |
| `04_cumulative_analysis.sql` | Running totals | Cumulative loan disbursement, 3-month moving average |
| `05_performance_analysis.sql` | Period comparison | MoM growth %, branch ranking, loan vs. product average |
| `06_data_segmentation.sql` | Categorization | Credit score bands, account balance tiers |
| `07_part_to_whole_analysis.sql` | Contribution % | Channel mix, loan type share, regional contribution |

## Tech stack

- **Snowflake** — SQL engine (window functions, `DATE_TRUNC`, `QUALIFY`-ready syntax)

## Getting started
In Snowflake (via SnowSQL or Snowsight):

```sql
-- 1. Run the init script to create tables and load data
--    (upload the CSVs to the stage first via SnowSQL PUT, or Snowsight's
--     "Load Data" UI, then run the COPY INTO statements)
!source scripts/00_init_database.sql

-- 2. Run any analysis script
!source scripts/03_changes_over_time_analysis.sql
```


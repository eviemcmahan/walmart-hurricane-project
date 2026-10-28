# Walmart Hurricane Analytics

**DS2002 Data Science Systems | Midterm Group Project | Fall 2026 | University of Virginia**

**Team HEJ:** Evie McMahan, Julia McPhillips, Honor Dold

## Start here

| What | Where |
|---|---|
| The full analysis (cleaning, weather API, all five questions) | [`notebooks/team_notebook.ipynb`](notebooks/team_notebook.ipynb) |
| Our slide presentations | `PRESENTATION`|
| Our reflection after completing the analysis | [`REFLECTION.md`](REFLECTION.md) |
| Our team goals, roles, and working agreement | [`CHARTER.md`](CHARTER.md) |

## Repository contents

```
walmart-hurricane-project/
|-- README.md
|-- CHARTER.md
|-- REFLECTION.md
|-- PRESENTATION
|-- data/
|   |-- walmart_transactions.csv      point-of-sale records, Florida stores, Sept 2024
|   |-- store_locations.csv           store metadata
|   |-- product_catalog.csv           master product and SKU list
|   |-- distribution_centers.csv      distribution center capacity
|   `-- inventory_and_sales.db        SQLite: daily_sales_summary + inventory_levels
`-- notebooks/
    |-- team_notebook.ipynb           main analysis notebook
    `-- scratch/
        `-- 2026-10-23 — Midterm Checkpoint — Lab.ipynb
```

## How to run

Open `notebooks/team_notebook.ipynb` in Colab or Jupyter and choose Restart and run all. It needs internet for the weather pull and no API key. It finds the data in `data/` or `../data`.

## Method

- **Cleaning:** `clean_all(raw)` runs 11 steps (spacing, missing values, duplicates, types, negative quantities, store IDs, categories, SKU consolidation, dates and timezones, database cleaning) and includes the decision log.
- **Weather:** [Open-Meteo Historical API](https://open-meteo.com/) (`https://archive-api.open-meteo.com/v1/archive`), daily rain, max wind and minimum pressure, in `America/New_York` time.
- **Windows:** our baseline used Sept 1 to 15, surge used Sept 19 to 25, and peak days used Sept 24 and 25.

## Findings

1. **Surge:** Breakfast (only Strawberry Pop-Tarts) surged the most (+414%). Emergency, Electronics, Entertainment and Alcohol products also rose, but Snacks barely increased.
2. **Pop-Tarts:** Four SKUs hid the true Pop-Tart surge. Combined, Pop-Tart volume peaked at 9.3 times baseline on Sept 25.
3. **Weather:** Sales line up best with wind 2 days later, showing that customers stocked up prior to the storm.
4. **Stores:** Every store surged 2.2 to 2.7 times, and distance from landfall didn't explain a variation in the level of the surge.
5. **Board games:** The +250% was not an artifact, but it only covers the two peak days. Over the full surging period, electronic sales increased about +126% to +145%. We found no sign of SKU miscoding, category lumping or inventory lag.
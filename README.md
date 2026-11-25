# JV Production Performance & Downtime Analytics

An interactive Power BI report for monitoring production against target and examining downtime across assets, regions, joint ventures, and products. It highlights where production is falling short and where operational teams may need to investigate reliability.


## Business question

How closely is production meeting target, and which regions, assets, and downtime patterns are associated with performance gaps?

**Reporting period:** January 2023–December 2025  

## Objectives

- Compare actual production with target and track achievement over time.
- Identify regional and asset-level performance differences.
- Make planned and unplanned downtime visible alongside production.
- Provide interactive filtering by year, product, and operational dimensions.

## Key findings

- **179,496,245.22 bbl** actual production against **186,703,236.00 bbl** target: **96.14% achievement**, a shortfall of **7,206,990.78 bbl**.
- **20,700 hours** total downtime: **10,792 planned** and **9,908 unplanned**. Unplanned downtime represents **47.86%** of total downtime.
- **Western Basin** has the highest regional production achievement at **99.77%**.
- **Central Basin** has the lowest achievement at **93.05%** and the highest unplanned downtime in the regional comparison, at **3,840 hours** (**57.14%** of its downtime).
- **Coastal Belt** has the highest actual production among the four displayed regions: **60,289,858.20 bbl**.


## Report pages



### Executive Summary

![JV3 Production Performance Dashboard — Executive Summary](images/executive-summary.png)

### Downtime Analysis

![JV3 Production Performance Dashboard — Downtime Analysis](images/downtime-analysis.png)

## Data model

The model uses `FactProduction` as the production and downtime fact table, related to asset, product, and date dimensions.

| Table | Role | Example fields |
|---|---|---|
| `FactProduction` | Production and downtime fact table | `Date`, `AssetID`, `ProductID`, `ActualProduction`, `TargetProduction`, `PlannedDowntimeHours`, `UnplannedDowntimeHours`, `TotalDowntimeHours`, `ProductionDays` |
| `DimAsset` | Asset and operating context | `AssetID`, `AssetName`, `JVName`, `Operator`, `Region`, `AssetType` |
| `DimProduct` | Product attributes | `ProductID`, `ProductName`, `Unit` |
| `Date` | Date filtering and time grouping | `Date`, `Year`, `Month`, `MonthNum` |
| `_Measures` | Central measure table | Production and downtime measures |
| `DimParam` | Field parameter table | `DimParam`, `DimParam Fields`, `DimParam Order` |

Active many-to-one relationships connect `FactProduction` to `DimAsset`, `DimProduct`, and `Date`, with single-direction filtering toward the fact table.

### Core DAX measures

- Actual Production (bbl)
- Target Production (bbl)
- Production Variance (bbl)
- Production Variance %
- Production Achievement %
- Planned Downtime (Hrs)
- Unplanned Downtime (Hrs)
- Total Downtime (Hrs)
- Unplanned Downtime %
- Achievement Colour
- Zero


## Project links

- **Live report:** [Add Power BI Service link, if published]
- **PBIX file:** [Add repository-relative path or approved download link]
- **PDF export:** [Add repository-relative path or approved download link]
- **DAX documentation:** [Add path, e.g. `docs/DAX.md`, when available]
- **Profile:** [Add your GitHub or professional profile URL]




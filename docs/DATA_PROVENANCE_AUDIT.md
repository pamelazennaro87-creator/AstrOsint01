# Data provenance and validation audit

**Project:** AstrOsint01 — NASA Space Apps Challenge 2026  
**Audit date:** 14 November 2026  
**Status:** Partial validation; not a scientific reprocessing or independent reproduction.

## 1. Files inspected

Source repository: https://github.com/AstrOsint01/nasa-water-storage-analysis

| File | Rows | Coverage | Observed TWSa/GWSa values | Filled months |
|---|---:|---|---:|---:|
| `central_valley.csv.csv` | 291 | 2002-04 to 2026-06 | 256 each | 35 each |
| `taoudeni-tanezrouft basin.csv.csv` | 291 | 2002-04 to 2026-06 | 256 each | 35 each |

Both files have columns for Date, TWSa, GWSa, their upper/lower bounds, filled series and filled flags, plus SMa, SWEa and CANa columns.

## 2. What is verified from the files

- Both CSVs contain 291 monthly rows, from April 2002 through June 2026.
- For TWSa and GWSa, 256 monthly entries are populated in the observed columns and 35 are marked as gap-filled.
- The CSV schema matches the GEOGloWS GRACE Regional Analyst CSV download documentation: https://training.geoglows.org/grace/app/downloading-data/
- The second filename is `taoudeni-tanezrouft basin.csv.csv`; it must not be represented as an Inner Niger Delta measurement.
- The Explorer currently fits trends to populated, non-filled observations and marks filled months separately.

## 3. Additional provenance found in Git history

The public Git history shows both CSV files were added together in commit `9e5d207eb18005557443ab8c008fb76b72f31490` on 14 November 2026 at 19:38:23 UTC. The commit message is "add water storage CSV data". This establishes when the files entered this Git repository, not when or how the source data were originally downloaded.

The source repository README was updated later on 14 November 2026 at 20:08:30 UTC and states "Downloaded on: 15 Nov 2026". That stated retrieval date is later than the README commit timestamp and cannot be treated as a verified download date. No original export receipt, selected polygon, or export configuration is archived with the files.

## 4. What is not verified yet

- Exact selected region polygons, polygon areas and mask versions.
- Exact source product/version and export configuration used for these particular files.
- Actual retrieval/download timestamp. The prior source README's stated date of 15 November 2026 was in the future relative to this audit date (14 November 2026) and had no archived export receipt. It is therefore not accepted as a verified retrieval date.
- Independent reproduction of the CSV values from the original source product.
- Whether the intended second case study should be Taoudeni–Tanezrouft or Inner Niger Delta.
- Statistical significance, serial correlation, sensitivity to the observation period and formal uncertainty of the fitted trends.

## 5. Descriptive calculations — not final scientific findings

The current Explorer's three time windows were independently recalculated from the populated, non-filled observations. The Central Valley trend changes sign in the most recent five-year window, so the full-period decline must not be presented as an unchanging trajectory.

| File | Variable | Full record | Last 10 years | Last 5 years |
|---|---|---:|---:|---:|
| Central Valley | TWSa | -1.355 | -0.329 | +4.232 |
| Central Valley | GWSa | -1.354 | -0.332 | +3.401 |
| Taoudeni–Tanezrouft | TWSa | +0.025 | +0.208 | +0.377 |
| Taoudeni–Tanezrouft | GWSa | -0.080 | +0.240 | +0.346 |

All values are cm/year. These are descriptive ordinary least-squares slopes, not significance-tested estimates. The last-five-year window runs from June 2021 through June 2026 (61 observed monthly values); the last-ten-year window runs from June 2016 through June 2026 (105 observed values); the full record has 256 observed values. The 35 filled months are excluded from each fit.


Ordinary least-squares slopes recalculated from populated, non-filled observations only, with time expressed in calendar years:

| File | Variable | Descriptive slope |
|---|---|---:|
| California Central Valley | TWSa | -1.355 cm/year |
| California Central Valley | GWSa | -1.354 cm/year |
| Taoudeni–Tanezrouft | TWSa | +0.025 cm/year |
| Taoudeni–Tanezrouft | GWSa | -0.080 cm/year |

These are descriptive calculations over the entire available record, not significance-tested estimates. They are not proof of causality, aquifer depletion rates at local scale, or a fair direct comparison between the two geographic areas.

## 6. Scientific context and interpretation limits

The GEOGloWS documentation confirms that GWSa is derived as:

`GWSa = TWSa − (SWEa + CANa + SMa)`

The surface-water component is not subtracted. Therefore GWSa can include storage changes in rivers, lakes, reservoirs and wetlands; it is a model-derived residual, not a direct well measurement. This is especially consequential in floodplains and wetlands such as the Inner Niger Delta. Source: https://training.geoglows.org/grace/background/deriving-groundwater/

The GEOGloWS workflow combines JPL GRACE TWSa with a three-model GLDAS 2.1 ensemble (Noah, VIC and CLSM) for soil moisture, snow and canopy water. It averages TWSa to a 1° grid for the derived GWSa calculation; TWSa itself is served on a 0.5° grid. Regional means use overlap-weighted cells, with cells included when at least 35% of their area lies within the region. The exact masks used for these CSV exports are still missing. Sources: https://training.geoglows.org/grace/background/deriving-groundwater/ and https://training.geoglows.org/grace/app/regional-view/


NASA/JPL's GRACE/GRACE-FO Mascon RL06.3 Version 04 product reports monthly water-storage anomalies as equivalent water thickness in centimetres. Its standard mascon solution uses an equal-area 3-degree grid of mascons; this is a regional-scale observation, not parcel-level measurement. NASA PO.DAAC dataset page: https://podaac.jpl.nasa.gov/dataset/TELLUS_GRAC-GRFO_MASCON_GRID_RL06.3_V4

The project CSVs are described in the source repository as GEOGloWS exports. That description is consistent with the published GEOGloWS CSV schema, but missing export receipts and polygon metadata prevent independent reproduction of these exact regional series at this stage.

## 7. Required next actions

1. Recover the original GEOGloWS export configuration and polygon for each region.
2. Decide and document the intended second study area. If it is Inner Niger Delta, create a new, separately named export from an explicit boundary; do not relabel the existing Taoudeni–Tanezrouft file.
3. Archive source version, date retrieved, polygon, area, gap-fill configuration and file checksum with every new export.
4. Add statistical diagnostics: Sen's slope, Mann–Kendall with serial-correlation handling, confidence intervals and sensitivity to filled months and period selection.
5. Keep the current two-region comparison explicitly exploratory until geographic and methodological alignment is demonstrated.

## 8. Source references

- GEOGloWS Training — Downloading CSV: https://training.geoglows.org/grace/app/downloading-data/
- GEOGloWS Training — Deriving Groundwater Storage: https://training.geoglows.org/grace/background/deriving-groundwater/
- GEOGloWS Training — Regional View and overlap-weighted masks: https://training.geoglows.org/grace/app/regional-view/
- GEOGloWS Training — Trend Analysis and least-squares windows: https://training.geoglows.org/grace/app/trends/
- GEOGloWS GRACE Regional Analyst: https://apps.geoglows.org/grace-anomalies
- NASA PO.DAAC — JPL GRACE/GRACE-FO Mascon RL06.3 Version 04: https://podaac.jpl.nasa.gov/dataset/TELLUS_GRAC-GRFO_MASCON_GRID_RL06.3_V4

---
**Audit conclusion:** The CSVs are real files with a documented, recognizable GEOGloWS schema. Their exact export provenance and region masks are not yet sufficiently archived to claim full reproducibility. The Explorer may display them as provisional source exports, with explicit limitations; it must not present the current African CSV as Inner Niger Delta data.

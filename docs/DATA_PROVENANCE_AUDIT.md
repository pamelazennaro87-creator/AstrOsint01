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

## 3. What is not verified yet

- Exact selected region polygons, polygon areas and mask versions.
- Exact source product/version and export configuration used for these particular files.
- Actual retrieval/download timestamp. The prior source README's stated date of 15 November 2026 was in the future relative to this audit date (14 November 2026) and had no archived export receipt. It is therefore not accepted as a verified retrieval date.
- Independent reproduction of the CSV values from the original source product.
- Whether the intended second case study should be Taoudeni–Tanezrouft or Inner Niger Delta.
- Statistical significance, serial correlation, sensitivity to the observation period and formal uncertainty of the fitted trends.

## 4. Descriptive calculations — not final scientific findings

Ordinary least-squares slopes recalculated from populated, non-filled observations only, with time expressed in calendar years:

| File | Variable | Descriptive slope |
|---|---|---:|
| California Central Valley | TWSa | -1.355 cm/year |
| California Central Valley | GWSa | -1.354 cm/year |
| Taoudeni–Tanezrouft | TWSa | +0.025 cm/year |
| Taoudeni–Tanezrouft | GWSa | -0.080 cm/year |

These are descriptive calculations over the entire available record, not significance-tested estimates. They are not proof of causality, aquifer depletion rates at local scale, or a fair direct comparison between the two geographic areas.

## 5. Scientific context and interpretation limits

NASA/JPL's GRACE/GRACE-FO Mascon RL06.3 Version 04 product reports monthly water-storage anomalies as equivalent water thickness in centimetres. Its standard mascon solution uses an equal-area 3-degree grid of mascons; this is a regional-scale observation, not parcel-level measurement. NASA PO.DAAC dataset page: https://podaac.jpl.nasa.gov/dataset/TELLUS_GRAC-GRFO_MASCON_GRID_RL06.3_V4

The project CSVs are described in the source repository as GEOGloWS exports. That description is consistent with the published GEOGloWS CSV schema, but missing export receipts and polygon metadata prevent independent reproduction of these exact regional series at this stage.

## 6. Required next actions

1. Recover the original GEOGloWS export configuration and polygon for each region.
2. Decide and document the intended second study area. If it is Inner Niger Delta, create a new, separately named export from an explicit boundary; do not relabel the existing Taoudeni–Tanezrouft file.
3. Archive source version, date retrieved, polygon, area, gap-fill configuration and file checksum with every new export.
4. Add statistical diagnostics: Sen's slope, Mann–Kendall with serial-correlation handling, confidence intervals and sensitivity to filled months and period selection.
5. Keep the current two-region comparison explicitly exploratory until geographic and methodological alignment is demonstrated.

## 7. Source references

- GEOGloWS Training — Downloading CSV: https://training.geoglows.org/grace/app/downloading-data/
- GEOGloWS GRACE Regional Analyst: https://apps.geoglows.org/grace-anomalies
- NASA PO.DAAC — JPL GRACE/GRACE-FO Mascon RL06.3 Version 04: https://podaac.jpl.nasa.gov/dataset/TELLUS_GRAC-GRFO_MASCON_GRID_RL06.3_V4

---
**Audit conclusion:** The CSVs are real files with a documented, recognizable GEOGloWS schema. Their exact export provenance and region masks are not yet sufficiently archived to claim full reproducibility. The Explorer may display them as provisional source exports, with explicit limitations; it must not present the current African CSV as Inner Niger Delta data.

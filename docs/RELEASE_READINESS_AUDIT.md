# Release-readiness audit

**Project:** AstrOsint01 — NASA Space Apps Challenge 2026  
**Audit date:** 15 November 2026  
**Scope:** Public website, Water Signal Explorer, CSV loading, region switching, Evidence Delta and Evidence Constellation.  
**Classification:** Live smoke test passed; scientific validation remains partial.

## 1. Deployment and browser checks

Public entry points:

- Website: https://pamelazennaro87-creator.github.io/AstrOsint01/
- Water Signal Explorer: https://pamelazennaro87-creator.github.io/AstrOsint01/explorer/
- Repository: https://github.com/pamelazennaro87-creator/AstrOsint01

GitHub Pages workflow run 53 completed successfully for commit `1d3fbefca82d51e0272bf570eccb948ea40e47f1`:

https://github.com/pamelazennaro87-creator/AstrOsint01/actions/runs/43693906089

A live browser smoke test confirmed:

- The Explorer page loads.
- Both external CSV files load successfully.
- Each CSV returns 291 monthly rows.
- The California Central Valley and Taoudeni–Tanezrouft region selector updates the chart and evidence section.
- Evidence Delta and Evidence Constellation render and update.
- No page-visible or console-visible errors were reported in the smoke test.
- A cache-busted retest confirmed the corrected full-record Evidence Delta calculation.

This is a functional smoke test, not a complete cross-browser, mobile-device, screen-reader or formal accessibility audit.

## 2. Corrected analytical defect

The first live test exposed a bug in `windowSlope()`: when the requested window was the full record (`years === null`), the code applied a date filter beginning at the final CSV month. The full-record card therefore used only one observation and returned no slope.

Fixed in commit:

https://github.com/pamelazennaro87-creator/AstrOsint01/commit/1d3fbefca82d51e0272bf570eccb948ea40e47f1

The full-record branch now uses the complete raw monthly series; 10-year and 5-year windows retain their date cut-offs. Live browser verification confirmed 256 observed months in the full record for both study areas.

## 3. Live Evidence Delta values

The values below are descriptive ordinary least-squares slopes in centimetres per year, calculated from populated, non-gap-filled observations only. Window counts refer to observed months.

| Study area | Full record | Last 10 years | Last 5 years |
|---|---:|---:|---:|
| California Central Valley | −1.35 cm/yr (256 months) | −0.33 cm/yr (105 months) | +4.23 cm/yr (61 months) |
| Taoudeni–Tanezrouft Basin | +0.02 cm/yr (256 months) | +0.21 cm/yr (105 months) | +0.38 cm/yr (61 months) |

These are outputs of the project CSVs as currently published. They are not independent reproductions of the upstream satellite product, formal significance tests, forecasts or causal findings. The sign change between the California full-record and recent five-year slope is a descriptive period sensitivity that warrants further investigation; it does not by itself establish recovery.

## 4. Data availability and dependency

The Explorer loads these files from the separate data repository:

- https://github.com/AstrOsint01/nasa-water-storage-analysis/blob/main/central_valley.csv.csv
- https://github.com/AstrOsint01/nasa-water-storage-analysis/blob/main/taoudeni-tanezrouft%20basin.csv.csv

The audited files each contain 291 monthly rows from April 2002 through June 2026, with 256 observed entries and 35 gap-filled entries in the TWSa and GWSa series. The Explorer depends on the availability of the external GitHub raw-content endpoints and an active network connection.

## 5. Scientific and evidentiary limits — still open

The project is not yet a fully independently validated scientific product. The following items remain unresolved and must not be represented as completed:

1. **Source provenance:** archive the exact upstream product identifier, processing version, download/export date, query settings and original export receipt for each CSV.
2. **Geographic reproducibility:** archive the exact study-area polygons or coordinates and document how each regional average was generated. The Taoudeni–Tanezrouft label must not be substituted with Inner Niger Delta.
3. **Independent validation:** no matched well, river, reservoir, field or InSAR time series is currently joined to the same polygon and period. The candidate portals in Evidence Constellation are research leads only.
4. **Statistical inference:** the current OLS slopes are descriptive. No formal significance test, serial-correlation treatment, robust uncertainty estimate or independent trend replication is implemented in the Explorer.
5. **Comparability:** the two regions are not established as equivalent geographic units or controlled like-for-like study areas.
6. **Accessibility validation:** reduced-motion and Safe Mode safeguards are present, but testing with screen readers, keyboard-only users, low-vision users and people with photosensitive epilepsy remains necessary.

NASA/JPL GRACE/GRACE-FO Mascon product documentation describes monthly equivalent-water-thickness anomalies and the product's spatial/temporal characteristics. It is useful for checking the claimed upstream methodology, but does not substitute for the missing export metadata for these specific CSVs:

- https://podaac.jpl.nasa.gov/dataset/TELLUS_GRAC-GRFO_MASCON_GRID_RL06.3_V4
- https://grace.jpl.nasa.gov/data/get-data/

## 6. Release decision

**Functional prototype: PASS.** Public page deployment, CSV loading, region switching, core chart, Evidence Delta and Evidence Constellation passed the live smoke test.

**Scientific reproducibility: PARTIAL / NOT YET CLOSED.** Exact region masks and export provenance remain missing; no independent matched validation series is integrated.

**Accessibility conformance: NOT CERTIFIED.** Design safeguards exist, but user and assistive-technology testing has not been completed.

Recommended public description:

> AstrOsint01 is an accessible, evidence-first exploratory prototype that visualizes GRACE/GRACE-FO-derived monthly water-storage series and makes uncertainty, data gaps and verification needs visible. Its current trends are descriptive and its independent regional validation remains in progress.

Do not claim that the project has completed independent validation, established causation, produced forecasts, or achieved clinical/accessibility certification.

---

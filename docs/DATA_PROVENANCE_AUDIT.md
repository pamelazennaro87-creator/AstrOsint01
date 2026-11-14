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

Both files have columns for Date, TWSa, GWSa, their upper/lower bounds, filled series and filled flags, plus SMa, SWEa and CANa columns. Current Git blob identifiers: `central_valley.csv.csv` = `109fd8cd68236bdd913fcb9788d2378ef31e322c`; `taoudeni-tanezrouft basin.csv.csv` = `cf3d20dcec1abfabe64c0546fb457d4e8e24c4b6`; source README = `132abbf9523c71be357954248d4ac1b4570bc153`.

## 2. What is verified from the files

- Both CSVs contain 291 monthly rows, from April 2002 through June 2026.
- For TWSa and GWSa, 256 monthly entries are populated in the observed columns and 35 are marked as gap-filled.
- The CSV schema matches the GEOGloWS GRACE Regional Analyst CSV download documentation: monthly dates; area-weighted anomalies in cm; upper/lower bounds representing mean ±1σ; seasonal-model filled columns and explicit fill flags. Source: https://training.geoglows.org/grace/app/downloading-data/
- The second filename is `taoudeni-tanezrouft basin.csv.csv`; the Taoudeni/Tanezrouft aquifer system is a documented transboundary hydrogeological system, but its exact polygon in this export is unknown. It must not be represented as an Inner Niger Delta measurement. Regional context: https://www.oss-online.org/sites/default/files/2022-11/OSS-GICRESAIT-Synth-Finale_En.pdf
- The Explorer currently fits trends to populated, non-filled observations and marks filled months separately.

## 3. Additional provenance found in Git history

The public Git history shows both CSV files were added together in commit `9e5d207eb18005557443ab8c008fb76b72f31490` on 14 November 2026 at 19:38:23 UTC. The commit message is "add water storage CSV data". This establishes when the files entered this Git repository, not when or how the source data were originally downloaded.

The source repository README was updated later on 14 November 2026 at 20:08:30 UTC and states "Downloaded on: 15 Nov 2026". That stated retrieval date is later than the README commit timestamp and cannot be treated as a verified download date. No original export receipt, selected polygon, or export configuration is archived with the files.

The source README also has substantive inconsistencies: its file list names `inner_niger_delta.csv`, but the actual file is `taoudeni-tanezrouft basin.csv.csv`; its period and results sections still contain placeholders; and it asserts that Central Valley loses groundwater more than 20 times faster than Taoudeni–Tanezrouft. That comparative ratio is not defensible from the current exports because the exact masks are missing, the geographic units are not aligned, and GWSa retains surface-water storage. Its listed TWSa/GWSa trends are also rounded narrative values, not a reproducible analysis record. The source repository README has not been corrected; the GitHub integration returned HTTP 403 when attempting to write to that separate repository. The main AstrOsint01 repository now carries this correction and the audit.

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


## 6. Scientific context and interpretation limits

The GEOGloWS documentation confirms that GWSa is derived as:

`GWSa = TWSa − (SWEa + CANa + SMa)`

The surface-water component is not subtracted. Therefore GWSa can include storage changes in rivers, lakes, reservoirs and wetlands; it is a model-derived residual, not a direct well measurement. This is especially consequential in floodplains and wetlands such as the Inner Niger Delta. Source: https://training.geoglows.org/grace/background/deriving-groundwater/

The GEOGloWS workflow combines JPL GRACE TWSa with a three-model GLDAS 2.1 ensemble (Noah, VIC and CLSM) for soil moisture, snow and canopy water. It averages TWSa from 0.5° to a 1° grid for the derived GWSa calculation; TWSa itself is served on a 0.5° grid. These grid spacings do not create equivalent independent spatial resolution: GRACE's native mascon support is about 3° (roughly 300 km). Regional means use overlap-weighted cells, with cells included when at least 35% of their area lies within the region. The exact masks used for these CSV exports are still missing. Sources: https://training.geoglows.org/grace/background/deriving-groundwater/ and https://training.geoglows.org/grace/app/regional-view/


NASA/JPL's GRACE/GRACE-FO Mascon RL06.3 Version 04 product reports monthly water-storage anomalies as equivalent water thickness in centimetres. Its standard mascon solution uses an equal-area 3-degree grid of mascons; this is a regional-scale observation, not parcel-level measurement. NASA PO.DAAC dataset page: https://podaac.jpl.nasa.gov/dataset/TELLUS_GRAC-GRFO_MASCON_GRID_RL06.3_V4

The project CSVs are described in the source repository as GEOGloWS exports. Their schema and missing-month pattern are consistent with GEOGloWS documentation, but that is not proof that the selected polygons, source-product versions or every value have been independently reproduced. The exact regional masks and original export receipts are absent, so full provenance remains unverified.

The separate 2025 Inner Niger Delta paper reports positive TWS trends of 7.3–9.5 mm/year for April 2002–September 2022, but it used UTCSR RL06 spherical-harmonic solutions, downscaled to 0.25°, plus GLDAS CLSM 2.2 and WaterGAP surface-water estimates. This differs from the GEOGloWS workflow documented for these CSVs (JPL GRACE plus a GLDAS 2.1 ensemble). It is useful scientific context, not a like-for-like comparison or a substitute for the Taoudeni–Tanezrouft CSV. Source: https://www.mdpi.com/2073-4441/17/8/1121

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
**Audit conclusion:** The two CSVs are valid structured files whose schema and 35-month missing-data pattern match GEOGloWS documentation. The public Git history verifies that they were uploaded on 14 November 2026, not when they were originally exported. Their exact region masks and export receipts remain missing. The Explorer may display them as provisional GEOGloWS-style exports with explicit limitations; it must not present the African CSV as Inner Niger Delta data or describe GWSa as a direct groundwater-well measurement.


## 9. NASA and Copernicus data discovery — second-pass verification (15 November 2026)

This section audits the proposed NASA data inventory separately from the existing GEOGloWS CSV provenance. A dataset being publicly catalogued does not mean that the current project has downloaded, subsetted, or independently reproduced it.

### 9.1 JPL GRACE / GRACE-FO Mascon RL06.3Mv04

**Verified product:** JPL GRACE and GRACE-FO Mascon Ocean, Ice, and Hydrology Equivalent Water Height, Release 06.3 Version 04.  
**PO.DAAC short name:** `TELLUS_GRAC-GRFO_MASCON_GRID_RL06.3_V4`  
**DOI:** [10.5067/TEMSC-3MJ634](https://doi.org/10.5067/TEMSC-3MJ634)  
**Official landing page:** https://podaac.jpl.nasa.gov/dataset/TELLUS_GRAC-GRFO_MASCON_GRID_RL06.3_V4

PO.DAAC confirms monthly global anomalies in equivalent water thickness, in centimetres, on a 0.5° latitude/longitude output grid, from April 2002 to present. The 0.5° grid spacing must not be described as the true independent spatial resolution: the mascon solution has much coarser effective spatial support (roughly 250–300 km; nominal mascon footprint around 3°). This is not a measurement of absolute water volume or a direct well-depth observation.

The product page describes a monthly NetCDF file and provides direct-access, Earthdata Search and OPeNDAP routes. Bulk programmatic access uses NASA Earthdata authentication; therefore do not promise anonymous direct HTTPS downloads. The PO.DAAC page labels the standard mascon product as expert-use and points users toward the CRI-filtered alternative for less expert workflows. Confirm the exact product variant and corrections before analysis.

### 9.2 GLDAS Noah 2.1 monthly

**Verified product:** GLDAS Noah Land Surface Model L4 monthly 0.25° × 0.25° V2.1.  
**Short name:** `GLDAS_NOAH025_M`  
**Verified DOI:** [10.5067/SXAVCZFAQLNO](https://doi.org/10.5067/SXAVCZFAQLNO)  
**NASA catalogue:** https://data.nasa.gov/dataset/gldas-noah-land-surface-model-l4-monthly-0-25-x-0-25-degree-v2-1-gldas-noah025-m-at-ges-di-23acd

NASA's catalogue states that the monthly product is a temporal average of 3-hourly GLDAS-2.1 Noah output, generated with Noah 3.6 in LIS 7, distributed in NetCDF, with 36 land-surface fields and coverage beginning January 2000. GLDAS-2.1 is an open-loop land-surface model product, not a direct observation of groundwater.

**Important DOI correction:** the proposed report lists DOI `10.5067/9GR6GJBW0QCX`. The official NASA catalogue entry for `GLDAS_NOAH025_M` identifies DOI `10.5067/SXAVCZFAQLNO`. Use the latter for this monthly product unless a separate NASA landing page proves that the former identifies a different, explicitly intended product.

**Variable-name correction:** the soil-moisture field is `SoilMoi0_10cm_inst`, not `SoilM0_10cm_inst`. The model also has layer fields `SoilMoi10_40cm_inst`, `SoilMoi40_100cm_inst`, and `SoilMoi100_200cm_inst`; snow water equivalent is represented by `SWE_inst), and canopy water by `CanopInt_inst`. Check the product's own variable table and units before processing.

Evapotranspiration (`Evap_tavg`) and precipitation (`Rainf_f_tavg`) are flux/rate variables. They are not storage components and must not be subtracted directly from GRACE TWSA. Likewise, GLDAS soil-moisture fields are state variables, not automatically anomalies on the same baseline as GRACE.

### 9.3 Groundwater residual method — required safeguards

A conceptual residual is:

`GWSA_estimate = TWSA_GRACE - SMSA_model - SWEA_model - CWSA_model`

This expression is not an executable recipe until all terms are harmonized. At minimum:

- Convert every component to equivalent water height with consistent units.
- Calculate anomalies against a clearly declared, common reference period.
- Align exact monthly timestamps and account for GRACE missing months.
- Regrid with a documented method and apply the same land mask and regional polygon.
- Use compatible model versions and document the structural uncertainty introduced by the land model.
- Include uncertainty propagation and sensitivity to the selected model.
- Explicitly state that surface-water storage is not necessarily removed by this residual. A residual may therefore retain river, lake, reservoir and wetland signals.
- Do not call the output a direct measurement of deep groundwater or a well observation.

NASA/JPL also distributes a GRACE-month-aligned GLDAS Noah aggregate product (soil moisture + snow + canopy water) at 1° for comparison/evaluation. This may be a more internally aligned starting point than independently aggregating monthly GLDAS Noah 2.1 fields, but its product version, variable definitions, temporal coverage and suitability for the selected regional analysis must still be checked. Reference: https://podaac.jpl.nasa.gov/dataset/TELLUS_GLDAS-NOAH-3.3_TWS-ANOMALY_MONTHLY

### 9.4 NASA VEDA / LIS-Noah-MP claim

NASA's LIS/Noah-MP terrestrial-water-storage work is real: NASA describes a global monthly TWS anomaly dataset produced by assimilating GRACE/GRACE-FO TWS anomalies together with ESA CCI soil moisture and MODIS leaf-area-index information. NASA SVS documents a related regional visualization spanning 2003–2019.

However, the supplied report does not identify an exact VEDA collection ID, DOI, STAC item, downloadable asset URL or versioned technical specification that verifies all of its specific claims (10 km resolution, September 2002–December 2021 coverage, COG/NetCDF formats and CC0 licence). These details remain **unverified** and must not be copied into the project as established metadata until the exact collection and licence are recovered.

NASA context:
- https://svs.gsfc.nasa.gov/5444
- https://www.earthdata.nasa.gov/

### 9.5 Copernicus Climate Data Store / GFZ C3S TWSA

**Verified product DOI:** [10.5880/GFZ.C3S_TWSA_v1.0](https://doi.org/10.5880/GFZ.C3S_TWSA_v1.0)  
**Current CDS catalogue:** https://cds.climate.copernicus.eu/datasets/satellite-terrestrial-water-storage

The GFZ dataset is based on COST-G RL02 GRACE/GRACE-FO Level-2B products and supplies monthly 0.5° gridded TWSA in NetCDF, including standard-deviation and filter-flag fields. The operational CDS catalogue describes the product as monthly TWSA in mm, with uncertainty and filter-strength information; the current catalogue coverage is April 2002 to September 2025 and the licence is CC-BY. The catalogue requires login/acceptance of licence terms for downloads; do not describe it as an anonymous no-account direct download.

This is useful as a cross-product comparison against JPL mascons, but it is not an independent sensor measurement: it is another GRACE/GRACE-FO-derived product with a different processing chain. Differences should be interpreted as product/processing sensitivity, not as a direct validation against ground truth.

### 9.6 Implementation decision for AstrOsint01

Recommended sequence:

1. Keep the current GEOGloWS CSV Explorer clearly labelled as provisional and preserve the provenance caveats in Sections 1–8.
2. Obtain a reproducible regional TWSA subset from JPL PO.DAAC RL06.3Mv04 or the Copernicus C3S TWSA product; archive exact collection ID, version, retrieval date, selected files, region polygon, mask and processing script.
3. Use GLDAS only for a clearly documented model-residual experiment, not as an unqualified direct groundwater measurement. Prefer a GRACE-aligned ancillary product where its provenance and compatibility are established.
4. Do not integrate the proposed VEDA 10 km product until its exact dataset record, downloadable assets, period and licence are verified.
5. Keep TWSA product intercomparison separate from GWSA residual estimation. Report both with uncertainty and do not imply that one validates the other against in-situ groundwater observations.

### 9.7 Source references for this second-pass audit

- NASA PO.DAAC JPL Mascon RL06.3Mv04: https://podaac.jpl.nasa.gov/dataset/TELLUS_GRAC-GRFO_MASCON_GRID_RL06.3_V4
- NASA catalogue, GLDAS Noah monthly 0.25° V2.1: https://data.nasa.gov/dataset/gldas-noah-land-surface-model-l4-monthly-0-25-x-0-25-degree-v2-1-gldas-noah025-m-at-ges-di-23acd
- NASA LDAS dataset overview: https://ldas.gsfc.nasa.gov/gldas/dataset
- NASA/JPL GRACE-aligned GLDAS Noah aggregate: https://podaac.jpl.nasa.gov/dataset/TELLUS_GLDAS-NOAH-3.3_TWS-ANOMALY_MONTHLY
- NASA SVS LIS/Noah-MP TWS regional views: https://svs.gsfc.nasa.gov/5444
- GFZ Data Services C3S TWSA DOI: https://doi.org/10.5880/GFZ.C3S_TWSA_v1.0
- Copernicus CDS TWSA catalogue and documentation: https://cds.climate.copernicus.eu/datasets/satellite-terrestrial-water-storage

**Second-pass conclusion:** JPL RL06.3Mv04 and C3S TWSA are valid candidate TWSA products. The exact GLDAS Noah monthly DOI is corrected here to `10.5067/SXAVCZFAQLNO`; the proposed variable typo is corrected. The VEDA metadata claims are not sufficiently identified to verify. No new NASA/GLDAS/COG/NetCDF data have been downloaded or integrated by this audit. Dataset discovery is not evidence of project-level integration.

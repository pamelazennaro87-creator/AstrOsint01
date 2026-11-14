# AstrOsint01 — Research Dossier (Source-Audited Revision)

**NASA Space Apps Challenge 2026 — Be An Earth System Trend Detective!**  
**Research focus:** Earth in Transition — California Central Valley and Inner Niger Delta  
**Revision date:** 2026-11-14

## Executive summary

AstrOsint01 investigates how large-scale water-storage changes relate to different regional and human contexts. The project uses NASA/JPL GRACE and GRACE-FO as its Earth-observation foundation and adds an evidence-led OSINT layer.

Two peer-reviewed regional studies provide useful published reference findings:

- **California Central Valley:** Liu et al. (2022) estimate a groundwater-storage-anomaly depletion trend of **15.7 ± 1.4 mm/year** for 2003–2021.
- **Inner Niger Delta:** Fatolazadeh & Goïta (2025) report a positive **total terrestrial water storage** trend range of **+7.3 to +9.5 mm/year** for April 2002–September 2022.

These values are not directly comparable. The California estimate is a derived groundwater component; the Niger estimate is total terrestrial water storage. The papers also use different GRACE processing, auxiliary datasets, spatial methods and time windows. They are published context, not AstrOsint01 calculations.

## 1. Primary NASA dataset selected

**JPL GRACE and GRACE-FO Mascon CRI-filtered RL06.3 Version 04**

- Short name: TELLUS_GRAC-GRFO_MASCON_CRI_GRID_RL06.3_V4
- DOI: https://doi.org/10.5067/TEMSC-3JC634
- Product record: https://podaac.jpl.nasa.gov/dataset/TELLUS_GRAC-GRFO_MASCON_CRI_GRID_RL06.3_V4
- Format: NetCDF-4; monthly global product
- Main variable: lwe_thickness, in cm equivalent liquid-water thickness
- Uncertainty variable: uncertainty, in cm
- Product record coverage: April 2002 to present; latest granule shown on audit date 2026-09-16
- Native solution: 4,551 equal-area 3° mascons; displayed on a 0.5° grid

The 0.5° display grid must not be mistaken for independent 0.5° measurement resolution. GRACE is appropriate for large-scale storage changes, not parcel, farm, well or village-scale claims. The CRI filter reduces leakage across coastlines; PO.DAAC recommends this filtered product for most land-hydrology applications.

The data collection's protected files require NASA Earthdata Login. Retrieval instructions and product metadata are recorded in data/README.md. No credentials are stored in this repository.

## 2. Published case-study findings

### California Central Valley

Liu et al. (2022), *Nature Communications* 13, 7825:  
https://doi.org/10.1038/s41467-022-35582-x

The paper derives groundwater storage anomalies from GRACE/FO TWS anomalies by subtracting soil-moisture, snow-water-equivalent and surface-water anomalies. The auxiliary inputs include NLDAS-2, SNODAS and California Data Exchange Center data.

Published result: **−15.7 ± 1.4 mm/year** groundwater storage anomaly trend, 2003–2021. The paper also estimates a groundwater loss of **20.0 ± 5.1 km³** from September 2019 to December 2021.

This is not the raw TWS trend from the selected JPL mascon product. It is not a result calculated by AstrOsint01.

### Inner Niger Delta

Fatolazadeh & Goïta (2025), *Water* 17(8), 1121:  
https://doi.org/10.3390/w17081121

The study uses UTCSR RL-06 GRACE/GRACE-FO spherical-harmonic coefficients, downscaled from about 1° to 0.25°, with GLDAS Catchment L4 V2.2 and WGHM 2.2d auxiliary inputs. The study period is April 2002–September 2022.

Published results include:
- positive TWS trend range **+7.3 to +9.5 mm/year**;
- seasonal variation approximately **−170 to +330 mm**;
- regional GRACE/GLDAS agreement **r = 0.92**, RMSE approximately **35 mm**.

The article says its processed data are available from the corresponding author upon reasonable request. Its monthly processed series is not treated here as openly downloadable.

## 3. Scientific comparison: limits and correct wording

The project may state:

> Published studies report groundwater-storage depletion in California’s Central Valley and increasing total terrestrial water storage in the Inner Niger Delta. These are contrasting hydrological contexts, but not a direct numerical comparison because the studies measure different storage components and use different input products, processing methods and time windows.

The project must not state that the two published slopes are the same TWS variable, that AstrOsint01 calculated them, or that increasing TWS proves improved water access or caused specific flood impacts.

For a new like-for-like AstrOsint01 comparison, extract the same JPL RL06.3Mv04 variable for both regions, use documented region masks and area weighting, select a common time window, retain missing months, and apply the same trend procedure. Report the project-derived result separately from published literature benchmarks.

Groundwater-specific comparisons require a separate component-separation workflow and auxiliary datasets for both regions.

## 4. OSINT research standard

For ownership, water allocation, pumping, exports, flood impacts or displacement, register each claim separately and link it to its exact source passage, table, figure or administrative record.

Use primary records where possible: water rights, well permits, pumping reports, land/parcel data, crop acreage, official flood records and satellite products. Peer-reviewed studies provide scientific context; official situation reports document reported impacts; journalism is a lead source, not proof of legal ownership or groundwater control.

Distinguish:
- **Observation:** what the dataset directly measures.
- **Published result:** what an external study reports.
- **Interpretation:** what the evidence reasonably suggests.
- **Hypothesis:** a plausible explanation requiring further verification.

Land ownership concentration does not by itself establish groundwater rights, pumping volumes or allocation. A regional TWS trend does not establish local household access to safe water. Flood reports do not establish that a long-term storage trend caused a specific flood.

## 5. Research status

**Verified in this revision:** NASA/JPL product metadata; the cited study abstracts and methods; the published values and their variable definitions; the Inner Niger study's data-availability statement.

**Not yet established as AstrOsint01 outputs:** raw monthly regional series, regional masks, trend slopes, confidence intervals, p-values, Mann–Kendall tests, Sen's slopes, InSAR subsidence calculations, ownership statistics, or causal attribution of flood impacts.

The repository's PUBLISHED_STUDY_BENCHMARKS.csv contains cited literature results and NASA product metadata—not raw monthly NASA observations. The actual NetCDF extraction, checksum, mask, processing script and project-generated series must be committed before claiming a team calculation.

## Source register

See:
- [Research audit and corrections](RESEARCH_AUDIT_AND_CORRECTIONS.md)
- [Evidence register](EVIDENCE_REGISTER_TEMPLATE.md)
- [NASA data provenance and access notes](../data/README.md)
- [Published study benchmark CSV](../data/PUBLISHED_STUDY_BENCHMARKS.csv)

**Primary sources**
1. Wiese et al. (2023), NASA/JPL PO.DAAC RL06.3Mv04 CRI-filtered mascon product: https://doi.org/10.5067/TEMSC-3JC634
2. Liu et al. (2022), Central Valley groundwater depletion: https://pmc.ncbi.nlm.nih.gov/articles/PMC9763392/
3. Fatolazadeh & Goïta (2025), Inner Niger Delta TWS: https://www.mdpi.com/2073-4441/17/8/1121
4. NASA GRACE Tellus documentation: https://grace.jpl.nasa.gov/data/get-data/jpl_global_mascons/

---
**This dossier is a source-audited research reference. It does not claim that the prototype or the team's own quantitative analysis has been tested or completed.**

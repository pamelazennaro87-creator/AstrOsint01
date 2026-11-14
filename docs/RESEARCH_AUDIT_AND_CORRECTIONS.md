# AstrOsint01 — Research Audit, Corrections & Verified Baseline

**Audit date:** 2026-11-14  
**Scope:** research claims and data provenance only. This document does not describe or test the prototype.

## Executive finding

The research direction is promising, but the previous FINAL_COMPLETE_OSINT_PACKAGE.md overstates what has been independently verified and treats two published estimates as if they were measurements of the same variable. That comparison is not scientifically valid as currently worded.

The most important correction:

- **California Central Valley:** Liu et al. (2022) report a *groundwater storage anomaly* (GWA) depletion trend of **15.7 ± 1.4 mm/year** for 2003–2021. Their GWA is derived from GRACE/FO total water storage after subtracting soil-moisture, snow-water-equivalent and surface-water anomalies.
- **Inner Niger Delta:** Fatolazadeh & Goïta (2025) report a *terrestrial water storage* (TWS) trend range of **+7.3 to +9.5 mm/year** for April 2002–September 2022. Their analysis uses UTCSR RL-06 spherical-harmonic GRACE/GRACE-FO solutions, downscaled to 0.25°, with GLDAS and WGHM auxiliary data.

These are **not like-for-like estimates**. They differ in physical variable, product/processing, time period and spatial method. They may be shown as two published case-study findings with explicit labels, but must not be presented as a controlled numerical comparison or as two outputs calculated by AstrOsint01.

## 1. Verified NASA source dataset

### Selected official product

JPL/PO.DAAC, **TELLUS_GRAC-GRFO_MASCON_CRI_GRID_RL06.3_V4**  
Release: **RL06.3Mv04**  
DOI: [10.5067/TEMSC-3JC634](https://doi.org/10.5067/TEMSC-3JC634)  
Product page: https://podaac.jpl.nasa.gov/dataset/TELLUS_GRAC-GRFO_MASCON_CRI_GRID_RL06.3_V4

Verified product metadata from PO.DAAC:

| Attribute | Verified metadata |
|---|---|
| Provider | NASA/JPL PO.DAAC |
| Product short name | TELLUS_GRAC-GRFO_MASCON_CRI_GRID_RL06.3_V4 |
| Release | RL06.3Mv04 |
| Format | netCDF-4 |
| Temporal cadence | Monthly |
| Product coverage | 2002-04-04 to present |
| Latest granule shown on audit date | 2026-09-16 |
| Main variable | lwe_thickness |
| Main variable units | cm equivalent liquid-water thickness |
| Uncertainty variable | uncertainty, cm |
| Other useful variables | land_mask, mascon_ID, scale_factor, time |
| Native mascon basis | 4,551 estimates on an equal-area 3° mascon grid |
| Display grid | 0.5° × 0.5° |
| CRI treatment | Reduces land/ocean leakage for mascons crossing coastlines |

**Important resolution warning:** a 0.5° display grid is not 0.5° independent measurement resolution. The native mascon solution is based on approximately 3° equal-area mascons. Do not describe this as village-, farm- or field-scale measurement.

PO.DAAC states that the CRI-filtered product is recommended for most land-hydrology applications. The product includes a land mask, mascon IDs and uncertainty information. Apply scale factors only if the analysis explicitly requires them and document the choice; do not silently apply them.

### Access and reproducibility

PO.DAAC documents the podaac-data-downloader / podaac-data-subscriber workflow. The underlying data files are in an Earthdata Login-protected collection; users need an Earthdata account/token to retrieve protected files. The repository should therefore record:

- exact filename and checksum of each downloaded granule or subset;
- download date and product DOI/version;
- variable name, units and any scale-factor decision;
- region polygon source, version and CRS;
- missing-month list;
- script/notebook commit that generated the regional series.

Official product page and download instructions:  
https://podaac.jpl.nasa.gov/dataset/TELLUS_GRAC-GRFO_MASCON_CRI_GRID_RL06.3_V4

A real monthly series must be extracted from the actual NetCDF granules. **Do not create, interpolate, digitize from a chart, or hand-type a monthly series and label it NASA data.** The CSV in data/PUBLISHED_STUDY_BENCHMARKS.csv is a set of published study results, not raw monthly observations.

## 2. Central Valley — what the paper actually measured

**Source:** Liu et al. (2022), “Groundwater depletion in California’s Central Valley accelerates during megadrought,” *Nature Communications* 13, 7825.  
https://www.nature.com/articles/s41467-022-35582-x  
Open-access full text: https://pmc.ncbi.nlm.nih.gov/articles/PMC9763392/

The paper reports:

- GRACE/GRACE-FO TWS anomalies for the combined Sacramento, San Joaquin and Tulare basins.
- Groundwater storage anomalies estimated as:

**GWA = TWSA − SMA − SWEA − SWA**

where SMA is soil-moisture anomaly, SWEA is snow-water-equivalent anomaly, and SWA is surface-water anomaly.
- The auxiliary inputs include NLDAS-2 soil moisture, SNODAS snow-water equivalent and California Data Exchange Center surface-water information.
- The published groundwater depletion trend is **15.7 ± 1.4 mm/year** over **2003–2021**.
- The paper also reports a groundwater loss of **20.0 ± 5.1 km³** from September 2019 to December 2021, with a much faster rate during that drought interval.

**Interpretation:** 15.7 ± 1.4 mm/year is a published, component-derived groundwater anomaly estimate. It is not the raw JPL mascon TWSA slope and it is not an AstrOsint01 calculation. Reproducing it requires the paper's auxiliary datasets, basin mask, anomaly baselines, gap treatment and processing choices—not just plotting the JPL TWS field.

## 3. Inner Niger Delta — what the paper actually measured

**Source:** Fatolazadeh, F. & Goïta, K. (2025), “Understanding Terrestrial Water Storage Changes Derived from the GRACE/GRACE-FO in the Inner Niger Delta in West Africa,” *Water* 17(8), 1121.  
https://doi.org/10.3390/w17081121  
Full text: https://www.mdpi.com/2073-4441/17/8/1121

Verified methods and findings:

- Study period: **April 2002–September 2022**.
- GRACE/GRACE-FO input: **UTCSR RL-06 spherical-harmonic coefficients**, degree/order up to 60, not the JPL RL06.3Mv04 CRI mascon grid selected above.
- The study reports a native spatial resolution of about 1° and a spectral-combination downscaling to 0.25°.
- GLDAS Catchment L4 V2.2 at 0.25° was used for soil moisture, canopy water, groundwater, precipitation and potential evapotranspiration.
- WGHM 2.2d was used for surface-water bodies; those surface-water data were available only through the end of 2016.
- The abstract reports TWS seasonal variation from approximately −170 to +330 mm and a positive TWS trend range of **+7.3 to +9.5 mm/year**.
- The paper reports GRACE/GRACE-FO versus GLDAS agreement of **r = 0.92** and **RMSE ≈ 35 mm** for the regional mean series.
- The paper explicitly notes coarse GRACE resolution and the need for higher-resolution hydrological models and in-situ observations.

**Data availability:** the article states that its data are available from the corresponding author upon reasonable request. The paper's reported results can be cited, but its processed monthly study series must not be represented as an openly downloadable dataset unless obtained from the authors.

**Interpretation:** the positive trend is a published TWS result. It does not establish that all households have improved access to safe water, nor does it by itself establish a causal increase in flood damage.

## 4. What the current comparison can and cannot say

### Defensible statement

> Published studies report groundwater-storage depletion in California’s Central Valley and increasing total terrestrial water storage in the Inner Niger Delta. These findings describe contrasting hydrological contexts, but they are not a direct numerical comparison: the studies use different storage components, input products, spatial processing and time windows.

### Not defensible without new analysis

- “NASA measures a −15.7 mm/year TWS trend in California and +7.3 to +9.5 mm/year TWS in Niger.”
- “Both rates were calculated by AstrOsint01.”
- “The Inner Niger trend is statistically significant” unless the exact statistical test and result are located and reported for the specific estimate being quoted.
- “Increasing TWS means every community has more available water.”
- “Increasing TWS caused the reported floods.”
- “Corporate land ownership proves control of groundwater rights, pumping or allocation.”

### A fair next-step comparison

Use the **same JPL RL06.3Mv04 CRI mascon product**, the same variable (lwe_thickness / TWS anomaly), common monthly time window, documented regional masks, same area-weighting method and same trend procedure for both regions. Report this as a new AstrOsint01 TWS comparison.

Keep the published groundwater-specific California estimate as a separate contextual reference. Do not mix it into the same chart as the Inner Niger TWS trend.

For a groundwater-component comparison, both regions would need a documented and scientifically defensible component-separation workflow, compatible auxiliary models and uncertainty treatment. That is a separate, more demanding analysis.

## 5. Audit of claims in the previous research package

The following claims should be removed, narrowed or left explicitly unverified until primary evidence is attached:

| Existing claim | Audit result | Required action |
|---|---|---|
| The two cited rates are opposite trends in the same TWS variable | Incorrect: California number is derived GWA; Niger number is TWS | Replace with the qualified statement in Section 4 |
| Inner Niger +7.3 to +9.5 mm/year is “statistically significant” | Not established by the cited abstract/range alone | Remove “statistically significant” unless test details are verified |
| NASA data “captures both trends with high confidence” | Overstates the team's own analysis | Attribute published findings; do not claim project calculations |
| Central Valley subsidence of about 1 m from 2015–2020 and peak rates of tens of cm/year | Specific numeric claim needs its exact InSAR source, polygon, period and figure/table | Hold until primary DWR/USGS/peer-reviewed source is registered |
| Top 10% own 73% of Fresno County farmland and 86% of Kings County farmland | Secondary-reported statistic; source and denominator need verification | Do not state as fact without original study, county definitions and ownership denominator |
| “Major actors” control groundwater | Land ownership is not proof of groundwater rights, pumping volumes or allocation | Build a separate evidence chain from water-rights, well/pumping and corporate records |
| Inner Niger rewetting caused higher flood risk/displacement in 2024–2026 | Causal claim and date-specific impacts are not established by the TWS paper | Require dated OCHA/national/field evidence and a separate attribution study |
| “New water bodies”, “reactivation of wadis”, “Lake Chad recovery” verify Inner Niger trend | Geographically and physically distinct claims; Lake Chad is not the Inner Niger Delta | Remove from this case unless separately scoped and sourced |
| All visuals already exist in repository | They were not present in the inspected main-branch tree | Mark as external/pending until committed with provenance |
| “Research phase complete”, “fully verified”, “competition ready” | Not supported by the inspected evidence | Replace with an honest status statement |

## 6. Evidence hierarchy for the OSINT layer

For every human-impact or control claim, prefer:

1. **Primary administrative data:** water rights, well permits, pumping/groundwater reports, land registry/parcel data, crop acreage, official flood records.
2. **Primary satellite/geospatial data:** NASA/USGS/JPL, Sentinel-1/2, Landsat, validated flood extent and subsidence products.
3. **Peer-reviewed research:** methods, study area, dates, uncertainty, figure/table and limitations.
4. **Official situation reports:** OCHA, national civil protection, basin authorities, Ramsar, FAO or other relevant agencies.
5. **Journalism and NGO reports:** useful for leads and human context, not a substitute for administrative proof.

Every claim must distinguish **observed fact**, **source-reported statement**, **interpretation** and **hypothesis**. Keep counter-evidence and uncertainty visible.

## 7. Repository status language

Until the team's own NetCDF extraction and calculations are committed and independently reproducible, use:

> “The project uses NASA/JPL GRACE-FO data as its primary Earth-observation source and cites peer-reviewed regional studies as published reference findings. The team’s own regional estimates are reported separately once the selected product, masks and processing workflow have been run and archived.”

Do not claim the team has calculated, validated or statistically tested a result unless the input file, processing code, output series and analysis metadata are available in the repository.

## 8. Primary references

- NASA/JPL PO.DAAC product record, JPL RL06.3Mv04 CRI mascons: https://podaac.jpl.nasa.gov/dataset/TELLUS_GRAC-GRFO_MASCON_CRI_GRID_RL06.3_V4
- Product DOI: https://doi.org/10.5067/TEMSC-3JC634
- Liu et al. (2022), Central Valley groundwater anomalies: https://pmc.ncbi.nlm.nih.gov/articles/PMC9763392/
- Fatolazadeh & Goïta (2025), Inner Niger Delta TWS: https://www.mdpi.com/2073-4441/17/8/1121
- NASA GRACE Tellus documentation: https://grace.jpl.nasa.gov/data/get-data/jpl_global_mascons/

---
**Status:** source audit completed for the sources above. This is not a claim that AstrOsint01's own regional time series or trend calculations have been completed.

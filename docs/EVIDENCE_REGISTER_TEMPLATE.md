# AstrOsint01 — Evidence Register (Source-Audited)

Use one row per factual claim that appears in the interface, presentation, README or spoken demo. Duplicate a row when one sentence contains multiple claims.

| ID | Exact claim / metric | Region / period | Source | Source class | What it supports | What it does NOT prove | AstrOsint01 status |
|---|---|---|---|---|---|---|---|
| NASA-JPL-01 | JPL RL06.3Mv04 CRI mascon product metadata; monthly lwe_thickness in cm; uncertainty field in cm | Global; 2002-04 to present (product record; latest granule 2026-09-16 at audit) | [NASA/JPL PO.DAAC product](https://podaac.jpl.nasa.gov/dataset/TELLUS_GRAC-GRFO_MASCON_CRI_GRID_RL06.3_V4), DOI [10.5067/TEMSC-3JC634](https://doi.org/10.5067/TEMSC-3JC634) | Primary data-product metadata | Product definition, release, variables, units, coverage, download instructions and scale limitations | No region-specific trend until actual granules are processed using a documented mask | Selected input product; no team extraction recorded |
| CA-GWA-01 | Published groundwater storage anomaly depletion trend −15.7 ± 1.4 mm/year | California Central Valley; 2003–2021 | Liu et al. (2022), [Nature Communications](https://doi.org/10.1038/s41467-022-35582-x) | Peer-reviewed study | Derived groundwater anomaly trend based on GRACE/FO TWSA less soil moisture, SWE and surface water anomalies | Not raw TWSA; not the JPL product's direct TWS slope; not an AstrOsint01 result | Published reference only; not reproduced |
| CA-GWA-02 | Published groundwater storage loss 20.0 ± 5.1 km³ | California Central Valley; Sep 2019–Dec 2021 | Liu et al. (2022), same paper | Peer-reviewed study | Published interval loss estimate during drought | Not a linear trend and not a project calculation | Published reference only; not reproduced |
| IND-TWS-01 | Published positive TWS trend range +7.3 to +9.5 mm/year | Inner Niger Delta; Apr 2002–Sep 2022 | Fatolazadeh & Goïta (2025), [Water 17(8), 1121](https://doi.org/10.3390/w17081121) | Peer-reviewed study | Published TWS trend range from UTCSR RL-06 GRACE/FO analysis | Does not establish a like-for-like comparison with California GWA; not an AstrOsint01 result | Published reference only; not reproduced |
| IND-TWS-02 | Seasonal TWS variation approximately −170 to +330 mm; GRACE/GLDAS r=0.92 and RMSE≈35 mm | Inner Niger Delta; Apr 2002–Sep 2022 | Fatolazadeh & Goïta (2025), same paper | Peer-reviewed study | Published seasonal amplitude and agreement statistics | Correlation does not make either dataset ground truth; no proof of universal water access | Published reference only; not reproduced |
| IND-DATA-01 | Processed study data available from corresponding author upon reasonable request | Inner Niger Delta study | Fatolazadeh & Goïta (2025), Data Availability Statement | Publisher statement | Access status for the paper's processed data | Does not mean the study's monthly series is openly downloadable | Access not obtained |
| ACCESS-01 | Accessibility feature/test statement | Application-wide | [WCAG 2.2](https://www.w3.org/TR/WCAG22/) plus recorded project test evidence | Standard + test evidence | Only criteria and scope actually tested | A design intention or one successful test does not prove the whole application is safe or conformant | Not tested until evidence attached |

## Critical comparability rule

The California −15.7 ± 1.4 mm/year figure is a derived **groundwater storage anomaly** estimate. The Inner Niger +7.3 to +9.5 mm/year figure is a **total terrestrial water storage** trend range. Different variables, source products, processing and periods mean these values must not be presented as a direct numerical comparison.

For an AstrOsint01 two-region comparison, calculate TWSA for both regions from the same JPL RL06.3Mv04 product, same time window, documented masks and identical processing. Keep published groundwater-specific estimates in a separate literature-reference panel.

## Evidence status vocabulary

- **Verified source metadata:** the original data-product record or paper has been inspected.
- **Published result:** a result reported by an external study; never present as the team's own calculation.
- **Team calculation:** independently reproduced from archived input data and versioned code.
- **Partially supported:** source supports part of the wording; narrow the claim.
- **Unverified:** source or underlying evidence has not been inspected.
- **Contradicted:** evidence conflicts with the claim; remove or correct it.

## Review rules

1. Keep a stable ID when the same claim appears in multiple project materials.
2. Save data-product version, access date, filename/checksum and processing commit for every team calculation.
3. Link to the original paper/report, not only a search result or secondary summary.
4. Record the exact figure/table/page that supports a numeric statement.
5. Record counter-evidence and limitations, not only confirming sources.
6. Remove claims that cannot be traced before the final demo.

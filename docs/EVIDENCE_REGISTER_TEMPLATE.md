# AstrOsint01 — Evidence Register (Working Template)

Use one row per factual claim that appears in the interface, presentation, README or spoken demo. Duplicate a row when one sentence contains multiple claims.

| ID | Exact claim shown to users | Region / period | Source title + publisher | Direct URL / DOI | Source class | Exact passage / page / figure | What it supports | What it does not prove | Confidence | Status / reviewer |
|---|---|---|---|---|---|---|---|---|---|---|
| TWS-CA-01 | Published Central Valley groundwater depletion estimate: 15.7 ± 1.4 mm/year, 2003–2021 | California Central Valley, 2003–2021 | Liu et al. (2022), Nature Communications | https://www.nature.com/articles/s41467-022-35582-x | Peer-reviewed study | Record the exact section/figure/table after review | Published GRACE/FO-based groundwater anomaly estimate | Not the same as the team's own raw TWSA slope; not a result calculated by this app unless independently reproduced | Pending team reproduction | Reference only |
| TWS-IND-01 | Published Inner Niger Delta TWS trend: +7.3 to +9.5 mm/year, April 2002–September 2022 | Inner Niger Delta, Mali, 2002–2022 | Fatolazadeh & Goïta (2025), Water 17(8), 1121 | https://doi.org/10.3390/w17081121 | Peer-reviewed study | Record exact section/table/figure after review | Published study's reported TWS trend range and seasonal context | Does not prove equal access, groundwater-only increase, or a causal explanation for local impacts | Pending team reproduction | Reference only |
| NASA-DATA-01 | Selected GRACE/GRACE-FO product metadata | Both case studies | NASA/JPL PO.DAAC RL06.3 v04 CRI-filtered mascon | https://podaac.jpl.nasa.gov/dataset/TELLUS_GRAC-GRFO_MASCON_CRI_GRID_RL06.3_V4 | Primary data product | Record version, variable, units, file ID and access date | Product definition, coverage, units and provider caveats | Does not itself validate a region-specific claim until processed with a documented mask | To be completed | Source selected |
| ACCESS-01 | Accessibility feature/test statement | Application-wide | WCAG 2.2 and recorded project tests | https://www.w3.org/TR/WCAG22/ | Standard + test evidence | Record criterion, test case and result | Conformance only for the criterion and scope actually tested | A design intention or one successful test does not prove the entire application is safe for every user | Not tested until evidence attached | Planned |

## Evidence status vocabulary

- **Verified:** source inspected and exact claim supported within its stated scope.
- **Partially supported:** source supports part of the wording; narrow the claim.
- **Unverified:** source or underlying evidence has not yet been inspected.
- **Contradicted:** evidence conflicts with the claim; remove or correct it.
- **Team calculation:** independently reproduced from archived input data and versioned code.
- **Published result:** a result reported by an external study; never present as the team's own calculation.

## Review rules

1. Keep a stable ID when the same claim appears in multiple project materials.
2. Save data-product version, access date, filename/checksum and processing commit for every team calculation.
3. Link to the original paper/report, not only a search result or secondary summary.
4. Quote or point to the exact figure/table/page that supports a numeric statement.
5. Record counter-evidence and limitations, not only confirming sources.
6. Remove claims that cannot be traced before the final demo.

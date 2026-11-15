# AstrOsint01

**Accessible, evidence-first Earth-observation investigation**  
NASA Space Apps Challenge 2026 — *Be An Earth System Trend Detective!*

## Project focus

**Earth is changing. Follow the water.**

AstrOsint01 explores monthly total-water-storage anomalies (TWSa), modelled land-water components and GEOGloWS-derived groundwater-storage residuals (GWSa). The project combines satellite-gravimetry products (GRACE / GRACE-FO), complementary land-surface modelling (GLDAS Noah), an interactive data explorer and an OSINT-style evidence workflow:

**DETECT → COMPARE → VERIFY → EXPLORE**

### Current study areas

- **California Central Valley** — the project CSV shows a negative full-record signal in TWSa and the model-derived GWSa residual. Independent research documents groundwater depletion and land subsidence.
- **Taoudeni–Tanezrouft Basin** — the second CSV is labelled for this basin. Its exported series shows near-flat total-water storage and a slightly negative groundwater trend.

**Important interpretation limitation:** GEOGloWS-derived GWSa is a model-derived residual, not a direct well measurement. Surface-water storage may remain in the residual. Taoudeni–Tanezrouft is not interchangeable with the Inner Niger Delta; the separate Inner Niger Delta study in the research dossier is contextual literature, not the result of this CSV.

The NASA PO.DAAC GLDAS Noah 3.3 collection documented here is a separate monthly model product: its stated aggregate is soil moisture + snow water + canopy water. It does not provide groundwater storage and must not be confused with the existing GEOGloWS CSV workflow or presented as an independent in-situ validation dataset.

## Explore

- [Open the website](https://pamelazennaro87-creator.github.io/AstrOsint01/)
- [Launch the Water Signal Explorer](https://pamelazennaro87-creator.github.io/AstrOsint01/explorer/)
- [Open the source code](https://github.com/pamelazennaro87-creator/AstrOsint01)
- [Central Valley CSV](https://github.com/AstrOsint01/nasa-water-storage-analysis/blob/main/central_valley.csv.csv)
- [Taoudeni–Tanezrouft CSV](https://github.com/AstrOsint01/nasa-water-storage-analysis/blob/main/taoudeni-tanezrouft%20basin.csv.csv)

## Method and evidence

The Explorer:
- reads monthly CSV files from the project data repository;
- lets visitors switch region, variable and time window;
- displays the time series and a descriptive ordinary least-squares trend;
- includes **Evidence Delta**, a three-window trend comparison (full record / 10 years / 5 years) that flags possible direction changes without presenting them as forecasts or causal findings;
- includes **Evidence Constellation**, an OSINT-style evidence chain linking the project CSV, reported satellite/model workflow, descriptive analysis and still-missing independent checks, with explicit provenance statuses;
- fits the trend to observed, non-filled values only;
- shows gap-filled months separately;
- states geographic and spatial-resolution limitations.

The trend is descriptive. It is not a significance test, forecast or causal model. GRACE's coarse spatial footprint requires complementary local evidence for finer-scale interpretation.

## Key documents

- [Data provenance and validation audit](docs/DATA_PROVENANCE_AUDIT.md) — inspected CSVs, confirmed fields, unresolved source metadata and next validation steps.
- [Evidence Constellation method](docs/EVIDENCE_CONSTELLATION_METHOD.md) — evidence-node definitions, status rules, geographic safeguards and what is required before a claim can be upgraded.
- [Copernicus TWSA — dataset profile](docs/COPERNICUS_TWSA_01_DATASET_PROFILE.md) — source identity, coverage, grid, variables and licence.
- [Copernicus TWSA — access and integration](docs/COPERNICUS_TWSA_02_ACCESS_AND_INTEGRATION.md) — STAC/CDS discovery, acquisition workflow and ingestion checks.
- [Copernicus TWSA — scientific use](docs/COPERNICUS_TWSA_03_SCIENTIFIC_USE.md) — interpretation, uncertainty, limitations and attribution.
- [NASA GLDAS Noah 3.3 — dataset profile](docs/NASA_GLDAS_NOAH_33_01_DATASET_PROFILE.md) — PO.DAAC source, components, coverage, variables and citation.
- [NASA GLDAS Noah 3.3 — access and integration](docs/NASA_GLDAS_NOAH_33_02_ACCESS_AND_INTEGRATION.md) — Earthdata/PO.DAAC discovery, acquisition workflow and validation.
- [NASA GLDAS Noah 3.3 — scientific use](docs/COPERNICUS_TWSA_03_SCIENTIFIC_USE.md#9-nasa-po-daac-gldas-noah-33-correct-scientific-role) — how GLDAS should and should not be compared with TWSA.

| Document | Purpose |
|---|---|
| [STORY.md](STORY.md) | Narrative, case files and evidence boundaries |
| [MISSION.md](MISSION.md) | Mission, method and accessibility goals |
| [Research dossier](docs/FINAL_COMPLETE_OSINT_PACKAGE.md) | Working research claims, sources and verification status |
| [Accessibility and photosensitive safety](docs/ACCESSIBILITY_EPILEPSY_SAFE.md) | Design safeguards and testing commitments |

## Official data sources

- [Copernicus C3S TWSA v1.0 — STAC collection](https://cds.climate.copernicus.eu/stac-browser/collections/satellite-terrestrial-water-storage?.language=en) — GRACE/GRACE-FO-derived TWSA product.
- [NASA PO.DAAC GLDAS Noah 3.3 — dataset page](https://podaac.jpl.nasa.gov/dataset/TELLUS_GLDAS-NOAH-3.3_TWS-ANOMALY_MONTHLY) — modelled soil moisture, snow and canopy-water aggregate.
- [NASA Earthdata granule search](https://search.earthdata.nasa.gov/search/granules?p=C2036877565-POCLOUD) — granule discovery for the PO.DAAC collection.
- [GLDAS project documentation](https://ldas.gsfc.nasa.gov/gldas)

## Accessibility

We prioritize keyboard navigation, readable structure, reduced motion, no flashing effects, data tables and text explanations alongside charts. Safe Mode is available in the site and Explorer. These are design safeguards, not clinical certification; testing with assistive technologies and users remains necessary.

## Current status

The website and CSV-backed Explorer are working research prototypes. The NASA PO.DAAC and Copernicus sources are documented, but this documentation update does not mean new NetCDF granules have been downloaded, processed or integrated into the Explorer. Geographic alignment, complete source traceability, statistical significance testing and user accessibility testing remain active validation tasks.

**Independent exploration. Shared evidence. Verifiable conclusions.**

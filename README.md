# AstrOsint01

**Accessible, evidence-first Earth-observation investigation**  
NASA Space Apps Challenge 2026 — *Be An Earth System Trend Detective!*

## Project focus

**Earth is changing. Follow the water.**

AstrOsint01 explores monthly terrestrial-water-storage and groundwater anomaly series derived from GRACE / GRACE-FO data. The experience combines an interactive data explorer with an OSINT-style evidence workflow:

**DETECT → COMPARE → VERIFY → EXPLORE**

### Current study areas

- **California Central Valley** — the project CSV shows a negative long-term signal in total-water and groundwater anomalies. Independent research documents groundwater depletion and land subsidence.
- **Taoudeni–Tanezrouft Basin** — the second CSV is labelled for this basin. Its exported series shows near-flat total-water storage and a slightly negative groundwater trend.

**Important geographic limitation:** Taoudeni–Tanezrouft is not interchangeable with the Inner Niger Delta. A separate peer-reviewed Inner Niger Delta study cited in the research dossier is contextual literature, not the result of this CSV. We do not present the two as the same measurement.

## Explore

- [Open the website](https://pamelazennaro87-creator.github.io/AstrOsint01/)
- [Launch the Water Signal Explorer](https://pamelazennaro87-creator.github.io/AstrOsint01/explorer/)
- [Open the source code](https://github.com/pamelazennaro87-creator/AstrOsint01)
- [Open the monthly source datasets](https://github.com/AstrOsint01/nasa-water-storage-analysis)

## Method and evidence

The Explorer:
- reads monthly CSV files from the project data repository;
- lets visitors switch region, variable and time window;
- displays the time series and a descriptive ordinary least-squares trend;
- fits the trend to observed, non-filled values only;
- shows gap-filled months separately;
- states geographic and spatial-resolution limitations.

The trend is descriptive. It is not a significance test, forecast or causal model. GRACE's coarse spatial footprint requires complementary local evidence for finer-scale interpretation.

## Key documents

- [Data provenance and validation audit](docs/DATA_PROVENANCE_AUDIT.md) — inspected CSVs, confirmed fields, unresolved source metadata and next validation steps.

| Document | Purpose |
|---|---|
| [STORY.md](STORY.md) | Narrative, case files and evidence boundaries |
| [MISSION.md](MISSION.md) | Mission, method and accessibility goals |
| [Research dossier](docs/FINAL_COMPLETE_OSINT_PACKAGE.md) | Working research claims, sources and verification status |
| [Accessibility and photosensitive safety](docs/ACCESSIBILITY_EPILEPSY_SAFE.md) | Design safeguards and testing commitments |

## Accessibility

We prioritize keyboard navigation, readable structure, reduced motion, no flashing effects, data tables and text explanations alongside charts. Safe Mode is available in the site and Explorer. These are design safeguards, not clinical certification; testing with assistive technologies and users remains necessary.

## Current status

The website and CSV-backed Explorer are working research prototypes. Geographic alignment, source traceability for all secondary claims, statistical significance testing and user accessibility testing remain active validation tasks.

**Independent exploration. Shared evidence. Verifiable conclusions.**

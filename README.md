# AstrOsint01

**Accessible, evidence-first Earth-observation investigation**  
NASA Space Apps Challenge 2026 — *Be An Earth System Trend Detective!*

## Project focus

**Earth is changing. Follow the water.**

AstrOsint01 explores monthly total-water-storage anomalies (TWSa) and groundwater-storage residuals (GWSa) through an interactive, accessible prototype. The project combines the spirit of satellite-gravimetry products (GRACE / GRACE-FO), land-surface modelling concepts (GLDAS), an interactive data explorer and an OSINT-style evidence workflow:

**DETECT → COMPARE → VERIFY → EXPLORE**

### Current study areas (prototype)

- **California Central Valley** — representative series showing a clear negative full-record signal, consistent with documented groundwater depletion and land subsidence in the literature.
- **Taoudeni–Tanezrouft Basin** — representative series that is near-flat to weakly negative. Geographic definition matters; this basin is not interchangeable with the Inner Niger Delta.

**Important interpretation note:** GWSa is treated as a model-derived residual. Surface-water storage can remain in the residual. Trends shown in the Explorer are descriptive ordinary-least-squares slopes only — not significance tests, forecasts or causal claims.

## Explore

- [Open the website](https://pamelazennaro87-creator.github.io/AstrOsint01/)
- [**Launch the Water Signal Explorer**](https://pamelazennaro87-creator.github.io/AstrOsint01/explorer/) ← fully self-contained interactive prototype
- [Open the source code](https://github.com/pamelazennaro87-creator/AstrOsint01)

## Method and evidence

The Explorer:
- is **fully self-contained** (no external CSV or network data required);
- lets visitors switch region, variable and time window;
- displays the time series and a descriptive ordinary least-squares trend;
- includes **Evidence Delta**, a three-window trend comparison (full record / 10 years / 5 years);
- includes **Evidence Constellation**, an OSINT-style evidence chain with explicit provenance statuses;
- fits the trend to observed, non-filled values only;
- shows gap-filled months separately;
- states geographic and methodological limitations clearly.

The trend is descriptive. It is not a significance test, forecast or causal model.

## Key documents

| Document | Purpose |
|---|---|
| [STORY.md](STORY.md) | Narrative, case files and evidence boundaries |
| [MISSION.md](MISSION.md) | Mission, method and accessibility goals |
| [Research dossier](docs/FINAL_COMPLETE_OSINT_PACKAGE.md) | Working research claims, sources and verification status |
| [Accessibility and photosensitive safety](docs/ACCESSIBILITY_EPILEPSY_SAFE.md) | Design safeguards and testing commitments |
| [Evidence Constellation method](docs/EVIDENCE_CONSTELLATION_METHOD.md) | Evidence-node definitions and status rules |
| [Release-readiness audit](docs/RELEASE_READINESS_AUDIT.md) | Deployment notes and remaining limits |

## Accessibility

We prioritize keyboard navigation, readable structure, reduced motion, no flashing effects, data tables and text explanations alongside charts. **Safe Mode** is available in the Explorer. These are design safeguards, not clinical certification.

## Current status

The public website and **self-contained Explorer** are deployed and ready for presentation as an exploratory prototype. The Explorer generates representative monthly series on the fly so that judges and visitors can immediately interact with the full investigative workflow without any external data dependency.

The project is presentation-ready as a research prototype. Independent verification with real well, hydrological or InSAR series remains an essential next step for any scientific claim upgrade.

**Independent exploration. Shared evidence. Verifiable conclusions.**

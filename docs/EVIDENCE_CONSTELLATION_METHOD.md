# Evidence Constellation — method and evidence rules

**AstrOsint01 · Water Signal Explorer**

## Purpose

Evidence Constellation is an OSINT-style claim-tracing view. It makes the path from a published project data file to an analytical statement visible, while showing missing links. It is designed to prevent a descriptive satellite/model signal from being presented as independently verified local ground truth.

## Nodes and status definitions

1. **Project source record — IN REPOSITORY**  
   The monthly CSV used by the Explorer is present in the linked project data repository. This status confirms file availability, not the original scientific export's completeness or correctness.

2. **Satellite signal — PROVENANCE LIMITED**  
   Project documentation reports a GRACE / GRACE-FO TWS anomaly workflow. The exact export receipt, product/version, processing configuration and region polygon are not archived alongside the CSV. The graph therefore does not claim that this chain has been independently reproduced from raw NASA granules.

3. **Model residual — MODEL-DERIVED**  
   GWSa is described as a residual derived using GLDAS land-surface components. It is not a direct groundwater-well measurement. Surface-water storage may remain in the residual and can influence interpretation.

4. **Analytical signal — REPRODUCIBLE IN EXPLORER**  
   The current browser Explorer calculates descriptive ordinary least-squares trends from observed, non-filled monthly values and compares nested time windows through Evidence Delta. Reproducibility of this calculation does not establish the validity of the original geographic mask or causal interpretation.

5. **Independent evidence — NOT YET LINKED**  
   The current graph does not join matched well measurements, river/reservoir observations, land-subsidence time series or field observations to the same region boundary and temporal window. External context in a research dossier is not equivalent to a spatially and temporally matched validation dataset.

## Geographic safeguards

- **California Central Valley:** external literature and public reporting describe groundwater depletion and land subsidence in the broader region. The Explorer does not currently link a specific well or subsidence series to the exact CSV polygon and period. Treat this as context for follow-up, not as point-by-point validation of the CSV.
- **Taoudeni–Tanezrouft Basin:** preserve the name used by the source CSV. Do not relabel this dataset as the Inner Niger Delta. The polygon and original export receipt remain unresolved; no matched independent hydrological observation is linked.

## Evidence-status rules

- **IN REPOSITORY** means a project file is present and addressable.
- **PROVENANCE LIMITED** means the claimed upstream lineage is documented at a high level, but one or more critical acquisition or processing records are missing.
- **MODEL-DERIVED** describes a model-based estimate or residual; it is not a quality score.
- **REPRODUCIBLE IN EXPLORER** means the displayed calculation is performed by the committed code from the selected CSV.
- **NOT YET LINKED** means the required independent dataset is not integrated into this evidence chain. It does not mean that no such data exist anywhere.

These labels are categorical workflow states, not probabilities, scientific confidence scores or truth rankings.

## Requirements to upgrade a node

Before upgrading provenance, archive:

- exact product short name, version, DOI/collection identifier and retrieval date;
- source granule/file names and checksums;
- export and processing settings;
- exact polygon geometry, coordinate reference system and area;
- treatment of missing months and gap filling;
- code/version used to generate the regional series.

Before upgrading independent validation, add a dataset with:

- traceable publisher and measurement method;
- spatial coverage demonstrably overlapping the exact study polygon;
- timestamps overlapping the satellite record;
- units, uncertainty and quality flags;
- documented limitations and a reproducible comparison method.

A dataset discovered in a catalogue is not an integrated dataset. A regional paper is not automatically a matched validation record. A correlation is not proof of causation.

## Candidate independent-source leads

The Explorer exposes discovery portals selected by study area. These links are **research leads only**; opening a portal does not mean its data have been downloaded, spatially matched, quality-controlled or used to validate the project CSV.

### California Central Valley

- [California Groundwater Live](https://calgwlive.water.ca.gov/) — California DWR groundwater-level, well and InSAR land-subsidence views.
- [California DWR groundwater data and tools](https://www.water.ca.gov/Programs/Groundwater-Management/Data-and-Tools) — official groundwater datasets and SGMA viewers.
- [NASA GRACE Tellus data](https://grace.jpl.nasa.gov/data/get-data/) — mission products and documentation for source-level verification.

### Taoudeni–Tanezrouft

- [OSS ITTAS programme document](https://www.oss-online.org/sites/default/files/2024-09/OSS-CoordinateManagementSharedWater.pdf) — regional context for the Iullemeden–Taoudeni/Tanezrouft transboundary aquifer system; not a matched monthly validation series for this CSV.
- [IGRAC data gateway](https://un-igrac.org/data/) — discovery route for groundwater datasets, wells and monitoring information. Coverage, licences and temporal availability must be checked.
- [NASA GRACE Tellus data](https://grace.jpl.nasa.gov/data/get-data/) — mission products and documentation for source-level verification.

A candidate source can be promoted to **INDEPENDENT DATA LINKED** only after the team records the exact dataset and version, publisher, download date, geometry/coordinates, temporal coverage, units, measurement method, uncertainty and quality flags. The comparison must then be reproducible and must use a spatial footprint and period appropriate to the project CSV. Do not infer basin-level coverage from a portal's general geographic scope.

## Interpretation principle

The graph's arrows represent the documented analytical workflow, not causal influence. Missing evidence is displayed as a first-class result. The purpose is to show what can be stated, what remains provisional and what observation would most efficiently reduce uncertainty.

**Design rule: every important claim should have a traceable source, a declared method and a visible uncertainty boundary.**

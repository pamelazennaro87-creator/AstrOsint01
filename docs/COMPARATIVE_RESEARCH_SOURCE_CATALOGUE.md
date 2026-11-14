# AstrOsint01 — Comparative Research Source Catalogue & Collection Plan

**Research scope:** Opposite Water Futures — California Central Valley and Inner Niger Delta (Mali).  
**Prepared:** 2026-11-14  
**Repository scope:** research/data documentation only. This document does not modify or validate the prototype.

## 1. Research questions

1. How have total terrestrial water storage anomalies changed in each region over a common observation period?
2. How do rainfall, river flow, flood extent and groundwater observations help explain the regional hydrological context?
3. Where are there independently observed signs of groundwater stress, land subsidence, drought or flood variability?
4. Which human activities and livelihoods depend on these water systems?
5. What can the available evidence establish about water management, and what remains unknown?

The analysis must distinguish physical water storage, groundwater levels, surface-water inundation, precipitation, water use and human access. They are related but are not interchangeable measurements.

## 2. Core cross-region dataset — NASA/JPL GRACE and GRACE-FO

**Selected product:** JPL GRACE/GRACE-FO Mascon CRI-filtered RL06.3 Version 04  
**Short name:** `TELLUS_GRAC-GRFO_MASCON_CRI_GRID_RL06.3_V4`  
**DOI:** https://doi.org/10.5067/TEMSC-3JC634  
**Product and access instructions:** https://podaac.jpl.nasa.gov/dataset/TELLUS_GRAC-GRFO_MASCON_CRI_GRID_RL06.3_V4

Use the same product, variable, time window, mask treatment, area weighting and trend procedure for both regions. Keep original monthly NetCDF-4 granules unchanged. Preserve `lwe_thickness`, `uncertainty`, `time`, `mascon_ID`, `land_mask` and relevant scale-factor metadata.

- Product coverage begins April 2002; retrieve the latest granules actually present in the archive.
- Check and report missing months, including the GRACE-to-GRACE-FO mission gap. Do not silently fill gaps.
- `lwe_thickness` is total terrestrial water storage anomaly (TWSA), not groundwater alone.
- The displayed 0.5° grid is not independent 0.5° measurement resolution; the native solution is based on approximately 3° equal-area mascons.
- Earthdata Login may be required. Never place credentials or access tokens in GitHub.

**Project output required:** one monthly regional TWSA CSV for each region, with units, uncertainty, spatial mask identifier/version, area-weighting method and missing-data flags. No team time series exists until these outputs are generated from archived granules and reproducible code.

## 3. California Central Valley — source inventory

### 3.1 Groundwater levels and well observations — California Department of Water Resources (DWR)

- Data and tools hub: https://www.water.ca.gov/Programs/Groundwater-Management/Data-and-Tools
- Periodic groundwater level measurements: https://data.cnra.ca.gov/dataset/periodic-groundwater-level-measurements
- Water Data Library: https://wdl.water.ca.gov/waterdatalibrary/
- California Groundwater Live: https://calgwlive.water.ca.gov/
- SGMA Data Viewer: https://sgma.water.ca.gov/webgis/?appid=SGMADataViewer

**Use:** independent well-level observations, monitoring locations, groundwater basin context and time series where available. DWR documentation notes that many periodic wells are measured about twice yearly, while some stations have more frequent or continuous observations. Record each well's location, measurement date, measurement type, datum and quality flags.

**Limitation:** well measurements are point observations and do not automatically represent the entire Central Valley. Do not average wells without a documented spatial sampling/weighting method.

### 3.2 Groundwater pumping, surface-water interaction and hydrologic model — USGS Central Valley Hydrologic Model (CVHM)

- Spatial database and downloads: https://ca.water.usgs.gov/projects/central-valley/cvhm-database.html

The CVHM database exposes model inputs/outputs and spatial layers including groundwater levels, streamflow, streamflow gain/loss, subsidence observations, precipitation, reference evapotranspiration, land use/crop properties and modeled pumping-related information.

**Use:** contextualize the mechanisms linking surface-water availability, land-use change, groundwater pumping, groundwater levels and subsidence.

**Limitation:** distinguish model outputs from direct measurements. Record model version, calibration period, scenario and variable. Do not describe simulated pumping as observed pumping.

### 3.3 Land subsidence — DWR / USGS

- DWR land subsidence and groundwater resources hub: https://www.water.ca.gov/Programs/Groundwater-Management/Data-and-Tools
- DWR InSAR subsidence dataset: https://data.cnra.ca.gov/dataset/tre-altamira-insar-subsidence
- DWR ground-surface displacement / extensometer data: https://data.cnra.ca.gov/dataset/wdl-ground-surface-displacement
- USGS Central Valley Hydrologic Model: https://ca.water.usgs.gov/projects/central-valley/cvhm-database.html

**Use:** compare groundwater stress with independently measured or remotely sensed land-surface displacement.

**Limitation:** subsidence can be spatially variable and partly irreversible. State the sensor, reference period, units, spatial footprint and whether the result is InSAR, extensometer or model output. Subsidence is not, by itself, proof of a specific actor's pumping.

### 3.4 Cropland and land use — DWR

- DWR data and tools hub (includes California Land Use Viewer): https://www.water.ca.gov/Programs/Groundwater-Management/Data-and-Tools
- Statewide crop mapping: https://data.cnra.ca.gov/dataset/statewide-crop-mapping

**Use:** describe crop type and land-use context and examine spatial/temporal coincidence with groundwater stress.

**Limitation:** crop presence does not establish water source, water-right ownership, pumping volume or legal control. Require separate water-use or well evidence.

### 3.5 Precipitation, evapotranspiration and surface-water context

- California Irrigation Management Information System (CIMIS): https://cimis.water.ca.gov/
- California Data Exchange Center (CDEC): https://cdec.water.ca.gov/
- DWR climate and water data hub: https://www.water.ca.gov/Programs/Groundwater-Management/Data-and-Tools

**Use:** station observations of precipitation, reference evapotranspiration, snow/rain and stream/reservoir context where relevant. Preserve station IDs and metadata.

**Limitation:** station coverage is uneven. Do not compare a single station to a region-wide GRACE average without explaining representativeness.

### 3.6 Scientific reference — Central Valley groundwater component

Liu et al. (2022), “Groundwater depletion in California’s Central Valley accelerates during megadrought,” *Nature Communications* 13, 7825.  
https://doi.org/10.1038/s41467-022-35582-x  
Open text: https://pmc.ncbi.nlm.nih.gov/articles/PMC9763392/

The paper reports a derived groundwater storage anomaly depletion trend of −15.7 ± 1.4 mm/year for 2003–2021. It derives groundwater anomaly by subtracting soil moisture, snow-water-equivalent and surface-water anomalies from GRACE/FO TWS anomaly. It is a published literature result, not raw JPL TWSA and not an AstrOsint01 calculation.

## 4. Inner Niger Delta — source inventory

### 4.1 Hydrometric observations and flood forecasts — OPIDIN / Mali DNH

- OPIDIN main portal: https://opidin.org/en
- Flood viewer and forecast: https://opidin.org/en/floodviewer
- Rainfall context: https://opidin.org/en/rainfall
- Technical background: https://opidin.org/en/background/technical-background-opidin
- Approach and institutional partners: https://opidin.org/en/approach

OPIDIN was developed with the Direction Nationale de l'Hydraulique (DNH) in Mali, Wetlands International Mali and Altenburg & Wymenga. Its flood prediction uses daily water levels from hydrometric stations together with rainfall in the Upper Niger Basin. The technical background describes long records at stations including Mopti, Douna, Diré and Akka (some series extending back to 1922, 1931 and 1955 respectively).

**Use:** flood peak height/timing, seasonal flood recession, station-level water-level context and early-warning information. Preserve station, date, observed vs forecast status, unit and source timestamp.

**Limitation:** OPIDIN forecasts are seasonal products and not a substitute for the full raw DNH historical time series. The management of the tool and input data is handled by DNH. For reproducible historical analysis, request the original station records and metadata from DNH or the relevant authors/partners. Do not scrape forecast maps and present them as raw daily observations.

### 4.2 Satellite-derived rainfall — NASA GPM IMERG

- NASA IMERG overview: https://gpm.nasa.gov/data/imerg
- NASA GPM data directory and current product versions: https://gpm.nasa.gov/data/directory
- NASA GES DISC IMERG archive: https://disc.gsfc.nasa.gov/datasets?keywords=IMERG
- Google Earth Engine catalog, IMERG V07: https://developers.google.com/earth-engine/datasets/catalog/NASA_GPM_L3_IMERG_V07

IMERG combines satellite precipitation estimates and provides a long record spanning the TRMM/GPM eras. The NASA directory documents product versions, temporal resolutions, data formats and access paths.

**Recommended use:** select a research-quality Final Run product/version; aggregate daily/monthly precipitation over the defined Upper Niger Basin contributing area and the Inner Niger Delta study polygon as separate zones. Document the exact collection, version, band, units, temporal aggregation and quality flags.

**Limitation:** rainfall over the delta and rainfall upstream are not interchangeable. OPIDIN specifically highlights Upper Niger Basin rainfall as a driver of downstream river flow and later flooding. IMERG is satellite-estimated precipitation, not a rain-gauge observation.

### 4.3 Long-term Sahel rainfall and flood extent — Sahel Rain Index

- Main site and methods/downloads: https://sahelrainindex.info/

The site provides downloadable CSV data for annual Sahel rainfall anomalies and maximum flood extent, including the Inner Niger Delta. It reports a long historical context (rainfall index from 1900; maximum flood extent from 1922 to the most recent flood season shown).

**Use:** long-term contextual benchmark for annual rainfall and maximum inundated area. Record the site update date, CSV retrieval date, methodology and citations supplied by the publisher.

**Limitation:** regional indices are not equivalent to monthly GRACE TWSA or local household water access. Check the index's spatial definition and uncertainty before combining it with other products.

### 4.4 Inundation extent — Landsat / Google Earth Engine

B.B. et al. (2024), “Inner Niger Delta Inundation Extent (2010–2022) Based on Landsat Imagery and the Google Earth Engine,” *Remote Sensing* 16(11), 1853.  
https://www.mdpi.com/2072-4292/16/11/1853  
DOI: https://doi.org/10.3390/rs16111853

The study analyzes interannual variability of seasonal inundation using Landsat imagery and Google Earth Engine. Its data availability statement says spatial datasets are available in Google Earth Engine; daily discharge data were obtained from Mali's DNH and are available from the authors upon request and with DNH permission.

**Use:** independently inspectable satellite-derived flood extent and seasonal/interannual inundation patterns for 2010–2022.

**Limitation:** this is not a complete 2002-present monthly flood record. The daily discharge data are not openly attached to the paper. Record the exact Earth Engine collection, filters, cloud masking, water-classification method and region boundary if reproducing the study.

### 4.5 Surface-water extent and volume — multispectral imagery and radar altimetry

“Quantification of surface water extent and volume in the Inner Niger Delta (IND) over 2000–2022 using multispectral imagery and radar altimetry.”  
Publisher page: https://www.tandfonline.com/doi/full/10.1080/10106049.2024.2311203  
Open institutional copy: https://horizon.documentation.ird.fr/exl-doc/pleins_textes/2024-03/010089531.pdf

The paper describes use of multispectral imagery and radar altimetry, including ICESat-2 ATL13 inland-water products, and a flood model connected to in-situ water levels.

**Use:** additional surface-water context over 2000–2022, complementary to GRACE's total water storage measurement.

**Limitation:** surface-water extent/volume and GRACE TWSA are different variables. Do not add them together or treat one as validation of the other without a documented mass-balance method.

### 4.6 Livelihoods, ecosystem dependence and human context

- Wetlands International, “Sustaining the Inner Niger Delta Lifeline” synthesis report: https://www.wetlands.org/wp-content/uploads/dlm_uploads/2020/10/Synthesis-Report-EN-online-LR2.pdf
- CIFOR-ICRAF, “Rapid assessment of the Inner Niger Delta of Mali”: https://www.cifor-icraf.org/publications/downloads/Publications/PDFs/WP17336.PDF
- OPIDIN objectives and early-warning context: https://opidin.org/en/objective

These sources describe the importance of seasonal flooding to fisheries, rice farming, pastoralism, biodiversity and local livelihoods.

**Use:** contextualize why timing and extent of the flood pulse matter to people and ecosystems.

**Limitation:** reports and interviews are not direct measurements of water quantity, water rights or causal impacts for every household. Attribute statements to the report, date, sample and location. Avoid generalizing beyond the evidence.

### 4.7 Scientific reference — Inner Niger TWS

Fatolazadeh & Goïta (2025), “Understanding Terrestrial Water Storage Changes Derived from the GRACE/GRACE-FO in the Inner Niger Delta in West Africa,” *Water* 17(8), 1121.  
https://doi.org/10.3390/w17081121  
Full text: https://www.mdpi.com/2073-4441/17/8/1121

The study period is April 2002–September 2022 and the analysis uses UTCSR RL-06 spherical harmonics, GLDAS and WGHM auxiliary inputs, not the selected JPL RL06.3Mv04 CRI mascon product. Its published TWS trend range (+7.3 to +9.5 mm/year) is a literature benchmark only. The paper's processed data are available from the corresponding author upon reasonable request; do not claim its monthly series is openly downloadable unless obtained.

## 5. Region boundaries and comparability

Before extracting any regional time series, create and version two polygons:

- Central Valley: define whether the project uses the three-basin Central Valley study area (Sacramento, San Joaquin and Tulare) or another official basin boundary. State the choice and cite the source.
- Inner Niger Delta: choose a published/official study boundary and document it. Do not silently use the broader Niger River Basin or Upper Niger Basin as if it were the delta.

For both masks, archive:
- original boundary source and URL;
- source date/version and license;
- CRS and geometry validity checks;
- area in km²;
- polygon file checksum;
- any buffer, clipping or exclusion;
- fractional cell/mascon overlap or area-weighting method.

The Upper Niger Basin rainfall catchment is a third, distinct polygon and must not be conflated with the Inner Niger Delta mask.

## 6. Suggested repository layout

```text
data/
├── raw/
│   ├── grace/
│   ├── california_dwr/
│   ├── california_usgs_cvhm/
│   ├── california_climate/
│   ├── niger_opidin_dnh/
│   ├── niger_imerg/
│   ├── niger_landsat/
│   └── niger_flood_extent/
├── boundaries/
│   ├── central_valley/
│   └── inner_niger_delta/
├── processed/
│   ├── grace/
│   ├── central_valley/
│   └── inner_niger_delta/
├── metadata/
│   ├── source_inventory.csv
│   ├── download_log.csv
│   └── processing_metadata.json
└── PUBLISHED_STUDY_BENCHMARKS.csv
```

Do not commit large binary archives or protected data tokens. For oversized files, use an approved external archive/release and record stable URLs, access dates, licenses and SHA-256 checksums. Keep only small derived tables, metadata and reproducible code in Git when repository limits require it.

## 7. Minimum data dictionary for processed outputs

Every processed table must include, where applicable:

- `date` (ISO 8601 or clearly defined monthly timestamp);
- `region_id` and `region_name`;
- `variable` and `value`;
- `units`;
- `uncertainty` and uncertainty units, if supplied;
- `source_product`, `version`, `source_file` and source DOI/URL;
- `spatial_mask_id` and `area_weighting_method`;
- `quality_flag` and `missing_data_flag`;
- `processing_script_commit`.

Do not combine different variables into one ambiguous “water availability” column.

## 8. Analysis sequence

1. Freeze the two region polygons and the separate Upper Niger rainfall catchment polygon.
2. Download and inventory source files; retain originals and checksums.
3. Extract monthly JPL GRACE TWSA for both regions with identical methods and a common time window.
4. Independently collect California well levels, subsidence, crop/land-use and climate data.
5. Independently collect Niger hydrometric/flood, IMERG rainfall, inundation and livelihood context.
6. Check temporal coverage, missingness, spatial representativeness, units and uncertainty before analysis.
7. Calculate trends only after the above checks; report estimator, confidence interval, p-value only when a named test was actually run, and sensitivity to start/end dates and missing months.
8. Compare the two regions on the common TWSA metric. Present groundwater, rainfall, flood extent and human-impact measures as separate evidence layers.
9. Register each displayed claim in `docs/EVIDENCE_REGISTER_TEMPLATE.md` and link the exact source and output.

## 9. Interpretation guardrails

- TWSA is not groundwater-only storage.
- Groundwater level at a well is not the same as basin-wide groundwater volume.
- Satellite rainfall is not a direct rain-gauge observation.
- Flood extent is not flood depth, duration, damage or attribution.
- Land use/crop mapping does not prove water rights or pumping.
- Land ownership does not prove water control.
- Water storage trends do not establish safe drinking-water access or distributional equity.
- A temporal association is not causation.
- A modelled value is not an observation.
- A published study result is not a team calculation.

## 10. Current evidence status

**Completed in this document:** source discovery and a reproducible collection plan with explicit uses and limitations.

**Not yet completed:** downloading source granules, securing DNH historical station data, freezing region masks, generating project-specific regional monthly CSVs, calculating AstrOsint01 trends, or validating any application visualization.

The project must not claim these tasks are complete until the files, scripts, metadata and reproducible outputs are committed.

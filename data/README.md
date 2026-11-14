# AstrOsint01 data directory

## What is in this directory

- `PUBLISHED_STUDY_BENCHMARKS.csv` contains **numeric results reported by cited peer-reviewed papers**. These are literature benchmarks, not raw monthly observations and not calculations made by AstrOsint01.
- No fabricated or reconstructed monthly time series is stored here.
- The complete source catalogue, access routes, intended uses and limitations are documented in [Comparative Research Source Catalogue & Collection Plan](../docs/COMPARATIVE_RESEARCH_SOURCE_CATALOGUE.md).

## Primary cross-region dataset: NASA/JPL GRACE and GRACE-FO

**Product:** JPL GRACE and GRACE-FO Mascon CRI-filtered RL06.3 Version 04

- Short name: `TELLUS_GRAC-GRFO_MASCON_CRI_GRID_RL06.3_V4`
- DOI: https://doi.org/10.5067/TEMSC-3JC634
- Product page: https://podaac.jpl.nasa.gov/dataset/TELLUS_GRAC-GRFO_MASCON_CRI_GRID_RL06.3_V4
- Format: NetCDF-4
- Main variable: `lwe_thickness`
- Units: cm equivalent liquid-water thickness
- Monthly; product coverage begins April 2002.
- Other useful variables: `uncertainty`, `land_mask`, `mascon_ID`, `scale_factor`, `time`.

The collection's protected data files may require NASA Earthdata Login. PO.DAAC documents the data-download tools on the product page. Never commit credentials or access tokens.

## Additional source families

### California Central Valley
- DWR groundwater levels, well observations, SGMA and groundwater data: https://www.water.ca.gov/Programs/Groundwater-Management/Data-and-Tools
- Periodic well measurements: https://data.cnra.ca.gov/dataset/periodic-groundwater-level-measurements
- USGS Central Valley Hydrologic Model database: https://ca.water.usgs.gov/projects/central-valley/cvhm-database.html
- DWR InSAR land subsidence: https://data.cnra.ca.gov/dataset/tre-altamira-insar-subsidence
- DWR crop mapping and land-use tools: https://data.cnra.ca.gov/dataset/statewide-crop-mapping
- CIMIS and CDEC climate/hydrology observations: https://cimis.water.ca.gov/ and https://cdec.water.ca.gov/

### Inner Niger Delta
- OPIDIN flood forecasts, rainfall context and hydrometric background: https://opidin.org/en
- NASA GPM IMERG precipitation data and documentation: https://gpm.nasa.gov/data/imerg
- Sahel rainfall and maximum flood-extent CSVs: https://sahelrainindex.info/
- Landsat-derived inundation study (2010–2022): https://www.mdpi.com/2072-4292/16/11/1853
- Surface-water extent/volume study (2000–2022): https://doi.org/10.1080/10106049.2024.2311203
- Wetlands International livelihood synthesis: https://www.wetlands.org/wp-content/uploads/dlm_uploads/2020/10/Synthesis-Report-EN-online-LR2.pdf

These sources measure different phenomena. Keep groundwater levels, precipitation, surface-water inundation, flood forecasts, land use and TWSA as separate variables.

## Required provenance when raw data are added

For every source file or subset, add a companion metadata record with:

1. Product/source title, provider, version and DOI/URL.
2. Original filename and SHA-256 checksum.
3. Retrieval date and collection/granule/station identifier.
4. Variable name, original units and any conversion.
5. Region polygon source/version, CRS and area-weighting method.
6. Missing-date/month inventory and any exclusion rule.
7. Processing script/notebook path and Git commit.
8. Output checksum and exact analysis settings.

## Scientific warning

The product's 0.5° gridded display is not its independent spatial resolution: the solution is based on 4,551 equal-area 3° mascons. It measures regional mass/storage anomalies, not local well levels or drinking-water access.

A raw JPL TWS series must not be labelled groundwater. Groundwater storage anomalies require a separately documented component-separation workflow and auxiliary datasets.

## Current status

This directory contains published benchmarks and source documentation. It does **not** yet contain original GRACE monthly granules, project-specific regional CSVs, or AstrOsint01-derived trend calculations. Add those only after downloading, processing and documenting the real source files.

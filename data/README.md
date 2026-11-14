# AstrOsint01 data directory

## What is in this directory

- PUBLISHED_STUDY_BENCHMARKS.csv contains **numeric results reported by the cited peer-reviewed papers**. These are literature benchmarks, not raw monthly observations and not calculations made by AstrOsint01.
- No fabricated or reconstructed monthly time series is stored here.

## Primary NASA input selected for a reproducible project analysis

**NASA/JPL PO.DAAC JPL GRACE and GRACE-FO Mascon CRI-filtered RL06.3 Version 04**

- Short name: TELLUS_GRAC-GRFO_MASCON_CRI_GRID_RL06.3_V4
- DOI: https://doi.org/10.5067/TEMSC-3JC634
- Product page: https://podaac.jpl.nasa.gov/dataset/TELLUS_GRAC-GRFO_MASCON_CRI_GRID_RL06.3_V4
- Format: NetCDF-4
- Main variable: lwe_thickness
- Units: cm equivalent liquid-water thickness
- Monthly; global; product coverage begins April 2002.
- Product also provides uncertainty, land_mask, mascon_ID, scale_factor, and time coordinates.

The collection's protected data files require NASA Earthdata Login. PO.DAAC documents the podaac-data-downloader and podaac-data-subscriber clients on the product page. Do not commit credentials or access tokens.

## Required provenance when raw data are added

For every source file or subset, add a companion metadata record with:
1. Product short name, release and DOI.
2. Original filename and SHA-256 checksum.
3. Retrieval date and Earthdata collection/granule identifier.
4. Variable name, original units and any conversion.
5. Region polygon source/version, CRS and area-weighting method.
6. Missing-month inventory and any exclusion rule.
7. Processing script/notebook path and Git commit.
8. Output CSV checksum and the exact trend-analysis settings.

## Scientific warning

The product's 0.5° gridded display is not its independent spatial resolution: the solution is based on 4,551 equal-area 3° mascons. It measures regional mass/storage anomalies, not local well levels or drinking-water access.

A raw JPL TWS series must not be labelled groundwater. Groundwater storage anomalies require a separately documented component-separation workflow and auxiliary datasets.

# NASA PO.DAAC GLDAS Noah 3.3 — Dataset Profile

**Project:** AstrOsint01  
**Dataset short name:** `TELLUS_GLDAS-NOAH-3.3_TWS-ANOMALY_MONTHLY`  
**Version:** 3.3  
**Processing level:** Level 3  
**Collection concept ID:** `C2036877565-POCLOUD`  
**DOI:** https://doi.org/10.5067/GGDAS-3NH33

## Identity and provenance

- Publisher/data provider: NASA JPL Physical Oceanography Distributed Active Archive Center (PO.DAAC).
- Model: Global Land Data Assimilation System (GLDAS), Noah v3.3 land-hydrology model.
- Related missions: GRACE and GRACE Follow-On (GRACE-FO); the product is prepared for comparison with their monthly observations.
- Release date shown by PO.DAAC: 9 April 2020.
- Status shown by PO.DAAC: ACTIVE.
- Format: NetCDF-4.
- Global coverage: 180°W–180°E; 89.5°S–89.5°N.
- Spatial grid: 1° × 1°.
- Temporal sampling: monthly, over nominal GRACE/GRACE-FO months.
- Start date shown by PO.DAAC: 4 April 2002; the catalogue reports coverage through the present. Verify the actual granules and time coordinate at retrieval.

## What this dataset represents

The monthly anomaly is the sum of three GLDAS Noah modelled land-water components:

1. soil moisture;
2. snow water;
3. canopy water.

It is a model-derived component aggregate designed to support comparison with GRACE/GRACE-FO terrestrial-water-storage observations. It is **not** a complete observation of total terrestrial water storage and does **not** include groundwater storage estimates. It must not be described as a direct groundwater measurement or as independent in-situ ground truth.

PO.DAAC describes the monthly values as computed over the same days in each month as the corresponding GRACE/GRACE-FO data. The current catalogue says these days match the GRACE-FO monthly Level-2 RL06.3 JPL solutions. Preserve this temporal-alignment detail when comparing products.

## Variables reported by the catalogue

| Variable | Meaning | Units |
|---|---|---|
| `TWS_monthly` | Monthly terrestrial water storage aggregate/anomaly | mm |
| `lat` | Latitude coordinate | degrees_north |
| `lon` | Longitude coordinate | degrees_east |
| `time` | Time coordinate | days since 2002-01-01 00:00:00 UTC |

Confirm the actual NetCDF variable attributes, anomaly baseline, dimensions, fill values and time convention against downloaded granules and current documentation before processing.

## Official access and documentation

- [NASA PO.DAAC dataset landing page](https://podaac.jpl.nasa.gov/dataset/TELLUS_GLDAS-NOAH-3.3_TWS-ANOMALY_MONTHLY)
- [Earthdata granule search](https://search.earthdata.nasa.gov/search/granules?p=C2036877565-POCLOUD)
- [PO.DAAC collection directory](https://cmr.earthdata.nasa.gov/virtual-directory/collections/C2036877565-POCLOUD)
- [PO.DAAC Data Subscriber](https://github.com/podaac/data-subscriber)
- [GLDAS project documentation](https://ldas.gsfc.nasa.gov/gldas)
- [Dataset DOI](https://doi.org/10.5067/GGDAS-3NH33)
- [Rodell et al. (2004), GLDAS overview](https://doi.org/10.1175/BAMS-85-3-381)

## Required citation

Rodell M, et al. (2020). *TELLUS_GLDAS-NOAH-3.3_TWS-ANOMALY_MONTHLY*. Version 3.3. PO.DAAC, CA, USA. DOI: 10.5067/GGDAS-3NH33. Include the actual access date in any final citation.

## AstrOsint01 integration status

This document records catalogue metadata and the intended scientific role. It does not certify that granules have been downloaded, inspected, processed, or integrated into the Explorer.

**Status:** NASA source identified; metadata documented; acquisition, NetCDF validation and integration pending.

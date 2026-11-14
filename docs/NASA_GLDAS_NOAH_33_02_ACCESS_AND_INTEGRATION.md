# NASA PO.DAAC GLDAS Noah 3.3 — Access and Integration

**Project:** AstrOsint01  
**Dataset:** `TELLUS_GLDAS-NOAH-3.3_TWS-ANOMALY_MONTHLY`  
**Collection concept ID:** `C2036877565-POCLOUD`  
**DOI:** https://doi.org/10.5067/GGDAS-3NH33

## Official access routes

- [PO.DAAC dataset landing page](https://podaac.jpl.nasa.gov/dataset/TELLUS_GLDAS-NOAH-3.3_TWS-ANOMALY_MONTHLY)
- [Earthdata granule search](https://search.earthdata.nasa.gov/search/granules?p=C2036877565-POCLOUD)
- [PO.DAAC virtual collection directory](https://cmr.earthdata.nasa.gov/virtual-directory/collections/C2036877565-POCLOUD)
- [PO.DAAC Data Subscriber documentation and code](https://github.com/podaac/data-subscriber)
- [GLDAS project](https://ldas.gsfc.nasa.gov/gldas)

The PO.DAAC page identifies the collection as cloud-enabled and active. Bulk download is supported through the PO.DAAC Data Subscriber. Protected S3 access requires Earthdata Login credentials; do not publish credentials, tokens or signed URLs.

## Recommended acquisition workflow

1. Open the PO.DAAC landing page and confirm that version 3.3 and collection ID `C2036877565-POCLOUD` remain current.
2. Search granules through Earthdata Search and select the required monthly interval and, where supported, spatial subset.
3. Follow the current PO.DAAC Data Subscriber installation and authentication instructions. Use the collection short name exactly as listed above.
4. Download a small test interval first; do not begin with a full archive.
5. Preserve original NetCDF-4 granules unchanged. Record each granule's filename, source granule URL/identifier, retrieval timestamp (UTC), collection ID, time coverage and SHA-256 checksum.
6. Inspect the NetCDF header and coordinates. Confirm variable names, units, anomaly reference, time bounds and fill values from the actual file.
7. Create regional subsets only after the original granule has been validated. Record polygon/mask, weighting, resampling and any temporal alignment operations.

The PO.DAAC page provides a Data Subscriber route and Earthdata granule search. Do not hard-code guessed asset names or assume that a catalogue listing means anonymous download is available.

## Data engineering manifest

Record at minimum:
- dataset title, short name, version, collection concept ID and DOI;
- exact granule identifiers and source URLs;
- retrieval timestamp in UTC and SHA-256 checksums;
- time coordinate, nominal month/day coverage and actual temporal range;
- latitude/longitude arrays, grid spacing, dimensions and coordinate conventions;
- variable names, units, attributes, anomaly baseline and fill values;
- any spatial subset, polygon, area weighting, regridding or aggregation;
- licence/terms and required citation.

Keep raw, intermediate and derived data separate. Do not commit large raw NetCDF files to Git unless the team has explicitly selected Git LFS or external object storage and checked repository limits.

## Suggested repository layout

    data/
      external/
        nasa_podaac_gldas_noah_3_3/
          raw/
          manifest/
          derived/
    docs/
      NASA_GLDAS_NOAH_33_01_DATASET_PROFILE.md
      NASA_GLDAS_NOAH_33_02_ACCESS_AND_INTEGRATION.md

## Validation before comparison or Explorer integration

- Confirm files open as NetCDF-4.
- Confirm `TWS_monthly`, `lat`, `lon` and `time`, or document version-specific differences.
- Verify units, time units, nominal-month alignment, anomaly baseline, fill values and coordinates.
- Check missing months and actual granule coverage; do not infer continuity from the catalogue's “Present” label.
- Preserve original 1° grid and document any transformation to another grid.
- Compare only common months and a common spatial mask/region.
- Do not label the GLDAS aggregate as groundwater.

## Current status

No GLDAS NetCDF granules were downloaded or integrated by this documentation change. Existing Explorer data remains unchanged. Acquisition and ingestion are pending.

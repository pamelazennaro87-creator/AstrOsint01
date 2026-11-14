# Copernicus C3S TWSA — Access and Integration

**Project:** AstrOsint01  
**Collection ID:** satellite-terrestrial-water-storage  
**Catalogue DOI:** https://doi.org/10.24381/c6f5085a

## Access routes
The product is discoverable through the ECMWF Data Stores STAC Catalogue API and Copernicus Climate Data Store (CDS).

- [STAC Browser collection — exact source URL supplied for this audit](https://cds.climate.copernicus.eu/stac-browser/collections/satellite-terrestrial-water-storage?.language=en)
- [CDS dataset page](https://cds.climate.copernicus.eu/datasets/satellite-terrestrial-water-storage)
- [CDS download form](https://cds.climate.copernicus.eu/datasets/satellite-terrestrial-water-storage?tab=download)
- [CDS portal and API access](https://cds.climate.copernicus.eu/)

The supplied catalogue identifies the ECMWF Data Stores STAC Catalogue API, version 1, and the collection ID above.

**Do not guess the STAC API root, item IDs, asset keys or download URLs.** The copied page does not expose those values. Developers must inspect the live collection JSON and follow its advertised STAC links (self, items, root) to establish exact endpoints. Record resolved URLs and retrieval time in the manifest.

## Recommended acquisition workflow
1. Open the official CDS dataset page and confirm version v1.0 is still the intended release.
2. Sign in and accept the CC-BY licence terms if requested.
3. Select the TWSA variable, version and required temporal subset in the CDS form.
4. Use **Show API request code** to obtain the exact current API request. Do not invent a request schema.
5. Retrieve NetCDF-4 through the supported CDS API route or the exact STAC asset href returned by the collection/item metadata.
6. Preserve the original file unchanged. Record UTC retrieval timestamp, filename, request parameters, source URL and SHA-256 checksum.
7. Inspect NetCDF metadata and time coordinates before processing.
8. Generate reproducible regional subsets only after validating the source file.

A visible catalogue entry does not prove anonymous direct download availability. Login, licence acceptance and a submitted request may be required.

## Data engineering manifest
Record at minimum:
- dataset title, collection ID, catalogue DOI and product version;
- retrieval timestamp in UTC;
- exact CDS API request or STAC item URL;
- original asset URL, filename and SHA-256 checksum;
- actual temporal start/end and timestamps;
- CRS, grid coordinates and dimensions;
- variable names, units, fill values and attributes;
- licence and attribution;
- spatial subset, regridding, masking and aggregation operations.

Keep raw, intermediate and derived data separate. Do not overwrite source files.

## Suggested repository layout
    data/
      external/
        copernicus_c3s_twsa/
          raw/
          manifest/
          derived/
    docs/
      COPERNICUS_TWSA_01_DATASET_PROFILE.md
      COPERNICUS_TWSA_02_ACCESS_AND_INTEGRATION.md
      COPERNICUS_TWSA_03_SCIENTIFIC_USE.md

Do not commit large raw NetCDF files to Git unless the team has explicitly selected Git LFS or external object storage and checked repository limits. Prefer manifests, checksums, small derived subsets and reproducible processing instructions.

## Validation before Explorer integration
- Confirm the file opens as NetCDF-4.
- Confirm twsa, twsa_uncertainty and flag_filter are present, or document version-specific differences.
- Verify units, dimensions, fill values and coordinate conventions.
- Confirm monthly timestamps and identify missing months.
- Confirm actual temporal coverage from the file, not only the landing page.
- Preserve uncertainty and filter flags.
- Compare regional aggregates only after matching polygons, masks, reference periods and methods.

## Current status
No Copernicus NetCDF file or STAC asset was acquired as part of this documentation change. Existing Explorer data remains the GEOGloWS-style CSV workflow. Copernicus ingestion is a separate pending task.


## Related NASA GLDAS Noah 3.3 source

AstrOsint01 also documents the complementary NASA PO.DAAC GLDAS Noah 3.3 monthly collection. It is a separate dataset and acquisition workflow; it does not replace the Copernicus C3S TWSA product. See [NASA GLDAS dataset profile](NASA_GLDAS_NOAH_33_01_DATASET_PROFILE.md) and [NASA GLDAS access and integration](NASA_GLDAS_NOAH_33_02_ACCESS_AND_INTEGRATION.md). Do not assume either dataset has been acquired until a granule, checksum and NetCDF validation manifest exist.

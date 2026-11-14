# Copernicus C3S TWSA — Dataset Profile

**Project:** AstrOsint01  
**Collection ID:** satellite-terrestrial-water-storage  
**Product version:** v1.0  
**Catalogue DOI:** https://doi.org/10.24381/c6f5085a

## Identity and provenance
- Dataset: Terrestrial water storage anomaly data from 2002 to present derived from satellite gravimetry observations.
- Provider: Copernicus Climate Change Service (C3S); catalogue provider ECMWF.
- Missions: GRACE and GRACE Follow-On (GRACE-FO).
- Product: gridded Level-3 terrestrial water storage anomaly.
- Domain: land hydrology; global coverage.
- Licence shown in the supplied catalogue record: CC-BY-4.0.
- Catalogue publication/update shown: 7 April 2026.
- Supplied snapshot sanity status: available; score 92 (Fair); timestamp 2026-11-14T23:21:30.388347+00:00.

The catalogue DOI identifies the catalogue record. The underlying product has a separate GFZ DOI; see the scientific-use document.

## What it measures
TWSA is the deviation from a long-term mean of water stored on or below the land surface. The integrated signal can include soil moisture, groundwater, surface water (rivers, lakes, reservoirs and wetlands), snow and ice.

**TWSA is not groundwater alone, a well-water level, absolute water volume, or a direct measurement of local water availability.**

## Spatial and temporal characteristics
| Property | Catalogue information |
|---|---|
| Grid | Regular latitude–longitude |
| Grid spacing | 0.5° × 0.5° |
| Coverage | Global |
| Vertical coverage | Single level / surface |
| Temporal resolution | Monthly |
| Product version | 1.0 |
| Format | NetCDF-4 |
| Conventions | CF 1.6; ACDD 1.3 |
| Units | mm equivalent water height |

**Temporal metadata discrepancy:** the copied STAC record reports 2002-04-04 through 2025-04-01. The current CDS overview describes monthly coverage from April 2002 through September 2025. Do not hard-code the STAC interval as the full time range. Inspect current collection/item metadata and the downloaded NetCDF time coordinate.

The CDS overview lists temporal gaps. Preserve missing months; do not silently interpolate.

## Variables
- TWSA values in mm equivalent water height; NetCDF variable: twsa.
- TWSA standard deviation / uncertainty in mm; variable: twsa_uncertainty.
- Filter-strength indicator; variable: flag_filter.

Confirm names, dimensions, attributes, fill values and units against the actual NetCDF and current Product User Guide before implementing ingestion.

## Official references
- [CDS dataset overview](https://cds.climate.copernicus.eu/datasets/satellite-terrestrial-water-storage?tab=overview)
- [ECMWF STAC Browser collection](https://cds.climate.copernicus.eu/stac-browser/collections/satellite-terrestrial-water-storage)
- [CDS download page](https://cds.climate.copernicus.eu/datasets/satellite-terrestrial-water-storage?tab=download)
- [Product documentation](https://cds.climate.copernicus.eu/datasets/satellite-terrestrial-water-storage?tab=documentation)
- [Catalogue DOI](https://doi.org/10.24381/c6f5085a)
- [Product User Guide and Specification](https://confluence.ecmwf.int/spaces/CKB/pages/514757357/TWSA+v01+Product+User+Guide+and+Specification+PUGS)

## AstrOsint01 integration status
This is a metadata record only. It does not mean NetCDF files have been downloaded, parsed, transformed, independently validated or integrated into the Explorer.

**Status:** source identified; metadata documented; acquisition and independent validation pending.

# Copernicus C3S TWSA — Scientific Use and Limitations

**Project:** AstrOsint01  
**Dataset:** C3S Terrestrial Water Storage Anomaly, v1.0  
**Catalogue DOI:** https://doi.org/10.24381/c6f5085a  
**Underlying product DOI:** https://doi.org/10.5880/GFZ.C3S_TWSA_v1.0

## 1. Interpretation
TWSA is a GRACE/GRACE-FO satellite-gravimetry-derived estimate of changes in total terrestrial water storage relative to a reference mean. It integrates contributions from soil moisture, groundwater, surface water, snow and ice.

- TWSA must not be labelled groundwater storage alone.
- It is an anomaly, not absolute stored water volume.
- Positive values indicate storage above the product reference mean; negative values indicate storage below it.
- It does not directly provide groundwater depth, well levels or local water availability.
- It is a monthly, spatially smoothed product.

## 2. Spatial resolution
The 0.5° × 0.5° grid is output grid spacing, not true independent spatial resolution. Product documentation reports effective spatial resolution of approximately 250–300 km. Filtering and limited resolution can cause signal leakage between neighbouring regions.

For AstrOsint01:
- Do not treat individual 0.5° cells as independent local measurements.
- Do not imply parcel-, town- or well-scale precision.
- Treat small study regions cautiously; surrounding areas may influence their estimates.
- State the study polygon, aggregation method and spatial limitations in regional outputs.

## 3. Temporal gaps and known issue
The CDS overview lists missing months. Preserve missing timestamps and make any gap handling explicit. Never silently interpolate.

The v1.0 documentation lists a known issue: the 30 July 2025 Kamchatka megathrust earthquake is not corrected in the data after July 2025. Analyses after that event should consider possible earthquake-related signals and consult the current issue notice and product documentation.

Monthly resolution cannot capture daily hydrological events with daily precision.

## 4. Uncertainty and filter flag
The product includes standard deviation / uncertainty (twsa_uncertainty) and filter-strength indicator (flag_filter). Retain both during ingestion.

Developers should document flag categories using the Product User Guide, preserve uncertainty in derived datasets, and avoid presenting estimates without uncertainty context. Standard deviation does not capture every structural, model, leakage or regional-boundary uncertainty.

## 5. Comparison with NASA GRACE and GLDAS
This Copernicus product is itself derived from GRACE/GRACE-FO. Comparing it with NASA/JPL GRACE products is a comparison between processing solutions, **not independent ground-truth validation**.

A conceptual groundwater residual is:

    GWSA_estimate = TWSA - SMSA - SWEA - CWSA

This is only defensible when all terms have compatible units (equivalent water height), anomaly baselines, monthly timestamps, spatial grids, masks, polygons and documented model versions.

The residual may still contain surface-water storage unless that component is explicitly estimated and removed. Label it a model-derived groundwater residual/estimate, not a direct well measurement.

Do not subtract precipitation or evapotranspiration fluxes directly from TWSA. Fluxes and storage states are different physical quantities.

## 6. Required safeguards for AstrOsint01
1. Declare a common anomaly reference period.
2. Use the same documented regional polygon for Copernicus and NASA comparisons.
3. Calculate area-weighted regional means using a documented mask and method.
4. Preserve missing months; do not silently interpolate.
5. Retain uncertainty and filter-quality information.
6. Compare like-for-like periods and disclose temporal-coverage differences.
7. Quantify product differences; do not describe agreement as ground truth.
8. Keep raw files, processed series and displayed values traceable to source files and code.

## 7. Attribution
The catalogue lists CC-BY-4.0. Follow current CDS terms and PUGS attribution requirements. The documentation requests citation of both the CDS catalogue entry and underlying C3S/GFZ product.

Suggested catalogue citation:

> Copernicus Climate Change Service (2026): Terrestrial water storage anomaly data from 2002 to present derived from satellite gravimetry observations. Copernicus Climate Change Service (C3S) Climate Data Store (CDS). DOI: 10.24381/c6f5085a. Accessed on [DD-MMM-YYYY].

Suggested product citation:

> Boergens, E., Dahle, C., Haas, J., Dobslaw, H., Flechtner, F. and Güntner, A. (2025). C3S Globally Gridded Terrestrial Water Storage Anomalies, Version 1.0. GFZ Data Service. DOI: 10.5880/GFZ.C3S_TWSA_v1.0. Accessed on [DD-MMM-YYYY].

The PUGS also requires visible Copernicus attribution. Use the exact current wording from the guide, including the year and disclaimer that the European Commission and ECMWF are not responsible for downstream use.

## 8. Scientific references
- [ECMWF Data Stores STAC Catalogue API v1 — collection source](https://cds.climate.copernicus.eu/stac-browser/collections/satellite-terrestrial-water-storage?.language=en)
- [CDS overview and variable names](https://cds.climate.copernicus.eu/datasets/satellite-terrestrial-water-storage?tab=overview)
- [Known limitations and documentation](https://cds.climate.copernicus.eu/datasets/satellite-terrestrial-water-storage?tab=documentation)
- [C3S TWSA Product User Guide and Specification](https://confluence.ecmwf.int/spaces/CKB/pages/514757357/TWSA+v01+Product+User+Guide+and+Specification+PUGS)
- [Catalogue DOI](https://doi.org/10.24381/c6f5085a)
- [Underlying GFZ product DOI](https://doi.org/10.5880/GFZ.C3S_TWSA_v1.0)

## 9. Integration status
This is a scientific-use specification, not evidence that Copernicus data have been downloaded, processed or independently validated in AstrOsint01.

**Status:** metadata documented; scientific safeguards defined; acquisition, processing, reproducibility and comparison pending.


## 9. NASA PO.DAAC GLDAS Noah 3.3: correct scientific role

AstrOsint01 has identified the NASA PO.DAAC collection `TELLUS_GLDAS-NOAH-3.3_TWS-ANOMALY_MONTHLY` (v3.3; DOI 10.5067/GGDAS-3NH33). It is a monthly, global 1° NetCDF-4 product generated from the GLDAS Noah land-hydrology model.

The catalogue describes its aggregate as the sum of **soil moisture, snow water and canopy water**. It does not include a groundwater-storage estimate. It is intended for comparison with GRACE/GRACE-FO observations, with monthly computation days aligned to the corresponding GRACE/GRACE-FO months (the PO.DAAC record specifies alignment with GRACE-FO monthly Level-2 RL06.3 JPL solutions).

Scientific safeguards:
- Treat this as a model-derived estimate of selected terrestrial-water components, not a satellite gravimetry observation or in-situ measurement.
- Do not call `TWS_monthly` a groundwater variable.
- Do not assume it equals all non-groundwater storage: the catalogue's stated aggregate is soil moisture + snow + canopy water; surface-water storage is not listed among those components.
- Do not subtract this GLDAS aggregate from a GRACE TWSA product and label the remainder “groundwater” without evaluating component definitions, baselines, time windows, spatial support, leakage and omitted surface-water terms.
- The 1° output grid is coarser than the Copernicus C3S TWSA 0.5° output grid. Regridding one product does not create additional physical resolution. Use a common, documented grid/mask and area-weighted regional aggregation for comparisons.
- The products are not independent ground truth: GLDAS is model output, while GRACE/GRACE-FO is satellite gravimetry. Agreement is a consistency/comparison result, not validation against wells.
- Confirm actual granule time coverage and NetCDF time coordinates; “to Present” in catalogue metadata is not a guarantee that every month exists.

### Keep the three data roles separate

| Dataset | What it represents | Role in AstrOsint01 |
|---|---|---|
| Copernicus C3S TWSA v1.0 | GRACE/GRACE-FO-derived total terrestrial-water-storage anomaly | Satellite-gravimetry TWSA product |
| NASA PO.DAAC GLDAS Noah 3.3 | Modelled soil-moisture + snow + canopy-water anomaly aggregate | Complementary model component estimate |
| Existing GEOGloWS-derived CSV residual | Existing project series produced by a separate workflow | Preserve its own provenance; do not silently replace it with this PO.DAAC collection |

Do not assume the existing GEOGloWS-derived CSVs were generated from this exact PO.DAAC collection/version unless their source code, input manifests and provenance demonstrate that relationship.

## 10. NASA source and citation

- [NASA PO.DAAC dataset landing page](https://podaac.jpl.nasa.gov/dataset/TELLUS_GLDAS-NOAH-3.3_TWS-ANOMALY_MONTHLY)
- [Earthdata granule search — collection C2036877565-POCLOUD](https://search.earthdata.nasa.gov/search/granules?p=C2036877565-POCLOUD)
- [PO.DAAC collection directory](https://cmr.earthdata.nasa.gov/virtual-directory/collections/C2036877565-POCLOUD)
- [GLDAS project documentation](https://ldas.gsfc.nasa.gov/gldas)
- [Dataset DOI](https://doi.org/10.5067/GGDAS-3NH33)
- [Rodell et al. (2004), The Global Land Data Assimilation System](https://doi.org/10.1175/BAMS-85-3-381)

Suggested dataset citation:

> Rodell M, et al. (2020). TELLUS_GLDAS-NOAH-3.3_TWS-ANOMALY_MONTHLY. Version 3.3. PO.DAAC, CA, USA. https://doi.org/10.5067/GGDAS-3NH33. Accessed [YYYY-MM-DD].


# Region boundaries

## Acquisition status (14 November 2026)

This directory is being populated from authoritative or research-grade GIS sources. **Do not extract GRACE or other regional data until the final analysis polygons are explicitly selected, validated and versioned.**

| Required geometry | Source identified | Current status | Important limitation |
|---|---|---|---|
| California Central Valley study domain | California DWR, i08 C2VSimFG Boundary | Official GeoJSON and Shapefile download endpoints verified; not yet committed as a local geometry | This is the C2VSimFG model domain based on Bulletin 118 basin boundaries generalized for model node spacing. It is a defensible hydrological study domain, not a generic administrative Central Valley outline. |
| Inner Niger Delta | Ramsar Site 1365, Delta Intérieur du Niger | Official Ramsar site record and 2025 information sheet verified; GIS polygon file still to be obtained and checked | Do not substitute a bounding box, a flood extent from one year, or a different protected-area polygon. The Ramsar designated area (4,119,500 ha reported) is not automatically identical to the hydrological/floodplain study boundary used by every paper. |
| Upper Niger Basin catchment | IRD/DataSuds SIEREM Niger basin GIS dataset (2025, v2) and HydroBASINS/HydroSHEDS | Downloadable basin shapefile dataset identified; exact upstream catchment selection still requires hydrological/topological verification | The whole Niger River Basin is not the Upper Niger Basin. Select upstream contributing sub-basins using network topology and document the outlet/inflow definition. Keep this polygon separate from the Inner Niger Delta. |

## Primary sources and download endpoints

### California Central Valley

- Publisher: California Department of Water Resources (DWR).
- Dataset: [i08 C2VSimFG Boundary](https://catalog.data.gov/dataset/i08-c2vsimfg-boundary).
- GeoJSON: https://gis.data.cnra.ca.gov/api/download/v1/items/e9cfa13dc006476abcf2250c9af91522/geojson?layers=0
- Shapefile ZIP: https://gis.data.cnra.ca.gov/api/download/v1/items/e9cfa13dc006476abcf2250c9af91522/shapefile?layers=0
- DWR ArcGIS service: https://gis.water.ca.gov/arcgis/rest/services/Geoscientific/i08_C2VSimFG_Boundary/FeatureServer/0
- DWR reports a model-domain area of 20,742 square miles, spanning the Sacramento, San Joaquin River and Tulare Lake regions. The dataset description says the boundary is based on Bulletin 118 (2003) basin boundaries generalized for model node spacing.
- Dataset record reports a Creative Commons Attribution license; retain publisher attribution and verify the current license metadata when downloading.

### Inner Niger Delta

- Publisher/authority: Ramsar Sites Information Service.
- Site: [Ramsar site 1365 — Delta Intérieur du Niger](https://rsis.ramsar.org/ris/1365).
- 2025 Ramsar Information Sheet: https://rsis.ramsar.org/RISapp/files/RISrep/ML1365RIS_2503_fr.pdf
- The 2025 record reports 4,119,500 ha. This is the designated Ramsar site area; do not treat the number as proof that the downloadable polygon has exactly that area.
- The older Ramsar information sheet describes the ecological delta as a variable flood-dependent landscape and distinguishes wet/inundated areas from peripheral dry land. The flood footprint varies seasonally and interannually.
- A 2017 World Bank environmental study includes a map of the Inner Niger Delta intervention/study boundary, but that map is not a substitute for the Ramsar GIS polygon: https://documents1.worldbank.org/curated/en/763211492592718452/pdf/SFG3269-V3-EA-FRENCH-P151909-Box402902B-PUBLIC-Disclosed-4-18-2017.pdf
- A 2022 baseline report by Wetlands International contains a detailed hydrographic map, useful for cross-checking but not yet an independently validated machine-readable boundary: https://uploads.water-energy-food.org/resources/FREXUS_Mali_Rapport-Final_Baseline_2022-11-15-130334_chiu.pdf

### Upper Niger Basin

- IRD/DataSuds dataset: [Contours des bassins versants et réseau hydrographique du fleuve Niger, v2](https://doi.org/10.23708/FWC87Z).
- Dataset landing page: https://dataverse.ird.fr/dataset.xhtml?persistentId=doi:10.23708/FWC87Z
- Public original-format archive listed as `SIEREM_FleuveNiger_Basins.zip` (3.4 MB); it contains sub-basin polygons, hydrometric station metadata and monthly discharge files. Inspect its README and metadata before selecting any geometry.
- HydroBASINS: https://www.hydrosheds.org/products/hydrobasins
- HydroBASINS is a nested, Pfafstetter-coded basin dataset. It supports upstream/downstream selection, but the correct level and outlet must be chosen for the research question.
- Cite Lehner & Grill (2013), *Global river hydrography and network routing: baseline data and new approaches to study large river systems*, Hydrological Processes 27(15), 2171–2186, DOI: https://doi.org/10.1002/hyp.9740.

## Required validation before committing polygons

For each final geometry, record:

1. Original source URL, publisher, retrieval date, dataset version and license/terms.
2. Original filename and SHA-256 checksum.
3. CRS/EPSG, coordinate order and geometry type.
4. Feature count, geometry validity, multipart handling and any repair operation.
5. Area in km² calculated in an appropriate equal-area CRS; compare against the source-reported area where available.
6. Exact spatial definition, exclusions, clipping and any buffer operation.
7. Whether the geometry represents a designated protected site, hydrological catchment, model domain, floodplain or annual inundation extent. These are not interchangeable.

Suggested final filenames:

- `central_valley_c2vsimfg_boundary.geojson`
- `inner_niger_delta_ramsar_1365.geojson`
- `upper_niger_upstream_catchment_sierem_or_hydrobasins.geojson`

Do not create placeholder polygons or infer boundaries from a centroid and bounding coordinates. If a geometry cannot be obtained or its identity cannot be verified, leave it pending and state that explicitly.

# Data metadata

This folder stores machine-readable provenance records for sources and processed outputs.

- `source_inventory.csv`: source catalogue with geographic scope, theme, provider, period, access route, intended use, limitations and collection status.
- Add `download_log.csv` when files are actually retrieved. Record retrieval timestamp (UTC), exact source filename/ID, version, URL, checksum and operator.
- Add `processing_metadata.json` only after regional extraction has been performed. Include mask version, CRS, weighting, missing data, units, script commit and output checksums.

Do not change a source status from "pending" to "downloaded" until the file exists and its checksum and metadata have been recorded.

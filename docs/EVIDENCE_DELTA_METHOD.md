# Evidence Delta — method note

**AstrOsint01 · Water Signal Explorer**

## Purpose

Evidence Delta helps visitors notice when a descriptive trend depends on the time window. It compares the selected region and variable across:

- the full available CSV record;
- the final 10 years of the record;
- the final 5 years of the record.

The windows are anchored to the final date in the selected CSV, not to the visitor's current date.

## Calculation

For each window, the Explorer:

1. selects rows whose dates fall within that window;
2. retains populated, non-filled values for the selected variable;
3. calculates an ordinary least-squares slope against monthly time;
4. expresses the slope in centimetres per year;
5. reports the number of observed months used.

Gap-filled values are not used in the regression. The displayed comparison is recalculated when the visitor changes study area or variable.

## Interpretation

If the full-record and shorter-window slopes have opposite signs, Evidence Delta labels this **signal tension** or a **possible recent shift**. This is a prompt for further investigation, not a finding that a region has recovered, deteriorated, or reached a tipping point.

A change in slope can reflect natural variability, seasonality, drought/recovery episodes, data coverage, processing choices or other factors. The panel does not identify a cause.

## What it does not do

Evidence Delta is not:

- a forecast or early-warning system;
- a formal trend-significance test;
- a Mann–Kendall test or Sen's slope estimator;
- an uncertainty interval;
- a correction for serial correlation;
- a substitute for independent groundwater, hydrological, land-subsidence or field evidence.

The existing CSV provenance limitations still apply. In particular, the second study-area polygon and original export configuration are not fully verified, and GEOGloWS-derived GWSa remains a model-derived residual that may retain surface-water storage signals.

## Reproducibility

The calculation runs in the browser from the same published monthly CSVs used by the Water Signal Explorer. It does not download or introduce a new NASA dataset. The source records and their limitations are documented in [the data provenance audit](DATA_PROVENANCE_AUDIT.md).

**Design principle:** a trend reversal should trigger a better question, not a louder claim.

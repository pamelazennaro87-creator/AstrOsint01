# AstrOsint01 — Scientific Validation & Prototype Integration Guide

**Purpose:** strengthen the existing *Earth in Transition: Opposite Water Futures* work without replacing the team's prototype or presenting planned work as completed.

**Status of this document:** implementation guidance. It is not evidence that the analyses or accessibility tests have already been run.

## 1. What the prototype must prove

The NASA challenge asks for a tool that can identify an Earth-science variable, obtain it for a region, create and visualize a sufficiently long time series, estimate the rate of change, and test whether the trend is statistically significant.

For the current two-region demonstration, the minimum defensible user journey is:

1. **Select a case:** California Central Valley or Inner Niger Delta.
2. **Inspect the measurement:** variable name, physical meaning, units, product/version, spatial and temporal resolution, reference period.
3. **Explore the time series:** monthly observations, missing months clearly marked, trend line shown separately from observations.
4. **Inspect the analysis:** period, sample count, slope, confidence interval, test, p-value, and caveats.
5. **Compare regions:** use the same variable definition, product family, units, temporal coverage and statistical procedure wherever scientifically appropriate.
6. **Open the evidence:** original NASA product and independent sources behind any human-impact interpretation.

The project’s OSINT layer should add context to the Earth-observation result. It must not substitute narrative or ownership research for the required quantitative trend analysis.

## 2. Scientific correction that must remain visible

### GRACE measures total terrestrial water storage

GRACE/GRACE-FO estimates changes in terrestrial water storage (TWS), expressed as equivalent water thickness. TWS includes contributions from groundwater, soil moisture, snow, surface water and other water stores. It is **not a direct measurement of groundwater alone**.

Therefore:
- Label the primary variable **Terrestrial Water Storage Anomaly (TWSA)**, not “groundwater level”.
- Do not describe a TWS trend as groundwater depletion or groundwater recovery unless an independent groundwater estimate or a documented component-separation method supports that interpretation.
- If estimating groundwater storage anomalies, state the calculation and inputs. A common approach subtracts land-surface-model estimates of soil moisture, snow water equivalent and canopy water from TWS; disclose the model, versions, assumptions and uncertainty.
- Do not equate a positive regional TWS trend with universal local water availability, safe drinking water, or equitable access.

### Spatial scale matters

GRACE mascon products have coarse effective spatial resolution (roughly a few hundred kilometres). They are suitable for large-scale storage changes, not parcel-level, farm-level or village-level conclusions. The Central Valley and Inner Niger Delta are regional case studies; make the region masks and scale limitations visible.

### Product choice

For a hydrology demonstration, start by evaluating the JPL RL06.3 Version 04 **CRI-filtered** mascon product. PO.DAAC describes CRI as reducing land/ocean signal leakage and recommends it for most land-hydrology applications. If the unfiltered product is used, explain why and address coastline leakage. Record the exact product short name, release, access date and file identifier.

Primary product:
- https://podaac.jpl.nasa.gov/dataset/TELLUS_GRAC-GRFO_MASCON_CRI_GRID_RL06.3_V4

General JPL mascon documentation:
- https://grace.jpl.nasa.gov/data/get-data/jpl_global_mascons/

## 3. Reproducible time-series procedure

For each region, preserve the following metadata alongside the data:

| Field | Required value |
|---|---|
| Variable | TWSA / equivalent water thickness |
| Product | Provider, product short name and release |
| Units | Original units and any conversion |
| Period | Exact first and last observation dates |
| Cadence | Monthly |
| Region | Named polygon and source/version |
| Aggregation | Area-weighted regional mean, with method |
| Missing data | Missing-month count and handling |
| Uncertainty | Product uncertainty and propagation/limitations |
| Processing | Script/notebook version or commit |

### Suggested processing sequence

1. Read the monthly NetCDF product and inspect its coordinates, units, time axis, fill values and uncertainty variables.
2. Define reproducible region polygons. Publish the polygon source, coordinate reference system and a map of the mask.
3. Intersect the grid with each region. Calculate the regional mean using an explicitly documented area-weighting method. Do not silently treat partial grid-cell intersections as full cells.
4. Keep missing observations missing. Do not interpolate gaps merely to make a smooth chart. If a method requires complete observations, state the exclusion rule and resulting sample size.
5. Convert units only once and record the conversion. For example, centimetres to millimetres: multiply by 10.
6. Plot the original monthly values. Show any seasonal adjustment or smoothing as a separate, clearly labelled analytical series.
7. Run the same primary trend procedure for both regions over a common comparison window, unless a documented scientific reason requires otherwise.
8. Save the processed series and analysis output as machine-readable CSV/JSON, with a script or notebook that reproduces them.

### Minimum statistical output

For each region report:
- observation count and date range;
- estimated slope in mm/year (or the original unit/year, clearly labelled);
- 95% confidence interval for the slope;
- test name, statistic and p-value;
- treatment of seasonality and serial autocorrelation;
- missing-data handling;
- a plain-language interpretation that does not overstate causation.

A simple linear regression can be a transparent baseline. Because monthly hydrological series can be seasonal and autocorrelated, do not interpret an ordinary regression p-value as definitive without checking residuals. A Mann–Kendall test with an appropriate seasonal/autocorrelation treatment and Sen's slope can be a useful robust companion. Do not claim a Mann–Kendall result or Sen's slope until the code has actually calculated it.

**Significance is not magnitude, and neither proves cause.** Show the slope and uncertainty, not only a green “significant” badge. If the result is not significant, report that honestly.

## 4. How to describe the two case studies responsibly

### California Central Valley

The cited 2022 *Nature Communications* paper reports GRACE/GRACE-FO groundwater anomalies for the Central Valley and estimates a 2003–2021 depletion trend of 15.7 ± 1.4 mm/year. That figure is a published study result, not automatically the output of AstrOsint01's own regional mask or processing.

Source:
- https://www.nature.com/articles/s41467-022-35582-x

Use wording such as:
> “A published GRACE/GRACE-FO analysis estimated groundwater depletion in California’s Central Valley at 15.7 ± 1.4 mm/year over 2003–2021. AstrOsint01 presents this as a published reference result; its own estimate is reported separately only after reproducing the analysis.”

Do not imply that this groundwater-specific rate is identical to the raw TWSA slope.

### Inner Niger Delta

The 2025 *Water* study analysed GRACE/GRACE-FO and GLDAS data from April 2002 to September 2022. Its abstract reports a positive TWS trend range of 7.3–9.5 mm/year and strong seasonal variation. The study's result should be attributed to the paper until the team independently reproduces it.

Source:
- https://doi.org/10.3390/w17081121

Use wording such as:
> “A 2025 study reported a positive TWS trend in the Inner Niger Delta over April 2002–September 2022. This indicates an increase in regional terrestrial water storage in that analysis; it does not, by itself, establish that all communities experienced improved water access or reduced water stress.”

### Keep the comparison scientifically fair

The two published rates above are not automatically directly comparable: they may refer to different derived quantities, masks, periods and processing methods. The prototype should show:
- **Published reference result** (attributed to its paper); and
- **AstrOsint01 reproduced result** (only after processing the selected NASA product with documented masks and methods).

Never put the two in one chart as if they were identical measurements without explaining the difference.

## 5. Evidence chain for the OSINT layer

Use an evidence register for every claim about ownership, exports, flooding, displacement, infrastructure or governance.

Each record should contain:
- claim ID and exact claim;
- geography and time period;
- source title, publisher, author and publication date;
- direct URL or DOI;
- source type (primary data, peer-reviewed paper, official report, journalism);
- exact supporting passage/table/figure/page;
- what the source establishes;
- what it does **not** establish;
- confidence and unresolved caveats;
- reviewer and last-checked date.

Apply these rules:
1. Separate **observation**, **interpretation** and **hypothesis**.
2. A news article may document a reported ownership estimate; it is not a land registry.
3. Land ownership concentration does not automatically prove control of groundwater rights, pumping volumes or water allocation.
4. Virtual-water export is a calculated concept; state the crop, water-footprint method, year and trade-flow source.
5. Flood reports establish reported impacts for the named period and area; they do not by themselves establish that a long-term TWS trend caused a specific flood.
6. Avoid causal wording (“caused”, “because of”) unless the cited research supports attribution.

## 6. Prototype interface contract

The application can remain visually distinctive and investigative. These are the minimum information elements each screen should expose:

### Case overview
- Region name and map with visible boundary.
- Variable and plain-language definition.
- Dataset/provider/version and period.
- One sentence explaining the scale limitation.

### Time-series explorer
- Monthly data points; no invented values.
- Axis title and units.
- Missing months visible.
- Toggle or separate view for raw series and any adjusted series.
- Text alternative and data table containing the same observations.
- Download/export of the displayed series and analysis metadata.

### Trend result
- Slope and units/year.
- Confidence interval.
- Test and p-value.
- Number of observations and analysis period.
- Plain-language result: positive, negative or no statistically detectable trend under the stated method.
- Clear note: statistical association is not causal attribution.

### Evidence explorer
- Each contextual claim opens its source.
- Distinguish primary, peer-reviewed, official and journalistic sources.
- Show publication date and geographic/time coverage.
- Display evidence limitations beside the claim, not hidden in a general disclaimer.

### Comparison view
- Same units, definitions and comparable periods wherever possible.
- If methods or periods differ, show the difference prominently.
- Never imply that opposite signs alone explain the social outcome.

## 7. Accessibility: implement, then verify

Do not label the application “epilepsy-safe” or claim full WCAG conformance based only on design intentions.

Minimum checks before making a public claim:
- no flashing content; inspect media and animations rather than relying only on a CSS preference;
- honour `prefers-reduced-motion` and provide an obvious manual reduced-motion option;
- no autoplaying animation, video or sonification;
- keyboard-only operation, visible focus and logical focus order;
- semantic headings, labels, buttons and table headers;
- screen-reader names and meaningful text alternatives for maps/charts;
- colour is not the only way to distinguish series; use labels, line styles and markers;
- sufficient contrast and scalable text;
- sonification is optional, user-initiated, stoppable and has a text/table equivalent;
- document test date, browser/device, assistive technology, tester and outcome.

Use accurate status labels:
- **Implemented** — present in the current build.
- **Tested** — verified with a named test and recorded outcome.
- **Planned** — not yet implemented.
- **Not tested** — implemented or present, but not verified.

Relevant standards:
- WCAG 2.2: https://www.w3.org/TR/WCAG22/
- Three Flashes or Below Threshold: https://www.w3.org/WAI/WCAG22/Understanding/three-flashes-or-below-threshold.html
- Reduced motion guidance: https://developer.mozilla.org/en-US/docs/Web/CSS/@media/prefers-reduced-motion

## 8. Team hand-off: definition of done

Before calling the prototype complete, the team should be able to answer “yes” to these questions:

- [ ] The live demo loads from a public, judge-accessible URL.
- [ ] The source code and setup/run instructions are in the repository.
- [ ] At least one real NASA dataset is loaded by the application.
- [ ] The displayed time series can be traced to the downloaded source file and processing steps.
- [ ] The trend calculation is reproducible and its output is shown with uncertainty and significance information.
- [ ] Both regions use documented masks and a fair comparison method.
- [ ] Published literature results are distinguished from the team's own calculations.
- [ ] Every contextual claim has a traceable source and an evidence limitation.
- [ ] Visual assets actually exist at the paths referenced by the documentation and have provenance/alt text.
- [ ] Accessibility features are labelled by implementation and test status.
- [ ] AI use and generated assets are disclosed according to the applicable event guidance.
- [ ] The demo explains what the user can investigate in a short, uninterrupted journey.

**Important:** This checklist is a quality-control aid, not a substitute for checking the current official submission instructions.

## 9. Authoritative starting references

- NASA challenge brief: https://www.spaceappschallenge.org/2026/challenges/earth-system-trend-detective/
- JPL/PO.DAAC CRI-filtered RL06.3 v04 product: https://podaac.jpl.nasa.gov/dataset/TELLUS_GRAC-GRFO_MASCON_CRI_GRID_RL06.3_V4
- JPL GRACE Tellus documentation: https://grace.jpl.nasa.gov/
- Liu et al. (2022), Central Valley groundwater depletion: https://www.nature.com/articles/s41467-022-35582-x
- Fatolazadeh & Goïta (2025), Inner Niger Delta TWS: https://doi.org/10.3390/w17081121
- WCAG 2.2: https://www.w3.org/TR/WCAG22/

---
**Prepared as an additive technical/research hand-off for AstrOsint01.** This guide does not modify the team's application code or claim that any unverified feature is complete.

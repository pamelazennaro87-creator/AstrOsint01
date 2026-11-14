# ASTROSINT 01 — The Story

## Earth is changing. Follow the water.

**NASA Space Apps Challenge 2026 · Be An Earth System Trend Detective**

A satellite can measure a change across hundreds of kilometres. It cannot, by itself, tell us who caused it, who benefits, or which household will face the consequences.

That is where our investigation begins.

AstrOsint01 follows the water signal from space to evidence on the ground. We compare two regional datasets, question what their boundaries really represent, and separate what is measured from what is inferred.

---

## Opening scene — One planet, two signals

Imagine looking at Earth from hundreds of kilometres above it.

There is no property line. No irrigation permit. No village boundary. No crop contract. There is only a changing mass of water, measured over a very large footprint.

GRACE and GRACE-FO help us observe those changes in terrestrial water storage. Their strength is scale and continuity. Their limitation is also scale: a regional satellite signal is not a street-level account of water access.

So we ask a different question:

**When the water signal changes, what can we prove—and what must we still investigate?**

## Case file 01 — California Central Valley

The project's Central Valley time series shows a negative full-record trend in TWSa and the GEOGloWS-derived GWSa residual.

That signal is consistent with a wider body of research documenting groundwater depletion in California's Central Valley. Published work by Liu et al. (2022) estimated groundwater depletion at 15.7 ± 1.4 mm/year for 2003–2021. Independent InSAR observations have documented land subsidence in affected areas.

These are different evidence layers:
- GRACE / GRACE-FO provides a broad regional water-storage signal.
- Ground-based and InSAR research helps investigate aquifer stress and land movement.
- Agricultural and water-use records help examine possible drivers and who is exposed.

**What the satellite does not prove:** which individual farm pumped how much, who owns a parcel, or who is legally responsible. Those questions require separate records and spatially appropriate evidence.

## Case file 02 — The Sahel/Sahara dataset

The second CSV currently used by our Explorer is named **Taoudeni–Tanezrouft Basin**. Its exported series shows a near-flat total-water-storage trend and a slightly negative full-record GWSa residual trend.

This is not the same geographic unit as the **Inner Niger Delta**.

A separate 2025 study cited in the research package reports a positive trend for the Inner Niger Delta. That published finding may be important context, but it cannot be substituted for the Taoudeni–Tanezrouft dataset or presented as if both refer to the same boundary.

This mismatch is not a footnote to hide. It is a research question to resolve:
- Which exact polygon was selected when the CSV was exported?
- Does it overlap the Inner Niger Delta, the wider basin, or neither?
- Can we obtain a second dataset using a clearly defined Inner Niger Delta boundary?
- Are the time period, units, processing and gap-filling methods comparable?

Until those questions are answered, we label the dataset by its actual source name.

## The investigative turn — A line is not an explanation

GEOGloWS derives GWSa by subtracting GLDAS soil-moisture, snow and canopy anomalies from TWSa. Surface-water storage is not subtracted, so GWSa may include rivers, lakes, reservoirs and wetlands. It is not a direct well measurement.

A trend can reveal a pattern. It cannot, alone, establish a cause.

Our investigation therefore follows four stages:

1. **DETECT** — inspect the monthly satellite-derived anomalies.
2. **COMPARE** — state the region, variable, period, units and processing for every comparison.
3. **VERIFY** — seek independent evidence such as InSAR, hydrological records, field studies and public documentation.
4. **EXPLORE** — ask how the physical change may intersect with livelihoods, infrastructure, governance and unequal exposure.

We keep observations, published findings, interpretations and open questions visibly separate.

## The human question

Water abundance is not automatically safety. Water scarcity is not distributed equally. A regional average can conceal seasonal extremes and local differences.

The next layer of this project is to connect verified physical evidence with carefully sourced information about:
- agricultural dependence and water use;
- flood exposure and infrastructure;
- local water governance and access;
- the distribution of costs, benefits and adaptation capacity.

We will not infer ownership, conflict, displacement or responsibility from a satellite trend. Each claim needs its own evidence.

## The interactive experience

The Water Signal Explorer lets visitors select a study area, switch between total-water storage (TWSa) and the model-derived GWSa residual, choose a time window, and inspect the monthly records.

The regression uses observed, non-filled values only. Gap-filled months remain visible and are counted separately. The trend is descriptive; it is not a significance test, forecast or causal model.

The next development step is a true side-by-side comparison with aligned axes, explicit geographic metadata and a downloadable evidence table.

## Accessibility is part of the method

An investigation is only useful if people can access its evidence.

We prioritize keyboard navigation, clear labels, reduced motion, no flashing effects, text explanations and data tables alongside charts. A manual Safe Mode is available. These measures are design safeguards, not a claim of clinical certification; accessibility must be tested with assistive technologies and users.

## Closing

We do not ask people to accept a dramatic map or a persuasive headline.

We invite them to follow the data, inspect the source, question the boundary and decide what the evidence can—and cannot—say.

**Look at the signal. Question the story. Verify the ground truth.**

*Independent exploration. Shared evidence. Verifiable conclusions.*

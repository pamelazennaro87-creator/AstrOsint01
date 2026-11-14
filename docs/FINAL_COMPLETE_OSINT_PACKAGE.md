# ASTROSINT 01
## WORKING OSINT RESEARCH DOSSIER
### Earth is changing. Follow the water.

**NASA Space Apps Challenge 2026 • Be An Earth System Trend Detective!**

> **Verification status:** This is a working research dossier, not a declaration that every claim is fully verified. The live Explorer uses a Central Valley CSV and a Taoudeni–Tanezrouft CSV. The latter must not be described as an Inner Niger Delta measurement. Published findings about the Inner Niger Delta are kept separate until geographic boundaries, time periods and processing methods are aligned.

---

## 1. Executive Thesis

This project investigates regional water-storage signals and the human questions that may follow from them. The current Explorer reads monthly CSV exports described by the data repository as GRACE / GRACE-FO combined with GLDAS 2.1, accessed through the GEOGloWS GRACE Regional Analyst.

The Central Valley CSV shows a negative long-term signal in total-water and groundwater anomalies. The second CSV is labelled Taoudeni–Tanezrouft Basin and shows a near-flat total-water-storage series with a slightly negative groundwater series. These are not equivalent geographic units and do not, by themselves, establish a controlled comparison.

The project uses **DETECT → COMPARE → VERIFY → EXPLORE** as its research workflow. Observations, published literature, interpretations and open questions must remain distinct. Claims about ownership, causation, flood impacts or responsibility require independent sources and spatially appropriate evidence.

---

## 2. Primary Dataset & Scientific Baseline

| Item | Details |
|------|--------|
| **Primary product** | JPL GRACE and GRACE-FO Mascon RL06.3 Version 04 (Equivalent Water Height) |
| **Alternative** | CSR RL06.3 Mascon (cross-check) |
| **Unit** | cm of equivalent water thickness |
| **Coverage** | April 2002 – present (monthly) |
| **Official source** | NASA PO.DAAC / grace.jpl.nasa.gov |
| **Why selected** | Long continuous record; operationally used by California Department of Water Resources; high scientific credibility and uncertainty characterization |

**Limitation:** GRACE spatial resolution is relatively coarse (hundreds of km). The signal is regional and cannot establish parcel-level or household-level conditions. Fine-scale interpretation requires complementary data (InSAR, optical, in-situ). The current project exports and their exact region masks still require documentation and independent review.

---

## 3. Regional Case A — California Central Valley (Depletion)

### 3.1 Detected Trend

GRACE/GRACE-FO records show a clear, long-term decline in terrestrial water storage across California’s Central Valley, strongest in the southern Tulare Basin. Published analysis reports groundwater depletion of **15.7 ± 1.4 mm/year (2003–2021)**, with acceleration during recent drought periods (Liu et al., 2022, *Nature Communications*). Partial recoveries occur only in exceptionally wet years; the multi-decadal trajectory remains negative.

### 3.2 Physical Verification — Land Subsidence

Independent Sentinel-1 InSAR measurements provide direct physical confirmation of aquifer compaction. In the Tulare Basin, cumulative subsidence of approximately **1 meter between 2015 and 2020** has been documented, with peak rates reaching several tens of centimeters per year in the most affected zones. Subsidence continues even in wetter years, indicating extraction of non-renewable storage (Scientific Reports 2022; California DWR / TRE Altamira InSAR products).

### 3.3 Power & Economic Layer (Unexpected Angle)

Ownership of farmland in key Central Valley counties is highly concentrated: the top 10% of owners hold **73%** of agricultural land in Fresno County and **86%** in Kings County (research reported in *San Francisco Chronicle*, 2025). Major actors include The Wonderful Company (Resnick family — leading global producer of almonds and pistachios), institutional investors, Farmland Reserve, and other corporate entities. High-value perennial crops (almonds, pistachios, alfalfa) convert local groundwater into exportable **virtual water**. This transforms a local physical depletion signal into a global transfer of water resources under concentrated private control.

---

## 4. Regional Case B — Taoudeni–Tanezrouft Basin (project CSV)

### 4.1 What the current export shows

The second CSV used by the Explorer is named `taoudeni-tanezrouft basin.csv.csv`. Across its full exported record, the series appears close to flat for total water storage, while the groundwater anomaly has a slight negative trend. The Explorer calculates a descriptive ordinary least-squares trend from non-filled monthly values; this is not a significance test.

### 4.2 Geographic boundary warning

This file must not be labelled as an Inner Niger Delta measurement unless the original region polygon and export settings establish that equivalence. The data repository README and file naming have used inconsistent regional descriptions. The precise selected polygon, spatial extent and relationship to the Inner Niger Delta remain to be documented.

### 4.3 Separate published literature

The research notes cite a 2025 study reporting a positive Inner Niger Delta TWS trend (+7.3 to +9.5 mm/year for April 2002–September 2022). That is a separate published result. It is contextual literature, not a trend calculated from the Taoudeni–Tanezrouft CSV. A fair comparison requires aligned boundaries, periods, units, processing and uncertainty treatment before the two values can be compared.

---

## 5. Comparative Matrix — Core Investigative Table

| Dimension | California Central Valley | Sahel (Inner Niger Delta) |
|-----------|---------------------------|---------------------------|
| **TWS signal** | Negative long-term signal in project CSV; published literature reports groundwater depletion | Near-flat TWS in the current Taoudeni–Tanezrouft CSV; separate Inner Niger Delta study reports a positive trend |
| **Possible drivers** | Groundwater pumping and drought are discussed in independent literature; attribution needs local evidence | Not established by the CSV; requires basin-specific hydrological evidence |
| **Physical evidence** | InSAR subsidence studies are cited and require direct source linkage | Not established for the current CSV region; separate field evidence must be geographically matched |
| **Human-system layer** | Agricultural water use and ownership concentration are research leads requiring traceable sources | Local water use and flood exposure require region-specific independent sources |
| **Control structure** | Ownership claims need direct documentation and careful attribution | Not established by the satellite dataset |
| **Human impact** | Subsidence and infrastructure impacts are reported in independent studies | Not inferred from the current CSV; requires local evidence |
| **Current project confidence** | Regional signal visible; source mask and all corroborating citations need audit | Geographic identity unresolved; not comparable to Inner Niger Delta study yet |

---

## 6. OSINT Methodology Applied

- **DETECT** — Inspect the monthly CSV exports and record the exact source product, export date, variable, unit and selected region polygon. The current second export is labelled Taoudeni–Tanezrouft.
- **COMPARE** — The Explorer currently reports descriptive OLS slopes using non-filled observations. Mann–Kendall, Sen’s slope, uncertainty estimates and a like-for-like comparison are not yet implemented.
- **VERIFY** — Planned evidence layers include complementary satellite data (InSAR, optical), hydrological records, ownership and economic-flow data, and local field reports. Each claim needs a direct, accessible source and geographic match.
- **EXPLORE** — Investigate who uses water, who benefits and who bears risk only after the physical signal and supporting human-system evidence are independently verified.

---

## 7. High-Resolution Visual Assets Generated

Four ultra-high-resolution visual assets have been produced:

1. **Comparative TWS Trend Graph** — Dual time series (California Central Valley in red vs Inner Niger Delta in blue) showing opposite long-term trajectories with seasonal cycles (2002–2024).
2. **Opposite Water Futures Infographic** — Main thesis visual centered on the question “Who Controls the Change?”.
3. **AstrOsint01 Methodology Diagram** — Clean four-stage process flow: DETECT → COMPARE → VERIFY → EXPLORE.
4. **Comparative Matrix Visual** — Structured side-by-side comparison across seven dimensions.

All visuals are designed for accessibility (clear labels, high contrast, accompanying data tables).

---

## 8. Guidance for the Development Engineer

**Immediate technical priorities**
1. Download JPL (or CSR) Mascon RL06.3 and extract exact time series for the two regional masks.
2. Compute linear trend, Mann-Kendall test, Sen’s slope and formal uncertainty estimates.
3. Build accessible dual time-series visualization + interactive comparative matrix component.
4. Integrate InSAR subsidence layer for California as physical verification evidence.
5. Implement full accessibility support: keyboard navigation, screen-reader compatibility, reduced motion, optional data sonification of the two opposite time series.

**Accessibility requirements (non-negotiable)**  
• Every graph and map must be accompanied by a structured data table and concise text alternative.  
• Color is never the sole means of conveying information.  
• Full keyboard and screen-reader compatibility.  
• Reduced-motion options and strict avoidance of flashing effects.

---

## 9. Primary Sources & Full Traceability

**NASA / Official Data Products**  
• JPL GRACE Tellus / PO.DAAC Mascon RL06.3 Version 04 — https://grace.jpl.nasa.gov  
• California Department of Water Resources — Semi-Annual Groundwater Reports and Sentinel-1 InSAR products

**Peer-reviewed Scientific Literature**  
• Liu et al. (2022). Groundwater depletion in California’s Central Valley accelerates during megadrought. *Nature Communications*. (15.7 ± 1.4 mm/yr, 2003–2021)  
• Fatolazadeh & Goïta (2025). Understanding Terrestrial Water Storage Changes... Inner Niger Delta. *Water*, 17(8), 1121. (+7.3 to +9.5 mm/year, April 2002–September 2022)  
• Werth et al. (2017). GRACE-detected rise of groundwater in the Sahelian Niger River basin. *Journal of Geophysical Research*  
• Multiple InSAR studies of Tulare Basin subsidence (Scientific Reports 2022 and subsequent analyses)

**Ownership, Virtual Water & Human Impacts**  
• Research on farmland ownership concentration (Fresno 73%, Kings 86% held by top 10%), reported in *San Francisco Chronicle* (2025)  
• Virtual water studies of California tree-nut exports  
• FEWS NET, OCHA, and national civil protection reports on flooding and displacement in Niger and the broader Sahel (2024–2026)

---

## 10. Final Status & Competition Positioning

This dossier is a working evidence base. The website and CSV-backed Explorer are research prototypes. Before treating the analysis as a final scientific comparison, the team must: (1) document the exact geographic masks and source export settings; (2) align the second study area with the intended Inner Niger Delta or rename the project scope consistently; (3) link every secondary claim to its original source; (4) implement and document statistical significance and uncertainty methods; and (5) test the accessibility experience with assistive technologies and users.

The project's strongest differentiator is its evidence-first investigative approach: it makes uncertainty visible, keeps geographic labels honest and distinguishes a measured signal from the human explanations that still need verification. This is a defensible foundation to develop—not a claim that every research question is already closed.

---

**Prepared by AstrOsint01 OSINT Cell**  
**WORKING DOSSIER — Validation and source audit remain in progress**

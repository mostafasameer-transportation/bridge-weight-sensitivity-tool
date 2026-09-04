# Weight & Influencing-Factor Sensitivity Tool

## Interpretable Network Metrics for Equity-Aware Prioritization of Bridge Rehabilitation and Recovery

An interactive analytical tool developed as part of **Ph.D. dissertation research at Florida International University (FIU), Moss School of Construction**. The application is designed to examine how factor weighting and the inclusion or exclusion of candidate influencing factors affect bridge rehabilitation priority rankings.

## Author and Academic Context

- **Prepared by:** Mostafa Sameer, PhD Candidate & Graduate Research Assistant
- **Institution:** Florida International University (FIU)
- **School/Department:** Moss School of Construction
- **Faculty Advisor:** Dr. Wallied Orabi, Associate Professor
- **Contact:** msame009@fiu.edu
- **Google Scholar:** https://scholar.google.com/citations?user=2y27LskAAAAJ&hl=en

## Live Interactive Tool

https://mostafasameer-transportation.github.io/bridge-weight-sensitivity-tool/

## Research Objective

The tool provides an interactive environment for testing how alternative factor weights and the inclusion of candidate influencing factors change bridge rehabilitation priority rankings across New York State.

The application was built directly from the **Master Factor Matrix (Sheet 3)** and **Factor Operationalization sheet (Sheet 6)** of the five-state bridge prioritization workbook and is applied to the full **NY-04 statewide bridge panel**.

The broader research title represented by the application is:

> **Interpretable Network Metrics for Equity-Aware Prioritization of Bridge Rehabilitation and Recovery**

## Current NY-04 Application

- **State:** New York
- **Panel:** NY-04
- **Structures:** 17,532
- **Data source:** NYSDOT / data.ny.gov
- **Panel source:** Sheet 15
- **Data pull date:** 2026-09-04

The current application embeds the bridge panel directly in the standalone HTML file so that the analytical tool can run without a separate database or backend service.

## Data Status: Real vs. Illustrative Variables

The application explicitly distinguishes between sourced bridge attributes and illustrative placeholder variables.

### Real / sourced values

- Condition (Poor Status)
- Region
- County
- Owner
- Age

### Illustrative / simulated values

- AADT (traffic exposure)
- Truck traffic %
- Detour length
- Scour / hydraulic risk
- Fracture-critical
- Material / structure risk
- Equity Index

These simulated variables are deterministic and are intended for methodological testing only. They must **not** be interpreted as validated measurements, official NYSDOT values, or final bridge-level estimates.

## Factor Framework

The sensitivity tool contains nine candidate factors:

| Factor | Status | Role in the tool |
|---|---|---|
| Condition (Poor Status) | Real | NYSDOT-flagged Poor condition |
| Age | Real | Years since construction or replacement |
| AADT (traffic exposure) | Illustrative | Traffic-volume exposure proxy |
| Truck traffic % | Illustrative | Truck-weighting / freight exposure proxy |
| Detour length | Illustrative | Network consequence proxy if a bridge is closed |
| Scour / hydraulic risk | Illustrative | Hydraulic vulnerability proxy |
| Fracture-critical | Illustrative | Binary structural-risk proxy |
| Material / structure risk | Illustrative | Material-related risk proxy |
| Equity index | Illustrative | Community-vulnerability / equity proxy |

Each factor can be switched on or off and assigned a user-controlled weight.

## Weighting Scenarios

### 1. Condition-only baseline
Condition receives 100% of the active weighting and all other factors are disabled.

### 2. Approx. NY LBPI-style
Condition 35; Age 10; AADT 20; Truck 12; Detour 18; Scour 5; remaining factors 0.

### 3. Risk / resilience-heavy
Condition 25; Age 10; AADT 10; Truck 5; Detour 10; Scour 20; Fracture-critical 15; Material risk 5; Equity 0.

### 4. + Equity & access test
Condition 25; Age 10; AADT 10; Truck 5; Detour 10; Scour 10; Fracture-critical 10; Material risk 0; Equity 20.

### 5. Reset — equal weights
All candidate factors are enabled with an initial weight of 50.

## Composite Priority Score

The application calculates a composite priority score using a weighted combination of **within-panel percentile ranks** across the active factors.

For each factor, raw values are converted to percentile ranks on a **0–100 scale**. Active weights are normalized by their total and combined:

**Composite Score = Σ (normalized factor weight × factor percentile rank)**

The resulting score sorts bridges from highest to lowest priority under the selected scenario. The baseline ranking uses Condition (Poor Status) alone.

## Ranking and Sensitivity Analysis

The application supports Top 25, Top 50, Top 100, Top 500, and all 17,532 bridges, plus search by BIN, county, region, and owner. It reports ranking movement relative to the condition-only baseline and provides current composite scores.

## Distribution & Regional Composition

The application includes a composite-score distribution across all 17,532 bridges and a regional-composition view comparing the current top 25 with statewide regional shares.

## Data Structure

Each embedded bridge record contains BIN, Region, County, Municipality, Owner, Year, Age, Poor-condition flag, AADT, Truck percentage, Detour, Scour, Fracture-critical, Material-risk, and Equity values.

## Technical Implementation

The tool is a **standalone HTML application** requiring no server, database, package installation, or build process. It uses HTML, CSS, JavaScript, embedded JSON, browser-side percentile normalization, scoring, ranking, filtering, charts, and CSV export.

## User Workflow

1. Open the interactive application.
2. Select a scenario or construct a custom weighting.
3. Adjust weights and factor inclusion.
4. Review priority ranking and ranking movement.
5. Search individual bridges.
6. Examine score distribution and regional composition.
7. Export the ranked list as CSV.

## Research Interpretation and Limitations

This is a **working analytical tool / research demonstration**, not a validated operational bridge-management system. Several candidate influencing-factor variables remain illustrative until real bridge-level datasets are joined. The application should not be interpreted as an official NYSDOT prioritization result or as a replacement for an agency's existing bridge-management methodology.

## Source Workbook Mapping

- **Sheet 3 — Master Factor Matrix:** candidate factors and framework gap/equity considerations
- **Sheet 6 — Factor Operationalization:** normalization and operational definitions
- **Sheet 14 — Task / data integration context:** outstanding real-data integration needs
- **Sheet 15 — NY-04 statewide bridge panel:** current New York bridge population

## Research Status

**Status:** Working Analytical Tool / Research Demonstration

Part of ongoing Ph.D. dissertation research at Florida International University and intended for methodological exploration, sensitivity analysis, and demonstration of the proposed equity-aware bridge prioritization framework.

## Repository Contents

- `index.html` — standalone interactive sensitivity tool and embedded NY-04 bridge panel
- `README.md` — project documentation and research context
- `.nojekyll` — static GitHub Pages support

## Academic Citation

Sameer, M. (2026). *Weight & Influencing-Factor Sensitivity Tool: Interpretable Network Metrics for Equity-Aware Prioritization of Bridge Rehabilitation and Recovery*. Florida International University.

## Acknowledgment

Developed in the context of Ph.D. dissertation research at Florida International University, Moss School of Construction, under the guidance of Dr. Wallied Orabi.

## License / Use

This repository is intended for academic research and methodological demonstration. No formal open-source license is currently specified; reuse and redistribution should therefore be treated as subject to the repository owner's permission unless a formal license is subsequently added.

<!-- deployment trigger: restored index source -->

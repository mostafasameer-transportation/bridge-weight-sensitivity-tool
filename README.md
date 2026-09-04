# Weight & Influencing-Factor Sensitivity Tool

## Interpretable Network Metrics for Equity-Aware Prioritization of Bridge Rehabilitation and Recovery

An interactive analytical tool developed as part of Ph.D. dissertation research at **Florida International University (FIU), Moss School of Construction**. The application is designed to examine how factor weighting and the inclusion or exclusion of candidate influencing factors affect bridge rehabilitation priority rankings.

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

The following fields are represented as real, sourced NY-04 values:

- Condition (Poor Status)
- Region
- County
- Owner
- Age

### Illustrative / simulated values

The following variables are currently placeholders used to demonstrate weighting and factor-inclusion mechanics before the corresponding real bridge-level datasets are joined:

- AADT (traffic exposure)
- Truck traffic %
- Detour length
- Scour / hydraulic risk
- Fracture-critical
- Material / structure risk
- Equity Index

These simulated variables are deterministic and are intended for methodological testing only. They must **not** be interpreted as validated measurements, official NYSDOT values, or final bridge-level estimates.

The application notes that replacing the placeholder columns with real figures does not require changing the overall structure or ranking formulas.

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

The interface provides predefined scenarios for sensitivity testing:

### 1. Condition-only baseline

Condition receives 100% of the active weighting and all other factors are disabled.

### 2. Approx. NY LBPI-style

- Condition: 35
- Age: 10
- AADT: 20
- Truck traffic: 12
- Detour: 18
- Scour: 5
- Fracture-critical: 0
- Material risk: 0
- Equity: 0

### 3. Risk / resilience-heavy

- Condition: 25
- Age: 10
- AADT: 10
- Truck traffic: 5
- Detour: 10
- Scour: 20
- Fracture-critical: 15
- Material risk: 5
- Equity: 0

### 4. + Equity & access test

- Condition: 25
- Age: 10
- AADT: 10
- Truck traffic: 5
- Detour: 10
- Scour: 10
- Fracture-critical: 10
- Material risk: 0
- Equity: 20

### 5. Reset — equal weights

All candidate factors are enabled with an initial weight of 50, allowing the user to construct an equal-weight sensitivity configuration.

## Composite Priority Score

The application calculates a composite priority score using a weighted combination of **within-panel percentile ranks** across the active factors.

For each factor, the raw values are converted to percentile ranks on a **0–100 scale**. For a selected scenario, the active factor weights are normalized by their total active weight and combined to produce the bridge's composite score.

Conceptually:

**Composite Score = Σ (normalized factor weight × factor percentile rank)**

The resulting score is used to sort bridges from highest to lowest priority under the selected scenario.

The baseline ranking is calculated using Condition (Poor Status) alone, allowing the interface to identify bridges that move up or down when additional factors are introduced.

## Ranking and Sensitivity Analysis

The application supports:

- Top 25 bridges
- Top 50 bridges
- Top 100 bridges
- Top 500 bridges
- All 17,532 bridges
- Search by BIN
- Search by county
- Search by NYSDOT region
- Search by owner
- Ranking movement relative to the condition-only baseline
- Current composite score
- Age and Poor-condition status for each ranked bridge

The ranking table identifies bridges whose positions move substantially relative to the condition-only baseline.

## Distribution & Regional Composition

The application includes a separate analytical view with two visualizations:

### Composite score distribution

Shows the composite score distribution across all 17,532 bridges and identifies the top-25 cutoff under the current weighting scenario.

### Regional composition of top 25

Shows the NYSDOT region of origin for the current top 25 bridges and compares the observed regional composition with each region's statewide share.

## Data Structure

Each embedded bridge record contains the principal fields used by the application, including:

- BIN
- Region
- County
- Municipality
- Owner
- Year
- Age
- Poor-condition flag
- AADT
- Truck percentage
- Detour value
- Scour value
- Fracture-critical flag
- Material-risk value
- Equity value

The embedded dataset is parsed directly by the browser from the standalone HTML application.

## Technical Implementation

The tool is intentionally implemented as a **standalone HTML application**. It does not require a server, database, package installation, or build process.

Core implementation components include:

- HTML for application structure
- CSS for the FIU/research interface and responsive layout
- JavaScript for factor controls, scenario presets, percentile normalization, scoring, ranking, filtering, and CSV export
- Embedded JSON bridge data for the current NY-04 panel
- Browser-side rendering of ranking and distribution views

The standalone design makes the tool suitable for GitHub Pages and other static hosting environments.

## User Workflow

1. Open the interactive application.
2. Select a predefined weighting scenario or construct a custom scenario.
3. Adjust factor weights.
4. Enable or disable candidate influencing factors.
5. Review the updated bridge priority ranking.
6. Compare ranking movement against the condition-only baseline.
7. Search for individual bridges using BIN, county, region, or owner.
8. Examine composite-score distribution and regional composition.
9. Download the complete ranked list as a CSV file when required.

## Research Interpretation and Limitations

This is a **working analytical tool / research demonstration**, not a validated operational bridge-management system.

The current ranking results are illustrative because several candidate influencing-factor variables have not yet been joined from their real bridge-level source datasets. In particular, AADT, detour, scour, fracture-criticality, and related influencing-factor fields require real-data integration and subsequent validation.

The tool therefore demonstrates:

- Factor-selection mechanics
- Weight sensitivity
- Ranking sensitivity
- Relative movement from a condition-only baseline
- Composite-score construction
- Equity/access sensitivity testing
- Regional composition analysis

It should not be interpreted as a validated replacement for an agency's existing bridge prioritization methodology or as an official NYSDOT prioritization result.

## Source Workbook Mapping

The analytical structure is explicitly connected to the five-state bridge prioritization workbook:

- **Sheet 3 — Master Factor Matrix:** candidate factors and framework gap/equity considerations
- **Sheet 6 — Factor Operationalization:** normalization and operational definitions
- **Sheet 14 — Task / data integration context:** outstanding real-data integration needs
- **Sheet 15 — NY-04 statewide bridge panel:** current New York bridge population used by the application

## Research Status

**Status:** Working Analytical Tool / Research Demonstration

The application is part of ongoing Ph.D. dissertation research and is intended for methodological exploration, sensitivity analysis, and demonstration of the proposed equity-aware bridge prioritization framework.

## Repository Contents

- `index.html` — standalone interactive sensitivity tool and embedded NY-04 bridge panel
- `README.md` — project documentation, methodology, data status, and research context
- `.nojekyll` — prevents Jekyll processing when using static GitHub Pages deployment

## Academic Citation

Sameer, M. (2026). *Weight & Influencing-Factor Sensitivity Tool: Interpretable Network Metrics for Equity-Aware Prioritization of Bridge Rehabilitation and Recovery*. Florida International University.

## Acknowledgment

Developed in the context of Ph.D. dissertation research at Florida International University, Moss School of Construction, under the guidance of Dr. Wallied Orabi.

## License / Use

This repository is intended for academic research and methodological demonstration. No formal open-source license is currently specified; reuse and redistribution should therefore be treated as subject to the repository owner's permission unless a formal license is subsequently added.

# Weight & Influencing-Factor Sensitivity Tool

## Interpretable Network Metrics for Equity-Aware Prioritization of Bridge Rehabilitation and Recovery

An interactive research tool developed as part of Ph.D. dissertation research at Florida International University (FIU), Moss School of Construction.

## Live Interactive Tool

**[Open the Interactive Tool](https://mostafasameer-transportation.github.io/bridge-weight-sensitivity-tool/)**

If the link returns a 404 immediately after deployment, wait a few minutes for GitHub Pages to finish publishing, then refresh the page.

## Research Context

This tool examines how alternative factor weights and the inclusion or exclusion of candidate influencing factors affect bridge rehabilitation priority rankings.

The application provides an interactive environment for sensitivity analysis and methodological demonstration of an equity-aware bridge prioritization framework.

## Current Application

The current version is applied to the NY-04 statewide bridge panel containing 17,532 structures.

- State: New York
- Panel: NY-04
- Number of structures: 17,532
- Data source: NYSDOT / data.ny.gov
- Data retrieval date: September 4, 2026

## Features

- Adjustable factor weights
- Factor inclusion and exclusion controls
- Predefined weighting scenarios
- Condition-only baseline
- Approximate NY LBPI-style scenario
- Risk / resilience-heavy scenario
- Equity and access sensitivity scenario
- Equal-weight reset
- Composite bridge priority rankings
- Top 25, 50, 100, 500, or all bridges
- Search by BIN, county, region, or owner
- Ranking movement relative to the condition-only baseline
- Composite score distribution
- Regional composition of the current top 25
- Full ranked-list CSV export

## Data and Methodological Note

This repository contains a research and demonstration version of the sensitivity tool.

Condition (Poor Status), Region, County, Owner, and Age are represented using sourced values from the NY-04 bridge panel.

The current application also contains illustrative placeholder values for AADT, Truck %, Detour, Scour, Fracture-Critical, Material Risk, and Equity Index. These variables are used to demonstrate weighting, factor inclusion, and ranking sensitivity before the corresponding real bridge-level datasets are fully joined.

The placeholder variables should not be interpreted as validated measurements or official bridge-level values.

## Composite Priority Score

The composite priority score is calculated as a weighted combination of within-panel percentile ranks across the active factors on a 0–100 scale.

The resulting score is used to generate the bridge priority ranking under the selected weighting scenario.

The tool demonstrates prioritization mechanics and sensitivity analysis. Rankings should be treated as illustrative until the required real-world influencing-factor datasets are integrated and the resulting model is validated.

## How to Use

1. Open the interactive application.
2. Select a predefined scenario or construct a custom configuration.
3. Adjust factor weights.
4. Enable or disable candidate influencing factors.
5. Review the resulting bridge priority ranking.
6. Search for individual bridges using BIN, county, region, or owner.
7. Open the Distribution & Regional Mix tab to examine score distributions and regional composition.
8. Download the complete ranked list as a CSV file when needed.

## Research Status

**Status:** Working Analytical Tool / Research Demonstration

This application is part of ongoing dissertation research. It is intended for methodological exploration, sensitivity analysis, and demonstration of the proposed bridge prioritization framework.

It should not be interpreted as an operational bridge-management decision system or as a validated replacement for an agency's existing bridge prioritization methodology.

## Institution

**Florida International University**  
Moss School of Construction  

**Faculty Advisor:** Dr. Walied Orabi, Associate Professor

## Citation

Sameer, M. (2026). *Weight & Influencing-Factor Sensitivity Tool: Interpretable Network Metrics for Equity-Aware Prioritization of Bridge Rehabilitation and Recovery*. Florida International University.

## License

This repository is intended for academic research and methodological demonstration. A formal open-source license can be added if unrestricted reuse and redistribution are intended.

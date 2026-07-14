# London Air Quality & Spatial Statistics Analysis

Investigating spatial patterns in urban air pollution and evaluating the causal impact of London's 2023 ULEZ expansion, using spatial statistics, regression modelling, and causal inference techniques.

## Motivation

Urban air pollution is a major public health issue, and policy responses (charging zones, low-emission areas) are increasingly common across UK cities. This project asks not just "where is pollution worst?" but "did a specific policy actually reduce it?" — treating the question with the same statistical rigor as environmental regulators and policy evaluators would expect, rather than relying on simple before/after comparisons.

## Location & Policy Context

**Location:** Greater London (full extent)
**Policy studied:** Ultra Low Emission Zone (ULEZ) expansion to cover all of Greater London, effective **29 August 2023**

London was chosen over Manchester after considering both. Greater Manchester's proposed Clean Air Zone was paused in 2022 and ultimately replaced by a non-charging, investment-led plan — meaning there is no clean spatial boundary or firm implementation date to exploit for causal inference. London's ULEZ expansion, by contrast, provides a clearly defined boundary and an exact intervention date, enabling rigorous difference-in-differences and interrupted time series designs. This project prioritises methodological soundness over convenience or personal geographic relevance.

## Research Questions

1. **Spatial autocorrelation:** Is there significant positive spatial autocorrelation in NO2 and PM2.5 concentrations across London monitoring stations? *(Moran's I)*
2. **Explanatory regression:** How much spatial/temporal variation in NO2/PM2.5 is explained by traffic density, land use, and meteorology, and does a traffic effect persist after controlling for weather? *(Multiple regression with spatial + meteorological controls)*
3. **Causal impact (DiD):** Did the 2023 ULEZ expansion cause a measurable reduction in NO2 in newly-covered areas relative to control areas? *(Difference-in-differences)*
4. **Causal impact (ITS):** Is there a significant change in the level/slope of the NO2 trend at the expansion date, independent of a control group? *(Interrupted time series)*
5. **Group comparison:** Do pollution distributions differ significantly between treated/control zones or pre/post periods? *(Mann-Whitney U, given expected right-skew)*

## Pollutants Studied

- **NO2 (primary):** Direct, mechanistic link to vehicle exhaust — the pollutant ULEZ specifically targets. Expected to show the clearest policy signal.
- **PM2.5 (secondary/robustness check):** Multiple sources beyond traffic (heating, industry, regional transport), so treated as a noisier, secondary test rather than the primary measure.
- **PM10 excluded:** Substantially overlaps with PM2.5's source profile without adding distinct signal relevant to a traffic-focused policy.

## Methods

- Spatial autocorrelation testing (Global & Local Moran's I)
- Multiple regression with spatial and meteorological controls
- Difference-in-differences and interrupted time series analysis
- Non-parametric hypothesis testing (Mann-Whitney U)

  The causal analysis compares stations inside vs. outside the final (August 2023) ULEZ boundary. A more granular three-group design (distinguishing areas newly added in 2023 from those already inside since 2021) was considered but not pursued, since no official machine-readable boundary exists for the intermediate October 2021 North/South Circular expansion; borough-boundary proxies were evaluated and found to disagree substantially with the true boundary.

## Repository Structure

data/raw          # Original, unmodified downloaded data
data/processed    # Cleaned, merged, analysis-ready datasets
notebooks         # Colab notebooks, numbered by project phase
src               # Reusable Python functions/modules
outputs           # Saved figures, tables, model outputs
report            # Final write-up materials

## Status

🚧 Work in progress — currently in early data acquisition and setup phase.

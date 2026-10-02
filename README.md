# Global Energy Transition Analysis

## Project Overview

This project explores the global energy transition using the Our World in Data (OWID) Energy Dataset.

The analysis examines how renewable energy adoption changed between 1990 and 2024, which countries have high renewable shares, where fossil-fuel dependence remains high, and how renewable electricity generation relates to the carbon intensity of electricity production.

The project was completed with Python, Pandas, Matplotlib, Country Converter, and Jupyter Notebook.

## Research Questions

1. How has the global share of renewable energy developed over time?
2. Which countries have high renewable energy shares, and which improved most since 1990?
3. Which countries remain highly dependent on fossil fuels?
4. Is there a relationship between renewable electricity share and the carbon intensity of electricity generation?

## Dataset

**Source:** Our World in Data (OWID) Energy Dataset

The repository includes a local snapshot of the OWID energy dataset used for this analysis.

Key variables include:

- `renewables_share_energy`
- `fossil_share_energy`
- `renewables_share_elec`
- `carbon_intensity_elec`
- `population`
- `iso_code`
- `country`
- `year`

The dataset contains both countries and aggregate regions. Country-level comparisons therefore filter to rows with a non-null ISO code to avoid mixing countries with regional aggregates.

## Methodology

### 1. Global time-series analysis

The OWID `World` aggregate is filtered to 1990–2024 to examine changes in renewable and fossil shares of total energy supply.

### 2. Country-level comparisons

Country rows are identified using non-null ISO codes. The analysis compares:

- renewable energy share in 2024,
- change in renewable energy share between 1990 and 2024,
- fossil-fuel share in 2024.

Only countries with the required values are included in each comparison.

### 3. European subset

`country_converter` is used to assign countries to continents for a separate European comparison.

### 4. Renewable electricity and carbon intensity

The final section compares:

- renewable electricity share (`renewables_share_elec`), and
- carbon intensity of electricity generation (`carbon_intensity_elec`).

Pearson correlation is used as a **descriptive measure of association**, not as a causal estimate. The same analysis is repeated for the European subset.

## Visualizations

### Global Energy Mix (1990–2024)

![Global Energy Mix](visuals/1_global_energy_mix.png)

### Global Renewable Energy Growth

![Global Renewable Energy Growth](visuals/2_global_renewable_energy_share.png)

### Countries with the Highest Renewable Energy Share (2024)

![Top Renewable Countries](visuals/3_top_renewable_energy_countries_2024.png)

### Countries with the Largest Increase in Renewable Energy Share Since 1990

![Renewable Improvement](visuals/4_countries_largest_increase_renewable_energy.png)

### Most Fossil-Fuel-Dependent Countries (2024)

![Fossil Dependence Global](visuals/5_most_fossil_fuel_2024.png)

### Most Fossil-Fuel-Dependent Countries in Europe (2024)

![Fossil Dependence Europe](visuals/6_most_fossil_fuel_europe_2024.png)

The notebook also generates two additional scatter plots for Question 4:

- renewable electricity share vs. carbon intensity, globally
- renewable electricity share vs. carbon intensity, Europe

These plots are regenerated when the notebook is executed.

## Main Findings

- Renewable energy's share of total energy supply increased substantially between 1990 and 2024.
- Fossil fuels still account for the majority of the global energy mix.
- Countries differ strongly in both their current renewable shares and the scale of improvement since 1990.
- Several countries remain highly dependent on fossil energy.
- The electricity analysis tests whether higher renewable-electricity shares are associated with lower electricity-sector carbon intensity.
- Any correlation found is descriptive and should not be interpreted as proof that renewable electricity alone causes lower carbon intensity.

## Reproducibility

The notebook uses project-relative paths and can be launched either from the repository root or from the `notebooks/` directory.

### Installation

```bash
python -m pip install -r requirements.txt
```

Then open:

```text
notebooks/energy_transition_analysis.ipynb
```

and run all cells from top to bottom.

The notebook recreates the charts in `visuals/`.

## Repository Structure

```text
global-energy-transition-analysis/
├── data/
│   └── owid_energy_data.csv
├── notebooks/
│   └── energy_transition_analysis.ipynb
├── visuals/
│   ├── 1_global_energy_mix.png
│   ├── 2_global_renewable_energy_share.png
│   ├── 3_top_renewable_energy_countries_2024.png
│   ├── 4_countries_largest_increase_renewable_energy.png
│   ├── 5_most_fossil_fuel_2024.png
│   └── 6_most_fossil_fuel_europe_2024.png
├── requirements.txt
└── README.md
```

## Limitations

- The project is descriptive and does not establish causal relationships.
- Country comparisons depend on data availability and may use different subsets of countries for different indicators.
- Cross-country rankings do not control for population, economic structure, geography, climate, energy demand, trade, or policy differences.
- Renewable energy share and renewable electricity share are different indicators and are used for different analytical questions.
- Carbon intensity in Question 4 refers specifically to electricity generation, not total national greenhouse-gas emissions.
- The OWID dataset is periodically revised as upstream sources and processing methods change.

## Conclusion

The analysis shows substantial but uneven progress in the global energy transition. Renewable energy has expanded, yet fossil fuels remain dominant in total energy supply.

The country comparisons highlight major differences in starting points and trajectories. The final electricity-sector analysis adds a separate perspective by examining whether renewable electricity share is associated with lower carbon intensity while keeping the interpretation explicitly descriptive.

Overall, the project demonstrates country filtering, time-series analysis, comparative analysis, visualization, and careful interpretation of multi-source energy indicators.

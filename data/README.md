# Data Sources

This project uses publicly available mortality and population data for
Mecklenburg County, North Carolina.

Raw source files are not stored in this repository. This directory documents
the datasets used, their role in the analysis, and the transformations applied
before analysis.

---

## 1. Mecklenburg County Mortality Data

**Analysis period:** 2019–2023

Annual mortality statistics were used to analyze:

- All-cause mortality
- Selected ICD-10 causes of death
- Mortality by age group
- Cause-of-death patterns by age

The annual mortality files were transformed into standardized analytical
tables before being combined into a multi-year mortality dataset.

### Key fields used

- Year
- ICD-10 Code
- Cause of Death
- Race
- Sex
- Total Deaths
- Age-specific death counts

### Important methodological consideration

Some age fields in the original mortality data overlap.

For example, infant categories such as:

- <1 day
- <1 week
- <28 days
- <1 year

are cumulative rather than mutually exclusive.

To avoid double counting, the analysis uses the <1 year total rather than
summing the overlapping infant categories.

Selected ICD-10 categories may also exist at different levels of the ICD
hierarchy and therefore should not automatically be summed.

---

## 2. U.S. Census Bureau Population Estimates

### Official Source

U.S. Census Bureau Population Estimates Program  
Vintage 2023 — Annual Resident Population Estimates by Selected Age Groups
and Sex: April 1, 2020 to July 1, 2023  
Table: PEP_AGESEX

https://data.census.gov/table/PEPCHARV2023.PEP_AGESEX?q=Resident+Population

**Population analysis period:** 2020–2023

Population denominators were derived from the U.S. Census Bureau Population
Estimates Program.

The project uses annual July population estimates for Mecklenburg County.

### County population totals used

| Year | Population |
|---|---:|
| 2020 | 1,117,423 |
| 2021 | 1,126,283 |
| 2022 | 1,144,075 |
| 2023 | 1,163,701 |

Population data were filtered to:

- Mecklenburg County, North Carolina
- Both sexes
- July annual population estimates

---

## 3. Analytical Age Groups

Mortality and population data used different source age structures.

To create compatible numerators and denominators, both datasets were mapped
into six analytical age groups:

| Analytical Age Group | Population Mapping |
|---|---|
| Under 25 | Under 5 + 5–9 + 10–14 + 15–19 + 20–24 |
| 25–44 | 25–44 |
| 45–64 | 45–64 |
| 65–74 | 65–69 + 70–74 |
| 75–84 | 75–79 + 80–84 |
| 85+ | 85 years and over |

This alignment was completed before calculating age-specific mortality rates.

---

## 4. Rate Calculations

Mortality rates were calculated using:

Mortality Rate = (Deaths / Population) × 100,000

The project includes:

- Crude mortality rates
- Age-specific mortality rates
- Selected cause-specific mortality rates within age groups

Age-specific mortality rates in this project are not age-standardized rates.

---

## 5. Power Query Data Architecture

Source-file locations are controlled through the Power Query parameter:

`ProjectDataPath`

The public portfolio workbook contains a placeholder value rather than the
author's local computer path.

To reproduce the workflow:

1. Obtain the corresponding public mortality and Census population source data.
2. Store the source files in a local project directory.
3. Open the portfolio workbook.
4. Open Power Query.
5. Change `ProjectDataPath` to the local source-data directory.
6. Confirm that the filenames match those referenced by the source queries.
7. Refresh the queries.

The transformation architecture can then process the source files through the
mortality and population pipelines.

---

## 6. Data Quality & Reproducibility Notes

The following controls were incorporated into the project:

- Annual mortality totals were reconciled after transformation.
- Population totals were validated by year.
- Mortality and population age groups were aligned before rate calculations.
- Overlapping infant mortality fields were not summed.
- Selected ICD-10 hierarchy categories were treated cautiously to avoid
  inappropriate aggregation.
- Mortality counts and population-adjusted rates were interpreted separately.
- Population-adjusted analysis begins in 2020 because of the population
  estimate series used.

---

## Data Use

This project was developed for analytical, educational, and portfolio
purposes using publicly available data.

The analysis is descriptive and does not establish causal relationships.

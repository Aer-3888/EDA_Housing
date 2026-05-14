# Housing Market EDA: Pays de la Loire, France (2014-2023)

Exploratory data analysis of housing prices across the Pays de la Loire region, focused on measuring the impact of COVID-19 on the real estate market.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Aer-3888/EDA_Housing/blob/main/EDA_Immobillier_france_covid.ipynb)

## What this does

Loads 10 years of French real estate transaction data (290k+ records nationally, ~12k for the region), filters to the 5 departments of Pays de la Loire, and compares three periods:

| Period | Years | Avg. Price | Avg. Price/m² |
|---|---|---|---|
| Pre-COVID | 2014-2019 | ~134k | ~1,384/m² |
| COVID | 2020-2021 | ~154k | ~1,550/m² |
| Post-COVID | 2022-2023 | ~172k | ~1,762/m² |

Departments covered: Loire-Atlantique (44), Maine-et-Loire (49), Mayenne (53), Sarthe (72), Vendee (85).

## Data source

[data.gouv.fr: Indicateurs immobiliers par commune et par annee (2014-2023)](https://www.data.gouv.fr/fr/datasets/indicateurs-immobiliers-par-commune-et-par-annee-prix-et-volumes-sur-la-periode-2014-2023/#/resources)

The dataset provides per-municipality, per-year real estate indicators including transaction counts, average prices, price per m², average surface area, and house/apartment splits.

## Requirements

- Python 3.x
- pandas
- matplotlib
- seaborn
- folium (pre-installed in Google Colab)
- numpy (pre-installed in Google Colab)

```
pip install -r requirements.txt
```

## Running

1. Download the yearly CSV files (`dvf2014.csv` through `dvf2023.csv`) from the data source above.
2. Place them in a directory and update the `file_path` variable in the notebook to point to that directory.
3. Open the notebook in Jupyter or Google Colab and run all cells.

## Notebook structure

1. **Data loading** — Reads and concatenates 10 yearly CSV files into a single dataframe.
2. **Filtering** — Keeps only municipalities from Pays de la Loire using INSEE commune codes.
3. **Cleaning** — Drops irrelevant columns, maps department names.
4. **Data preparation** — Audits missing values and duplicates, removes invalid entries, detects and Winsorizes outliers (1.5×IQR), validates INSEE commune code format.
5. **Period splitting** — Segments data into pre-COVID, COVID, and post-COVID.
6. **Descriptive statistics** — Summary stats for each period and overall.
7. **Basic visualizations** — Sales volume bar chart, price trends over time, price/m² trends, property size distribution, yearly price boxplots.
8. **Advanced visualizations**
   - Interactive choropleth map (folium) of avg price/m² by department
   - Price/m² evolution by department (multi-line with COVID shading)
   - Correlation heatmap of numeric variables
   - COVID impact grouped bar chart (pre/during/post by department)
   - Year-over-year % price change rate
   - Violin plots of price distribution by period
   - Scatter plot of price vs surface area (by period and department)

## Key findings

- Average prices rose ~29% from pre-COVID to post-COVID.
- Price per m² increased ~27% over the same span.
- Transaction volume stayed remarkably stable (~1,200/year) throughout all three periods.
- The steepest price acceleration occurred during 2020-2022.

## License

Dataset: [Licence Ouverte / Open Licence](https://www.etalab.gouv.fr/licence-ouverte-open-licence/) (French government open data).

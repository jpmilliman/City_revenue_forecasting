# City Revenue and Spending Forecasts

**Live dashboard:** <https://jpmillim.shinyapps.io/city-forecasts/>

An interactive dashboard of revenue and spending forecasts for the 300 largest US cities, built in R with Shiny and the `fable` forecasting package.

![Property tax forecasts for Los Angeles, Chicago, Houston and Phoenix, with 95% forecast ranges](screenshots/compare.png)

## What it does

-   Shows each city's history and a three-year forecast for nine accounts, from total revenue and property tax to spending, with 80% and 95% forecast ranges (prediction intervals).
-   Compares one line item across several cities, or every line item for one city.
-   Switches between nominal and inflation-adjusted dollars.
-   Flags unusual values in the history (such as one-off spikes) and fills short gaps in the record.
-   Exports any selection as a CSV table.

![Total revenue for New York City with its forecast range](screenshots/chart.png)

## How it was built

-   **Data:** the Government Finance Database (Pierson, Hand and Thompson, Willamette University), a cleaned version of the US Census Bureau's surveys of city finances, 1970 to 2023.
-   **Source Citation:** Pierson, Kawika, Michael L. Hand, and Fred Thompson. 2015. “The Government Finance Database: A Common Resource for Quantitative Research in Public Financial Analysis.” PLOS ONE 10(6): e0130119. doi:10.1371/journal.pone.0130119.
-   **Cleaning:** checks every series for gaps, stray zeros and unusual values before forecasting.
-   **Forecasting:** exponential smoothing (ETS) and ARIMA models fitted with [`fable`](https://fable.tidyverts.org), on a log scale, with forecast distributions that give the ranges on the chart; inflation adjustment uses the consumer price index from FRED.
-   **Dashboard:** Shiny and bslib, reading forecasts stored as parquet files.

This repository shows the finished dashboard only. The forecasting code and model evaluation are not public; I'm happy to discuss the approach or adapt it for a specific city or agency.

## Contact

Jeffrey Milliman · [jeffrey-milliman.com](https://jeffrey-milliman.com) · [GitHub](https://github.com/jpmilliman)

*Built with AI-assisted development (Claude, by Anthropic), at my direction. Forecasts are demonstrations on public data, not official forecasts or financial advice.*

# Inflation-Adjusted Hourly Wage Growth Across U.S. Industries (2015–2025)

**Lindsey Ramsey**  
NC State University | DSA 405 | Fall 2026

## Project Overview

This project examines how average hourly wages changed across eight major U.S. private-sector industries between 2015 and 2025 after accounting for inflation.

My research question is:

**Which major U.S. private-sector industries experienced the greatest and smallest inflation-adjusted hourly wage growth from 2015 through 2025?**

I chose this topic because wage increases do not always mean workers have more purchasing power. This is a highly spoken about topic today, hence the idea to do a deeper dive. By adjusting hourly earnings for inflation, I wanted to better understand which industries experienced the most and least real wage growth.

## Data Sources

I used two publicly available datasets listed below and provided in the repository.

### 1. Bureau of Labor Statistics (BLS)

- **Data:** Average hourly earnings for eight major private-sector industries
- **Time period:** January 2015–December 2025
- **Frequency:** Monthly
- **Observations:** 1,056
- **Access method:** BLS Public Data API

Source: https://www.bls.gov/

API documentation: https://www.bls.gov/developers/

API terms: https://www.bls.gov/developers/termsOfService.htm

### 2. Federal Reserve Economic Data (FRED)

- **Data:** Consumer Price Index for All Urban Consumers (CPIAUCSL)
- **Frequency:** Monthly
- **Purpose:** Adjust hourly earnings for inflation
- **Access method:** CSV download

Source: https://fred.stlouisfed.org/series/CPIAUCSL

API documentation: https://fred.stlouisfed.org/docs/api/fred/

Terms of use: https://fred.stlouisfed.org/docs/api/terms_of_use.html

The CPI data is originally produced by BLS and made available through FRED.

## Project Files

The repository includes:

- **P2 notebook:** Audits and cleans the BLS hourly earnings data.
- **P3/P4 notebook:** Combines the BLS and CPI datasets, verifies the merge, calculates inflation-adjusted wages, and produces the final analysis and visualizations. 
- **Datasets:** The CSV files provided in the repository.
- **requirements.txt:** Lists the Python packages needed to run the notebooks, also listed in the notebooks themselves.

The P4 analysis was added to the P3 notebook because it builds directly on the data integration completed during that milestone.

## Data Cleaning and Integration

I started by checking the BLS dataset for missing values, duplicate records, incorrect data types, and unusual values.

Then, I converted the year and hourly earnings variables into numeric types and created month and date columns to make the data easier to analyze. It also allowed me to integrate the datasets with the shared key.

I then combined the BLS wage data with the FRED CPI data using a left join on the monthly date.

The merged dataset contained 1,056 observations. All BLS dates matched CPI dates, but eight observations from October 2025 had missing CPI values.

Rather than estimate the missing CPI values, I excluded these eight observations from the final analysis to avoid incorrect information and analysis. This left 1,048 observations.

For the 2015-to-2025 comparison, I also excluded October 2015 so both years used the same 11 months.

## Analysis Methods

I calculated inflation-adjusted hourly wages using:

**Real Hourly Wage = (Nominal Hourly Earnings / CPI) × 100**

The resulting values are expressed in 1982–1984 dollars per hour.

I then calculated the average real hourly wage for each industry in 2015 and 2025, using the same months in both years.

Finally, I calculated percentage growth for each industry:

**Real Wage Growth (%) = ((2025 Real Wage − 2015 Real Wage) / 2015 Real Wage) × 100**

I used Python and Matplotlib to visualize the results.

## Key Findings

All eight industries experienced positive inflation-adjusted hourly wage growth from 2015 to 2025.

| Industry | Real Wage Growth |
|---|---:|
| Leisure and Hospitality | 17.38% |
| Financial Activities | 11.03% |
| Information | 10.23% |
| Professional and Business Services | 8.13% |
| Construction | 6.74% |
| Trade, Transportation, and Utilities | 4.76% |
| Private Education and Health Services | 3.74% |
| Manufacturing | 3.35% |

**Leisure and Hospitality experienced the greatest growth at 17.38%, while Manufacturing experienced the smallest growth at 3.35%.**

Although Leisure and Hospitality had the highest percentage growth, it still had the lowest average real hourly wage among the industries studied.

## Limitations

This analysis has several limitations.

First, it focuses on eight major private-sector industries rather than every industry in the United States.

Second, the data represents industry averages rather than individual workers' wages. Therefore, the results do not show whether all workers within an industry experienced similar wage growth.

Third, I used national CPI data, which does not account for differences in living costs between regions.

Finally, the October 2025 CPI value was missing from my dataset, so I used 11 matching months for the endpoint comparison.

These findings describe differences in average real wage growth, but they do not establish what caused those differences.

## Software and Packages

The project uses Python and Jupyter notebooks.

Required packages:

- pandas
- numpy
- requests
- matplotlib

These packages are listed in `requirements.txt`.

## How to Run the Project

1. Download or clone this GitHub repository.
2. Open the project in Jupyter Notebook or Google Colab.
3. Install the required packages using:

   `pip install -r requirements.txt`

4. Make sure the BLS and FRED CSV files are available in the file locations expected by the notebooks.
5. Open the P2 notebook and run all cells to reproduce the data audit and cleaning.
6. Open the combined P3/P4 notebook and run all cells to reproduce the data integration, verification, calculations, and visualizations.

The final analysis produces a table of real wage growth by industry and two visualizations:

- A horizontal bar chart comparing inflation-adjusted wage growth across industries.
- A line graph showing inflation-adjusted hourly wages over time.

## AI Use

I used ChatGPT to help troubleshoot Python errors, as well as understand data-cleaning and merging decisions.

I reviewed the code and checked the outputs rather than relying on AI-generated suggestions without verification.

One important correction involved making sure the 2015 and 2025 comparisons used the same months after identifying the missing October 2025 CPI value.

A huge resource that was not AI, but assisted me in learning better code for my project is the matplotlib.org lessons, as well as w3schools.com and docs.python.org.

## Conclusion

This project showed that all eight industries experienced positive average hourly wage growth after adjusting for inflation, but the size of the increases varied considerably 

Leisure and Hospitality experienced the greatest real wage growth, while Manufacturing experienced the smallest.

The project also helped me improve my skills in data cleaning, integrating multiple sources, verifying results, and communicating findings clearly.

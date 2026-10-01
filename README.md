# DSA 405-project
# Industry Wage Growth and Inflation

This project examines how average hourly earnings have changed across eight U.S. industries from 2015 through 2025. The goal of the project is to compare wage growth across industries and eventually determine how those changes compare after accounting for inflation.

## Data Source

The wage data come from the U.S. Bureau of Labor Statistics (BLS) Current Employment Statistics (CES) program. The dataset contains monthly average hourly earnings from January 2015 through December 2025 for eight industries:

- Construction
- Manufacturing
- Trade, Transportation, and Utilities
- Information
- Financial Activities
- Professional and Business Services
- Private Education and Health Services
- Leisure and Hospitality

The original BLS data used for the project are preserved in data/raw/bls_hourly_earnings_raw.csv. Additional source information and the retrieval date are documented in data/raw/SOURCES.md.
## Running It
To run it, open the notebook in Google Colab and run the cells from top to bottom. 

## Part 2: Data Audit and Cleaning

Part 2 audits and cleans the BLS wage dataset. The notebook examines data types, missing values, distinct values, numeric ranges, categorical levels, duplicates, monthly coverage, sentinel values, identifiers, and other potential data-quality issues.

The cleaned data retain all 1,056 original observations. The cleaning process converts `year` and `hourly_earnings` to appropriate data types and creates `month` and `date` variables for chronological analysis.

## Repository Structure

- `data/raw/` — preserved raw BLS data and source documentation
- `data/raw/SOURCES.md` — data source and retrieval information
- `README.md` — project description and instructions
- Project notebook — data audit, cleaning, documentation, and analysis


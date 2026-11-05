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

## P3: Acquisition & Integration

### Data Sources

- **Bureau of Labor Statistics (BLS):** Monthly average hourly earnings across eight U.S. industries.
- **Federal Reserve Economic Data (FRED):** Consumer Price Index for All Urban Consumers (`CPIAUCSL`).

Both datasets cover January 2015 through December 2025.

### Data Acquisition

The BLS dataset was obtained during the earlier project milestones and cleaned for use in P3.

The CPI dataset was acquired from FRED using its CSV. The notebook checks for a cached file before downloading, uses a request timeout, and validates the dataset.

Raw files are stored in `data/raw/`, and processed datasets are stored in `data/processed/`.

### Data Integration

The datasets are joined using the monthly `date` column.

- Join type: Left join
- Relationship: Many-to-one
- BLS observations: 1,056
- CPI observations: 132
- Final merged observations: 1,056
- Unmatched dates: 0

The merge uses `validate="many_to_one"` to protect against duplicate CPI matches.

### Data Verification

The notebook has seven assertions to verify row preservation, unique dates, matched observations, and CPI data quality.

One CPI value is missing for October 2025. Because the BLS dataset contains eight industries per month, this produces eight missing CPI values in the merged dataset.

The missing values were documented, not automatically filled.

### Reproducing the Project

1. Open `DSA405_002_FA26_P3_laramse3.ipynb` in Google Colab.
2. Make sure the BLS file is available at the path expected by the notebook.
3. Run the cells in order.
4. The CPI acquisition code will use the cached CSV if it exists or attempt to download it from FRED.
5. Run the merge and verification cells.
6. Confirm the seven assertions pass.

The final output is saved as:

`data/processed/bls_cpi_merged_verified.csv`


# Mortgage Rates, Housing, and Macroeconomic Conditions

This project analyzes the relationship between U.S. mortgage rates, household formation, inflation, and monetary policy using historical time series data. The analysis focuses on long-run trends and monthly dynamics beginning in the early 1990s, leveraging cleaned and merged datasets from multiple authoritative sources.

## Datasets

### Dataset 1: Mortgage Rates (Freddie Mac PMMS)
**Source:** Freddie Mac Primary Mortgage Market Survey (PMMS)  
https://www.freddiemac.com/pmms  

- File: `historicalweeklydata.xlsx`
- Frequency: Weekly (resampled to monthly)
- Coverage: Pre-1991 to present (analysis restricted to August 1991 onward)

**Variables:**
- `Date`
- `30yr_FRM`: 30-year fixed-rate mortgage
- `30yr_Fees`
- `15yr_FRM`: 15-year fixed-rate mortgage
- `15yr_Fees`

**Processing:**
- Skipped non-data header rows
- Dropped missing values
- Converted date formats to datetime
- Filtered data from August 1991 onward
- Resampled weekly observations to monthly frequency for consistency with other datasets

---

### Dataset 2: Household Estimates (U.S. Census Bureau)
**Source:** U.S. Census Bureau, Housing Vacancy Survey  
Table 13: *Monthly Household Estimates: 1955 to Present*  
https://www.census.gov/housing/hvs/data/histtabs.html  

- File: Excel spreadsheet
- Frequency: Monthly
- Coverage: 1955 to present (entire dataset used)

**Structure:**
- Original format: Wide (one row per year, columns for Jan–Dec)
- Variables: `Year`, monthly household estimates

**Processing:**
- Skipped header and metadata rows
- Dropped NaN values
- Cleaned the `Year` column by extracting numeric values
- Renamed monthly columns for clarity
- Transformed data from wide to long format using `melt`
- Mapped month names (e.g., Jan–Dec) to numeric month values
- Converted observations to a consistent Year–Month format

This transformation produces a long-format dataset where each row corresponds to a unique monthly household observation, enabling direct alignment with mortgage rate data.

---

### Dataset 3: Consumer Price Index (CPI)
**Source:** Federal Reserve Economic Data (FRED)  
Series: CPIAUCSL  
https://fred.stlouisfed.org/series/CPIAUCSL  

- File: CSV
- Frequency: Daily
- Coverage: 1955 to present

**Processing:**
- Data was not altered
- Merged directly with existing dataframes after date alignment

---

### Dataset 4: Federal Funds Rate
**Source:** Federal Reserve Economic Data (FRED)  
Series: FEDFUNDS  
https://fred.stlouisfed.org/series/FEDFUNDS  

- File: CSV
- Frequency: Daily
- Coverage: 1955 to present

**Processing:**
- Data was not altered
- Merged directly with existing dataframes after date alignment

---

## Data Integration & Methodology

- Mortgage rate data is resampled to monthly frequency
- Household, CPI, and Federal Funds data are aligned by Year–Month
- Datasets are merged to create a unified monthly panel suitable for:
  - Time series visualization
  - Correlation analysis
  - Regression modeling
  - Macro–housing relationship analysis

This long-format, monthly panel structure enables clean comparison between mortgage rates, household formation trends, inflation, and monetary policy over time.

## Tools
- Python
- pandas, NumPy
- Jupyter Notebook
- matplotlib / statistical analysis libraries

📓 **Notebook:** [`mortgage_rates.ipynb`](mortgage-rate-analysis.ipynb)

## Notes
This project is for educational and analytical purposes only and does not constitute financial or investment advice.


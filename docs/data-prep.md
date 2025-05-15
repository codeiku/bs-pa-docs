# Data Preparation

Parameters Analyzer requires your data in one of two formats:

- **Unified dataset** with event IDs, timestamps, parameters and quality classification (e.g. a `event,timestamp,quality,parameter` header row)
- **Two separated datasets** with parameters, event IDs and timestamps, plus a target dataset of parameters. The application matches event IDs and merges all columns (using a `left join` recipe step). 

See [data model](data-model.md) for complete details.

> **Note**: Data preparation is critical for Parameters Analyzer. While the application can unify separate datasets, we recommend preparing data into a single dataset in a separate project. This gives you full control over preparation steps and avoids implicit assumptions that might affect interpretation or cause issues in joining your data.

# Data Preparation Recommendations

Follow these guidelines to ensure accurate results aligned with the required **[data model](data-model.md)**:

1. Ensure correct data types
2. Parse dates
3. Use valid column names
4. Remove columns with only empty values
5. Handle target column empty values
6. Optional: remove columns with many empty values
7. Optional: remove duplicated rows
8. Optional: remove highly correlated columns
9. Optional: optimize by splitting datasets and/or encoding categoricals

New to data preparation in Dataiku? Follow our [Data Preparation Quick Start](https://academy.dataiku.comdata-prep.mdaration-quick-start) training.

### 1. Ensure correct data types
- Verify **numerical columns** are stored as numerical types for proper processing
- Update column types directly in Dataiku's dataset schema if needed

### 2. Parse dates
- Make all date columns correctly parsed for compatibility
- Use a prepare recipe as recommended in [Dataiku documentation on parsing dates](https://doc.dataiku.com/dss/latest/preparation/dates.html)

### 3. Use valid column names
- Rename columns using a data preparation recipe
- Use only common characters and enable column naming checks in the [data preparation](data-prep.md)

### 4. Remove columns with only empty values
- Empty columns add no value and increase computation time
- Use Data Quality Rules to check for empty columns ([Column values are empty](https://doc.dataiku.com/dss/latest/metrics-check-data-quality/data-quality-rules.html#column-values-are-empty))
- Remove empty columns using the Dataiku preparation recipe

### 5. Target column with some empty values
- Filter and remove empty values in your target column before analysis
- Use Data Quality Rules to check for empty values
- Remove empty values using Dataiku preparation or filter recipe

### 6. Optional: remove columns with many empty values
- Columns with >50% empty cells may increase computation time without adding value
- Use Data Quality Rules to calculate empty cell percentage
- Consider removing these columns unless critical to your analysis

### 7. Optional: remove duplicated rows
- Duplicated rows increase computation time and may affect results
- Use the [Distinct Recipe](https://doc.dataiku.com/dss/latest/other_recipes/distinct.html) to keep only unique rows

### 8. Optional: remove highly correlated columns
- Remove highly correlated columns for better performance and reduced redundancy
- Generate a correlation matrix to identify redundant columns:
  1. Click on Statistics tab
  2. Select Multivariate analysis then Correlation matrix
  3. Select columns to analyze
  4. Generate the matrix to identify redundant columns

### 9. Optional: optimize processing
- Split datasets with many columns to reduce processing impact and improve interpretation
- Consider encoding categorical columns (stored as `string`) into numerical types for faster processing
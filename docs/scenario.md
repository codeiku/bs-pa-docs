# Scenario

Scenarios in Parameters Analyzer help in preparing your data and environment. 

They handle:

- [Preparing your data](data-prep.md) (creating datasets and pointing the application to your data)
- Checking your data shape for database compatibility
- (Re)building code environments (for admins)

These scenarios are packaged with the application code and cannot be customized. 

## Checking Columns
The data preparation step checks column naming against recommendations. These are based on the overlapping character set supported by all database engines Parameters Analyzer can use in [pushdown mode](processing-mode.md) (only letters, numbers, spaces, hyphens, and underscores). 

Enable column checking by changing `"data_check": false` to `true` in [variables](variables.md).

When enabled, the data preparation step checks your data shape and provides helpful messages for non-conforming columns:

```
Data validation failed:
- Column 'Mixture °C' contains invalid characters: ['°']
- Column 'Recipe, Version' contains invalid characters: [','] 
- Column 'Batch#' contains invalid characters: ['#']
```

**Important**: Data checks are designed not to break existing deployments and must be **enabled explicitly** (see [variables](variables.md)). If set to `true`, the data preparation scenario will not complete if column names don't conform.

## Code Environment
As an admin, you can run the code_environment scenario step to automatically configure the code environment for this application.

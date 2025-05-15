# Release notes

## Version 2.3.2 - Update Release - 2025-05
- Added automatic system turn off when idle
- Added Snowflake compatibility for computation pushdown

## Version 2.3.1 - Bug fixes - 2025-04

- Fixed bug in databricks connection
- Fixed bug when interacting with boolean columns

## Version 2.3.0 - Update Release - 2025-04

### Major improvements
- Added capability to delegate all computations to the database containing the product data. 
- Improved performance for small datasets using the "in-memory" option.
- General improvements to architecture, application quality and maintability.

Handling bigger (massive) datasets is compatible with Databricks and PostgreSQL. Performance is directly related to available computation power: the bigger the underlying database cluster, the faster Parameters Analyzer will run on big datasets. 

### Minor improvements
- Removed the 50k limit on the number of points for the target chart.
- Eliminated initial data duplication.
- Enhanced application launch performance.
- Fixed a minor bug in outliers computation.

## Version 2.1.0 - Stability Release - 2024-12

The most important changes for the December 2024 release (version 2.1.0):

- **Important logical changes**:
    - Adjusted the NOK rate computation to avoid issues with empty fields, see [Methodology](article:8).
    - In some cases score computation could be larger than 100%, fixed. 
- **UX improvements**:
    - Introducing a helpful step to check column naming when preparing data (see [Requirements & data model](article:1)).
    - Selecting the date column in the Dataiku app before launching now only includes `date` columns.
- In these docs, added additional clarity on the assumptions Parameters Analyzer makes about your data and tested limitations. 
- Added Filesystem as supported storage type. Note that filesystem can be less performant than SQL processing on larger datasets.   
- Saving studies and working on a copy of study is now fixed.
- Overall bugfixes and minor improvements to front- and backend.
- (For technical users) general improvements to logging

## Version 2.0.3 - Bug fixes - 2024-09
- Fixed bugs in "local" nok rate computing 
- Filter message fix for categorical variables

## Version 2.0.2 - Update Release - 2024-09
- Fixed bugs in backend
- Fixed bugs in frontend
- Enhanced scenario
- Enhanced defect_binary column handling in backend
- Several UX improvements with filters

## Version 2.0.1 - Bug fixes - 2024-08
- Fixed bugs in frontend
- Fixed bugs in scenario

## Version 2.0.0 - Update Release - 2024-08
- Complete redesign of the Dataiku Application
- Added filtering in the web Application
- Make outliers filtering deactivable
- Charts unified between Standard and Expert mode

## Version 1.2.3 - Bug fixes - 2024-07
- Adjusted Initial build scenario to avoid schema update bug of Dataiku

## Version 1.2.2 - Update Release - 2024-07
- Added Snowflake compatibility
- Added MS SQL compatibility
- Adjusted schema inference logic
- Adjusted [FileUpload] Input Reconfiguration scenario to avoid schema update bug of Dataiku
- Adjusted casting logic in SQL connections
- Fixed bug in statistics when using Dataiku < 12.6
- Renamed 'Correlation' to 'Impact' in charts
- Fixed bug in handling boolean variables

## Version 1.2.1 - Update Release - 2024-06
- Rolled back schema inference
- Fixed bug in target caching logic
- Fixed bug in scoring to avoid rank < 1
- Improved target handling robustness
- Fixed bug in handling booleans (in variables and target)
- Minor bug fixes

## Version 1.2.0 - Update Release - 2024-05
- Improved performance in PostgreSQL
- Enhanced robustness, particularly in handling variables containing integers
- Better management of studies loading

## Version 1.1.2 - Bug fixes - 2024-04
- Fixed bug in Snowflake connection
- Fixed bug in 'mode' statistics display

## Version 1.1.1 - Update Release - 2024-03
- Fixed bug for Dataiku cloud
- Adjust categorical variables detection
- Minor bug fixes

## Version 1.1.0 - Update Release - 2024-03
- All columns displayed in dataiku app, date parsed in the backend
- Dataiku app message to explain how to select a table
- New statistics when target is selected
- Fix bug statistics not updated in study definition
- Improve user experience when defining study (remove all variables, confirmation popin when saving,..)
- Various front end improvements
- Update web app infrastructure

## Version 1.0.2 - Bug fixes - 2024-03
- Fixed bug on scenarios error
- Add exceptions in initial build scenario if empty dataset or selected date doesn't exist
- Minor bug fixes in web app
- Auto date parsing fix
- Renaming solution
- Fixed bug on "load from database" option

## Version 1.0.0 - Initial Release - 2023-12
- Load a csv or connect to a SQL-like database with process and outcome data
- Run analysis through the web app
- Set and save rules
- See the saved rules
- Work on a copy of a saved rule
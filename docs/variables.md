# Variables 

Parameters Analyzer supports several settings you can control via the _settings_ pane in DSS.

As an example, this is a valid _global variables_ field:

```json
{
  "outliers_filtering": true,
  "data_check": true,
  "pushdown": "memory",
  "idle_timeout_in_minutes": 30,
  "check_interval_for_timeout_in_seconds": 60
}
```

Details for each variable are below. 

## User preferences

### Outlier filtering
If the key `outliers_filtering` is set to `true`, the app will automatically remove the top and bottom 1.5% of values. This setting is designed as an easy way to improve validity of the analysis (outliers can skew your insight as they occur infrequently but can vary wildly from the statistical center of your data). It should however be noted this comes at the cost of control. In any case the preferred way of filtering data is in your prepare step (outlier filtering applied before the data is used in Parameters Analyzer). 

```json
{
  "outliers_filtering": true
}
```

If you have outliers filtered in the dataset you are using Parameters Analyzer with, make sure to put this value to `false` or you will filter unnecessarily. 

### Data checks
If the key `data_check` is set to `true`, the scenario will include a sanity check on your column naming and schema. The exact working is detailed under [Scenario](scenario.md)

```json
{
  "data_check": true
}
```

## Technical variables

### Processing Mode
Version 2.3 of Parameters Analyzer introduced a difference in [processing mode](processing-mode.md): `pushdown` or `memory`. In pushdown mode, all computations are run using the database engine that holds the dataset. In memory mode, all data and computations are loaded into the web application memory. Performance considerations and more details are in the [specs](processing-mode.md).

```json
{
  "pushdown": "memory | pushdown"
}
```

### Idle shutdown
As every user runs their own instance of Parameters Analyzer, applications that are not in use will still occupy a part of the overall resources. To free up these resources, instances of Parameters Analyzer can shut themselves down when no activity is recorded after a specified timeframe and check interval. 

Generally, a lower idle_timeout will free up more unused resources, at the expense of user convenience. It is advised to set the idle_timeout to a value over 30 minutes to make sure there are no unintended shutdowns.

```json
{
  "idle_timeout_in_minutes": 30,
  "check_interval_for_timeout_in_seconds": 60
}
```

# Technical Requirements

## Instance Requirements
Parameters Analyzer requires **Dataiku V13.3+**

## Code Environment
The application uses the code environment **solution_parameters-analyzer** with Python version `3.9`.

Required packages:

```
arrow==1.3.0
boto3==1.37.13
duckdb==1.2.1
Flask-Caching==2.3.1
humanize==4.12.2
pandas==2.2.3
polars==1.25.2
psutil==7.0.0
pyarrow==19.0.1
pydantic==2.10.6
python-dotenv==1.0.1
sqlglot==26.10.1
```

As admin, you can run the _code environment_ [scenario step](scenario.md) to create or update this environment.

## Processing, Database and Connections
Version 2.3 introduced two [processing modes](processing-mode.md): in-memory and pushdown (set through [variables](variables.md)).

- **In-memory option** is compatible with any connection (for smaller datasets)
- **Pushdown option** is tested with PostgreSQL, Snowflake and Databricks (support for other database engines is planned)

With in-memory processing, all computation happens directly in the application instance. This is significantly faster for smaller datasets and with limited users.

For large datasets, Databricks and Snowflake are much more efficient as they're designed for large analytical datasets.

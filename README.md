# globicus_economic_indicators

Pull data from the [Federal Reserve Bank of St. Louis (FRED)](https://fred.stlouisfed.org/) and apply 
transformations to create custom economic indicators.

## Prerequisites

- R
- A FRED account and API key — register at https://fred.stlouisfed.org/ and request a key under 
  *My Account > API Keys*
- MariaDB installed with access to the 'fred' database

## Configuration

Before running, replace the hardcoded credentials in each script with your own:

**FRED API key** (in `usco` and `usld`):
```r
fredr_set_key("your_fred_api_key")
```

**MariaDB connection** (in `usco` and `usld`):
```r
con <- dbConnect(MariaDB(),
                 user = 'your_username',
                 password = 'your_password',
                 dbname = 'fred',
                 host = '127.0.0.1')
```



## Project Structure

| File/Module | Description |
|---|---|
| `econ_data_functions` | Core functions for transforming raw FRED data into economic indicators |
| `usld` | Applies transformations to leading variables to produce leading indexes |
| `usco` | Applies transformations to lagging variables to produce lagging indexes |

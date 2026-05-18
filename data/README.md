# DATA 221 Final Project Data Pull

Pulled from the World Bank API for 10 countries over 2010–2020.

## Countries

- United States (`USA`)
- China (`CHN`)
- Russian Federation (`RUS`)
- United Kingdom (`GBR`)
- Germany (`DEU`)
- Korea, Rep. (`KOR`)
- France (`FRA`)
- Japan (`JPN`)
- Saudi Arabia (`SAU`)
- Israel (`ISR`)

## Files

- `raw/world_bank/*.json`: raw API responses by World Bank indicator.
- `raw/world_bank/*.csv`: normalized long-form data by indicator.
- `processed/world_bank_country_year_2010_2020.csv`: long-form combined dataset.
- `processed/world_bank_country_year_2010_2020_wide.csv`: analysis-ready country-year table, one row per country-year.
- `processed/world_bank_codebook.csv`: indicator codebook.
- `processed/world_bank_missingness.csv`: missing-value counts by variable.

## Indicators

| Variable | World Bank indicator | Role |
|---|---|---|
| `pm25_mean_exposure` | `EN.ATM.PM25.MC.M3` | Environmental / outcome |
| `fossil_fuel_energy_pct` | `EG.USE.COMM.FO.ZS` | Direct predictor |
| `energy_use_per_capita_kg_oil_eq` | `EG.USE.PCAP.KG.OE` | Direct predictor |
| `industry_value_added_pct_gdp` | `NV.IND.TOTL.ZS` | Direct predictor |
| `urban_population_pct` | `SP.URB.TOTL.IN.ZS` | Structural predictor |
| `forest_area_pct_land` | `AG.LND.FRST.ZS` | Structural predictor |
| `renewable_energy_pct_total_final` | `EG.FEC.RNEW.ZS` | Structural predictor |
| `life_expectancy_years` | `SP.DYN.LE00.IN` | Social / USI candidate |
| `fertilizer_consumption_kg_per_ha` | `AG.CON.FERT.ZS` | Agricultural / USI candidate |
| `gdp_per_capita_current_usd` | `NY.GDP.PCAP.CD` | Economic / USI candidate |
| `access_to_electricity_pct` | `EG.ELC.ACCS.ZS` | Infrastructure / USI candidate |
| `school_enrollment_secondary_gross_pct` | `SE.SEC.ENRR` | Education / USI candidate |

## Reproduce

From the project directory:

```bash
.venv/bin/python scripts/pull_world_bank_data.py
```

Note: `school_enrollment_secondary_gross_pct` has missing values for some country-years. The fossil fuel indicator also has some missing values and should be inspected before modeling because some later-year values may be reported as zero by the API rather than as missing.

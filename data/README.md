# Data guide

Last updated: 2026-08-25

## Published inputs

| Path | Institution | Period | Granularity and unit | Analytical role | License |
|---|---|---|---|---|---|
| `raw/destatis/12411-0005_de_flat.zip` | Destatis | 2021–2025 | Germany, year-end population by age; persons | National totals | Datenlizenz Deutschland 2.0 |
| `raw/destatis/12411-0013_de_flat.zip` | Destatis | 2021–2025 | State × sex × age × year; persons | Population structure | Datenlizenz Deutschland 2.0 |
| `raw/destatis/23631-0001_de_flat.zip` | Destatis | 2020, 2023 | ICD-10 group × metric × year; million EUR or EUR per resident | Disease-cost context | Datenlizenz Deutschland 2.0 |
| `raw/rki/JHealthMonit_2025_01_Adipositas_Rauchen.pdf` | Robert Koch Institute | 2003/04–2023 | Published adult survey estimates; percent and 95% CI | Obesity trend | CC BY 3.0 DE |

`processed/` contains only the five essential analytical CSV tables used by the public notebooks. These files preserve source periods, units and denominators. No interpolation or imputation is used.

## Restricted WIdO input

The 2024 GLP-1 utilization data were obtained from WIdO PharMaAnalyst. Redistribution rights were not confirmed, so neither the original export nor `fact_wido_observed.csv` is included. An authorized user should export the A10BJ active-ingredient table and place it at:

`data/external/wirkst_export.csv`

The file must be semicolon-delimited and encoded as Windows-1252. Expected columns are listed in `data/external/wido_expected_schema.csv`: `Jahr` (string/integer), `ATC-Code` (string), `Wirkstoff` (string), and the five German-formatted numeric columns for prescriptions, DDD, net costs, cost per prescription and cost per DDD. The notebook validates the schema, year, four expected ATC codes, missing values and duplicate keys before transforming values.

After obtaining authorized access, run `uv sync` and execute `notebooks/05_glp1_utilization_analysis.ipynb`, followed by notebook 07. Without that file, the notebook displays acquisition and placement instructions instead of failing. The WIdO module is **reproducible with authorized external data**, not reproducible from the public clone alone.

Raw files must remain unchanged. Local databases, Parquet files, caches, PBIX files and restricted exports are ignored by Git.

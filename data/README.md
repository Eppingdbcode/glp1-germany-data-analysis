# Data acquisition and local-placement guide

Last updated: 2026-08-27

## Operational acquisition matrix

| Dataset | Exact raw path | Project input | Acquisition method | Required local filename | Original format and encoding | Processed output | Responsible notebook | Redistribution status |
|---|---|---|---|---|---|---|---|---|
| Destatis 12411-0005 | `data/raw/destatis/12411-0005_de_flat.zip` | [Open archived ZIP actually used](raw/destatis/12411-0005_de_flat.zip) | Flat file downloaded through the [GENESIS table 12411-0005 interface](https://www-genesis.destatis.de/datenbank/online/statistic/12411/table/12411-0005) | `12411-0005_de_flat.zip` | ZIP containing semicolon-delimited German CSV | [`fact_population_observed.csv`](processed/fact_population_observed.csv) | [`01_data_inventory_and_import.ipynb`](../notebooks/01_data_inventory_and_import.ipynb); analysis/export in notebook 07 | Public; Datenlizenz Deutschland 2.0 attribution |
| Destatis 12411-0013 | `data/raw/destatis/12411-0013_de_flat.zip` | [Open archived ZIP actually used](raw/destatis/12411-0013_de_flat.zip) | Flat file downloaded through the [GENESIS table 12411-0013 interface](https://www-genesis.destatis.de/datenbank/online/statistic/12411/table/12411-0013) | `12411-0013_de_flat.zip` | ZIP containing semicolon-delimited German CSV | [`fact_population_state_age_sex.csv`](processed/fact_population_state_age_sex.csv) | [`03_population_analysis.ipynb`](../notebooks/03_population_analysis.ipynb); export in notebook 07 | Public; Datenlizenz Deutschland 2.0 attribution |
| Destatis 23631-0001 | `data/raw/destatis/23631-0001_de_flat.zip` | [Open archived ZIP actually used](raw/destatis/23631-0001_de_flat.zip) | Flat file downloaded through the [GENESIS table 23631-0001 interface](https://www-genesis.destatis.de/datenbank/online/statistic/23631/table/23631-0001) | `23631-0001_de_flat.zip` | ZIP containing semicolon-delimited German CSV | [`fact_disease_cost_observed.csv`](processed/fact_disease_cost_observed.csv) | [`06_disease_cost_analysis.ipynb`](../notebooks/06_disease_cost_analysis.ipynb); export in notebook 07 | Public; Datenlizenz Deutschland 2.0 attribution |
| RKI/GEDA obesity trend | `data/raw/rki/JHealthMonit_2025_01_Adipositas_Rauchen.pdf` | [Open archived PDF](raw/rki/JHealthMonit_2025_01_Adipositas_Rauchen.pdf) | Download of the [official RKI publication](https://edoc.rki.de/handle/176904/12455) | `JHealthMonit_2025_01_Adipositas_Rauchen.pdf` | PDF | [`fact_obesity_observed.csv`](processed/fact_obesity_observed.csv), manually structured from published aggregates and confidence intervals | [`04_obesity_trend_analysis.ipynb`](../notebooks/04_obesity_trend_analysis.ipynb); export in notebook 07 | Public; CC BY 3.0 DE publication |
| WIdO PharMaAnalyst A10BJ | `data/external/wirkst_export.csv` | Not available in the repository | Manual portal export; see instructions below | `wirkst_export.csv` | Semicolon-delimited Windows-1252 CSV | Restricted row-level output is not published; notebook creates a validated in-memory analytical table and derived figures | [`05_glp1_utilization_analysis.ipynb`](../notebooks/05_glp1_utilization_analysis.ipynb) | Redistribution rights not confirmed; do not publish raw or row-level data |
| EMA selected GLP-1 authorisations | No archived RAW file; official URLs are stored per row | [`ema_glp1_eu_authorisations.csv`](processed/ema_glp1_eu_authorisations.csv) | Manual consultation and curation from individual EMA EPAR pages | Not applicable | Web/HTML and regulatory product information | [`ema_glp1_eu_authorisations.csv`](processed/ema_glp1_eu_authorisations.csv) | Inventory in notebook 01; export in notebook 07 | Public official pages; curated factual snapshot with per-row URLs |

The **Project input** link opens the archived file actually used in this analysis. The linked repository file is the reproducible snapshot. Each GENESIS link opens the official table interface, establishes provenance, and may require parameter selection and export; it is not a guaranteed direct download of the identical archived ZIP, and the official table may later be revised.

## WIdO PharMaAnalyst: legitimate local acquisition

Do not reconstruct, scrape or commit restricted WIdO observations. A user with legitimate access must:

1. Open the [WIdO PharMaAnalyst portal](https://arzneimittel.wido.de/PharMaAnalyst/).
2. Select reporting year **2024**.
3. Select ATC group **A10BJ** and the **active-ingredient table** (`Wirkstoff`).
4. Export the table as CSV.
5. Preserve the semicolon delimiter and Windows-1252 encoding.
6. Save the unmodified export locally as `data/external/wirkst_export.csv`.
7. Compare its header with [`data/external/wido_expected_schema.csv`](external/wido_expected_schema.csv).
8. Run `uv sync`, execute notebook 05, and then execute notebook 07 for reconciliation.

The expected columns are `Jahr`, `ATC-Code`, `Wirkstoff`, `Verordnungen in Tsd.`, `Tagesdosen in Tsd. DDD`, `Nettokosten in Tsd. Euro`, `Nettokosten je Verordnung`, and `Nettokosten je Tagesdosis`. Notebook 05 checks the schema, year, expected ATC codes, missing values and duplicate keys before parsing German-formatted numeric fields. Without a legitimately obtained file, it prints acquisition guidance instead of exposing or fabricating observations.

## Reproducibility boundaries

Public RAW and processed inputs are preserved and auditable, but the current repository does not automate the full Destatis RAW-to-processed reconstruction. RKI values were manually transcribed from published aggregate estimates and confidence intervals; no OCR or individual-level data were used. EMA rows were manually curated from individual official EPAR pages. WIdO reproduction is conditional on an independently obtained legitimate export. No acquisition API is implemented.

Raw source files must remain unchanged. Local databases, Parquet files, caches, PBIX files and restricted exports are ignored by Git.

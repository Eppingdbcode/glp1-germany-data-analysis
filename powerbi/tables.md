# Dashboard tables

| Table | Grain | Main fields | Source | Dashboard usage |
|---|---|---|---|---|
| ema_glp1_authorisations | Selected EU authorisation | active ingredient, product, date, indication | EMA; publicly included | Regulatory table |
| fact_population_observed | Year × official age code | year, age label, population | Destatis 12411-0005; publicly included | National checks |
| fact_population_state_age_sex | Year × state × sex × age | year, state, sex, age group, population | Destatis 12411-0013; publicly included | Population page |
| fact_obesity_observed | Published survey period | period, estimate, 95% CI | RKI; publicly included | Obesity KPIs and trend |
| fact_disease_cost_observed | Year × diagnosis group × metric | year, ICD-10 group, value, unit | Destatis 23631-0001; publicly included | Disease-cost KPI |
| fact_wido_observed | 2024 × ATC active ingredient | prescriptions, DDD, reported costs | WIdO PharMaAnalyst; externally required, not distributed | GLP-1 use and costs |

`dim_date`, `dim_geography`, `dim_sex`, `dim_age` and `dim_substance` are small semantic-model dimensions derived from these fields; they are not separate public exports.

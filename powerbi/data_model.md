# Data model

```mermaid
flowchart LR
  Date[dim_date] --> Obesity[fact_obesity_observed]
  Date --> Costs[fact_disease_cost_observed]
  Date --> Population[fact_population_state_age_sex]
  Geography[dim_geography] --> Population
  Sex[dim_sex] --> Population
  Age[dim_age] --> Population
  Date --> WIdO[fact_wido_observed external]
  Substance[dim_substance] --> WIdO
  EMA[ema_glp1_authorisations] -. regulatory context .-> Substance
```

Dimensions filter facts in a single direction. Facts retain their native grains and periods; no fact-to-fact filtering is used. The national population table supports reconciliation, while the state-age-sex table drives interactive population analysis. Auto Date tables are intentionally omitted.

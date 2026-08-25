# Measure catalog

| Measure | Purpose | Source table | Python/notebook equivalent | Format |
|---|---|---|---|---|
| Population Display | Population in selected context | fact_population_state_age_sex | Notebook 03, grouped sum | `0.0 Mio.` |
| Population Share Display | Selected share of national total | fact_population_state_age_sex | Notebook 03, grouped sum / national sum | `0.0%` |
| Obesity Prevalence 2023 Display | Latest published prevalence | fact_obesity_observed | Notebook 04, 2023 estimate | `0.0%` |
| Adipositas Veränderung pp Display | Absolute prevalence change | fact_obesity_observed | Notebook 04, end minus start | signed percentage points |
| Adipositasprävalenz Anzeige | Trend-series value | fact_obesity_observed | Notebook 04, estimate_pct | `0.0%` |
| Diabetes Cost 2023 Display | E10–E14 costs in 2023 | fact_disease_cost_observed | Notebook 06, filtered value | `0.00 Mrd. €` |
| Prescriptions Observed | Recorded 2024 prescriptions | fact_wido_observed (external) | Notebook 05, sum × 1,000 | integer |
| Arzneimittelkosten Mio EUR | Reported 2024 medicine costs | fact_wido_observed (external) | Notebook 05, sum × 1,000 / 1,000,000 | `0.0 Mio. €` |

# Power BI dashboard

The five-page dashboard tells this story:

1. **Overview** — national headline indicators for population, obesity and diabetes costs.
2. **Population** — 2021–2025 resident population by year, federal state, sex and age group.
3. **GLP-1 authorisations and GKV use** — selected EMA authorisations plus 2024 prescriptions and reported medicine costs from legitimately obtained WIdO data.
4. **Insights** — interpretation, scope boundaries and unanswered policy questions.
5. **Sources** — provenance, periods and limitations.

Preserved public processed tables reproducibly feed the overview, population, obesity, disease-cost and EMA elements, and notebook 07 copies them deterministically into `data/powerbi_exports/`. The public RAW snapshots and processed tables are auditable, but the repository does not currently automate complete Destatis RAW-to-processed reconstruction. RKI aggregates were manually transcribed from the official publication, and EMA fields were manually curated from individual EPAR pages. WIdO-powered GLP-1 visuals require an independently obtained legitimate local export because redistribution rights are not confirmed. Reporting periods remain separate: obesity 2003/04–2023, disease costs 2020/2023, population 2021–2025, and WIdO 2024. They are not a single directly comparable time series.

See [tables.md](tables.md), [data_model.md](data_model.md), [measures.dax](measures.dax), and [measure_catalog.md](measure_catalog.md).

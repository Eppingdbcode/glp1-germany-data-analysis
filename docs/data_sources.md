# Data sources

Last updated: 2026-08-25

| Institution | Dataset | Period | Geography / population | Unit and use | Limitations | Official URL |
|---|---|---|---|---|---|---|
| Destatis | Population tables 12411-0005 and 12411-0013 | 2021–2025 | Germany; registered residents | Persons; totals and demographic structure | Census-basis break between 2021 and 2022 | [GENESIS-Online](https://www-genesis.destatis.de/) |
| Robert Koch Institute | GEDA obesity trend | 2003/04–2023 | Germany; weighted adults aged 18+ | Percent and 95% CI; national trend | Self-reported height/weight; age-standardized; not a resident-population rate | [RKI publication](https://edoc.rki.de/handle/176904/12455) |
| WIdO | PharMaAnalyst, ATC A10BJ | 2024 | German GKV outpatient prescriptions in covered pharmacies | Thousand prescriptions, DDD and EUR; utilization comparison | Prescriptions are not patients; indication unavailable; private/self-pay excluded | [WIdO PharMaAnalyst](https://arzneimittel.wido.de/PharMaAnalyst/) |
| Destatis | Disease costs 23631-0001 | 2020, 2023 | Germany; all payers | Million EUR and EUR per resident | E10–E14 includes type 1, type 2 and other diabetes; not GLP-1 costs | [GENESIS-Online](https://www-genesis.destatis.de/) |
| European Medicines Agency | EU authorisations for displayed reference products | 2006–2022 | European Union | Authorisation date and indication context | Does not establish German market entry or utilization | [EMA medicines](https://www.ema.europa.eu/en/medicines) |

The WIdO source file and its row-level processed table are excluded because redistribution rights were not confirmed. Authorized users must place the export at `data/external/wirkst_export.csv`; the required schema and rerun instructions are in `data/README.md`. Consequently, the WIdO module is **reproducible with authorized external data**.

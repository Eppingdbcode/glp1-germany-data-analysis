# Methodology

Last updated: 2026-08-25

## Analytical question

How do Germany's population structure, published adult obesity estimates, direct disease costs and recorded 2024 GKV GLP-1 utilization describe the context for a future reimbursement assessment?

## Workflow

Official source files are inventoried and imported with explicit encodings and delimiters. Validation covers schema, keys, duplicates, missing values, periods, categories, units and source-specific control totals. German-formatted numbers are converted only after removing thousands separators and replacing decimal commas. Published composite periods such as 2003/04 remain intact.

The analysis keeps four scopes separate: registered residents, weighted adult survey participants, GKV outpatient prescriptions, and national all-payer disease costs. Derived measures include absolute percentage-point change, relative change, prescription and cost shares, and cost per prescription. They are calculated transparently in Python and reconciled with the DAX measures used by Power BI.

The processed CSVs are the interface between Python and Power BI. No missing value is converted to zero, no year is interpolated and no incompatible population or payer scope is combined. The WIdO transformation can be rerun only when an authorized local export is supplied.

## Limitations

Sources use different periods and denominators. Prescriptions are not patients, indication is unavailable, and WIdO covers 2024 GKV outpatient activity only. Obesity estimates are national, adult, weighted and age-standardized and cannot be filtered reliably by sex or federal state. Disease costs cover all payers; E10–E14 does not isolate type 2 diabetes. The data support descriptive context, not causal GLP-1 effects, ROI, savings or budget impact.

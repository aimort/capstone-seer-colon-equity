# capstone-seer-colon-equity
Predicting late-stage diagnosis and surgical treatment gaps in colon cancer (SEER)

QM 640 Data Analytics Capstone — Walsh College
Author: Mohamed Mortagy

## Problem
Colon cancer can be detected ny screening and is curable when diagnosed early and treated with surgery. However, many patients are diagnosed after disease spread, and some patients with curable disease don't receive surgery. Both problems could happen with disadvantaged patients. Acancer-control program can target
screening and allocate resources

## Research questions
- RQ1: Which characteristics are independently associated with a late-stage diagnosis?
- RQ2: How well can late-stage diagnosis be predicted?
- RQ3: Which characteristics are associated with non-receipt of cancer-directed surgery?
- RQ4: How well can non-receipt of surgery be predicted?

##  Data availability
This project uses the **SEER Research Data (17 Registries, November 2025
submission)** from the U.S. National Cancer Institute.

**The data are NOT included in this repository and cannot be redistributed**,
per the SEER Research Data Use Agreement.

To obtain the data yourself:
1. Request access at https://seer.cancer.gov/data/access.html
   (you must sign the SEER Data Use Agreement)
2. Install SEER*Stat: https://seer.cancer.gov/seerstat/
3. Run the query in [`seerstat/query_spec.md`](seerstat/query_spec.md), which
   reproduces the exact cohort used here.
4. Export as a text file and place it in `data/` (git-ignored).

## Dataset
- **Source:** SEER Incidence, 17 Registries, Nov 2025 sub (2000–2023), linked to
  county attributes (income/rurality) - URL: https://seer.cancer.gov/data-software/documentation/seerstat/nov2025/ 
- **Cohort:** adults 18+, first primary colon adenocarcinoma, 2018–2023,
  microscopically confirmed. N = 100,131.
- **Outcomes:** late-stage at diagnosis (regional/distant vs localized);
  receipt of surgery
- **Key features:** age band, sex, race/ethnicity, colon subsite, county median
  household income, rurality, marital status, tumour grade, histology, tumour size
- **Data dictionary:**
**late_stage**  Combined Summary Stage with Expanded Regional Codes (2004+). Binary. Outcome (RQ1, RQ2). 1 = regional/distant; 0 = localized.
**surgery**  Reason no cancer-directed surgery. Binary. Outcome (RQ3, RQ4). 1 = cancer-directed surgery; 0 = none.
**age_group**  Age at diagnosis. Categorical. Predictor (all RQs). <50; 50-64; 65-74; 75+.
**age_num**  Age at diagnosis. Numerical. Predictor (all RQs). Years.
**sex**  Sex. Categorical. Predictor (all RQs). Male; Female.
**race_eth**  Race/ethnicity recode. Categorical. Predictor (all RQs). Non-Hispanic White; Non-Hispanic Black; Hispanic; Non-Hispanic Asian or Pacific Islander; Non-Hispanic American Indian or Alaska Native.
**subsite**  Primary Site - labeled. Categorical. Predictor (all RQs). Proximal/right (C18.0, C18.2-C18.4); distal/left (C18.5-C18.7).
**income5** County median household income (SEER county attribute). Ordinal. Predictor (all RQs). <$60k; $60-75k; $75-90k; $90-110k; $110k+.
**rurality**  Rural-Urban Continuum (derived). Categorical. Predictor (all RQs). Metropolitan; non-metropolitan.
**marital**  Marital status at diagnosis (recode). Categorical. Predictor (all RQs). Married; unmarried (single/separated/divorced/widowed).
**grade**  Grade. Categorical. Predictor (RQ3, RQ4). Low; High.
**histology**  ICD-O-3 histology. Categorical. Predictor (RQ3, RQ4). Adenocarcinoma NOS; variant.
**tumor_size**  Tumor Size Summary. Continuous. Predictor (RQ3, RQ4). Millimetres.

## How to run
```bash
pip install -r requirements.txt
jupyter notebook notebooks/01_cleaning.ipynb
```

## Compliance
Data cannot be redistributed; code is shared without data per the SEER DUA.
Only aggregated, non-identifying outputs appear in this repository. 
Any table cell based on a count of 1–4 is suppressed.

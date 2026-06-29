# IDX Exchange Data Science Track

This repository contains weekly work for a housing-price prediction project using CRMLS sold-property data.

## Progress

**Week 1: Metadata Review**

- Reviewed the project scope and key metadata fields.
- Set the required analysis filter to `Residential` and `SingleFamilyResidence`.
- Identified `ClosePrice` as the target variable.
- Noted early data-leakage concerns for modeling.

**Week 2: EDA Exploration**

- Created `01_exploration.ipynb`.
- Loaded selected columns from the local `data/` folder.
- Filtered to the required residential single-family population.
- Explored distributions for `ClosePrice`, `LivingArea`, bedrooms, bathrooms, and lot size.
- Added basic summary tables and EDA plots.

**Week 3: Data Preprocessing**

- Created `02_preprocessing.ipynb` and `data/week3_cleaned.csv`.
- Added training-only imputation, missing-value flags, categorical encoding, outlier clipping, and numerical scaling.
- Reserved May 2026, the most recent close month, as the test set.
- Compared 3- to 48-month rolling windows on April 2026 and selected `X = 36` months.
- Exported a modeling table with numeric, non-missing features and explicit train/test labels.

## Files

- `WEEK1_SETUP_AND_METADATA_NOTES.md`: brief Week 1 setup and metadata notes.
- `01_exploration.ipynb`: Week 2 pandas exploration notebook.
- `02_preprocessing.ipynb`: Week 3 preprocessing and time-split notebook.
- `data/week3_cleaned.csv`: cleaned modeling data (local only; ignored by git).

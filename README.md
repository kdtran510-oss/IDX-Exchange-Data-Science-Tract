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

**Week 4: Baseline Model**

- Created `03_baseline_model.ipynb`.
- Trained an ordinary least squares Linear Regression model on the Week 3 cleaned training set.
- Evaluated on the May 2026 holdout test set.
- Recorded baseline test R² = 0.300, with MAE about $511,938 and RMSE about $1.40M.

**Week 5: Additional Models**

- Created `04_model_comparison.ipynb`.
- Installed and used `scikit-learn` for Decision Tree and Random Forest regressors.
- Used a 30-month training window from November 2023 through April 2026, with May 2026 held out for testing.
- Removed implausible/extreme target values using a $50K lower bound and the training-set 99.5th percentile upper bound.
- Added training-only smoothed city/ZIP target encodings.
- Compared test R²: Linear Regression = 0.736, Decision Tree = 0.735, Random Forest = 0.838.
- Documented that Random Forest performed best, while the single Decision Tree was more brittle on R².

## Files

- `WEEK1_SETUP_AND_METADATA_NOTES.md`: brief Week 1 setup and metadata notes.
- `01_exploration.ipynb`: Week 2 pandas exploration notebook.
- `02_preprocessing.ipynb`: Week 3 preprocessing and time-split notebook.
- `03_baseline_model.ipynb`: Week 4 Linear Regression baseline notebook.
- `04_model_comparison.ipynb`: Week 5 Decision Tree and Random Forest comparison notebook.
- `data/week3_cleaned.csv`: cleaned modeling data (local only; ignored by git).

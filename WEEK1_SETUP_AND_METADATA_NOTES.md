# Week 1 - Orientation, Setup, and Metadata Notes

## 1. Project goal

Build a reproducible machine-learning workflow that predicts `ClosePrice`, the final sale price of a California residential single-family property, from characteristics available at prediction time.

The required modeling population is:

- `PropertyType = Residential`
- `PropertySubType = SingleFamilyResidence`

At least six months of `CRMLSSold` data must be copied from the FTP raw folder to a local, read-only data folder. Raw source files must never be modified.

## 2. Environment and repository status

Fill this section before submission.

| Check | Status / evidence |
|---|---|
| Operating system | Windows 10 |
| Python installed | `[fill in: python --version]` |
| Git installed | `[fill in: git --version]` |
| IDE or Jupyter available | `[fill in: VS Code / JupyterLab / Colab]` |
| Virtual environment created | `[fill in date]` |
| Dependencies installed | `[fill in date]` |
| Raw data folder protected by `.gitignore` | Yes |
| FTP access confirmed | `[fill in date]` |
| Metadata PDF reviewed | `[fill in date]` |

## 3. Dataset access log

Do not paste credentials into this document or into source code.

| Item | Confirmation |
|---|---|
| FTP directory | `/raw/California` |
| Filename prefix | `CRMLSSold` |
| Local raw-data folder | `data/raw/` |
| Number of source files | `[fill in after download]` |
| Earliest close month | `[YYYY-MM]` |
| Latest close month | `[YYYY-MM]` |
| Distinct close months | `[must be at least 6]` |
| Approximate total rows | `[fill in]` |
| Access-check result | `[PASS / needs attention]` |

## 4. Key columns

The first eight rows below are the minimum Week 1 notes directly implied by the task. Names can vary slightly across exports, so reconcile the exact field name and official wording with `Trestle Property MetaData.pdf` before submission.

| Column or concept | Working meaning | How it will be used |
|---|---|---|
| `ClosePrice` | Final recorded sale price. This is the target variable. | Predicted outcome; never included in model inputs. |
| `CloseDate` | Date the transaction closed. | Confirms month coverage, supports time trends, and later defines train/test periods. |
| `PropertyType` | Broad property classification. | Required scope filter: keep `Residential`. |
| `PropertySubType` | More specific property classification. | Required scope filter: keep `SingleFamilyResidence`. |
| `LivingArea` | Reported living-area quantity; verify the unit field and metadata definition. | Core size feature and EDA distribution. |
| `BedroomsTotal` or equivalent | Reported number of bedrooms. | Core count feature and EDA distribution. |
| `BathroomsTotalInteger`, `BathroomsTotalDecimal`, or equivalent | Reported bathroom count. Prefer the most complete total field available. | Core count feature and EDA distribution. |
| `LotSizeArea` and `LotSizeUnits`, or square-foot equivalent | Reported lot size plus its unit. Unit consistency must be checked before modeling. | Core land-size feature and EDA distribution. |
| `YearBuilt` | Reported year the structure was built. | Later supports property-age feature engineering. |
| `Latitude`, `Longitude` | Geographic coordinates, when present. | Later supports regional features and school-district spatial joins. |
| `City`, `PostalCode`, `CountyOrParish` | Geographic labels. | EDA by area and possible categorical model features. |
| `ListPrice` | Most recent or recorded list price, depending on metadata. | Treat cautiously: it may be unavailable for off-market query properties and can dominate the prediction. |
| `StandardStatus` or equivalent | Listing/transaction status. | Data-quality validation that sold records are actually closed. |
| Source filename | Name of the CRMLSSold file from which a row was loaded. | Auditing, month coverage checks, and reproducibility. |

## 5. Data-leakage rules established in Week 1

A feature leaks information when it would not be known at the moment the prediction is supposed to be made.

Do not use any of the following as model inputs unless the mentor explicitly approves a narrowly defined prediction timestamp:

- `ClosePrice` or any transformed copy of it;
- fields created after closing, such as final concessions or buyer-side closing outcomes;
- fields that directly encode the final transaction result;
- post-sale status dates or remarks that reveal the sale price.

`ListPrice` requires a deliberate decision. The task asks for predictions for properties that may not currently be listed, so a core model should be able to run without it. A later experiment can compare a property-characteristics-only model against a listed-property model that includes list price.

## 6. Initial data-quality questions for Week 2

1. Are all six months structurally consistent, or do column names/types change?
2. How many rows survive the required property filters?
3. Are prices and areas numeric after removing commas and currency symbols?
4. Which core fields have the highest missingness?
5. Are lot-size units mixed across rows?
6. Are there impossible or extreme values, such as zero price, zero living area, or implausible bedroom counts?
7. Does the number of records vary sharply by month?
8. Are duplicate listing identifiers or duplicate property-month records present?

## 7. Week 1 completion statement

> I reviewed the project prompt, established a reproducible Python environment, copied at least six months of CRMLSSold files without modifying the FTP raw folder, reviewed the Trestle metadata, documented the core fields, and defined the required Residential / SingleFamilyResidence scope and initial leakage rules.

Replace this statement with actual confirmation only after `python week1_access_check.py` passes and the access-log blanks are filled.

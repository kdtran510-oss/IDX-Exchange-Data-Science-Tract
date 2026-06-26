# Week 1 - Setup and Metadata Notes

## Project Scope

The goal is to build a reproducible data-science workflow for predicting `ClosePrice`, the final sale price of a California residential single-family property.

The required analysis population is:

- `PropertyType = Residential`
- `PropertySubType = SingleFamilyResidence`

Raw CRMLS sold files are stored locally in the `data/` folder and are ignored by git so they are not pushed to GitHub.

## Metadata Review

The Week 1 review focused on identifying the target variable, required filters, and core property fields needed for early exploration and later modeling.

| Field | Purpose |
|---|---|
| `ClosePrice` | Target variable to predict. |
| `CloseDate` | Used to check time coverage and close-month patterns. |
| `PropertyType` | Required filter for residential properties. |
| `PropertySubType` | Required filter for single-family residences. |
| `LivingArea` | Main property-size feature. |
| `BedroomsTotal` | Bedroom-count feature. |
| `BathroomsTotalInteger` | Bathroom-count feature. |
| `LotSizeSquareFeet` / `LotSizeArea` | Lot-size feature for land area. |
| `City`, `PostalCode`, `CountyOrParish` | Location fields for later analysis. |
| `Latitude`, `Longitude` | Geographic fields for possible spatial features. |
| `YearBuilt` | Potential feature for property age. |
| `ListPrice` | Useful but should be treated carefully because it may not always be available at prediction time. |

## Leakage Notes

`ClosePrice` is the outcome and should not be used as a model input. Any fields created after closing, or fields that directly reveal final transaction results, should also be excluded from model features.

`ListPrice` may be useful for later experiments, but the main model should first work from property characteristics that would be available before knowing the final sale price.

## Week 1 Outcome

Week 1 established the project scope, reviewed the metadata, identified the key fields, and set up the basic rule that analysis should focus on residential single-family properties only.

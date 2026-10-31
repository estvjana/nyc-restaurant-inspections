# Data Overview

**Source:** NYC DOHMH Restaurant Inspection Results (NYC Open Data). Snapshot date: 2026-08-27.

## At a Glance

| Item | Raw dataset | Prepared dataset |
|---|---|---|
| Rows | 296,012 | 295,843 |
| Columns | 27 | 32 |
| Unique restaurants (CAMIS) | 31,366 | 31,366 |
| Restaurants with at least one real inspection | 27,652 | 27,652 |
| Inspections (one per restaurant, date and type, excluding placeholders) | 93,292 | 93,292 |
| Inspection dates | 2007-08-10 to 2026-08-24 | same |

The prepared dataset is the raw dataset after data preparation and structural cleaning (Tasks 1 to 11). See the README to download it and the `handoff` folder for the files that explain every change.

Most records are from 2022 to 2026. Only about 2,600 rows are older, so trend and seasonality work should focus on 2022 to 2026.

## How the Data Is Structured

Each row is one **violation**, not one inspection. An inspection with several violations appears on several rows, and the score, grade and date repeat on each of them. Counts of rows are therefore not counts of inspections or restaurants.

## Data Quality Issues

Numbers in the Size column are from the raw dataset.

| Issue | Size | Plan or status |
|---|---|---|
| Placeholder date 01/01/1900 (restaurant not inspected yet) | 3,714 rows | Done: flagged in `AWAITING_INSPECTION`. The rows and the date are kept. |
| BORO = 0 (borough unknown) | 351 rows (84 restaurants) | Done: flagged in `BORO_UNKNOWN`. BORO keeps its original value. |
| Latitude and Longitude both 0 | 3,032 rows (447 restaurants) | Done: both set to empty and flagged in `ZERO_COORDINATES`. |
| BBL with 1 digit instead of 10 | 4,268 rows (612 restaurants) | Done: BBL set to empty and flagged in `BBL_INCOMPLETE`. |
| Exact duplicate rows | 169 rows | Done: removed from the prepared dataset and listed in `handoff/duplicate_exclusion_log.csv`. |
| Wrong data types | Dates were text. ZIPCODE, Community Board, Council District, Census Tract, BIN and BBL were numbers. | Done: dates converted to dates and identifiers stored as text. Load the file with the code in the last cell of `01_data_exploration.ipynb`. |
| GRADE empty | 150,672 rows (51%) | Expected: grades are only issued on some inspections. Keep as missing. |
| GRADE DATE empty | 160,961 rows (54%) | Same reason as GRADE. |
| SCORE empty | 17,226 rows (6%) | About 10,336 inspections. Most are inspection types that are not scored. Keep as missing. |
| GRADE codes N, Z, P | 10,299 / 4,801 / 747 rows | Official status codes (not yet graded, grade pending). Keep as they are. |
| CRITICAL FLAG "Not Applicable" | 8,262 rows | Used when no violation was recorded. |
| VIOLATION CODE and DESCRIPTION empty | 6,444 rows (2%) | No violation to describe. Keep. |
| Other missing values | CUISINE 3,794, ZIPCODE 3,082, Census Tract 4,742, Latitude and Longitude 1,672 | Review column by column. |

## Key Columns

| Purpose | Columns |
|---|---|
| Restaurant identity | CAMIS, DBA (name), CUISINE DESCRIPTION |
| Outcome | SCORE, GRADE, ACTION (closures and re-openings) |
| Risk | VIOLATION CODE, CRITICAL FLAG |
| Text mining | VIOLATION DESCRIPTION |
| Place | BORO, ZIPCODE, NTA, Census Tract, Latitude, Longitude |
| Inspection details | INSPECTION DATE, INSPECTION TYPE |

**Planned data integration:** merge census tract income and demographic data using the Census Tract column.

## Data Files

The CSV files are large, so they are not stored in the repo.

- **Raw dataset:** download it from the Releases page (tag `data-v1`) or from the team Google Drive folder (see README).
- **Prepared dataset:** download `restaurants_prepared.csv.zip` from the Releases page (tag `prepared-data-v1`). Use this one for the analysis.
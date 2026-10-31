# Data Overview

**Source:** NYC DOHMH Restaurant Inspection Results (NYC Open Data). Snapshot date: 2026-08-27.

## At a Glance

| Item | Value |
|---|---|
| Rows | 296,012 |
| Columns | 27 |
| Unique restaurants (CAMIS) | 31,366 |
| Restaurants with at least one real inspection | 27,652 |
| Inspections (one per restaurant, date and type, excluding placeholders) | 93,292 |
| Inspection dates | 2007-08-10 to 2026-08-24 |

Most records are from 2022 to 2026. Only about 2,600 rows are older, so trend and seasonality work should focus on 2022 to 2026.

## How the Data Is Structured

Each row is one **violation**, not one inspection. An inspection with several violations appears on several rows, and the score, grade and date repeat on each of them. Counts of rows are therefore not counts of inspections or restaurants.

## Data Quality Issues

| Issue | Size | Plan |
|---|---|---|
| Placeholder date 01/01/1900 (restaurant not inspected yet) | 3,714 rows | Flag as "awaiting inspection". Keep in the source. |
| BORO = 0 (borough unknown) | 351 rows (32 restaurants) | Mark as unknown. |
| Exact duplicate rows | 169 rows | Review, then remove from the working copy and record in an exclusion log. |
| GRADE empty | 150,672 rows (51%) | Expected: grades are only issued on some inspections. Keep as missing. |
| GRADE DATE empty | 160,961 rows (54%) | Same reason as GRADE. |
| SCORE empty | 17,226 rows (6%) | About 10,336 inspections. Most are inspection types that are not scored. Keep as missing. |
| GRADE codes N, Z, P | 10,299 / 4,801 / 747 rows | Official status codes (not yet graded, grade pending). Keep as they are. |
| CRITICAL FLAG "Not Applicable" | 8,262 rows | Used when no violation was recorded. |
| VIOLATION CODE and DESCRIPTION empty | 6,444 rows (2%) | No violation to describe. Keep. |
| Other missing values | CUISINE 3,794, ZIPCODE 3,082, Census Tract 4,742, Latitude and Longitude 1,672 | Review column by column. |
| Wrong data types | Dates are text. ZIPCODE, Census Tract, BIN and BBL are numbers. | Convert dates to dates and identifiers to text. |

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


## Data File

The CSV is large, so it is not stored in the repo. Download it from the Releases page or from the team Google Drive folder (see README).
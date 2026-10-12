# Healthcare Dataset Cleaning in Excel

Cleaning a messy 55,500-row hospital admissions dataset using Excel, with every issue, fix and assumption documented.

## Dataset
- Source: Kaggle "Healthcare Dataset" (user: prasad22)
- Note: the data is **synthetic**, not real patient records
- Size: 55,500 rows, 15 columns (patient, doctor, hospital, admission and discharge dates, billing, medication, test results)

## Issues found and fixes

| Issue | Fix | Count |
|---|---|---|
| Exact duplicate records | Data > Remove Duplicates | 534 removed (55,500 → 54,966 rows) |
| Patient names with random upper/lower case | Standardised to proper case | 54,933 |
| Titles and suffixes in patient names (Mr., Dr., MD, Jr. etc.) | Stripped to plain names for consistency | 2,064 |
| Titles and suffixes in doctor names | Stripped to plain names for consistency | 2,192 |
| Hospital names with "and" and commas out of place, and suffixes (Inc, Ltd, LLC) at the front | Reformatted using Excel formulas | 45,130 |
| Negative billing amounts | Flagged, then converted to positive | 106 |
| Billing values with long decimals | Rounded to 2 decimals | All rows |

## Assumptions
- Negative billing amounts were treated as sign-entry errors. In real billing they could be refunds, so this would be confirmed with the data owner.
- Hospital names looked word-shuffled, so I **standardised the format** rather than claiming to restore the original names.
- Titles and suffixes were removed to keep names consistent across patient and doctor columns.

## Validation
After cleaning: 0 duplicates, 0 blank cells, 0 negative billing values, and every discharge date falls on or after its admission date.

## Tools
Excel: Remove Duplicates, LET, TEXTSPLIT, TEXTBEFORE, TEXTAFTER, FILTER, ROUND, ABS, COUNTIF, TRIM,.

## Files
- `raw/` original dataset, untouched
- `cleaned/` cleaned dataset

## Author
 Afolashade Adebowale, Business Intelligence/Data Analyst.

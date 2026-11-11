 Step 1: Initial Attempt (Diagnosis & Planned Decisions)
 Commit Snapshot Hash
`[Paste your git commit hash here after committing your initial work before AI]
Data Diagnosis (`teaching_prices_messy.csv`)
Before running any external tools, our manual inspection of the messy dataset revealed the following issues:
1. Missing Values: The `unit_price` column contains null values and empty strings.
    Code revealing it: `df.isnull().sum()`
   Planned Decision: Investigate / Correct (impute missing values with the median by category rather than dropping rows).
2. Inconsistent Casing & Whitespaces: `item_name` and `item_category` contain irregular capitalization and extra whitespace (e.g., `" Milk "` vs `"milk"`).
   Code revealing it: `df['item_name'].unique()`
   Planned Decision: Correct (strip whitespace and standardize string casing).
3. Data Type Mismatches: Price values contain currency symbols, preventing numeric operations.
    Code revealing it: `df.dtypes`
    Planned Decision: Correct (strip symbols and cast to float).
4. Duplicate Rows: Identical transaction records repeated across overlapping dates.
    Code revealing it: `df.duplicated().sum()`
    Planned Decision: Exclude (drop exact duplicate rows).

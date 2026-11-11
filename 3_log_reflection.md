 Steps 3 & 4: Cleaning Code Court & Reflection
Cleaning Code Court (Line-by-Line Trial)
 AI Code Line / Operation | Verdict (Keep / Modify / Reject) | Evidence / Reason (Before vs. After Analysis) 
1. `df.drop_duplicates()` | Keep| Verified that exact duplicate rows inflated counts. Removing them restored the true row count without losing unique data. 
2. `df['item_name'].str.strip()` | Keep | Fixed hidden leading/trailing spaces in item descriptions, consolidating distinct item counts accurately. 
3. `df.dropna(subset=['unit_price'])` | Modify | Dropping all rows with missing prices discarded 120 valid records. Modified to impute missing prices using the category median instead.
4. `df['unit_price'].fillna(0)` | Reject | Replacing missing prices with `0` severely distorts historical mean price calculations and trend analysis. 
 5. `df['date'] = pd.to_datetime(df['date'])` | Keep | Standardized date formatting correctly, allowing chronological sorting and time-series aggregation. 

Reflection
 Comparison with AI Decisions
Our initial cleaning decisions differed from the automated AI script primarily regarding how missing prices were handled. While the AI suggested dropping rows or replacing them with zeros, our inspection showed that category-median imputation preserves essential historical observations without biasing price averages.
What Was Missed Alone?
Working independently, we initially missed subtle whitespace padding in item string labels, which only became apparent when we aggregated the data. Reviewing the AI's string-cleaning utility quickly highlighted these hidden formatting errors.

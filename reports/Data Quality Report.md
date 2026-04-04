# DATA QUALITY REPORT — Olist Dataset
# Date:03-04-2026
# Analyst: Tejali Gangane

## EXECUTIVE SUMMARY
-----------------
8 tables assessed | 100k+ records | 3 critical issues found

## TABLE-BY-TABLE FINDINGS
------------------------
### Orders Table:
  - 0.0001% of missing order approval timestamps for delivered orders → likely pipeline or system issue where the approval event was triggered but was not recorded by system in the database
   - 2.9% missing delivery timestamps → likely processing, shipped or cancelled orders
  - 0 duplicate order_ids ✅
  - Orders delivered before order date - <missing data to be added later>

### Products Table:
- 610 rows missing `category_name`, dimensions, photos → likely **incomplete product listings**
- Only 2 rows missing physical dimensions — negligible
    """Flag these products. Don't use them in category-level analysis without acknowledging the gap.
- Product weight has outliers up to 40kg 

### 🗺️ Geolocation Table

- No issues


### Order Reviews Table — Biggest Issue

review_comment_title   — 88.34% missing 🔴
review_comment_message — 58.70% missing 🔴
*Some people left ratings without providing textual reveiws.

### Order payments Table
- No issues

### Order reviews Table
- No issues

### Sellers Table
- No issues



## RECOMMENDATIONS
---------------

1. Exclude orders missing order approval timestamps from time analysis or choose a median to impute values for the comumn as it is robust for time-based analysis.
2. Exclude orders missing delivery dates from time analysis.
3. Flag products with no descriptions — do not use in text related processing tasks
3. Investigate and remove impossible delivery date records (where delivery date is earlier thean order purchase date)
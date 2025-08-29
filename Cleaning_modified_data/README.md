Customer Churn Data Cleaning Project
Overview
This project demonstrates a complete Data Cleaning and Preprocessing pipeline for a customer churn dataset containing 3,150 records and 13 features.
The dataset has been intentionally modified to include missing values, invalid entries, and inconsistent data types, specifically to demonstrate data cleaning skills.
The cleaned dataset will later be used for modeling customer churn.
--------------
--------------
Dataset Description
•	Source: https://archive.ics.uci.edu/ml/datasets/Iranian+Churn+Dataset?TB_iframe=true&width=370.8&height=658.8
•	Features:
| Column | Description | Type |
|--------|-------------|------|
| call_failure | Number of call failures | int |
| complains | Whether customer lodged a complaint (0 = No, 1 = Yes) | int |
| subscription_length | Customer subscription length in months | int |
| charge_amount | Monthly charge amount | int |
| seconds_of_use | Total seconds used in calls | int |
| frequency_of_use | Number of call sessions | int |
| frequency_of_sms | Number of SMS messages | int |
| distinct_called_numbers | Number of distinct called numbers | int |
| tariff_plan | Customer tariff plan code | int |
| status | Customer account status | int |
| age | Customer age | float |
| customer_value | Customer monetary value | float |
| churn | Whether the customer churned (Yes/No) | object |

--------------
--------------
Purpose
•	Demonstrate data cleaning and preprocessing skills on a dataset with deliberate inconsistencies.
•	Prepare the dataset for subsequent modeling tasks such as predicting customer churn.

--------------
--------------
Steps and Methodology
--------------
1. Column Standardization

•	Original column names contained spaces, inconsistent capitalization, and typos.

•	Column names were converted to snake_case for better readability and consistency.
--------------
2. Creating a Working Copy

•	A copy of the original dataset (df_clean) was created to preserve raw data.
--------------
3. Cleaning Individual Features

call_failure

•	Non-numeric values were coerced to NaN and replaced with 0.

•	Column converted to int64.

•	Final values checked with .unique() and .value_counts().

complains

•	Binary column (0 = no complaint, 1 = complaint).

•	All non-zero invalid entries were replaced with 1.

•	Missing values were replaced with 1.

subscription_length

•	Negative values converted to absolute.

•	Missing values filled with column mean.

•	Converted to int64.

charge_amount

•	Erroneous string values (e.g., 'OOO', 'o1', '2.00001') replaced with correct numeric equivalents.

•	Missing values filled with 0.

•	Converted to absolute integers (int64).

seconds_of_use

•	Erroneous value 'O3915' corrected to 3915.

•	Converted to numeric.

•	Negative values replaced with absolute values.

•	Missing values filled with median (robust to outliers).

frequency_of_use, frequency_of_sms, distinct_called_numbers

•	Negative values replaced with absolute values.

•	Missing values filled with column mean.

•	Converted to integers.

customer_value

•	Missing values filled with median to reduce influence of outliers.

•	Kept as float64.

age

•	Negative values converted to absolute.

•	Values 0 or above 120 considered invalid and replaced with median of valid ages.
--------------
4. Outlier Detection

•	Numeric columns visualized using boxplots (2 per row).

•	Number of potential outliers printed per column for further consideration.

•	Note: Outliers were identified but not removed at this stage.

•	Final Dataset Overview

•	Total records: 3,150

•	Fully cleaned numeric columns: 10

•	Columns with remaining missing values: only age initially, now cleaned

•	Binary columns: complains, tariff_plan, status, churn

All columns are now consistent, numeric types corrected, missing values handled, and extreme values identified. The dataset is ready for exploratory data 

analysis, feature engineering, or modeling.
--------------
--------------
Key Takeaways
•	Systematic, column-wise cleaning ensures data integrity and reproducibility.
•	Missing values were imputed with mean or median depending on feature type and presence of outliers.
•	Negative or erroneous values were corrected using absolute values or manual replacements.
•	Outlier detection performed to support downstream modeling decisions.
•	Code is modular, readable, and fully documented, demonstrating professional Data Cleaning workflow.



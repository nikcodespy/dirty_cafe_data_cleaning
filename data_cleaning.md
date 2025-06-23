🧹 Step 1: Handle Invalid Values

On initial inspection, I noticed two major issues:
1. The column names used spaces instead of snake_case, e.g. Transaction ID instead of transaction_id.
2. Several columns had incorrect data types (e.g., Total Spent was stored as text instead of a numeric type).

When I attempted to convert the Total Spent column to a FLOAT, I received SQL Error Code 1265, indicating that non-numeric values, such as 'ERROR' and 'UNKNOWN', were causing conversion failures.

To fix this, I replaced all invalid values ('ERROR', 'UNKNOWN', and blanks) across relevant columns with NULL using UPDATE ... WHERE IN (...). This ensured the dataset could be cleanly cast to the correct data types in the next steps.

![Image](https://github.com/user-attachments/assets/7de393fc-2a28-4263-a1d2-ab94436cc0f4)


🛠️ Step 2: Rename Columns & Fix Data Types

Once the invalid entries were replaced with NULL, I used the ALTER TABLE statement to:

Rename all columns using consistent snake_case formatting
→ e.g. Transaction ID → transaction_id, Total Spent → total_spent

Update data types to match the nature of the data:

quantity → INT

price_per_unit, total_spent → FLOAT

transaction_date → DATE

This improved query readability and ensured all numeric and date fields were correctly typed for calculations and filtering in later steps

![Image](https://github.com/user-attachments/assets/996dada7-a211-476c-b0a2-6c7737cb63eb)

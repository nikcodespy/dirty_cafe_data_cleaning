 **🧹 Step 1: Handle Invalid Values**

On initial inspection, I noticed two major issues:
1. The column names used spaces instead of snake_case, e.g. Transaction ID instead of transaction_id.
2. Several columns had incorrect data types (e.g., Total Spent was stored as text instead of a numeric type).

When I attempted to convert the Total Spent column to a FLOAT, I received SQL Error Code 1265, indicating that non-numeric values, such as 'ERROR' and 'UNKNOWN', were causing conversion failures.

To fix this, I replaced all invalid values ('ERROR', 'UNKNOWN', and blanks) across relevant columns with NULL using UPDATE ... WHERE IN (...). This ensured the dataset could be cleanly cast to the correct data types in the next steps.

![Image](https://github.com/user-attachments/assets/7de393fc-2a28-4263-a1d2-ab94436cc0f4)


**🛠️ Step 2: Rename Columns & Fix Data Types**

Once the invalid entries were replaced with NULL, I used the ALTER TABLE statement to:

Rename all columns using consistent snake_case formatting
→ e.g. Transaction ID → transaction_id, Total Spent → total_spent

Update data types to match the nature of the data:

quantity → INT

price_per_unit, total_spent → FLOAT

transaction_date → DATE

This improved query readability and ensured all numeric and date fields were correctly typed for calculations and filtering in later steps

![Image](https://github.com/user-attachments/assets/996dada7-a211-476c-b0a2-6c7737cb63eb)


**🔎 Step 3: Check for Duplicate Transactions**

To ensure there were no duplicate transactions in the dataset, I ran a query to check for any repeated transaction_id values by grouping and counting occurrences.

The query:

Groups by transaction_id

Filters using HAVING COUNT(*) > 1 to catch duplicates

✅ Result: No duplicate transaction_ids were found, so no further action was needed for deduplication.

![Image](https://github.com/user-attachments/assets/b6eff4dc-3687-4123-b221-2d5ae5de1c5e)


**🔢 Step 4: Validate Numeric Ranges**

Since manually inspecting all 9,000+ rows wasn't practical, I performed a range check on the three key numeric columns using MIN() and MAX():

quantity

price_per_unit

total_spent

This helped confirm that all values were within expected logical ranges (e.g., no negative numbers, no prices that were too high, no zero-quantity transactions).

✅ Result: All numeric values appeared valid — no further cleaning required for these fields.

![Image](https://github.com/user-attachments/assets/64ea3aaf-906c-4efd-8412-8910794fb35c) | ![Image](https://github.com/user-attachments/assets/90b8948e-b628-4ea0-a223-0df022d9ecfc)


**🧠 Step 5: Impute Missing item Values Using Price (Where Unambiguous)**



To identify which items had consistent pricing, I used SELECT DISTINCT item, price_per_unit. This allowed me to see that most items had a unique price, except Smoothie and Sandwich, which both had a unit price of 4.

Using this information, I created a CASE statement to fill in NULL values in the item column where the price_per_unit was uniquely associated with a single item. For example:

2 → Coffee

3 → Cake

1 → Cookie

5 → Salad

1.5 → Tea

Items priced at 4 were left untouched since they could not be reliably identified as either Smoothie or Sandwich.

✅ Result: All NULL items (except ambiguous cases) were successfully imputed using price logic.

![Image](https://github.com/user-attachments/assets/f28a2a7f-911d-43a7-be0a-b2cf362c2368) | ![Image](https://github.com/user-attachments/assets/d4c25d54-5006-49d2-b614-b5ab6175beba)

![Image](https://github.com/user-attachments/assets/ae9da953-a267-4397-bfd8-d29845a3c5af)



**💰 Step 6: Calculate Missing total_spent Values**

Some rows in the dataset had a missing total_spent value. Since this can be reliably derived using the formula:

total_spent = quantity * price_per_unit

…I used an UPDATE query to fill in those NULL values only when both quantity and price_per_unit were present.

✅ Result: All missing total_spent values were correctly calculated, ensuring this column is now complete and consistent.

![Image](https://github.com/user-attachments/assets/53dddfd3-2d71-49bc-b481-435cfc58269d)


**🕳️ Step 7: Leave Remaining NULLs for Unrecoverable Fields**
In the dataset, there were still some NULL values in the following columns:

location

payment_method

transaction_date

After analysis, I determined that these fields could not be reliably imputed:

Some values were evenly distributed (e.g., smoothies were purchased equally via multiple payment methods).

No strong correlation or pattern could be used to fill the gaps confidently.

There were no external reference data available for the missing transaction_date values.

❌ Rather than guessing and introducing noise, I left these values as NULL to maintain data integrity.


**📦 Step 8: Create Final Cleaned Table**


After completing all cleaning operations on the original dataset (dirty_cafe_sales), I created a new table called clean_cafe_sales using CREATE TABLE AS SELECT *.

This preserved the cleaned version separately, allowing for:

A clear audit trail between raw and cleaned data

Easy access to a reliable dataset for analysis or visualisation

Safe rollback or review of the source if needed

✅ The data is now structured, consistent, and ready for exploratory analysis or export to tools like Excel, Tableau, or Power BI.

![Image](https://github.com/user-attachments/assets/1d9ea500-930b-4708-b9bd-ca4964e19432) | ![Image](https://github.com/user-attachments/assets/eae0ac90-03e1-432f-bd05-29450db7a97e)

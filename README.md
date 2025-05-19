# Dirty Cafe Sales Data Cleaning Project

## Overview

    This project focuses on cleaning and preparing the Dirty Cafe Sales dataset. The dataset contains 10,000 rows of synthetic data representing cafe sales. 
    The dataset has missing values, inconsistent data and errors. 

    This project demonstrates how to perform practical data cleaning and data wrangling.

## Dataset Summary

    - dirty_cafe_sales.csv
    - 10,000 rows
    - 8 columns

## Column Description

    | Column Name       | Description                                                      | Example                  |
    |-------------------|------------------------------------------------------------------|--------------------------|
    | Transaction ID    | Unique transaction identifier                                    | `TXN_1234567`            |
    | Item              | Item purchased (may have missing/invalid values like "ERROR")    | `Coffee`, `Sandwich`     |
    | Quantity          | Quantity of items purchased (may have "UNKNOWN")                 | `1`, `3`, `UNKNOWN`      |
    | Price Per Unit    | Price per item (may have missing/invalid values)                 | `2.00`, `4.00`           |
    | Total Spent       | Total amount spent (should = Quantity × Price Per Unit)          | `8.00`, `12.00`          |
    | Payment Method    | Payment type (may have `None`, "UNKNOWN")                        | `Cash`, `Credit Card`    |
    | Location          | Where transaction occurred (may be missing)                      | `In-store`, `Takeaway`   |
    | Transaction Date  | Date of transaction (may be missing or incorrect)                | `2023-01-01`             |

## Tools

  - Python
  - Pandas
  - Jupyter Notebook

## Data Cleaning Steps

    - Standardised column names for consistency (lowercase, underscores).
    - Replaced invalid values such as "ERROR", "UNKNOWN" and blank strings with NaN.
    - Handled missing values:
    - Filled numeric columns (quantity, price_per_unit) with the median.
    - Filled categorical columns (item, payment_method, location) with "Unknown".
    - Filled missing transaction_date entries using the most frequent date (mode).
    - Converted data types:
        quantity remains a float for flexibility in further analysis
        price_per_unit & total_spent converted to float
        transaction_date converted to datetime
    - Recalculated total_spent using quantity × price_per_unit to ensure accuracy.
    - Created new date-related features:
        day_of_week (e.g. Monday, Tuesday)
        month (e.g. January, February)
    - Removed duplicate rows (if present).
    - Validated data integrity: all missing values have been resolved, and key calculations are consistent.

## Project Motivation
  
    The project was selected as a hands-on opportunity to practice real-world data cleaning techniques. It demonstrates how to handle messy, inconsistent & incomplete datasets.

## License

    This dataset is synthetic and publicly available for educational use under the CC BY-SA 4.0 Licence.
    

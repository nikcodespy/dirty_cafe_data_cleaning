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

  - MySQL

## Data Cleaning Steps

🧹 Step 1: Handle Invalid Values
🛠️ Step 2: Rename Columns & Fix Data Types
🔎 Step 3: Check for Duplicate Transactions
🔢 Step 4: Validate Numeric Ranges
🧠 Step 5: Impute Missing item Values Using Price (Where Unambiguous)
💰 Step 6: Calculate Missing total_spent Values
🕳️ Step 7: Leave Remaining NULLs for Unrecoverable Fields
📦 Step 8: Create Final Cleaned Table

## Project Motivation
  
    The project was selected as a hands-on opportunity to practice real-world data cleaning techniques. It demonstrates how to handle messy, inconsistent & incomplete datasets.

## License

    This dataset is synthetic and publicly available for educational use under the CC BY-SA 4.0 Licence.
    

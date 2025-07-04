# ☕ Dirty Cafe Sales — SQL Data Cleaning Project

## 📌 Overview 

    This project focuses on cleaning and preparing the Dirty Cafe Sales dataset. The dataset contains 10,000 rows of synthetic data representing cafe sales. 
    The dataset has missing values, inconsistent data and errors. 

    This project demonstrates how to perform practical data cleaning and data wrangling.

## 🗂️ Dataset Summary

    - dirty_cafe_sales.csv
    - 10,000 rows
    - 8 columns

## 📄 Column Descriptions

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

## 🛠️ Tools Used

  - MySQL
  - Excel
  - GitHub

## 🧼 Data Cleaning Steps

- 🧹 Step 1: Handle Invalid Values
- 🛠️ Step 2: Rename Columns & Fix Data Types
- 🔎 Step 3: Check for Duplicate Transactions
- 🔢 Step 4: Validate Numeric Ranges
- 🧠 Step 5: Impute Missing Item Values Using Price (Where Unambiguous)
- 💰 Step 6: Calculate Missing total_spent Values
- 🕳️ Step 7: Leave Remaining NULLs for Unrecoverable Fields
- 📦 Step 8: Create Final Cleaned Table

## 📊 Exploratory Data Analysis (EDA)
After cleaning the data, I performed exploratory analysis to identify sales patterns, item performance, and customer behaviour using **MySQL window functions, aggregates, and date functions**.
- ❓ What are the top-selling items by quantity?
- ❓ Which items generate the most revenue?
- ❓ What are the peak revenue months?
- ❓ What is the revenue trend over time (cumulative)?
- ❓ When did each item pass £2,000 in total revenue?
- ❓ What is the revenue breakdown by location?
- ❓ What are the most common payment methods?
- ❓ Which day of the week has the most sales?

## 🚀 Project Motivation
  This was selected as a **realistic cleaning challenge** to practise:
- Handling messy datasets
- Working with SQL `CASE`, `IS NULL`, data types
- Performing logic-driven imputations
- Preparing data for downstream analysis and visualisation

## 🔐 License 

   This project uses synthetic data and is licensed under **CC BY-SA 4.0** for educational use.

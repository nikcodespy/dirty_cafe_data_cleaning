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

1. Rename columns to snake_case and fix data types
2. Replace 'ERROR', 'UNKNOWN', and blank strings with NULL values
3. Fill missing price_per_unit values based on the item name (where price is unique per item)
4. Calculate missing total_spent using quantity * price_per_unit
5. Calculate the missing quantity using total_spent / price_per_unit
6. Fill missing item values where the price uniquely maps to an item (skipping ambiguous prices)
7. Remove duplicate transactions based on transaction_id
8. Create a new cleaned table called clean_cafe_sales containing all cleaned data

## Project Motivation
  
    The project was selected as a hands-on opportunity to practice real-world data cleaning techniques. It demonstrates how to handle messy, inconsistent & incomplete datasets.

## License

    This dataset is synthetic and publicly available for educational use under the CC BY-SA 4.0 Licence.
    

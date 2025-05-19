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

  - 

# Layoff Data Cleaning SQL Project

This project cleans a layoff dataset using SQL. The raw dataset contains company layoff data with duplicates, inconsistent formatting, and missing or null values. The goal is to standardize, deduplicate, and prepare the data for further analysis.


## Overview

The layoff dataset contains information about layoffs across companies, including company name, location, industry, total laid off, percentage laid off, date, stage, country, and funds raised. Cleaning this data ensures it is reliable for analytics and decision-making.

## Workflow Summary

1. **Load Data:** Import the raw data into a staging table.
2. **Remove Duplicates:** Identify and remove duplicate records using the `ROW_NUMBER()` window function.
3. **Standardize Data:** 
   - Trim whitespaces.
   - Fix inconsistent values (e.g., industry names).
   - Standardize date formats.
   - Clean country names.
4. **Manage Nulls and Blanks:** 
   - Impute missing industry values where possible.
   - Delete records with insufficient data.
5. **Finalize Table:** Drop helper columns and verify clean data.

## Key Steps

- **Deduplication**:  
  Identify duplicates based on company, location, industry, layoffs, etc., and keep only the first occurrence.
  
- **Standardization**:  
  - Trim spaces in company and country names.
  - Replace partial industry names (e.g., all starting with `Crypto` to just `Crypto`).
  - Update date fields to proper `DATE` format.

- **Null Handling**:  
  - Set blank industries to `NULL`.
  - Update missing industries by matching companies with existing industry info.
  - Remove records where both layoffs figures are missing.

- **Schema Handling**:  
  - Use staging tables for stepwise cleaning.
  - Remove helper columns (like `row_num`) after process.

## How to Use

1. **Clone this repository.**
2. **Import your raw data** into a SQL database table named `layoffs`.
3. **Run the SQL scripts:**  
   - Open and execute `DATA-CLEANING.sql` step by step on your database.
4. **Your cleaned data** will be available in `layoffs_staging2`.

> **Note:** This script is written for MySQL syntax and may require adjustments for other SQL dialects.



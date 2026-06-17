# task-01-manahilkhan
as a inturn in decodelabs this is my first task done dataset cleaning
Project 1 Data Cleaning & Preparation

DecodeLabs Industrial Training Kit | Batch 2026

Overview

This project is the foundation phase of the DecodeLabs Data Analytics track. The goal is to take a raw, messy e-commerce orders dataset and transform it into a clean, reliable, analysis-ready source of truth without using any "fancy" charts or models. Just pure data integrity work.


Objective

Clean the raw dataset by:


Identifying and handling missing values
Removing duplicate records
Correcting inconsistent data formats (dates, numbers, text)


Dataset

File: Dataset_for_Data_Analytics.xlsx
Rows: 1,200
Columns: 14 OrderID, CustomerID, Date, Product, Quantity, UnitPrice, TotalPrice, PaymentMethod, OrderStatus, ReferralSource, ShippingAddress, CouponCode, TrackingNumber

Methodology

The cleaning process follows the three phases defined by DecodeLabs:

Phase 1 Strategic Imputation

Handle the gaps. Don't just delete.

The CouponCode column had 309 missing values (25.8% of rows). Rather than deleting these rows (which would reduce statistical power), missing values were filled with "No Coupon" — a domain-logic imputation, since a blank coupon code simply means no coupon was applied to that order.

Phase 2 The Integrity Audit

One truth, one record.

Checked for duplicate rows and duplicate OrderID values to ensure no transaction was counted more than once. Result: 0 duplicate rows and 0 duplicate OrderIDs found — the dataset passed this check with no removal needed.

Phase 3 Speak One Language

Standardize formats across the dataset.


Dates converted to ISO 8601 format (YYYY-MM-DD)
Text columns (Product, PaymentMethod, OrderStatus, ReferralSource, ShippingAddress, CouponCode, etc.) had whitespace trimmed and were standardized to Title Case
Numeric columns (UnitPrice, TotalPrice) rounded to 2 decimal places to fix floating-point precision errors


Tools Used


Python 3 with Pandas for data manipulation
Chosen over Excel/Power Query for reproducibility — the cleaning logic is scripted, version-controlled, and can be re-run on updated data without repeating manual steps


Verification Gate

Before marking this project complete, the cleaned dataset was verified against DecodeLabs' required threshold:

CheckRequirementResultDuplicate OrderIDs0%✅ PassIncorrectly formatted dates0%✅ PassRemaining null values0✅ Pass

Files in This Submission

FileDescriptionDataset_for_Data_Analytics.xlsxOriginal raw dataset (unmodified, kept for reference)data_cleaning_project1.pyPython script containing all cleaning logicCleaned_Dataset.xlsxFinal cleaned output datasetChange_Log.pdfDocumented log of every change made, with description, impact, and statusREADME.mdThis file

How to Run


Place data_cleaning_project1.py in the same folder as Dataset_for_Data_Analytics.xlsx
Install dependencies if needed: pip install pandas openpyxl
Run the script: python data_cleaning_project1.py
Output: Cleaned_Dataset.xlsx is generated, and a full audit log prints to the console

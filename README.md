# Task-1
Data cleaning and feature engineering on customer personality dataset using Python and Pandas.

Project Overview:
This project focuses on performing data cleaning and feature engineering on the Customer Personality dataset using Python and Pandas.
The objective of this task is to prepare raw data for analysis by removing inconsistencies, handling missing values, and creating meaningful new features.

Objective:
To clean raw customer data
To handle missing and duplicate values
To transform data into a structured and usable format
To generate new derived features for better analysis

Data Cleaning Process:
The following data cleaning steps were performed:

1.Duplicate Removal - Duplicate records were identified and removed to avoid biased analysis.

2.Handling Missing Values - Missing values in the Income column were replaced with the median value.
Missing values in the Education column were filled with a default category.
Records with missing Marital_Status were removed.

3.Data Type Conversion - Income values were converted into numeric format.
The date column was converted into datetime format.

4.Category Standardization - Values in the Marital_Status column were standardized to reduce category variation.

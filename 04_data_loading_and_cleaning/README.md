# Data Loading & Cleaning

## Objective
This module focuses on loading the raw IBM HR Analytics dataset and performing
initial data quality checks to ensure the dataset is clean, consistent, and ready
for exploratory data analysis and modeling.

---

## Contents

| File Name | Description |
|---------|------------|
| `01_data_loading_and_initial_checks.ipynb` | Loads the raw dataset, validates structure, checks for missing values, duplicates, and data types |

---

## Key Steps Performed

1. **Dataset Loading**
   - Loaded raw CSV file using pandas
   - Implemented safe file path handling using `pathlib`

2. **Initial Validation**
   - Verified dataset shape (rows & columns)
   - Reviewed column names and schema
   - Inspected data types using `.info()`

3. **Data Quality Checks**
   - Missing value analysis
   - Duplicate record detection
   - Target variable (`Attrition`) distribution check

4. **Readiness Assessment**
   - Confirmed dataset is clean
   - Identified categorical and numerical features
   - Prepared dataset for exploratory analysis

---

## Dataset Notes

- Raw dataset is **excluded from GitHub** using `.gitignore`
- Users must place the CSV file locally at:
01_dataset/raw/IBM_HR_Analytics_Employee_Attrition_Performance.csv


---

## Output
- Clean, validated pandas DataFrame
- No modifications applied at this stage (read-only validation)

---

## Change History

| Date       | Change Description                          | Author |
|------------|----------------------------------------------|--------|
| 2026-01-06 | Initial data loading and quality checks      | Abraham PonnuRaj |

---

## Next Step
Proceed to **Exploratory Data Analysis (EDA)** to uncover patterns and insights
related to employee attrition.

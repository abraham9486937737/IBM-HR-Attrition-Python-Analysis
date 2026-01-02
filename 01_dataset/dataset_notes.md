# Dataset Documentation – IBM HR Analytics

## 1. Dataset Source
- **Name:** IBM HR Analytics Employee Attrition & Performance
- **Source:** Kaggle
- **URL:** https://www.kaggle.com/datasets/pavansubhasht/ibm-hr-analytics-attrition-dataset
- **Format:** CSV
- **Records:** 1,470
- **Features:** 35

---

## 2. Folder Structure
01_dataset/
├── raw/
│ └── IBM_HR_Analytics_Employee_Attrition_Performance.csv
└── processed/


---

## 3. Raw Dataset (`raw/`)
The `raw` folder contains the **original, untouched dataset**.

### Rules:
- ❌ Do NOT edit or modify files in this folder
- ❌ Do NOT rename the original CSV
- ✅ Use raw data only for reading and reference
- ✅ This ensures reproducibility and data integrity

---

## 4. Processed Dataset (`processed/`)
The `processed` folder will store:
- Cleaned datasets
- Transformed datasets
- Feature-engineered datasets

### Naming Convention:
hr_attrition_cleaned_v1.csv
hr_attrition_feature_engineered_v1.csv


Each processed dataset will:
- Be generated programmatically using Python
- Be documented with transformation details

---

## 5. Target Variable
- **Attrition**
  - `Yes` → Employee left the organization
  - `No` → Employee stayed

This variable will be the primary focus of analysis.

---

## 6. Data Quality Notes
- No missing values in the original dataset
- Several categorical features require encoding
- Some numeric features may need scaling
- Class imbalance exists in the Attrition variable

---

## 7. Usage Guidelines
- Always load data from `raw/` in analysis notebooks
- Save any modified dataset to `processed/`
- Maintain version control for processed datasets
- Document major transformations in analysis notebooks

---

## 8. Status
🟢 Dataset structure finalized and ready for analysis.


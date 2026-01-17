SQL vs Python Analysis – Employee Attrition

This document presents a comparative analysis of employee attrition
using SQL queries and equivalent Python (Pandas) operations.

The objective of this step is to validate analytical consistency across tools
and demonstrate strong end-to-end data analysis skills using both SQL and Python.

Dataset Context

Dataset: IBM HR Analytics – Employee Attrition & Performance

Source: Kaggle (IBM Sample Dataset)

Total Records: 1,470 employees

Target Variable: Attrition (Yes / No)

The dataset includes employee demographics, job roles, compensation,
work conditions, work-life balance, and satisfaction metrics.

Analysis Questions
Q1: Attrition by Department
Business Question

Which departments experience the highest employee attrition rates?

SQL Query

SELECT
    Department,
    COUNT(*) AS Total_Employees,
    SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) AS Attrition_Count,
    ROUND(
        SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) * 100.0 / COUNT(*),
        2
    ) AS Attrition_Rate
FROM [dbo].[IBM_HR_Analytics_Employee_Attrition]
GROUP BY Department
ORDER BY Attrition_Rate DESC;

Python (Pandas)

attrition_by_dept = (
    df.groupby("Department")
      .agg(
          Total_Employees=("Attrition", "count"),
          Attrition_Count=("Attrition", lambda x: (x == "Yes").sum())
      )
)

attrition_by_dept["Attrition_Rate"] = (
    attrition_by_dept["Attrition_Count"] /
    attrition_by_dept["Total_Employees"] * 100
).round(2)

attrition_by_dept.sort_values("Attrition_Rate", ascending=False)

Insight

Sales and Human Resources show the highest attrition rates

Research & Development has comparatively lower attrition

Indicates department-specific pressure, workload, or role expectations

Q2: Attrition by Job Role
Business Question

Which job roles contribute most to employee attrition?

SQL Query

SELECT
    JobRole,
    COUNT(*) AS Total_Employees,
    SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) AS Attrition_Count
FROM [dbo].[IBM_HR_Analytics_Employee_Attrition]
GROUP BY JobRole
ORDER BY Attrition_Count DESC;

Python (Pandas)

df.groupby("JobRole")["Attrition"] \
  .value_counts() \
  .unstack() \
  .fillna(0) \
  .sort_values(by="Yes", ascending=False)

Insight

Laboratory Technicians show the highest attrition

Sales Executive and Sales Representative roles have consistently high attrition

Managerial and research-oriented roles show greater stability

Suggests workload intensity, performance pressure, and shift patterns as key drivers

Q3: Attrition vs Overtime
Business Question

Does working overtime increase the likelihood of attrition?

SQL Query

SELECT
    OverTime,
    COUNT(*) AS Total_Employees,
    SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) AS Attrition_Count
FROM [dbo].[IBM_HR_Analytics_Employee_Attrition]
GROUP BY OverTime;

Python (Pandas)

df.groupby("OverTime")["Attrition"] \
  .value_counts() \
  .unstack() \
  .fillna(0)

Insight

Employees working overtime show significantly higher attrition

Highlights work-life imbalance as a major contributor to employee exits


Q4: Monthly Income vs Attrition
Business Question

Is compensation level associated with employee attrition?

SQL Query

SELECT
    Attrition,
    ROUND(AVG(MonthlyIncome), 2) AS Avg_Monthly_Income
FROM [dbo].[IBM_HR_Analytics_Employee_Attrition]
GROUP BY Attrition;

Python (Pandas)

df.groupby("Attrition")["MonthlyIncome"].mean().round(2)


Insight

Employees who left the organization earn significantly less on average

Compensation is a strong predictor of attrition

Summary & Cross-Tool Validation

All analytical results generated using SQL were successfully
validated using Python (Pandas).

This confirms:

Accurate data understanding

Consistent transformations

Reliable analytical logic

Readiness for predictive modeling

Consolidated Findings

Key drivers of employee attrition identified through analysis:

Department and Job Role

Overtime work

Monthly income level

Work-life balance indicators

These variables will be prioritized during feature engineering and model building.

Next Step

Proceed to Feature Engineering & Data Preparation, where the identified
attrition drivers will be transformed into model-ready features
for predictive machine learning analysis.
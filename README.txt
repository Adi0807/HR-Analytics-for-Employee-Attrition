HR Analytics - Employee Attrition Analysis
Project Overview
This project analyzes employee attrition data to uncover trends and insights about the factors influencing employee turnover. Using Python for data cleaning and visualization, and Power BI for interactive dashboards, the goal is to understand key drivers of attrition in an organization.

Dataset Information
The dataset used in this project is the IBM HR Employee Attrition Dataset. It contains various employee attributes, including demographic information, job role, work-life balance, and performance metrics.

Dataset Attributes
The dataset includes the following columns:

EmployeeID: Unique identifier for each employee.
Attrition: Target variable (Yes = employee left, No = employee stayed).
Age: Employee's age.
Department: Department in which the employee works (e.g., Sales, Research & Development, Human Resources).
JobRole: Specific job role within the department.
Gender, MaritalStatus, OverTime: Demographic information.
JobSatisfaction, WorkLifeBalance: Satisfaction scores.
MonthlyIncome, YearsAtCompany, YearsInCurrentRole: Job and salary-related features.
Python Code
Data Cleaning and Preprocessing
The data was cleaned and preprocessed using Python:

Missing Values: Verified that no missing values existed.
Binary Encoding: Converted categorical Attrition values to binary (1 = Yes, 0 = No).
One-Hot Encoding: Applied one-hot encoding to columns like Gender, JobRole, MaritalStatus, and OverTime to make them suitable for analysis.
Age Group Binning: Binned the Age column into age groups (20–30, 30–40, etc.) to simplify analysis by age range.
Data Visualization and Insights
The following insights were generated using Python visualizations:

Attrition Rate by Department: Visualized with a bar chart, indicating which departments experience the highest attrition rates.
Attrition Rate by Age Group: Displayed as a bar chart, showing age groups with the highest turnover rates, indicating possible retention challenges among younger employees.
Attrition by Job Role: Analyzed specific job roles with higher attrition, guiding focused interventions for certain roles.
Income Distribution by Attrition: A boxplot revealed that employees with lower monthly incomes tend to have higher attrition rates, suggesting income as a factor in retention.
Correlation Analysis: A heatmap highlighted correlations between attributes, such as monthly income and years at the company, and how they relate to attrition.
Python Code Sample
python
Copy code
# Importing libraries
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

# Load dataset
data = pd.read_csv('WA_Fn-UseC_-HR-Employee-Attrition.csv')

# Convert Attrition to binary
data['Attrition'] = data['Attrition'].apply(lambda x: 1 if x == 'Yes' else 0)

# One-hot encoding for categorical variables
data = pd.get_dummies(data, columns=['Gender', 'JobRole', 'MaritalStatus', 'OverTime'], drop_first=True)

# Bin Age into groups
data['AgeGroup'] = pd.cut(data['Age'], bins=[20, 30, 40, 50, 60], labels=['20-30', '30-40', '40-50', '50-60'])

# Attrition Rate by Department
attrition_by_dept = data.groupby('Department')['Attrition'].mean() * 100
plt.figure(figsize=(10, 6))
plt.bar(attrition_by_dept.index, attrition_by_dept.values, color='skyblue')
plt.title('Attrition Rate by Department')
plt.xlabel('Department')
plt.ylabel('Attrition Rate (%)')
plt.show()
Power BI Dashboard and Insights
In addition to Python, a Power BI dashboard was created to explore data interactively. Key insights derived from Power BI:

Department-Wise Attrition: Visualization on Power BI showed that the Sales and Research & Development departments had the highest attrition rates.
Attrition by Monthly Income: A detailed analysis of income showed a higher attrition rate among employees with lower monthly income, supporting the Python findings.
Impact of Work-Life Balance: Employees with lower work-life balance ratings showed higher attrition, suggesting that improving work-life balance could help reduce turnover.
Overtime and Attrition: Employees working overtime frequently had a higher likelihood of leaving, pointing to the need for workload management policies.
Conclusion
This project provides a comprehensive look at the factors contributing to employee attrition in an organization. The Python analysis highlights key trends, while the Power BI dashboard allows for dynamic exploration of these findings. Together, these insights can be used by HR to develop data-driven strategies for reducing attrition and improving employee retention

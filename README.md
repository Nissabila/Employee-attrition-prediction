## 🧩 Problem Context

XYZ Company faces a high annual employee attrition rate of **16.1%**. This has a ripple effect, negatively impacting:

- Project workflows  
- Recruitment costs (~$35,000 per new hire)  
- Training efficiency  
- Team workloads  
- Retention of key knowledge workers  

---

## ❗ Why This Analysis Matters

Employee attrition is a universal business challenge that directly affects **costs, productivity, and morale**.  
While the ideal attrition rate varies by industry, the general benchmark is **below 10%**.  
With a current gap of **6.1%** from this ideal, a timely analysis is crucial to:

- Identify root causes  
- Implement strategic, data-driven solutions  

---

## 🎯 Expected Outcomes

Our objective is to reduce the annual attrition rate from **16.1%** to **10%** within **12 months**.

To achieve this, we will:

- Build a **predictive system** to analyze and identify employees with high attrition risk  
- Enable HR and management to perform **proactive interventions** before resignation occurs  
- Enhance decision-making using **data insights** to improve retention strategies  

## 📌 Problem Scope

### 🔍 Focus Areas

- High-accuracy employee attrition prediction  
- Classification model for attrition risk  
- Metrics suitable for imbalanced data  
- 🎯 Target: 30% reduction in attrition rate  

---

## 🤖 Machine Learning Output

- A **classification model** predicting resignation likelihood  
- **Clear reports and dashboards** for HR and management  
- **Proactive intervention strategies** to prevent attrition  

---

## 🧾 Data and Assumptions

### 📂 Data Source and Scope

- **Source**: Internal company data  
- **Scope**: 4,410 employees  
- **Period**: 2015 snapshot  
- **Format**: Tabular HRIS export (`.csv`)  
- **Target Variable**: `Attrition` (Yes/No)  

---

### 🧠 Available Features

The dataset includes six main feature categories:

1. **Demographic & Personal**  
   - Age, Gender, Marital Status, Education, Education Field  
   - Distance from Home, Over18, NumCompaniesWorked  

2. **Career Tenure & History**  
   - TotalWorkingYears, YearsAtCompany, YearsSinceLastPromotion  
   - YearsWithCurrManager, TrainingTimesLastYear  

3. **Satisfaction Metrics**  
   - JobSatisfaction, EnvironmentSatisfaction, WorkLifeBalance, JobInvolvement  

4. **Job & Role Information**  
   - Department, JobRole, JobLevel, BusinessTravel  
   - EmployeeCount, EmployeeNumber, StandardHours  

5. **Compensation & Benefits**  
   - MonthlyIncome, PercentSalaryHike, PerformanceRating, StockOptionLevel  

6. **Attendance**  
   - `in_time`, `out_time`  

**Model Features Used**:  
`Age`, `Gender`, `Marital Status`, `Distance From Home`, `Department`, `Job Role`, `Education Field`, `Business Travel`, `Total Working Years`, `Years with Current Manager`, `Years at Company`, `Number of Companies Worked`, `Years Since Last Promotion`, `Training Times Last Year`, `Monthly Income`, `Percent Salary Hike`, `Average Work Hours per Day`, `Overtime Days`, `Work-Life Balance`, `Job Satisfaction`, and `Environment Satisfaction`.

---

### ⚙️ Assumptions

- Prior research indicates **IBM HR Analytics achieved 95% prediction accuracy**.  
- An **IBM India pilot reduced attrition by 2–3%**.  

This project aims to develop a **predictive model** to help XYZ Company **mitigate attrition risks through data-driven interventions**.

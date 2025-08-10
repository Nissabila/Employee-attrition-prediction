## EMPLOYEE ATTRITION PREDICTION ANALYSIS
## Background and Objectives
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

**The specific variabels used for the model will be:**  
`Age`, `Gender`, `Marital Status`, `Distance From Home`, `Department`, `Job Role`, `Education Field`, `Business Travel`, `Total Working Years`, `Years with Current Manager`, `Years at Company`, `Number of Companies Worked`, `Years Since Last Promotion`, `Training Times Last Year`, `Monthly Income`, `Percent Salary Hike`, `Average Work Hours per Day`, `Overtime Days`, `Work-Life Balance`, `Job Satisfaction`, and `Environment Satisfaction`.

---

### ⚙️ Assumptions

- Prior research indicates **IBM HR Analytics achieved 95% prediction accuracy**.  
- An **IBM India pilot reduced attrition by 2–3%**.  

This project aims to develop a **predictive model** to help XYZ Company **mitigate attrition risks through data-driven interventions**.

## Exploratory Data Analysis

### When Pay Doesn’t Explain Attrition

Employees across different income levels show similar attrition rates. In fact, those with higher salary increases are sometimes more likely to leave. The chart below illustrates how attrition rates remain steady across income brackets, even among those with significant raises.


<img width="7000" height="2000" alt="EDA1" src="https://github.com/user-attachments/assets/b88e156b-522e-44f7-8f4d-eb77f546e517" />


_Figure 1. Attrition remains consistent across income and raise levels,suggesting that pay increases alone don’t prevent turnover._

### Why is HR Leaving?

Attrition is highly concentrated in HR, with a 30.2% turnover rate- Double that of other departements and 40.7% among those with HR education. '
Even after controlling for key factors, being in HR increases attrition odds by 2.22x, poibting to potential systemic issues. The chart below illustrates the attrition distribution actoss departements and educational background.

<img width="7000" height="2000" alt="EDA2" src="https://github.com/user-attachments/assets/cc948447-6ed3-401c-bcf3-b1b93acaae2c" />

_Figure 2. HR shows significantly higher attrition rates compared to other departements, pasrticularly among those with an HR educational background._

### Root Causes Analysis 

Through comprehensive exploratory analysis across tenure, level, and department dimensions, we identified three primary drivers of employee attrition:

### 1.Excessive Workload (Overtime)

Our analysis reveals a strong correlation between overtime exposure and attrition rates. Work-life balance scores demonstrate an inverse relationship with employee retention, indicating that excessive workload directly contributes to turnover decisions. This trend is clearly reflected in the charts below.

<img width="4872" height="1321" alt="EDA3" src="https://github.com/user-attachments/assets/3b221c74-f2dd-4880-b5ee-c931b9a0abe9" />

_Figure 3. Attrition rate by overtime status and work-life balance rating._

### 2. Low Job & Environmental Satisfaction

Job satisfaction demonstrates clear predictive power for retention outcomes. Environmental satisfaction follows similar attrition patterns, suggesting that workplace conditions significantly influence employee departure decisions. The following visualizations illustrate this pattern. This is demonstrated in the charts below.

<img width="7000" height="2000" alt="EDA4" src="https://github.com/user-attachments/assets/ae2de740-60db-4f1b-ae93-9195934f0109" />

_Figure 4. Attrition rate by  job satisfaction and environment satisfaction levels._

### 3. Limited Experience Profile

Age and total working years emerge as stronger predictors of attrition than compensation factors. Younger, less experienced employees represent the highest flight risk, indicating that experience level serves as a critical retention factor.

<img width="7000" height="2000" alt="EDA5" src="https://github.com/user-attachments/assets/aa5bbba6-98f8-4b13-b81f-09bb3f5f7771" />

_Figure 5. Attrition rate by age and total working years._

### Multivariate Analysis: No Single Cause for Attrition

Below is a correlation heatmap showing the relationship between various features and employee attrition.

<img width="9600" height="6400" alt="EDA6" src="https://github.com/user-attachments/assets/2fa4ede8-f006-4c87-ac72-58a439eb8bc8" />

_Figure 6. Correlation heatmap showing weak relationships between features and attrition._

The analysis shows that no single feature strongly correlates with attrition — all correlation values are below 0.2. This indicates that employee turnover is influenced by a combination of factors rather than one dominant cause.

### Model Selection and Performance 

## Model Comparison

An initial exploration was performed on six different models to establish a performance baseline. The models were evaluated based on their F2-Score, Precision, and Recall. This metric selection prioritized minimizing false negatives, which is crucial in this domain.

| Model | F2-Score | Precision | Recall |
| --- | --- | --- | --- |
| **CatBoost** | **0.98** | **0.99** | **0.98** |
| **Extra Trees** | **0.98** | **0.99** | **0.98** |
| XGBoost | 0.98 | 0.99 | 0.97 |
| KNN | 0.98 | 0.94 | 0.99 |
| Random Forest | 0.97 | 0.99 | 0.97 |
| MLPClassifier | 0.97 | 0.99 | 0.97 |

#### Hyperparameter Tuning

The top-performing models from the initial comparison were then subjected to hyperparameter tuning to optimize their performance further. The table below shows the best configurations and the resulting F2 Mean score.

| Model | Best Parameters | F2 Mean |
| --- | --- | --- |
| **CatBoost** | `depth=8`, `iter=200`, `lr=0.2`, `l2=1` | **0.9806** |
| XGBoost | `max_depth=6`, `lr=0.2`, `n_est=300`, `subsample=0.8` | 0.9805 |
| Extra Trees | `crit=entropy`, `max_feat=log2`, `n_est=300` | 0.9797 |
| KNN | `n=11`, `p=1`, `weights=distance`, `metric=minkowski` | 0.9757 |
| Random Forest | `crit=entropy`, `max_feat=sqrt`, `n_est=300` | 0.9750 |
| MLPClassifier | `hl=(100,)`, `act=tanh`, `alpha=0.001`, `lr=const`, `solver=adam` | 0.9685 |

#### Final Model Selection: CatBoost

Based on the tuning results, CatBoost was selected as the final model due to its exceptional performance and unique advantages for this application.

Key Performance Metrics:

- F2-Score: 0.9586
- Prediction Time: 0.0057s (Enabling near real-time predictions)

Advantages of CatBoost:

- Exhibits consistent and reliable performance on diverse datasets.
- The model's low prediction latency makes it suitable for deployment in time-sensitive environments.
- It efficiently manages categorical features without the need for manual preprocessing.
- Provides individual prediction explanations, which is vital for business stakeholders to understand model decisions.
- Its built-in regularization techniques help maintain stable performance.

The final parameters used for the production model are:

```python
best_params = {
    'depth': 8,
    'iterations': 200,
    'l2_leaf_reg': 1,
    'learning_rate': 0.2,
    'verbose': False
}
```

#### Threshold Optimization

To further refine the model's output, we performed a threshold optimization analysis to maximize the F2-Score. As illustrated in the plot below, the F2-Score remains stable and high across a range of thresholds, but it reaches its optimal value at threshold = 0.73. This threshold provides the best trade-off between minimizing false negatives and avoiding false positives, which aligns with the business requirement to prioritize recall while maintaining high precision.

<p align="center"><img width="700" alt="Threshold vs F2-Score Curve showing optimal threshold at 0.73" src="https://github.com/user-attachments/assets/6142d07e-35e5-4c7d-a368-1052030a0e22" /></p>
<p align="center"><sub><i>Figure 7. Threshold Optimization Curve — F2-Score peaks at threshold = 0.73, offering the best balance between precision and recall</i></sub></p>

#### Final Model Evaluation

By applying the optimized threshold of 0.73, the model's performance was significantly enhanced, particularly in minimizing false positives.

| Metric | Before (0.5) | After (0.73) | Improvement |
| --- | --- | --- | --- |
| **Precision** | 0.97 | **1.00** | +0.03 |
| **Recall** | 0.95 | **0.95** | Maintained |
| **False Positives** | 3 | **0** | -3 |
| **False Negatives** | 5 | **5** | No change |
| **F2-Score** | 0.96 | **0.96** | Maintained |

Confusion Matrix with Optimal Threshold:

<p align="center"><img width="500" alt="Confusion Matrix after Threshold Optimization (Threshold = 0.73)" src="https://github.com/user-attachments/assets/30fd9216-cbff-40a3-a10a-98adeef53c29"/></p>

<p align="center"><sub><i>Figure 8. Confusion Matrix after applying the optimized threshold. The model achieved zero false positives while maintaining a high true positive count</i></sub></p>

- True Negatives: 555
- True Positives: 102
- False Positives: 0
- False Negatives: 5

This optimization resulted in a perfect precision score of 1.00, meaning the model generates zero false alarms. This is a critical achievement, as it ensures that any positive prediction is highly reliable, allowing stakeholders to act with complete confidence.

## Strategic Recommendations

Our analysis leads to a two-pronged approach for addressing attrition, combining broad, company-level strategies with targeted, individual interventions powered by machine learning.

#### 1. Company-Level Interventions

These are organization-wide initiatives designed to address systemic issues and a proactive approach to reduce attrition. They are based on macro-level trends observed in historical company data.

- Enhanced Onboarding & Integration: Focus on providing strong socialization resources for new employees, particularly those with 0-4 years of experience (this group has a 28.7% attrition rate). Research from PMC NCBI shows that this can significantly improve employee adjustment and retention.
- Overtime & Workload Management: Excessive overtime is the number one driver of attrition. We recommend implementing policies to distribute workloads and monitor overtime patterns. Attrition rates for employees with over 66 days of overtime are 28-30%, compared to just 12.9% for those with less.
- Mentorship & Coaching Programs: Based on our SHAP analysis, this is a key driver. Create structured mentoring programs, especially for early-career employees (`TotalWorkingYears` 0-4), as supported by research from CNBC/SurveyMonkey.
- HR Departmental Review: A Chi-square test confirmed a statistically significant attrition rate within the HR department (30.2% vs. 15% in other departments). A comprehensive review of HR practices and culture is needed to address these systemic issues.

#### 2. Individual-Level Interventions

These are targeted, confidential interventions for high-risk individuals identified by our machine learning model. SHAP analysis provides diagnostic insights into key risk drivers, allowing HR to customize their approach.

5 Intervention Areas:

1. Work-Life Balance: Implement flexible work policies for employees with low work-life balance scores.
2. Career Development: Offer targeted development and training programs, focusing on employees with long `YearsSinceLastPromotion` periods.
3. Compensation: Conduct regular compensation reviews to ensure competitive salaries.
4. Work Environment: Use stay interviews to address environment satisfaction issues.
5. Roles & Positions: Implement strategic job rotation and create clear career paths for high-risk profiles.

#### Future Work & Model Enhancement

- Integrate the model with an HRIS system to create an automated data pipeline and real-time dashboard for HR.
- Expand the dataset with more historical data and external factors (e.g., economic trends).
- Implement time-series analysis to find seasonal patterns and survival analysis to predict the "time until attrition."
- Continuously track the effectiveness of interventions with A/B testing and retrain the model with new data.
- Expand the model to predict performance degradation and develop a succession planning module.

## Installation and Usage

To run this project, you will need the following Python packages. All dependencies are listed in the `requirements.txt` file.

Dependencies:

- `streamlit`
- `pandas`
- `numpy`
- `plotly`
- `joblib`
- `catboost`
- `shap`
- `datetime`
- `XlsxWriter`
- `openpyxl`
- `xlrd`

#### Deployment and Live Application

The predictive model is already deployed as a live application on Streamlit Cloud. You can use the application directly to make predictions without any local setup.

**Live Application Link:** https://employee-attrition-prediction-wrugqt9mzx4bzz8xeng5ay.streamlit.app/

How to Use the Application:

1. Upload a CSV file that has the same format as the training data. The application will check for all required columns.
2. The application will automatically process your data using the trained CatBoost model with the optimal threshold of 0.73 to maximize detection accuracy.
3. You can view the prediction results, including probability scores, and also explore SHAP explanations for individual predictions to understand the key risk factors.
4. The results can be downloaded in an Excel format for easy reporting.

The dashboard also features interactive visualizations created with Plotly and provides real-time batch processing for your data.

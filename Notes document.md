# HR Employee Attrition Dataset — Column Notes
> IBM HR Analytics dataset. 1,470 employees. Target variable: **Attrition** (Yes/No).

---

## Target Variable

| Column | Type | Notes |
|--------|------|-------|
| **Attrition** | Categorical (Yes / No) | **This is the main outcome we're analyzing.** "Yes" = employee left the company. "No" = still employed. Only ~16% of rows are "Yes" — the dataset is imbalanced, which is typical for attrition data. |

---

## Employee Demographics

| Column | Type | Values / Range | Notes |
|--------|------|----------------|-------|
| **Age** | Numeric | ~18–60 | Employee's age in years. Useful for age-group segmentation (e.g., 18–25, 26–35, 36–45, 46+). Younger employees tend to have higher attrition. |
| **Gender** | Categorical | Male / Female | Biological sex. Useful for gender-based attrition comparison. |
| **MaritalStatus** | Categorical | Single / Married / Divorced | Personal life situation. Single employees often show higher attrition — they have fewer anchors keeping them in one place. |
| **Over18** | Categorical | Always "Y" | **Useless column. Drop it.** Every single employee is over 18. No analytical value. |

---

## Job & Role Information

| Column | Type | Values / Range | Notes |
|--------|------|----------------|-------|
| **Department** | Categorical | Sales / Research & Development / Human Resources | Which department the employee belongs to. One of the most important grouping columns. R&D is the largest department. |
| **JobRole** | Categorical | 9 roles (Sales Executive, Research Scientist, Laboratory Technician, Manufacturing Director, Healthcare Representative, Manager, Research Director, Sales Representative, Human Resources) | Specific job title/function. More granular than Department. Some roles like Sales Representative and Lab Technician tend to have higher attrition. |
| **JobLevel** | Numeric (Ordinal) | 1 to 5 | Seniority level: 1 = Entry-level, 5 = Executive/Very Senior. Lower levels = higher attrition risk — entry-level employees leave more often. |
| **EducationField** | Categorical | Life Sciences / Medical / Marketing / Technical Degree / Human Resources / Other | The field the employee studied, not necessarily related to current role. |
| **Education** | Numeric (Ordinal) | 1–5 | Education level: 1 = Below College, 2 = College, 3 = Bachelor's, 4 = Master's, 5 = Doctorate. |

---

## Compensation & Financial

| Column | Type | Values / Range | Notes |
|--------|------|----------------|-------|
| **MonthlyIncome** | Numeric | ~$1,000–$20,000 | **Primary salary metric.** Monthly salary in dollars. This is the most reliable compensation figure — use this for salary analysis. Low-income employees are much more likely to leave. |
| **DailyRate** | Numeric | ~$100–$1,500 | Daily pay rate. Not the same as MonthlyIncome ÷ 30. Could reflect a separate rate used for contracts or bonuses. Less commonly used than MonthlyIncome for analysis. |
| **HourlyRate** | Numeric | ~$30–$100 | Hourly pay rate. Again, doesn't directly correspond to MonthlyIncome. Treat as a supplementary compensation metric. |
| **MonthlyRate** | Numeric | ~$2,000–$27,000 | Another rate figure. Distinct from MonthlyIncome — could be a target rate vs. actual pay. Context is limited; use MonthlyIncome as the primary salary field. |
| **PercentSalaryHike** | Numeric | ~10%–25% | Percentage of the most recent salary increase. Linked to performance. Very low hikes can signal dissatisfaction and predict attrition. |
| **StockOptionLevel** | Numeric (Ordinal) | 0–3 | Stock options granted: 0 = None, 1 = Low, 2 = Medium, 3 = High. Employees with 0 stock options may feel less financially tied to the company. |

---

## Work Experience & Tenure

| Column | Type | Values / Range | Notes |
|--------|------|----------------|-------|
| **TotalWorkingYears** | Numeric | 0–40 | Total years of professional experience across all companies. Different from YearsAtCompany — includes experience before this employer. |
| **NumCompaniesWorked** | Numeric | 0–9 | Number of previous employers. High number = more job-hopping tendency = possibly higher attrition risk. |
| **YearsAtCompany** | Numeric | 0–40 | Years with the current company. Employees in their first 1–3 years are most likely to leave. |
| **YearsInCurrentRole** | Numeric | 0–18 | How long in the current job title/role. Low values might indicate someone who was recently moved and hasn't settled. |
| **YearsSinceLastPromotion** | Numeric | 0–15 | How long since last promotion. High values = potential frustration with career stagnation = attrition risk. |
| **YearsWithCurrManager** | Numeric | 0–17 | How long working under the current manager. If someone recently got a new manager and leaves, that's a signal. |

---

## Satisfaction & Engagement Scores

> All 4 of these use the same 1–4 scale: **1 = Low, 2 = Medium, 3 = High, 4 = Very High**

| Column | Type | Values | Notes |
|--------|------|--------|-------|
| **JobSatisfaction** | Numeric (Ordinal) | 1–4 | How satisfied the employee is with their job overall. Low scores = strong attrition predictor. |
| **EnvironmentSatisfaction** | Numeric (Ordinal) | 1–4 | Satisfaction with the physical/social work environment. Poor environment → higher likelihood of leaving. |
| **RelationshipSatisfaction** | Numeric (Ordinal) | 1–4 | Satisfaction with workplace relationships (colleagues, manager). Poor relationships → higher attrition. |
| **WorkLifeBalance** | Numeric (Ordinal) | 1–4 | 1 = Bad, 2 = Good, 3 = Better, 4 = Best. Employees with poor work-life balance leave more often, especially when combined with OverTime = Yes. |

---

## Performance & Involvement

| Column | Type | Values | Notes |
|--------|------|--------|-------|
| **PerformanceRating** | Numeric (Ordinal) | 1–4 | 1 = Low, 2 = Good, 3 = Excellent, 4 = Outstanding. In this dataset, nearly all employees are rated 3 or 4 — very low variance. Not as useful as a standalone predictor because of this. |
| **JobInvolvement** | Numeric (Ordinal) | 1–4 | 1 = Low, 2 = Medium, 3 = High, 4 = Very High. How engaged/invested the employee is in their work. Low involvement = disengaged = attrition risk. |
| **TrainingTimesLastYear** | Numeric | 0–6 | Number of training sessions the employee attended in the past year. May reflect company investment in the employee or personal development appetite. |

---

## Travel & Lifestyle

| Column | Type | Values | Notes |
|--------|------|--------|-------|
| **BusinessTravel** | Categorical | Non-Travel / Travel_Rarely / Travel_Frequently | How often the employee travels for work. Frequent travelers tend to have higher attrition — travel is disruptive to personal life. |
| **DistanceFromHome** | Numeric | 1–29 | Distance in miles/km from home to office. Employees who live far away face daily friction — this correlates with higher attrition, especially when combined with no remote work. |
| **OverTime** | Categorical | Yes / No | Whether the employee regularly works overtime. **One of the strongest attrition predictors in this dataset.** OverTime = Yes employees leave at a significantly higher rate. |

---

## Columns to Drop / Ignore

| Column | Reason |
|--------|--------|
| **EmployeeCount** | Always = 1. Zero analytical value. |
| **Over18** | Always = "Y". Zero analytical value. |
| **StandardHours** | Always = 80. Zero analytical value. |
| **EmployeeNumber** | Just a row ID/unique identifier. Not predictive. |

---

## Key Relationships to Watch (for Dashboard Design)

- **OverTime → Attrition**: The single most impactful binary predictor. Overtime employees leave at ~2× the rate.
- **MonthlyIncome → Attrition**: Clear inverse relationship — lower pay = more attrition.
- **YearsAtCompany → Attrition**: U-shaped risk — very new employees and those stagnating long-term both leave more.
- **JobRole + Department → Attrition**: Sales Representatives and Laboratory Technicians are highest-risk roles.
- **JobSatisfaction + EnvironmentSatisfaction → Attrition**: Stacking low scores predicts attrition strongly.
- **YearsSinceLastPromotion → Attrition**: Stagnation signal — people who haven't been promoted recently are more likely to leave.
- **Age + MaritalStatus → Attrition**: Young, single employees = highest risk group by demographics.
- **BusinessTravel = Travel_Frequently → Attrition**: Frequent travelers leave more than non-travelers or rare travelers.

---

## Scale Reference Card

| Score | Meaning (for satisfaction/involvement/balance columns) |
|-------|-------------------------------------------------------|
| 1 | Low / Bad |
| 2 | Medium / Good |
| 3 | High / Better |
| 4 | Very High / Best |

| JobLevel | Meaning |
|----------|---------|
| 1 | Entry-level |
| 2 | Junior |
| 3 | Mid-level |
| 4 | Senior |
| 5 | Executive |

| Education | Meaning |
|-----------|---------|
| 1 | Below College |
| 2 | College |
| 3 | Bachelor's |
| 4 | Master's |
| 5 | Doctorate |

| StockOptionLevel | Meaning |
|-----------------|---------|
| 0 | No stock options |
| 1 | Low |
| 2 | Medium |
| 3 | High |
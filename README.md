# 📊 Job Market Intelligence Dashboard

An end-to-end data project that turns raw job-posting data into actionable
insights for **job seekers** and **employers**. Python is used for data
cleaning, analysis and machine learning; Power BI is used for the interactive
dashboard.

![Python](https://img.shields.io/badge/Python-3.x-blue)
![Power BI](https://img.shields.io/badge/Power%20BI-Dashboard-yellow)
![scikit-learn](https://img.shields.io/badge/scikit--learn-ML-orange)

---

## 🎯 Project Idea

| For job seekers | For employers |
|---|---|
| Identify high-demand roles and required experience levels | Understand hiring trends and posting patterns |
| Compare salaries across locations and work types | Benchmark work types and experience-level demand |
| Discover the most in-demand skills | See which industries and companies are hiring |
| Find where opportunities are concentrated | Align job requirements with skills in demand |

## 🛠️ Tech Stack

- **Python:** pandas, numpy, matplotlib, seaborn, scikit-learn, joblib
- **Power BI Desktop:** 3-page interactive dashboard
- **Jupyter Notebook**

## 🔄 Workflow

1. **Explore & assess** – structure, missing values, duplicates, invalid salary values (negative, zero, min > max).
2. **Clean & enrich** – converted timestamps, filled missing experience level / company / description, built `is_remote`, `city`, `state_or_country`, posting date features, description length / word count and `application_rate`.
3. **Analyze & model** – EDA charts and a salary-prediction model (see below).
4. **Visualize in Power BI** – three dashboard pages.

## 🤖 Salary Prediction Model

- **Target:** `normalized_salary` (USD only, filtered to 10K–500K).
- **Features:** experience level, work type (one-hot encoded) and job skills (TF-IDF, 500 features).
- **Data:** ~35K postings with salary and skills, 80/20 train/test split.

| Model | MAE | RMSE | R² |
|---|---|---|---|
| **Linear Regression** | 25,191 | 38,014 | **0.554** |
| Random Forest (200 trees, depth 20) | 27,237 | 40,428 | 0.496 |

Linear Regression performed best and was exported (`salary_model.pkl`) together
with the dropdown options (`form_options.json`) for use in a salary-estimator form.

## 📈 Dashboard Pages

1. **Job Market Overview** – KPIs, postings per day, work type, top job titles, experience level.
2. **Salary Intelligence** – salary by experience level, location and remote flag.
3. **Skills & Industry Intelligence** – top skills, top industries, top remote-hiring companies.

PDF export: [`dashboard/final_dashboard.pdf`](dashboard/final_dashboard.pdf)

## 🔑 Key Findings

- ~**123.8K** job postings across **~24.5K** companies and **~8.5K** locations.
- **Full-time** roles make up **79.78%** of postings.
- **Mid-Senior** and **Entry-level** roles have the highest demand.
- Most posted titles: **Sales Manager (673)**, **Customer Service Representative (482)**, **Project Manager (358)**.
- **Executive** roles have the highest median salary (~$194K).
- Only about **29%** of postings include salary information.
- Remote vs. non-remote salary figures in the dashboard: **44.67K** vs **19.86K**.
- Top skills by postings: Information Technology, Sales, Management, Manufacturing, Health Care Provider.


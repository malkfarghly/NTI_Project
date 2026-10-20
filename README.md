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
On average, its predictions are off by about $25K, so it is best used as a rough
salary estimate rather than an exact figure.

## 📈 Dashboard Pages

1. **Job Market Overview** – KPIs, postings per day, work type, top job titles, experience level.
2. **Salary Intelligence** – salary by experience level, location and remote flag.
3. **Skills & Industry Intelligence** – top skills, top industries, top remote-hiring companies.


## 🔑 Key Findings

### 1. Market size
The dataset covers **~123.8K job postings** from **~24.5K companies** across
**~8.5K locations**, giving a broad view of the job market.

### 2. Work type
**Full-time** jobs dominate with **79.78%** of postings (~98.8K), followed by
**Contract** roles (~12.1K). Part-time, temporary, internship and volunteer
roles together make up a small share of the market.

### 3. Demand by experience level
**Mid-Senior** (41,489 postings) and **Entry-level** (36,708) roles lead the
market, followed by postings with no specified level (29,402). Associate,
Director, Internship and Executive roles are much less common
(9,826 / 3,746 / 1,449 / 1,222).

### 4. Most in-demand job titles
**Sales Manager** is the most posted title (673), followed by
**Customer Service Representative** (482) and **Project Manager** (358). Sales,
administrative, finance and healthcare roles (Registered Nurse, Senior
Accountant) also appear in the top 10.

### 5. Salary by experience level
Salary rises clearly with seniority. Median salaries in the dashboard are roughly:
**Executive ~$194K**, **Director ~$167K**, **Mid-Senior ~$108K**,
**Associate ~$73K**, **Entry-level ~$52K** and **Internship ~$49K**.
The jump from Entry-level to Mid-Senior is about 2x.

### 6. Salary by location
The locations with the highest **total** median salary are **New York, NY**,
**Chicago, IL**, **Austin, TX** and **Washington, DC** (after the country-wide
"United States" entry). These are sums of salaries, so they also reflect the
number of postings in each place, not only pay levels.

### 7. Remote work
In the dashboard, remote jobs show a higher salary figure (**44.67K**) than
non-remote jobs (**19.86K**). Companies hiring the most remote roles include
**J. Galt**, **Talentify.io**, **DataAnnotation** and **Swooped**.

### 8. Skills and industries
**Information Technology** is the most requested skill (~26K postings), followed
by **Sales**, **Management**, **Manufacturing** and **Health Care Provider**.
Each job lists about **2 skills** on average (35 distinct skills in total).
The industries with the most postings include **Hospitals & Health Care**,
**Financial Services**, **IT Services**, **Staffing** and **Software**.

### 9. Data quality note
Only about **29%** of postings (~36K) include salary information, so all salary
insights and the prediction model are based on this subset and may not represent
the whole market.

## 💡 Recommendations

### For job seekers
- **Target mid-senior and entry-level roles:** they account for most openings, so competition for visibility is lower than the number of applicants might suggest.
- **Build skills in Information Technology, Sales, Management and Business Development:** these appear most often in postings.
- **Plan for salary growth:** moving from Entry-level to Mid-Senior roughly doubles the median salary, so gaining experience pays off.
- **Look at remote roles:** they show higher salary figures in this dataset, but check the role and seniority behind the number first.
- **Check salary ranges before applying:** most postings do not list pay, so use the salary model or similar roles as a reference.

### For employers
- **Publish salary ranges:** only ~29% of postings do, so listing pay can help your posting stand out.
- **State the experience level:** ~24% of postings leave it unspecified, which makes it harder for candidates to find and filter the job.
- **Benchmark pay by level and location:** use the salary-by-experience and salary-by-location views to keep offers competitive.
- **Consider remote or flexible options** to widen the talent pool, especially for roles in high-demand skills.
- **Match job requirements to in-demand skills** so postings use the terms candidates actually search for.

### For future work
- Add more features to the model (job title, location, company size) and try gradient boosting to improve on R² = 0.55.
- Analyze skills per job title to show which skills matter most for each role.
- Collect a longer time range to study seasonal hiring patterns instead of a single short window.

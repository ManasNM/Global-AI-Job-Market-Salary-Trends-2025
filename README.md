# 📊 Global AI Job Market & Salary Trends 2025 – Excel Data Analysis Project

---

## 🎯 Objective

To analyze the global AI job landscape in 2025 by extracting, transforming, and visualizing insights related to salaries, skill demands, experience levels, remote policies, benefits, and hiring patterns — using Excel’s data modeling and visualization capabilities.

---

## 🧭 Purpose

This project is designed for:
- 📌 Job seekers to understand high-paying roles and skill requirements.
- 📌 Recruiters and analysts to assess hiring patterns and salary expectations.
- 📌 Data enthusiasts to explore real-world Excel data analysis techniques.

Using a cleaned dataset of 15,000+ AI job postings, this project leverages Excel formulas, PivotTables, Power Query, and dashboarding to deliver actionable insights.

---

## 📂 Repository Contents

| File Name                             | Description                                                                 |
|--------------------------------------|-----------------------------------------------------------------------------|
| `ai_job_dataset.csv`                 | Cleaned AI job market data with 15,000+ global postings                     |
| `Global AI Job Market & Salary Trends 2025.xlsx` | Excel project file containing all sheets, pivot visuals, and dashboard    |
| `AI_Job_Market_2025_Attribute_Details.pdf` | PDF document describing all attributes and formula logic used in the project |
| `README.md`                          | Complete project documentation with objectives, tools, insights, and steps |

---

## 📁 About the Dataset

**Title**: Global AI Job Market & Salary Trends 2025  
**Source**: [Kaggle – AI Job Market Dataset](https://www.kaggle.com/datasets/)  
**Size**: 15,000+ job postings  
**Scope Includes**:
- Salary (USD)
- Job Titles
- Experience & Education Level
- Remote Ratio
- Skills
- Company Size
- Location
- Benefits Score
- Posting Dates

---

## 🧱 Sheet Structure & Analysis Workflow

### 📄 Sheet: `tbl_ai_jobs`
- Pasted directly from Kaggle CSV
- Dataset is pre-cleaned and analysis-ready
- Buttons included:
  - 🔗 View Dataset on Kaggle
  - 📂 View on GitHub
  - 📝 Attribute Details
  - 📊 Dashboard Access

---

### 🧼 Sheet: `data_cleaning`
New calculated columns using Excel formulas:

| Column Name            | Description                                  | Formula (Example) |
|------------------------|----------------------------------------------|-------------------|
| `posting_year`         | Year from posting_date                       | `=YEAR(tbl_ai_jobs!O2)` |
| `posting_month`        | Month name from posting_date                 | `=TEXT(tbl_ai_jobs!O2, "mmmm")` |
| `salary_k`             | Salary in thousands                          | `=tbl_ai_jobs!C2/1000` |
| `remote_type`          | Remote, Hybrid, or On-site                   | `=IF(tbl_ai_jobs!J2=100,"Remote",IF(tbl_ai_jobs!J2=0,"On-site","Hybrid"))` |
| `experience_level_label` | Code mapping: EN→Entry, MI→Mid, etc.        | Manually mapped |
| `company_size_label`   | Code mapping: S→Small, etc.                  | Manually mapped |
| `skills_count`         | Total skills listed per job                  | `=LEN(K2)-LEN(SUBSTITUTE(K2,",",""))+1` |
| `is_remote`            | 1 if fully remote                            | `=IF(tbl_ai_jobs!J2=100,1,0)` |
| `job_title`, `salary_usd`, `job_id` | Re-included for centralized analysis | — |

> These fields were recreated to support clean pivot creation later in `doc_data_cleaning`.

---

### 🗃️ Sheet: `doc_data_cleaning`
- Merges raw and derived columns
- Master table used in **all PivotTables and charts**

---

## 🧠 Skill Demand Analysis

### Sheets: `required_skills copied frm main`, `skill_demand_raw`, `skill_demand`

To analyze skills in demand, we split comma-separated strings using **Power Query**.

---

#### Step-by-Step (Power Pivot using Power Query):

1. Copy `required_skills` to a new sheet.
2. Select column → `Data` tab → `From Table/Range`
3. In Power Query:
   - Split by delimiter (`,`) → Into Rows
   - Trim whitespace
   - Rename to `skill_name`
4. Load data to sheet as `skill_demand_raw`
5. Create Pivot Table from `skill_demand_raw` → Result stored in `skill_demand` showing total count of each skill.

---

## 📊 Insight-Based Sheets

Each sheet contains:
- Insight Objective (with relevance & impact)
- PivotTable and visual chart
- Slicers and interactivity
- “Go back to dashboard” button

| Sheet Name              | Insight Objective                                                                 |
|-------------------------|-----------------------------------------------------------------------------------|
| `top10_highest_paying_jobs` | Identify the top 10 highest paying AI roles                                  |
| `salary_by_experience_level` | Salary breakdown across experience levels                                    |
| `salary_by_work_type`     | Compare Remote vs. On-site vs. Hybrid salaries                                 |
| `salary_by_company_size`  | Salary distribution by company size                                            |
| `monthly_job_postings`    | Monthly job trend across the year                                              |
| `salary_by_experience`    | Salary variation by experience (granular)                                      |
| `remote_by_experience`    | Experience level vs. remote preference                                          |
| `salary_by_month`         | Salary trends per month                                                        |
| `jobs_by_size_experience` | Cross-analysis of job size and experience levels                                |
| `Avg_Salary_Title`        | Avg salary per job title                                                       |
| `Salary_by_Country`       | Salary trend by geographic location                                            |
| `Remote_Countries`        | Countries most active in remote hiring (filtered)                              |
| `Benefits_Analysis`       | Avg benefits score across job title/company size                               |

---

## 📊 Dashboard: `AI_Job_Insights_Dashboard`

A visually consolidated dashboard that includes:
- 6 charts arranged in 3x2 layout
- Navigation buttons to insights
- Consistent fonts, shadows, and headers
- Interactive slicers
- Minimal gridlines for cleaner UI

---

## 🧮 Summary of Key Calculations

| Column Name            | Formula/Logic                                        |
|------------------------|------------------------------------------------------|
| `posting_year`         | Extract year from `posting_date`                    |
| `salary_k`             | Divide salary by 1,000                              |
| `remote_type`          | If 100 = Remote, 0 = On-site, else Hybrid           |
| `skills_count`         | Count commas + 1 in `required_skills`               |
| `is_remote`            | Flag 1 for fully remote (remote_ratio = 100)        |
| `experience_level_label` | Manual code-to-text conversion                   |
| `company_size_label`   | Manual code-to-text conversion                      |

---

## 🛠 Tools & Features Used

- Microsoft Excel 365
- PivotTables & Charts
- Power Query (Data > Get & Transform)
- Hyperlinks & Form Controls
- Slicers, Conditional Formatting
- Chart Types: Clustered, Stacked, Bar, Line

---

## ✅ Enhancements Implemented

- Interactive buttons for navigation
- Chart alignment and design consistency
- Dashboard sheet with 1-click overview
- Axis labels, titles, and text boxes styled
- External link to Kaggle dataset embedded in Sheet 1

---

## 📍 Conclusion

This Excel project delivers a full-scale business intelligence solution for the AI job market — from raw CSV to a final, interactive dashboard. Ideal for data-driven decision-making by job seekers, analysts, and recruiters.

---

## 🔗 Links

- 📂 [View Dataset on Kaggle](https://www.kaggle.com/datasets/)
- 💻 [GitHub Repository](https://github.com/your-username/ai-job-market-2025)

---

## 🙋‍♂️ Author

**Manas Nayan Mukherjee**  
 Aspiring Data Analyst
 Excel & BI Enthusiast  
---

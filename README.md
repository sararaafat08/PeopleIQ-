# 👥 PeopleIQ — HR Analytics & Workforce Intelligence Dashboard

> A comprehensive HR analytics project built on 3,150 employee records — uncovering workforce trends across departments, training effectiveness, employee turnover, satisfaction, and performance through an interactive Power BI dashboard.

---

## 📌 Project Overview

This project analyzes a real-world **HR dataset of 3,150 employees** across 6 departments and 25 divisions, delivering actionable insights into:

- 🏢 **Workforce composition** — headcount, status, and departmental structure
- 🎓 **Training effectiveness** — program outcomes, cost, duration, and performance impact
- 📉 **Employee turnover** — termination types, at-risk roles, and department-level churn

---

## 🗂️ Project Structure

```
├── HR_Dataset.csv           # Raw HR dataset (3,150 employees × 39 columns)
├── Day_DashBoard.pbix       # Power BI dashboard (3 pages)
└── README.md
```

---

## 📊 Dataset — `HR_Dataset.csv`

**3,150 rows × 39 columns** | No critical missing values (Exit Date blank for active employees)

### 👤 Employee Information
| Column | Description | Values / Range |
|---|---|---|
| `FirstName`, `LastName` | Employee name | — |
| `Title` | Job title | Production Technician, Network Engineer, Data Architect, etc. |
| `DepartmentType` | Department | Production, Sales, IT/IS, Software Engineering, Admin, Executive |
| `Division` | Sub-division (25 total) | Finance, Aerial, Field Operations, Engineers, Sales & Marketing, etc. |
| `EmployeeStatus` | Current status | Active, Future Start, Voluntarily Terminated, Leave of Absence, Terminated for Cause |
| `EmployeeType` | Employment type | — |
| `PayZone` | Salary band | Zone A, Zone B, Zone C |
| `GenderCode` | Gender | Male, Female |
| `RaceDesc` | Ethnicity | — |
| `MaritalDesc` | Marital status | — |
| `State`, `LocationCode` | Work location | — |
| `StartDate`, `ExitDate` | Employment period | — |

### 📈 Performance & Engagement
| Column | Description | Range |
|---|---|---|
| `Performance Score` | Manager rating | Exceeds / Fully Meets / Needs Improvement / PIP |
| `Current Employee Rating` | Current rating score | — |
| `Engagement Score` | Employee engagement | 1 – 5 |
| `Satisfaction Score` | Job satisfaction | 1 – 5 |
| `Work-Life Balance Score` | WLB rating | 1 – 5 |

### 🎓 Training
| Column | Description | Range |
|---|---|---|
| `Training Program Name` | Program | Leadership Development, Customer Service, Technical Skills, Project Management, Communication Skills |
| `Training Type` | Delivery method | Internal, External |
| `Training Outcome` | Result | Passed, Completed, Incomplete, Failed |
| `Training Duration(Days)` | Length | 1 – 5 days |
| `Training Cost` | Cost per session | $100 – $1,000 |

### 🚪 Termination
| Column | Description | Values |
|---|---|---|
| `TerminationType` | How they left | Voluntary, Involuntary, Resignation, Retirement |

---

## 📈 Dashboard — `Day_DashBoard.pbix` (3 Pages)

### Page 1 — 👥 Employees
Workforce overview across departments and divisions.

| Visual | What it shows |
|---|---|
| Bar Chart | **Total Employees** by Department |
| Pie Chart | Employee breakdown by **Status** (Active / Terminated / Leave) |
| Line Chart | Workforce trend over time |
| Bar Chart | **Avg Performance After Training** by Department |
| Bar Chart | **Avg Performance After Training** by Job Title |
| Slicer | Filter by **Division** and **Department** |

### Page 2 — 🎓 Training
Training program effectiveness and performance impact.

| Visual | What it shows |
|---|---|
| Donut Chart | Distribution of **Training Outcomes** (Passed / Failed / Incomplete) |
| Bar Chart | Count of each **Training Outcome** |
| Column Chart | **Avg Performance After Training** by Training Type (Internal vs External) |
| Bar Chart | **Avg Performance** by **Training Program Name** |
| Scatter Chart | **Performance vs Training Duration** per program |
| Slicers | Filter by **Training Type** and **Training Program Name** |

### Page 3 — 📉 Turnover
Churn analysis by department, title, and termination type.

| Visual | What it shows |
|---|---|
| Column Chart | **Turnover %** by Department |
| Bar Chart | **Turnover %** by Job Title |
| Pie Chart | Breakdown by **Termination Type** (Voluntary / Involuntary / Resignation / Retirement) |
| Slicer | Filter by **Job Function** |

---

## 💡 Key Business Questions Answered

- Which departments have the highest employee turnover?
- Does training duration affect post-training performance?
- Which training programs deliver the best performance outcomes?
- Are internal or external training programs more effective?
- What is the ratio of active vs terminated employees per department?
- Which job titles have the highest resignation or involuntary termination rates?
- How do engagement, satisfaction, and work-life balance scores vary across divisions?

---

## 🚀 How to Use

### View the Dashboard
1. Download `Day_DashBoard.pbix`
2. Open with [Power BI Desktop](https://powerbi.microsoft.com/desktop/) (free)
3. Navigate pages: **Employees → Training → Turnover**
4. Use slicers to filter by Department, Division, Training Type, or Job Function

### Explore the Raw Data
```python
import pandas as pd

df = pd.read_csv('HR_Dataset.csv')

# Active vs terminated
print(df['EmployeeStatus'].value_counts())

# Avg satisfaction by department
print(df.groupby('DepartmentType')['Satisfaction Score'].mean().sort_values(ascending=False))

# Training outcome distribution
print(df['Training Outcome'].value_counts())

# Turnover rate by department
turnover = df[df['EmployeeStatus'].str.contains('Terminated', na=False)]
print(turnover.groupby('DepartmentType').size())
```

---

## 🛠️ Tech Stack

| Tool | Purpose |
|---|---|
| Power BI Desktop | 3-page interactive HR dashboard |
| CSV (HR Dataset) | Source data — 3,150 employee records |
| Python / Pandas | Optional further analysis |

---

## 📄 License

Free to use for learning and portfolio purposes. Attribution appreciated.

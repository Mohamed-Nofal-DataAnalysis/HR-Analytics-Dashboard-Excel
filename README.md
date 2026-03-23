# 👥 HR Analytics Dashboard — Excel

<p align="center">
  <img src="https://img.shields.io/badge/Tool-Microsoft%20Excel-217346?style=for-the-badge&logo=microsoft-excel&logoColor=white"/>
  <img src="https://img.shields.io/badge/Domain-Human%20Resources-4B8B3B?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/Status-Completed-brightgreen?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/Dashboards-2-orange?style=for-the-badge"/>
</p>

---

## 📌 Project Overview

An interactive **HR Analytics Dashboard** built entirely in **Microsoft Excel**, designed to give HR managers and business leaders a comprehensive view of workforce performance, salary distribution, departmental structure, and employee demographics — across **5 countries** and **20 departments**.

The project contains **two interactive dashboards**:
- 🏢 **Departments Dashboard** — focuses on department-level KPIs and salary metrics
- 👤 **Employees Dashboard** — focuses on individual employee analytics, geography, and demographics

---

## 📊 Dashboards Preview

### 🏢 Departments Dashboard
| KPI | Value |
|-----|-------|
| Total Annual Salary | $17,099,892 |
| Total Monthly Salary | $1,424,991 |
| Total Employees | 689 |
| AVG Years of Experience | 6.5 |
| Number of Departments | 20 |
| AVG Monthly Salary | $2,068.20 |

**Charts Included:**
- 📈 Total Employees By Year (Line Chart — 2016 to 2020)
- 📊 AVG Overtime Hours By Department (Horizontal Bar Chart)
- 📉 Total Annual Salary & AVG Hourly Rate By Department (Combo Chart)
- 📊 Total Monthly Salary & Total Employees By Department (Combo Chart)

---

### 👤 Employees Dashboard
| KPI | Value |
|-----|-------|
| AVG Annual Salary | $24,818.42 |
| AVG Hourly Rate | $11.75 |
| AVG Job Rate | $3.59 |
| AVG Total Leaves | 2 |
| AVG Overtime Hours | 14 |
| Number of Countries | 5 |

**Charts Included:**
- 🍩 Total Annual Salary by Center (Donut Chart)
- 🗺️ Total Annual Salary by Country (Map Chart — Bing Maps)
- 📋 TOP 10 Employees by Total Annual Salary (PivotTable)
- 🍩 Total Employees by Gender (Donut Chart — 65% Male / 35% Female)
- 📊 Total Employees By Rate (Bar Chart)

---

## 🌍 Data Scope

| Dimension | Details |
|-----------|---------|
| **Countries** | Egypt, Lebanon, Saudi Arabia, Syria, UAE |
| **Centers** | East, Main, North, South, West |
| **Gender** | Male, Female |
| **Departments** | 20 departments (Manufacturing, IT, HR, Sales, Training, etc.) |
| **Time Period** | 2016 – 2020 |

---

## 🧹 Data Cleaning

Before building the dashboards, the raw HR data went through a thorough cleaning process:

### Steps Applied:
1. **Removed Duplicates** — Eliminated duplicate employee records using Excel's built-in *Remove Duplicates* feature
2. **Handled Missing Values** — Identified and filled or removed blank cells in critical columns (Salary, Department, Country)
3. **Standardized Text Fields** — Normalized inconsistent text entries (e.g., department names, country spellings) using `TRIM()`, `PROPER()`, and `SUBSTITUTE()`
4. **Fixed Data Types** — Converted salary columns stored as text to numeric format; ensured date columns were in proper date format
5. **Validated Salary Logic** — Cross-checked that `Monthly Salary × 12 ≈ Annual Salary` to detect formula errors
6. **Outlier Detection** — Identified unusually high/low salary values and verified them against source data
7. **Renamed & Restructured Columns** — Renamed columns to be consistent and descriptive for PivotTable compatibility
8. **Created Helper Columns** — Added calculated columns such as `Years of Experience Bucket`, `Salary Band`, and `Rate Category` to support slicers and charts

---

## ⚙️ Excel Features & Techniques Used

### 🔄 PivotTables & PivotCharts
- All charts are powered by **PivotTables** for dynamic, real-time filtering
- PivotCharts connected to slicers for interactive cross-dashboard filtering

### 🎛️ Slicers & Filters
- **Country Slicer** — Filter by: Egypt, Lebanon, Saudi Arabia, Syria, UAE
- **Center Slicer** — Filter by: East, Main, North, South, West
- **Gender Slicer** — Filter by: Male, Female
- All slicers are **linked across both dashboards** for synchronized filtering

### 📐 DAX-Style Excel Formulas
Although this project uses Excel (not Power BI), advanced formulas were used to replicate DAX-style calculations:

```excel
// Total Annual Salary
=SUMIF(Department_Table[Dept], [@Department], Employee_Table[Annual_Salary])

// AVG Overtime Hours by Department
=AVERAGEIF(Data[Department], A2, Data[Overtime_Hours])

// TOP 10 Employees by Salary (used in PivotTable with Value Filter)
=LARGE(Salary_Range, ROW()-ROW($A$1)+1)

// AVG Years of Experience
=AVERAGEIFS(Data[Years_Exp], Data[Country], Slicer_Country, Data[Gender], Slicer_Gender)

// Monthly Salary Calculation
=Annual_Salary / 12

// Salary Banding (Helper Column)
=IFS([@Annual_Salary]<15000,"Band 1", [@Annual_Salary]<25000,"Band 2", [@Annual_Salary]<40000,"Band 3", TRUE,"Band 4")
```

### 🗺️ Map Chart
- Used Excel's **Bing Maps integration** to display `Total Annual Salary by Country` geographically
- Requires Microsoft 365 or Excel 2019+

### 🎨 Design & UX
- Custom color theme: **Forest Green (#4B8B3B)** + **Warm Beige** background for professional HR branding
- HR company logo integrated in the header
- Rounded card-style KPI boxes with borders
- Consistent font hierarchy and spacing across both dashboards

---

## Dashboard Screenshots (Click to enlarge) :
<img src="https://github.com/Mohamed-Nofal-DataAnalysis/HR-Analytics-Dashboard-Excel/blob/main/Departments.png">
<img src="https://github.com/Mohamed-Nofal-DataAnalysis/HR-Analytics-Dashboard-Excel/blob/main/Employies.png">

---

## 📁 File Structure

```
HR-Analytics-Dashboard-Excel/
│
├── 📊 HR_Dashboard.xlsx          # Main Excel file with both dashboards
├── 📄 README.md                  # Project documentation
└── 📸 screenshots/
    ├── departments_dashboard.png  # Departments Dashboard preview
    └── employees_dashboard.png   # Employees Dashboard preview
```

---

## 🚀 How to Use

1. **Download** `HR_Dashboard.xlsx`
2. **Open** in Microsoft Excel 2019 or Microsoft 365
3. Use the **Slicers** (Country / Center / Gender) to filter data interactively
4. Both dashboards update **simultaneously** when slicers are applied
5. To reset filters — click the **Clear Filter** icon (≡ + funnel icon) on any slicer

> ⚠️ **Note:** The Map Chart requires an active internet connection and Microsoft 365 to render properly.

---

## 🛠️ Tools & Technologies

| Tool | Usage |
|------|-------|
| Microsoft Excel 365 | Dashboard development, PivotTables, Charts |
| Excel PivotTables | Data aggregation and dynamic calculations |
| Excel Slicers | Interactive cross-filtering |
| Bing Maps (Excel) | Geographic salary visualization |
| Excel Formulas | Data cleaning, helper columns, KPI calculations |
| Excel PivotCharts | All visualizations (Line, Bar, Donut, Combo, Map) |

---

## 🔎 Project Insights

After analyzing the HR data across all dashboards, several key findings emerged:

### 💰 Salary Insights
- The **Manufacturing** department leads with the highest total annual salary and the largest headcount, reflecting its operational scale
- Despite high headcount, **AVG Monthly Salary ($2,068)** remains moderate — suggesting the workforce is largely mid-level with few senior outliers
- **Ahmad** tops the individual salary chart with **$870,264** in total annual salary, significantly ahead of the second-highest earner — worth investigating for role justification
- The **Main Center** accounts for **36%** of total annual salary spend, making it the most financially significant center

### 📈 Workforce Trends
- Employee count **peaked in 2019** then saw a noticeable drop in 2020 — likely tied to COVID-19 impacts or a planned restructuring initiative
- The organization maintained a relatively **stable workforce between 2016–2018**, followed by aggressive hiring in 2018–2019
- With only **6.5 average years of experience**, the workforce skews relatively junior — presenting opportunities for upskilling and retention programs

### ⏱️ Overtime Analysis
- **Major Mfg Projects** department records the highest AVG overtime hours (**39 hours**) — nearly **13× more** than Environmental Health/Safety (**3 hours**)
- High overtime in Manufacturing-adjacent departments (Major Mfg Projects, Training, Quality Control) signals potential **understaffing or peak-load inefficiencies**
- Departments with low overtime (Environmental Health/Safety, Product Development) appear well-staffed relative to their workload

### 🌍 Geographic Distribution
- **Saudi Arabia** dominates salary expenditure on the map, likely hosting the highest-paid workforce segment
- The **North Center (30%)** and **Main Center (36%)** together account for **66% of total salary** — concentration risk worth monitoring
- The **East Center** has the smallest footprint at only **8%** of total salary spend

### 👥 Demographics
- The gender split is **65% Male / 35% Female** — while male-dominated, a 35% female representation is noteworthy in a manufacturing-heavy environment
- **Rate distribution** shows the majority of employees fall in **Rate 3 (208 employees)** and **Rate 5 (215 employees)**, with a gap at mid-range rates (Rate 4.5: 124) — suggesting a bimodal compensation structure
- AVG Total Leaves of **2 days** is notably low, which may reflect strong engagement — or under-reporting that warrants HR review

---

## ⭐ Final Conclusion

This **HR Analytics Dashboard** demonstrates how Microsoft Excel, when used to its full potential, can serve as a powerful business intelligence tool — no specialized BI software required.

### What This Project Achieves:
- ✅ Transforms raw, messy HR data into **clean, structured, decision-ready insights**
- ✅ Provides HR managers with a **360° view** of workforce, salary, and performance across departments, centers, countries, and gender
- ✅ Enables **real-time interactive filtering** through synchronized slicers — making it easy for non-technical stakeholders to explore the data themselves
- ✅ Highlights **actionable patterns**: overtime hotspots, salary concentration, workforce growth and decline, and gender distribution

### Key Takeaways for Business:
> 📌 The Manufacturing cluster is the organization's **core cost and productivity engine** — and should be monitored closely for overtime burnout and salary equity.

> 📌 The **2019–2020 employee drop** warrants a retrospective review to understand attrition drivers and prevent recurrence.

> 📌 The **bimodal rate distribution** suggests two distinct employee tiers — a structure that should be intentional and well-communicated in HR policy.

> 📌 Geographic salary concentration in **Saudi Arabia and Main/North Centers** highlights where compensation strategy decisions will have the most impact.

### Skills Demonstrated:
| Skill | Application |
|-------|-------------|
| Data Cleaning | Deduplication, type fixing, outlier handling, standardization |
| Data Modeling | Structured tables, helper columns, salary banding |
| Excel Formulas | SUMIF, AVERAGEIFS, LARGE, IFS — advanced aggregation logic |
| Data Visualization | 8+ chart types across 2 dashboards |
| Dashboard Design | Professional UX with slicers, KPI cards, consistent branding |
| Business Analysis | Insight extraction, pattern recognition, HR domain knowledge |

---

> 💡 *"Good data analysis doesn't just show what happened — it tells you what to do next."*
> This dashboard was built with that philosophy in mind.

---

## 👨‍💼 Author
Mohamed Nofal
Data & Business Analyst  
Transforming raw data into actionable business insights.
> Built with ❤️ using Microsoft Excel
> Feel free to ⭐ the repo if you found it useful!

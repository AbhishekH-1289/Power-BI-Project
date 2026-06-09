# Power-BI-Project
An interactive, high-density Power BI healthcare dashboard mapping cardiovascular and chronic disease risk factors by synthesizing complex demographic and clinical datasets. Features advanced DAX modeling, cohort analysis, and multi-dimensional cross-tabulations.

# Clinical Risk Analytics & Patient Cohort Dashboard

## 📊 Project Overview
This repository contains a production-grade **Power BI Enterprise Dashboard** designed to analyze clinical patient distributions and evaluate chronic health risks (such as cardiovascular disease and hypertension). 

Utilizing a comprehensive health dataset containing both high-cardinality categorical attributes and complex continuous clinical vitals, this dashboard delivers granular patient insights to enable data-driven clinical decisions, map chronic disease clusters, and track key risk metrics.


## 💡 Key Business & Clinical Insights Delivered
* **Demographic Escalation:** Identifies exactly how heart disease risk and elevated cholesterol scale against aging cohorts, showing massive data skew in senior demographics (`Senior (55+)`).
* **Cross-Tab Risk Matrix:** Intersects lifestyle habits (`Smoker Status`) directly against physiological baselines (`Blood Pressure`, `BMI`, `Glucose`) to isolate multi-morbid risk patient cohorts.
* **Hypertension Distribution:** Maps out operational patient strain across varying tiers of hypertensive categories to assist clinical facilities with predictive resource scheduling.



## 🛠️ Dashboard Architecture & Layout
The project is built around a unified, high-density dashboard tracking multiple analytical facets:

1. **Executive Metric Banner (KPI Cards):** Instant, high-level tracking of core patient volumes, average glucose levels ($mg/dL$), metabolic baselines (Average BMI), and overall heart disease prevalence rates.
2. **Multi-Metric Risk Matrix:** A deep-dive cross-tabulation table breaking down dynamic clinical metrics simultaneously across `Gender`, `Smoking Status`, and `Blood Pressure`.
3. **Clinical Health Profiler (Treemap):** A multi-dimensional layout organizing absolute patient volume counts nested inside `Blood Pressure Tiers` and further segmented by `Gender`.
4. **Lifestyle Threat Radar (Donut & Funnel Charts):** Isolates high-risk populations across smoking profiles and blood pressure funnels to immediately determine patient prioritization.
5. **Dual-Axis Demographic Trend Chart:** Displays total patient counts by age bracket while simultaneously trending `Avg Cholesterol` lines across a secondary Y-axis to track metabolic anomalies across younger cohorts.



## 🧪 Data Schema & Features
The dashboard processes data for **300 unique anonymized patients** across the following schema:

| Column Name | Data Type | Description / Analytics Significance |
| :--- | :--- | :--- |
| `Patient_ID` | Text (Unique Key) | Primary key for calculating unique footprints (`Total Patients`). |
| `Age` / `Age_Group` | Numeric / Categorical | Continuous age converted via custom Power Query logic into distinct tiers. |
| `Gender` | Categorical | Demographic feature for population segmentation. |
| `Cholesterol_mg_dL` | Numeric (Continuous) | Serum cholesterol measurement tracking lipid cardiovascular risk. |
| `Blood_Pressure` | Categorical (Ordinal) | Segmented into Normal, Elevated, Hypertension Stage 1, and Stage 2. |
| `BMI` | Decimal (Continuous) | Body Mass Index assessing weight-to-height clinical tracking. |
| `Glucose_mg_dL` | Numeric (Continuous) | Fasting blood glucose tracking metabolic and diabetic profiles. |
| `Smoker_Status` | Categorical | Behavioral lifestyle index tracking risk multipliers (Never, Former, Current). |
| `Heart_Disease_Risk` | Categorical (Binary) | Primary objective classification feature (**Yes / No**). |


## 🧮 Data Engineering & Custom DAX Measures
Rather than relying on implicit data models, this project utilizes explicit, highly optimized **Data Analysis Expressions (DAX)** managed inside a dedicated measures table container (`_Measures`):

### Total Patient Count

```DAX
Total Patients = COUNTROWS('Sheet1')

```


### High Risk Isolation

```DAX
High Risk Patients = 
CALCULATE(
    [Total Patients], 
    'Sheet1'[Heart_Disease_Risk] = "Yes"
)

```

### Heart Disease Prevalence Rate

```DAX
Heart Disease Rate = 
DIVIDE(
    [High Risk Patients], 
    [Total Patients], 
    0
)

```

### Continuous Metric Averages

```DAX
Avg BMI = AVERAGE('Sheet1'[BMI])
Avg Glucose = AVERAGE('Sheet1'[Glucose_mg_dL])
Avg Cholesterol = AVERAGE('Sheet1'[Cholesterol_mg_dL])

```



## ⚡ Technical Implementations & UI/UX Optimizations

* **Power Query ETL Pipeline:** Engineered custom conditional extraction layers to split raw numerical continuous ages into logical categorical health buckets (`Young Adult`, `Middle Aged`, `Senior`).
* **Visual Color Discipline:** Applied a crisp, corporate UI theme layout leveraging high-contrast color markers (**Coral Red** reserved strictly for risk alerts and **Muted Cobalt Blue** for standard population baselines) to ensure maximum scannability.
* **Dynamic Cross-Filtering:** Configured mutual cross-filtering parameters across all elements—clicking any specific lifestyle indicator (e.g., *Current Smoker*) completely recalibrates the entire dashboard's visual matrix instantly.



## 🚀 How to Run the Project

1. Clone this repository to your local directory.
2. Ensure you have the latest version of [Power BI Desktop](https://powerbi.microsoft.com/) installed.
3. Open the `.pbix` file included in the repository root directory.
4. The dataset is completely self-contained and pre-loaded into the data model—no external database configurations or API keys are required.

```

### 📌 Next Steps for You:
1. Create a new public repository on GitHub called `clinical-risk-analytics-powerbi`.
2. Copy and paste the text above into a file named `README.md` in that repository.
3. Save your Power BI project by going to **File > Save As** and naming it `Medical_Dashboard.pbix`. 
4. Upload that `.pbix` file directly into your GitHub repository along with your project screenshot (`image_4554dd.png`) to give users a visual preview of your dashboard.

```

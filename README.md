# Healthcare Patient Flow Analytics
## Optimizing Patient Flow While Maintaining Quality Care

**A Data Analytics Case Study | 2023–2024**

**Prepared by:** Brightdata Consult  
**Website:** brightdataconsult.com  
**Project Category:** Healthcare Analytics | Business Intelligence | Operational Performance Analysis  
**Tools:** Microsoft Excel, Power Query, Power Pivot, DAX and Excel Dashboards

---

# 1. Executive Summary

Healthcare institutions operate in increasingly demanding environments where efficient patient flow, timely service delivery and quality patient care must be balanced.

Understanding patient admission patterns, waiting times, departmental referrals and patient satisfaction can help healthcare administrators identify operational patterns and areas requiring further investigation.

This project analyses a healthcare patient-flow dataset containing 9,216 patient encounter records. The analysis examines patient demographics, admission patterns, waiting-time categories, departmental referrals, admission periods and recorded patient satisfaction scores.

Microsoft Excel was used throughout the analytical process, including data cleaning and transformation with Power Query, data modelling and calculations with Power Pivot and DAX, and interactive dashboard development.

The analysis identified the following headline results:

| Key Performance Indicator | Result |
|---|---:|
| Total Patient Encounters | 9,216 |
| Total Admissions | 4,612 |
| Overall Admission Rate | 50.04% |
| Average Waiting Time | 35.26 |
| Average Patient Satisfaction Score | 4.99/10 |
| Patient Satisfaction Data Coverage | 27.31% |

The analysis revealed several noteworthy patterns:

- Seniors represented the largest age-group category, accounting for 25.03% of patient encounters.
- Children recorded the highest admission rate among the age groups at 51.45%.
- The admission rate generally declined across the defined waiting-time categories, from 51.76% for patients in the Short category to 48.95% for those in the Excessive category.
- The Afternoon period recorded the highest admission rate at 51.03%.
- Renal referrals recorded the highest departmental admission rate at 53.49%, although the category contained only 86 patients.
- Only 27.31% of patient encounters had recorded satisfaction scores, highlighting an important limitation in the interpretation of patient experience findings.

The findings provide an analytical foundation for understanding patient-flow patterns and identifying areas for further operational investigation. They should not be interpreted as proof of causation or as a substitute for detailed clinical and operational assessments.

# 2. Background and Business Context

Modern healthcare facilities face considerable pressure to optimize patient flow while maintaining quality care.

Effective patient-flow management involves balancing several operational considerations, including:

- Patient admission decisions.
- Departmental capacity and referral patterns.
- Patient waiting times.
- Staffing and scheduling arrangements.
- Patient experience and satisfaction.
- Efficient utilization of available healthcare resources.

Delays in patient processing, variations in admission patterns and gaps in patient experience monitoring can affect operational efficiency and service delivery.

Data analytics provides an opportunity to examine these operational patterns systematically, identify potential areas of concern and support evidence-based management decisions.

This project applies practical data analytics techniques to a healthcare patient-flow dataset to explore these issues.

# 3. Objectives of the Analysis

The primary objective was to analyse patient-flow patterns to support improved operational understanding and decision-making.

The specific objectives were to:

1. Examine patient demographics and their distribution across age groups, gender and race.
2. Determine overall patient admission volumes and admission rates.
3. Examine admission patterns across the available reporting years.
4. Analyse patient referrals across specialist departments.
5. Investigate the relationship between waiting-time categories and admission rates.
6. Examine patient admission patterns across different periods of the day.
7. Assess recorded patient satisfaction scores and their distribution.
8. Develop an interactive dashboard to communicate the findings.
9. Identify operational areas that may benefit from further investigation.

# 4. Project Work Flow 
```
RAW HEALTHCARE DATA
        |
        v
DATA PROFILING & QUALITY ASSESSMENT
        |
        v
DATA CLEANING
        |
        v
POWER QUERY TRANSFORMATIONS
        |
        v
POWER PIVOT DATA MODELLING
        |
        v
DAX MEASURES & CALCULATIONS
        |
        v
PIVOTTABLES & PIVOTCHARTS
        |
        v
INTERACTIVE DASHBOARD
        |
        v
INSIGHTS & RECOMMENDATIONS
```

# 5. Dataset Description

The dataset contains 9,216 patient encounter records and includes variables relating to patient demographics, admission information, waiting times, departmental referrals and satisfaction scores.

The principal fields used in the analysis included:

| Variable | Description |
|---|---|
| Patient ID | Unique patient encounter identifier |
| Patient Admission Date | Date of the patient encounter |
| Patient Admission Time | Time associated with the encounter |
| Patient Gender | Recorded patient gender |
| Patient Age | Patient age |
| Patient Race | Recorded patient race |
| Department Referral | Department associated with the referral |
| Patient Admission Flag | Admission decision |
| Patient Satisfaction Score | Recorded satisfaction score, ranging from 0 to 10 |
| Patient Waittime | Recorded patient waiting-time value |

The cleaned dataset contained 9,216 records.

The actual date values in the cleaned dataset ranged from **1 April 2023 to 30 October 2024**.

An important metadata discrepancy was identified: the dataset's About section describes the period as September 2023 to December 2024, whereas the actual admission-date values indicate April 2023 to October 2024. The date values in the records were therefore used for the analysis.

# 6. Data Preparation and Methodology

Data preparation was an important stage of this project because the reliability of the analysis depended on the consistency and usability of the source data.

Microsoft Excel and Power Query were used to inspect, clean and transform the dataset before analytical modelling.

## 6.1 Data Quality Assessment and Cleaning

Several data-quality issues were identified and addressed.

### A. Admission Date Standardization

A significant number of admission dates were stored as text rather than recognized Excel date values.

A total of 5,603 records were affected.

The ISNUMBER function was used to identify the issue. The Text to Columns approach was subsequently applied to convert the affected entries into valid Excel date values.

This enabled consistent date-based analysis.

### B. Gender Data Correction

Seventeen records contained the malformed gender entry `Femaleemale`.

These entries were recategorized as `Unknown` rather than assuming the intended gender.

This preserved the records while maintaining transparency about the data-quality issue.

### C. Department Referral Classification

The 5,400 records containing the source value None were recategorized as Not referral for this analysis. This classification was adopted to separate these records from encounters assigned to specialist departments.

### D. Age Categorization

Patient ages were grouped into five analytical categories:

| Age Range | Category |
|---|---|
| 1–17 years | Children |
| 18–29 years | Young Adults |
| 30–45 years | Adults |
| 46–59 years | Matured Adults |
| 60–79 years | Seniors |

These categories facilitated demographic comparisons.

### E. Waiting-Time Categorization

Waiting-time values were grouped into four categories:

| Waiting-Time Range | Category |
|---|---|
| 10–15 | Short |
| 16–30 | Moderate |
| 31–45 | Long |
| 46–60 | Excessive |

The dataset documentation did not explicitly identify the unit of measurement. For this operational analysis, the recorded waiting-time values were interpreted as minutes.

This interpretation is an analytical assumption and should be verified against the original data source where possible.

### F. Patient Satisfaction Classification

The recorded satisfaction scores ranged from 0 to 10.

For analytical purposes, they were grouped as follows:

| Score Range | Category |
|---|---|
| 0–4 | Dissatisfied |
| 5–7 | Moderately Satisfied |
| 8–10 | Satisfied |

These are analytical groupings adopted for this project, rather than independently verified institutional satisfaction standards.

## 6.2 Date-Based Transformations

Power Query was used to derive additional date-related fields, including:

- Year
- Month
- Month Name
- Quarter

The dataset was also categorized into four periods of the day:

- Early Morning
- Morning
- Afternoon
- Evening

These transformations supported temporal analysis of patient encounters and admissions.

## 6.3 Data Modelling and Calculations

Power Pivot was used to load the transformed dataset into the Excel Data Model.

DAX measures were developed to calculate the principal performance indicators.

The following measures were used:

**Total Patients**

Total Patients :=
COUNTROWS(PatientsTable)


**Total Admissions**

```dax
Total Admissions :=
CALCULATE(
    COUNTROWS(PatientsTable),
    PatientsTable[Patient Admission Flag] = "Admission"
)
```

**Admission Rate**

```dax
Admission Rate :=
DIVIDE(
    [Total Admissions],
    [Total Patients],
    0
)
```

**Average Satisfaction**

```dax
Average Satisfaction :=
AVERAGE(PatientsTable[Patient Satisfaction Score])
```

**Patients with Satisfaction Scores**

```dax
Patients with Satisfaction Scores :=
COUNT(PatientsTable[Patient Satisfaction Score])
```

**Satisfaction Coverage**

```dax
Satisfaction Coverage :=
DIVIDE(
    [Patients with Satisfaction Scores],
    [Total Patients],
    0
)
```

The average satisfaction calculation excludes blank values but includes recorded zero scores.

**Average Waiting Time**
```dax
Average Waiting Time :=
AVERAGE(PatientsTable[Patient Waittime])
```

# 7. Interactive Dashboard and Key Performance Indicators

An interactive Microsoft Excel dashboard was developed to provide a consolidated view of healthcare patient-flow performance.

The dashboard brings together key performance indicators (KPIs), demographic analysis, admission patterns, waiting-time analysis, departmental referrals and patient satisfaction.

It was designed to help users explore the dataset, identify operational patterns and obtain insights through interactive filtering.

### 7.1. Key Performance Indicators

The dashboard presents six principal performance indicators:

| KPI | Result |
|---|---:|
| Total Patients | 9,216 |
| Total Admissions | 4,612 |
| Admission Rate | 50.04% |
| Average Waiting Time | 35.26 |
| Average Satisfaction Score | 4.99/10 |
| Satisfaction Coverage | 27.31% |

### 7.2 Dashboard Visualisations

The dashboard contains nine analytical visualisations covering:

1. Patient Gender Volumes and Admission Rates.
2. Patient Volumes and Admission Rates by Age Group.
3. Patient Distribution and Admission Rate by Race.
4. Annual Patient Volumes and Admission Rates.
5. Monthly Patient Volumes, Admissions and Admission Rates.
6. Patient Volumes and Admission Rates by Period of Day.
7. Department Referral Admissions and Rates.
8. Patient Volumes and Admission Rates by Waiting Time.
9. Patient Volumes and Admission Rates by Satisfaction Groups.

Combination charts were used to present patient volumes and admission rates together, allowing users to compare absolute counts with admission percentages.

### 7.3 Interactive Filtering

Slicers were incorporated to enable dynamic exploration of the dashboard.

Users can filter the visualisations by:

- Admission Year.
- Gender.
- Age Group.

The interactive elements allow users to examine different patient segments without having to navigate through multiple worksheets.

### 7.4 Dashboard Preview

The following image provides a visual overview of the completed dashboard.

[<img width="1285" height="901" alt="patient_flow_dashboard" src="https://github.com/user-attachments/assets/e84b9ce6-302d-4be9-b317-55c0ca677204" />


*Figure 1: Interactive Healthcare Patient Flow Analytics Dashboard developed using Microsoft Excel.*

The dashboard serves as the primary visual interface for communicating the analytical findings and supporting further exploration of patient-flow patterns.

## 7.5 Download the Excel Workbook

Explore the complete Excel project, including data cleaning, Power Query transformations, Power Pivot data modelling, DAX measures and the interactive dashboard.

[![Download Excel Workbook](https://img.shields.io/badge/Download-Excel%20Workbook-217346?style=for-the-badge&logo=microsoft-excel&logoColor=white)](https://github.com/brighttwumasi/Healthcare-Patient-Flow-Analytics/raw/refs/heads/main/patients_flow_analytics.xlsx)


# 8. Key Findings and Analysis

## 8.1 Overall Patient Admission Performance

The dataset contained 9,216 patient encounters, of which 4,612 resulted in admissions.

| Admission Status | Number of Patients | Percentage |
|---|---:|---:|
| Admission | 4,612 | 50.04% |
| Not Admission | 4,604 | 49.96% |
| **Total** | **9,216** | **100%** |

The overall admission rate was 50.04%.

This indicates that approximately half of the recorded patient encounters resulted in admission.

The relatively balanced distribution between admitted and non-admitted encounters provides a useful starting point for examining factors associated with admission decisions.


## 8.2 Patient Demographic Analysis

### A. Gender Distribution and Admission Patterns

| Gender | Total Patients | Admissions | Admission Rate |
|---|---:|---:|---:|
| Female | 4,470 | 2,239 | 50.09% |
| Male | 4,729 | 2,362 | 49.95% |
| Unknown | 17 | 11 | 64.71% |
| **Total** | **9,216** | **4,612** | **50.04%** |

Male patients accounted for a slightly larger proportion of patient encounters.

Female patients recorded a marginally higher admission rate than male patients.

The difference between the two groups was very small, suggesting broadly similar admission proportions in the dataset.

The Unknown category contained only 17 records and should not be used to draw strong conclusions.

### B. Age-Group Distribution and Admission Patterns

| Age Group | Total Patients | Admissions | Admission Rate |
|---|---:|---:|---:|
| Children | 1,971 | 1,014 | 51.45% |
| Young Adults | 1,452 | 712 | 49.04% |
| Adults | 1,868 | 931 | 49.84% |
| Matured Adults | 1,618 | 812 | 50.19% |
| Seniors | 2,307 | 1,143 | 49.54% |
| **Total** | **9,216** | **4,612** | **50.04%** |

Seniors represented the largest age group, accounting for 25.03% of all patient encounters.

Children followed with 21.39%.

However, Children recorded the highest admission rate at 51.45%.

This distinction is important: the age group with the highest patient volume is not necessarily the group with the highest admission rate.

The findings may help guide further investigation into age-related service demand and admission patterns.

### C. Patient Distribution and Admission Rate by Race

| Race | Total Patients | Admissions | Admission Rate |
|---|---:|---:|---:|
| White | 2,571 | 1,289 | 50.14% |
| African American | 1,951 | 995 | 51.00% |
| Two or More Races | 1,557 | 763 | 49.00% |
| Asian | 1,060 | 541 | 51.04% |
| Declined to Identify | 1,030 | 508 | 49.32% |
| Pacific Islander | 549 | 265 | 48.27% |
| Native American/Alaska Native | 498 | 251 | 50.40% |
| **Total** | **9,216** | **4,612** | **50.04%** |

White patients accounted for the largest number of patient encounters and admissions.

Asian patients recorded the highest admission rate at approximately 51.04%, closely followed by African American patients at approximately 51.00%.

The differences across racial categories were relatively small.

These findings are descriptive and should not be interpreted as evidence that race determines admission outcomes. Further investigation would be required to understand the influence of clinical conditions, age, service utilization and other relevant factors.

## 8.3 Annual Patient Volumes and Admission Rates

| Year | Total Patients | Total Admissions | Admission Rate |
|---|---:|---:|---:|
| 2023 | 4,338 | 2,157 | 49.72% |
| 2024 | 4,878 | 2,455 | 50.33% |
| **Total** | **9,216** | **4,612** | **50.04%** |

The recorded 2024 encounters exceeded the 2023 total by 540, while admissions increased by 298.

The admission rate increased by approximately 0.61 percentage points.

However, these figures must be interpreted carefully.

The actual date coverage is April–December 2023 and January–October 2024. Therefore, the two years do not represent equivalent full-year observation periods.

The figures describe the recorded encounters in each available period and should not be interpreted as a like-for-like annual growth comparison.

## 8.4 Monthly Patient Admission Patterns

The monthly aggregation showed variations in patient volumes and admissions.

Selected observations included:

- April: 454 admissions.
- May: 495 admissions.
- June: 487 admissions.
- July: 502 admissions.
- August: 476 admissions.
- September: 485 admissions.
- October: 486 admissions.

July recorded the highest monthly admission count in the aggregated results, with 502 admissions.

However, the monthly aggregation combines records from different years.

For example, April includes both 2023 and 2024 encounters, whereas January–March contain only 2024 records and November–December contain only 2023 records.

Consequently, the monthly totals are based on unequal periods of observation.

The monthly chart is useful for describing the aggregated records, but it should not be used to establish seasonality or make direct month-to-month comparisons without separating the years and accounting for the different date coverage.

## 8.5 Department Referral Analysis

The department referral analysis focused on the 3,816 encounters assigned to specialist departments.

The 5,400 encounters categorized as `Not referral` were excluded from this particular analysis.

| Department | Total Patients | Admissions | Admission Rate |
|---|---:|---:|---:|
| General Practice | 1,840 | 887 | 48.21% |
| Orthopedics | 995 | 498 | 50.05% |
| Physiotherapy | 276 | 137 | 49.64% |
| Cardiology | 248 | 122 | 49.19% |
| Neurology | 193 | 97 | 50.26% |
| Gastroenterology | 178 | 89 | 50.00% |
| Renal | 86 | 46 | 53.49% |
| **Total** | **3,816** | **1,876** | **49.16%** |

General Practice recorded the highest referral volume, accounting for approximately 48.2% of the specialist-referral analysis population.

Renal recorded the highest admission rate at 53.49%.

However, Renal had only 86 patient encounters. Its admission rate should therefore be interpreted cautiously.

The findings provide an opportunity to examine referral distribution and departmental admission patterns more closely.

They do not, on their own, establish differences in departmental efficiency or clinical performance.

## 8.6 Waiting-Time Analysis

Waiting-time analysis examined the relationship between the defined waiting-time categories and admission outcomes.

| Waiting-Time Category | Total Patients | Admissions | Admission Rate |
|---|---:|---:|---:|
| Short | 1,082 | 560 | 51.76% |
| Moderate | 2,667 | 1,354 | 50.77% |
| Long | 2,717 | 1,352 | 49.76% |
| Excessive | 2,750 | 1,346 | 48.95% |
| **Total** | **9,216** | **4,612** | **50.04%** |

The analysis showed a declining admission rate across the four waiting-time categories.

Patients in the Short category recorded an admission rate of 51.76%, compared with 48.95% among patients in the Excessive category.

The difference suggests an association between the defined waiting-time categories and admission outcomes within this dataset.

However, this relationship should not be interpreted as evidence that longer waiting times cause lower admission rates.

Other factors, including patient condition, clinical assessment, service availability and admission criteria, may influence both waiting time and admission decisions.

The waiting-time unit was interpreted as minutes for this analysis based on the operational context and recorded values. The original dataset documentation did not explicitly specify the unit.

## 8.7 Patient Admission Patterns by Period of Day

Patient encounters and admissions were examined across four periods of the day.

| Period | Total Patients | Admissions | Admission Rate |
|---|---:|---:|---:|
| Early Morning | 2,316 | 1,138 | 49.14% |
| Morning | 2,316 | 1,148 | 49.57% |
| Afternoon | 2,275 | 1,161 | 51.03% |
| Evening | 2,309 | 1,165 | 50.45% |
| **Total** | **9,216** | **4,612** | **50.04%** |

Patient volumes were relatively similar across the four periods.

Admission volumes increased progressively from Early Morning through Evening.

The Afternoon period recorded the highest admission rate at 51.03%, while Evening recorded the highest admission count at 1,165.

These findings may support further examination of staffing arrangements, patient arrival patterns and service demand across different periods of the day.

The results alone do not establish that staffing levels or operational capacity caused the observed differences.

## 8.8 Patient Satisfaction Analysis

Patient satisfaction scores ranged from 0 to 10.

Of the 9,216 patient encounters, only 2,517 contained recorded satisfaction scores.

This represents a data coverage rate of 27.31%.

The average recorded satisfaction score was 4.99 out of 10.

The distribution across the analytical satisfaction categories was:

| Satisfaction Category | Total Patients | Admissions | Admission Rate |
|---|---:|---:|---:|
| Dissatisfied | 1,148 | 556 | 48.43% |
| Moderately Satisfied | 708 | 330 | 46.61% |
| Satisfied | 661 | 349 | 52.80% |
| **Total** | **2,517** | **1,235** | **49.07%** |

Among patients with recorded satisfaction scores, the Dissatisfied category contained the largest number of encounters.

The Satisfied category recorded the highest admission rate at 52.80%.

These findings should be interpreted with considerable caution because satisfaction scores were available for only 27.31% of the patient population.

The missing satisfaction information may introduce response bias, and the available scores may not represent the experiences of all patients.

The 222 recorded zero scores were retained as valid numerical observations because the source data did not establish that zero represented missing information.

# 9. Recommendations

The findings suggest several areas that healthcare administrators could investigate further.

## 9.1 Strengthen Patient Flow Monitoring

Healthcare administrators should consider monitoring patient volumes, admission decisions and waiting times together.

A combined monitoring approach can provide a more complete picture of operational demand than examining individual indicators in isolation.

## 9.2 Investigate Waiting-Time Patterns

The declining admission rate across the waiting-time categories warrants further investigation.

Management could examine whether waiting-time differences are associated with patient condition, clinical assessment, service availability or other operational factors.

The objective should be to understand the drivers of waiting time and identify opportunities to improve patient flow.

## 9.3 Review Staffing and Scheduling Patterns

The differences observed across periods of the day provide an opportunity to examine whether staffing arrangements and departmental capacity are aligned with patient demand.

Further analysis using shift-level staffing information, patient arrival timestamps and department-level workload data would strengthen this assessment.

## 9.4 Examine Departmental Referral Patterns

General Practice accounted for the largest proportion of specialist referral encounters.

Healthcare administrators could examine referral volumes, processing times, departmental workloads and admission outcomes to identify potential capacity constraints.

Departments with relatively small encounter volumes should be assessed using sufficient observation periods before drawing conclusions from their admission rates.

## 9.5 Improve Patient Satisfaction Data Collection

The 27.31% satisfaction coverage represents a significant limitation.

Healthcare facilities should consider reviewing their patient feedback collection processes to improve response coverage.

Improved collection and documentation of satisfaction scores would provide a more representative basis for monitoring patient experience.

## 9.6 Strengthen Data Quality and Documentation

The project identified issues involving date formats, malformed gender entries, missing referral classifications and incomplete satisfaction records.

Healthcare institutions should establish consistent data-entry standards, validation procedures and documentation practices.

Clear definitions for fields such as waiting time, admission status and satisfaction scores are particularly important.

## 9.7 Develop More Detailed Operational Forecasting

The dataset's business context identifies patient-volume forecasting and operational efficiency as potential use cases.

Further work could incorporate historical patient arrivals, staffing levels, departmental capacity and other operational variables to develop more detailed forecasting models.

The current analysis provides a foundation for such work but does not itself constitute a validated forecasting model.

# 10. Limitations of the Analysis

The findings should be interpreted in light of the following limitations.

### 10.1 Date Coverage Discrepancy

The dataset's About section describes the observation period as September 2023 to December 2024.

However, the actual admission-date values range from 1 April 2023 to 30 October 2024.

The analysis therefore uses the actual dates recorded in the dataset.

### 10.2 Unequal Annual Observation Periods

The 2023 records cover April to December, while the 2024 records cover January to October.

The annual totals are not directly comparable as full-year performance indicators.

### 10.3 Unequal Monthly Coverage

The monthly analysis aggregates records across years.

Some months contain observations from both years, while others contain observations from only one year.

Consequently, the monthly totals should not be interpreted as a like-for-like seasonal comparison.

### 10.4 Missing Patient Satisfaction Data

Only 2,517 of the 9,216 encounters contained satisfaction scores.

The resulting 27.31% coverage may introduce response bias.

Satisfaction findings therefore apply only to the records with available scores.

### 10.5 Waiting-Time Unit

The original dataset documentation does not explicitly identify the unit of measurement for patient waiting time.

Minutes were adopted as the working interpretation based on the operational context and recorded values.

This assumption should be verified against the original source documentation where possible.

### 10.6 Analytical Categorization

Age groups, waiting-time categories and satisfaction classifications were created for this analysis.

They should not be interpreted as official clinical, institutional or regulatory classifications.

### 10.7 Descriptive Rather Than Causal Analysis

The project primarily examines descriptive patterns and relationships.

The observed differences in admission rates do not establish causation.

Further statistical analysis and additional operational data would be required to investigate underlying drivers.

### 10.8 Limited Operational Variables

Although the dataset's business context identifies staffing, capacity and patient-flow management as relevant use cases, the available analysis does not establish the effects of staffing levels, bed availability or clinical severity.

These variables would be valuable additions to future analysis.

# 11. Conclusion

This project demonstrates how Microsoft Excel can be used to transform raw healthcare operational data into structured information that supports business and operational analysis.

Through data cleaning, transformation, data modelling, DAX calculations and interactive dashboard development, the project examined 9,216 patient encounters and identified patterns relating to admissions, demographics, waiting times, departmental referrals and patient satisfaction.

The overall admission rate was 50.04%, while the average recorded satisfaction score was 4.99 out of 10.

The analysis also highlighted important data-quality and coverage considerations, particularly the limited availability of patient satisfaction scores and the need for consistent documentation of operational variables.

Although the findings do not establish causal relationships, they provide a foundation for further investigation into patient-flow efficiency, service demand and patient experience.

Ultimately, effective healthcare analytics is not simply about producing charts or calculating performance indicators. It is about translating reliable data into meaningful insights that can inform better decisions.

**Insights. Integrity. Impact.**

---

# 12. Project Deliverables and Technical Skills Demonstrated

The project demonstrates practical application of the following analytical capabilities:

| Area | Techniques Applied |
|---|---|
| Data Quality Assessment | Data profiling, error identification and validation |
| Data Cleaning | Excel functions and data standardization |
| Data Transformation | Power Query |
| Date Transformation | Year, Month, Month Name and Quarter extraction |
| Data Categorization | Age, waiting-time and satisfaction grouping |
| Data Modelling | Excel Data Model and Power Pivot |
| Analytical Calculations | DAX measures |
| Data Analysis | PivotTables and comparative analysis |
| Data Visualization | PivotCharts and combination charts |
| Dashboard Development | KPI indicators, slicers and interactive visualizations |
| Business Interpretation | Findings, operational implications and recommendations |

## Tools and Technologies

- Microsoft Excel
- Power Query
- Power Pivot
- Data Analysis Expressions (DAX)
- PivotTables
- PivotCharts
- Interactive Excel Dashboards

## Future Development Opportunities

Potential extensions of this project include:

1. Building a month-year trend analysis to support valid temporal comparisons.
2. Developing patient-volume forecasting models.
3. Examining the relationship between patient characteristics and admission outcomes using appropriate statistical techniques.
4. Investigating departmental waiting-time performance.
5. Incorporating staffing and capacity data.
6. Developing predictive models for admission risk and operational planning.
7. Extending the dashboard into Power BI for broader business intelligence applications.

---

# About Brightdata Consult

Brightdata Consult provides services in Data Analytics, Quality Management Systems, Compliance, Data Protection, Research and Insight Development.

We help organizations transform data into meaningful insights, strengthen operational processes and support informed decision-making.

Our approach is guided by three principles:

**Insights. Integrity. Impact.**

Website: https://brightdataconsult.com

**Project Portfolio:** Healthcare Patient Flow Analytics

### Dataset Source and Licence

The dataset used in this project was obtained from Kaggle:

**Source:** Hassan Jameel Ahmed – [Healthcare Analytics: Patient Flow Data](https://www.kaggle.com/datasets/hassanjameelahmed/healthcare-analytics-patient-flow-data)

**Licence:** CC0 1.0 Universal (Public Domain Dedication).

The dataset is released under the CC0 1.0 licence, which permits copying, modification, distribution and reuse, including commercial use, without requiring permission or attribution. 
The CC0 licence applies to the source dataset. The original analytical work, including the Excel workbook, dashboard, documentation and interpretations, was independently developed for this project.

All data preparation, transformations, analytical modelling, DAX calculations, visualisations and interpretations presented in this project were undertaken as part of this independent analysis.

*This project is presented as an analytical case study demonstrating the application of Microsoft Excel and business intelligence techniques to healthcare operational data.*

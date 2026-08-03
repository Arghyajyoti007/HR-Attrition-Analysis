# Employee Attrition Dashboard for HR Analysis

## Introduction

Employee attrition is one of the major challenges faced by organizations across industries. It can result in significant financial and operational costs over time. Through this two-page automated HR Dashboard, I aimed to help HR teams monitor and analyze employee attrition trends and identify the key factors contributing to employee turnover using a dataset of approximately **1,500 employees**.

---

# 🛠️ Tech Stack

| Category | Technologies |
|----------|--------------|
| Data Source | HTTP Source |
| Data Integration | Microsoft Fabric Dataflow Gen2 |
| Data Storage | Microsoft Fabric Lakehouse (Delta Table) |
| Data Validation | SQL Endpoint |
| Semantic Layer | Microsoft Fabric Semantic Model |
| Visualization | Microsoft Power BI |
| Connectivity | DirectLake |
| Security | OneLake Security |
| Languages | SQL, DAX, Power Query (M) |

---

# 🏗️ Solution Architecture

```text
                 HTTP Source
                      │
                      ▼
         Microsoft Fabric Dataflow Gen2
        (Cleaning & Data Transformation)
                      │
                      ▼
        Lakehouse (Delta Table Storage)
                      │
                      ▼
        SQL Endpoint (Data Validation)
                      │
                      ▼
          Fabric Semantic Model
                      │
                      ▼
         Power BI Dashboard (DirectLake)
                      │
                      ▼
          Microsoft Fabric App
```

---

# ✨ Key Features

- End-to-end HR Analytics solution built on Microsoft Fabric
- Automated employee attrition analysis dashboard
- Data ingestion from an HTTP source
- Data transformation using Fabric Dataflow Gen2
- Delta Table storage in Microsoft Fabric Lakehouse
- Data validation using SQL Endpoint
- Semantic Model for optimized reporting
- DirectLake connectivity for high-performance analytics
- Interactive dashboard with drill-through and cross-filtering
- Employee segmentation by Age Group and Salary Band
- OneLake security for protecting sensitive employee data
- Published as a Microsoft Fabric App

---

## Questions to Be Answered

* What is the overall attrition rate?
* Which departments are experiencing the highest attrition?
* Is there a relationship between salary, age, and employee attrition?

---

## Deliverables

A fully automated, governed, and secure HR Analytics Dashboard.

---

## Dashboard Overview

![HR Attrition Dashboard - Executive Summary](https://github.com/user-attachments/assets/ef5d49ba-ff6a-4c18-83d6-db4706a4bec2)

![HR Attrition Dashboard - Detailed Analysis](https://github.com/user-attachments/assets/f424ff89-e279-4d01-9248-84283069b5e0)

---

## Live Dashboard

* **[Open Dashboard App](https://app.fabric.microsoft.com/Redirect?action=OpenReport&appId=dd5f001b-7f1f-48a4-a6c8-94630be5d62b&reportObjectId=922fd4f3-769e-4493-bc58-4b3d3ac6d0c3&ctid=68925209-7378-4959-87b9-88ea918ae4e0&reportPage=90745bee0a00a7831092&pbi_source=appShareLink&portalSessionId=3ad205d6-25f5-44ab-bdf3-32ec54bae17f)**

* **[Open Dashboard](https://app.fabric.microsoft.com/links/D9bW6U3op5?ctid=68925209-7378-4959-87b9-88ea918ae4e0&pbi_source=linkShare)**

> ⚠️ **Note:** Access to the live dashboard requires a Microsoft account with appropriate permissions. If access is unavailable, you can view the dashboard using the screenshots, PDF version, or the Power BI (.pbix) file included in this repository.

---

## Approach

Based on the business requirements, the dashboard was designed to answer key business questions while identifying the factors that influence employee attrition.

### Data Ingestion

Employee data was pulled from an HTTP source and ingested into **Microsoft Fabric Dataflow Gen2** for data preparation and transformation.

### Why Dataflow Gen2?

The dashboard is intended for HR teams. While HR professionals are generally familiar with Power BI, SQL, and Excel, they may not be comfortable working with technical tools such as Python, PySpark, or data pipelines.

Microsoft Fabric Dataflow Gen2 provides an Excel-like Power Query experience, allowing users to:

* Clean and transform data
* Remove null values and duplicates
* Set appropriate data types
* Create calculated columns

For relatively small datasets, this approach also helps reduce unnecessary infrastructure and processing costs.

Two calculated columns were created:

* **Age Group** – To identify which age groups have the highest employee attrition.
* **Salary Band** – To analyze attrition across salary ranges instead of individual salaries.

### Transformation

* Converted the calculated columns from mixed Number/Text to **Text** for better categorization.
* Stored the transformed data in the **Lakehouse** as a Delta Table.

**Dataflow Gen2**

![Dataflow Gen2](https://github.com/user-attachments/assets/1f25da47-91a0-4bc1-9765-fdead9b237a3)

---

## Lakehouse

After the transformations in Dataflow Gen2, the cleaned data was stored in the **Lakehouse**. The data was validated using the SQL Endpoint before creating a Semantic Model for reporting.

Since the dataset is relatively small, a separate star-schema data modeling phase was skipped, and the dashboard was built directly on the flat table.

Within the Lakehouse, OneLake security was configured to restrict access to sensitive employee information such as salary data.

![Lakehouse](https://github.com/user-attachments/assets/02b888fa-3ee5-400e-9433-ce95cd587554)

---

## Semantic Model

A Semantic Model was created from the Lakehouse, and a blank Power BI report was generated in Microsoft Fabric.

The report was then downloaded and developed into the HR Attrition Dashboard using **DirectLake** mode to provide faster query performance and automatic data refresh.

After completion, the report was published to a Microsoft Fabric Workspace, and a Fabric App was created for end users.

<img width="1823" height="809" alt="image" src="https://github.com/user-attachments/assets/5d7de104-4f0c-4d67-81e7-88ec259d6fff" />

---

## Outcomes

Key findings from the analysis:

* Overall employee attrition rate is **16.1%**, while the average industry attrition rate is approximately **10–15%**.
* The **Sales** department has the highest attrition rate at **20.6%**.
* Employees earning **3K or less** have the highest attrition rate (**28.6%**).
* Employees aged **18–25** have the highest attrition rate (**35.8%**).
* Employees working overtime have an attrition rate of **30.5%**.
* Employees who travel frequently for work have an attrition rate of **25.5%**.

These findings indicate a strong relationship between employee attrition and factors such as department, salary, age, overtime, and business travel.

---

## Recommendations

* The Sales department has the highest overtime and contributes significantly to overall attrition. Review workload distribution and work schedules.
* Employees earning **3K or less**, particularly in Sales, show higher attrition. Consider revising compensation structures.
* Review salary ranges for **Sales Representatives** and **Sales Executives** to ensure they align with industry standards.
* Where feasible, introduce Hybrid or Work From Home (WFH) options and reduce unnecessary business travel.


---

# 📁 Repository Structure

```text
HR-Attrition-Analysis/
│
├── Dashboard/
│   ├── hr_attrition_dashboard.pbix
│   └── hr_attrition_dashboard.pdf
│
└── README.md
```

---

# 📂 Files Included

| File | Description |
|------|-------------|
| `hr_attrition_dashboard.pbix` | Editable Microsoft Power BI dashboard |
| `hr_attrition_dashboard.pdf` | Dashboard exported in PDF format |
| `README.md` | Project documentation |

---

# 🔄 Project Workflow

```text
HTTP Source
      │
      ▼
Dataflow Gen2
      │
      ▼
Lakehouse (Delta Table)
      │
      ▼
SQL Endpoint Validation
      │
      ▼
Semantic Model
      │
      ▼
Power BI Dashboard (DirectLake)
      │
      ▼
Microsoft Fabric App
```

---

# 👨‍💻 Author

**Arghyajyoti Samui**

Data Analyst | Microsoft Fabric | Power BI | SQL | Python

- **GitHub:** https://github.com/Arghyajyoti007
- **LinkedIn:** *([LinkedIn Profile](https://www.linkedin.com/in/arghyajyoti-samui/))*

---

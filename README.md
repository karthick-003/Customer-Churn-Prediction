# Telco Customer Churn & Retention Analysis

An end-to-end data analytics project designed to identify core drivers of customer attrition for a telecommunications provider. This project processes over 7,000 raw customer records using Python to diagnose data anomalies and builds an interactive Power BI dashboard to deliver revenue-saving strategic recommendations.

## 📊 Interactive Dashboard Preview
*Insert a high-quality screenshot of your finalized Power BI dashboard right here to instantly grab a recruiter's attention!*

## 🏢 Business Problem
The company is facing a high baseline churn rate that threatens recurring revenue stability. The objective of this analysis is to answer three critical business questions:
1. What is our baseline organizational churn rate?
2. What contract and billing variables are driving customers to leave?
3. Are there specific demographic segments experiencing severe friction?

## 🛠️ Tech Stack & Skills Demonstrated
*   **Data Pipeline & EDA:** Python (Pandas, NumPy) via Jupyter Notebook
*   **Business Intelligence & Visualization:** Power BI Desktop
*   **Analytical Coding:** Custom Data Analysis Expressions (DAX)
*   **Framework:** Problem-Action-Result (PAR) methodology

## 📂 Project Workflow & Methodology

### Phase 1: Python Data Engineering & Cleaning
*   **Anomaly Detection:** Discovered that the `TotalCharges` column was incorrectly stored as an 'object' (text) data type due to hidden blank character spaces.
*   **Data Type Enforcement:** Utilized `pd.to_numeric` with coercion to force data formatting and isolate missing entries.
*   **Missing Value Strategy:** Identified 11 records with null values in `TotalCharges` paired with a customer tenure of `0` (new accounts not yet billed). Dropped these records to preserve statistical accuracy, resulting in a finalized sample of 7,032 records.
*   **Data Pipeline Export:** Overcame regional file-parsing errors by explicitly exporting the cleaned DataFrame via a semicolon-delimited text layout (`sep=';'`).

### Phase 2: Power BI Metrics Engineering (DAX)
Developed custom business measures to calculate critical KPIs dynamically:
*   **Total Churned Customers:**
    ```dax
    Total Churned = CALCULATE(COUNTA('Fixed_Churn_Data'[Churn]), 'Fixed_Churn_Data'[Churn] = "Yes")
    ```
*   **Organizational Churn Rate %:**
    ```dax
    Business Churn Rate % = DIVIDE([Total Churned], DISTINCTCOUNT('Fixed_Churn_Data'[customerID]), 0)
    ```

### Phase 3: Dashboard Architecture & UX Design
*   **KPI Banner:** Aligned Total Volume (7.032K), Loss Volume (2K), and Churn Rate (26.58%) across the top margin to establish an instant visual summary.
*   **Interactive Slicing:** Embedded functional demographic filters allowing stakeholders to slice all visual matrices dynamically by consumer variables.
*   **Data Density Optimization:** Maximized the data-to-ink ratio by removing redundant gridlines and secondary text axes, using integrated data labels instead.

## 💡 Executive Insights & Strategic Recommendations

*   **Contract Type Vulnerability:** Customers on Month-to-month contracts exhibit a staggering **42.71% churn rate**, compared to an exceptionally stable **2.85% rate** for 2-year agreements.
    *   *Recommendation:* Introduce a proactive promotional campaign offering a 10% bill credit to incentivize Month-to-month holders to transition into structured 1-year or 2-year commitments.
*   **Payment Method Friction:** Customers utilizing manual **Electronic Checks** churn at an alarming rate of **45.29%**, contrasting deeply with automated billing flows (Credit Card/Bank Transfer) which remain under 17%.
    *   *Recommendation:* Perform a technical audit on the electronic portal payment flow and offer a one-time \$5 incentive for users migrating to automated auto-pay features.
*   **Senior Citizen Retention Crisis:** Utilizing interactive dashboard slicing revealed that **Senior Citizens experience double the average company churn rate, climbing to 54.65%**.
    *   *Recommendation:* Launch a dedicated customer success outreach pipeline or simplify digital account accessibility layouts specifically tailored to optimize the user experience for older demographics.

## 🚀 How to Run This Project
1. Clone this repository or download the `Telco_Customer_Churn_Analysis.ipynb` notebook.
2. Download the source dataset directly from Kaggle.
3. Execute the Python notebook to generate the cleaned, semicolon-separated export file (`Fixed_Churn_Data.csv`).
4. Open the `Fixed_Churn_Data.csv` inside Power BI Desktop using a Semicolon delimiter to view or edit the dashboard structure.

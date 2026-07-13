## Customer-churn-analysis-sql-python
End-to-end Customer Churn &amp; Retention Analysis using Python and SQLite. Includes ETL data pipelines, support metric tracking, feature engineering (churn risk scoring), and revenue-at-risk analytics.

## Project Summary
Risk Scoring & Segmentation (Risk Analysis & Segmentation)
Developed a multi-dimensional churn risk scoring model by synthesising subscription tenure, plan type, and support escalation signals across three relational tables (20+ KPIs), segmented the customer base into risk tiers using composite churn scores, exposed a significant lifetime value gap between churned and retained cohorts, and recommended prioritising Premium annual-plan retention over Basic monthly acquisition to maximise long-term revenue yield.

## 🛠️ Tech Stack & Dependencies

- **Database:** SQLite (`customer_churn.db`)
- **Language:** Python 3

### 🐍 Python Libraries Used
  **Import core data analysis and visualization libraries **

`import numpy as np`  
`import pandas as pd`  
`import matplotlib.pyplot as plt`  
`import seaborn as sns`  
`import sqlite3`

### 2. Time-Series & Categorical Churn Trends

* **Monthly Churn Trend:** Tracks customer cancellations over time to identify seasonal spikes (e.g., peak churn in September 2024).

<img width="800" height="400" alt="Screenshot 2026-07-13 171034" src="https://github.com/user-attachments/assets/5f377f31-1b7e-48be-b286-f52805ee0dad" />


* **Churn by Plan Type:** Analyzes customer attrition rates across Basic, Premium, and Standard subscription plans.

<img width="800" height="400" alt="Screenshot 2026-07-13 171044" src="https://github.com/user-attachments/assets/a1b9d7b8-9ba3-450f-9746-4a6ba0e1e2db" />


* **Churn by State:** Visualizes geographic churn rates across different states/regions.

<img width="800" height="400" alt="Screenshot 2026-07-13 171121" src="https://github.com/user-attachments/assets/be65e9c9-4722-4b42-9ae1-46eee3cca2fc" />

**Correlation Heatmap:** Highlights key relationships between churn scores, contract types, and churn flags.

<img width="800" height="800" alt="Screenshot 2026-07-13 171146" src="https://github.com/user-attachments/assets/1c9c0751-4fbd-4191-a95c-3b534850cce3" />


* **Pairplot Analysis:** Explores multivariate distributions across encoded features.

<img width="900" height="700" alt="Screenshot 2026-07-13 171017" src="https://github.com/user-attachments/assets/d071e043-e02f-42df-8a1e-2ae4462d39d2" />


## 🗄️ Database Schema & Sample Query

### Table Structure
* `customers`: Contains demographic data and geographic location.
* `subscriptions`: Stores plan types (Basic, Premium), start dates, and status.
* `support_tickets`: Tracks customer complaints and resolution times.

### Sample Analysis: Churn Rate Calculation Query
```sql
SELECT 
    subscription_type,
    COUNT(customer_id) AS total_customers,
    SUM(CASE WHEN status = 'Churned' THEN 1 ELSE 0 END) AS churned_customers,
    ROUND(AVG(CASE WHEN status = 'Churned' THEN 1.0 ELSE 0 END) * 100, 2) AS churn_rate_pct
FROM subscriptions
GROUP BY subscription_type;

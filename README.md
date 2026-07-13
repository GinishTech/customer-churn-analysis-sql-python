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

<img width="713" height="348" alt="Screenshot 2026-07-13 181541" src="https://github.com/user-attachments/assets/78918e18-ae06-4683-939b-b370b451c9de" />


* **Churn by Plan Type:** Analyzes customer attrition rates across Basic, Premium, and Standard subscription plans.

<img width="659" height="379" alt="Screenshot 2026-07-13 181616" src="https://github.com/user-attachments/assets/b87294e0-65c0-4474-aedc-2920e43f9165" />


* **Churn by State:** Visualizes geographic churn rates across different states/regions.

<img width="653" height="380" alt="Screenshot 2026-07-13 181704" src="https://github.com/user-attachments/assets/c02fb330-0c05-463f-a9b6-0d71536b15ac" />

**Correlation Heatmap:** Highlights key relationships between churn scores, contract types, and churn flags.

<img width="582" height="235" alt="Screenshot 2026-07-13 181926" src="https://github.com/user-attachments/assets/6f9300c7-1b3f-4a81-b6d0-4475bbd56c56" />

<img width="575" height="310" alt="Screenshot 2026-07-13 181943" src="https://github.com/user-attachments/assets/49cc4d41-ad4d-4c46-8852-a0a643659741" />


* **Pairplot Analysis:** Explores multivariate distributions across encoded features.

<img width="700" height="700" alt="Screenshot 2026-07-13 171017" src="https://github.com/user-attachments/assets/d071e043-e02f-42df-8a1e-2ae4462d39d2" />


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

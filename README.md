## Customer-churn-analysis-sql-python
End-to-end Customer Churn &amp; Retention Analysis using Python and SQLite. Includes ETL data pipelines, support metric tracking, feature engineering (churn risk scoring), and revenue-at-risk analytics.


"C:\Users\nahal\Pictures\Screenshots\Screenshot 2026-07-13 171146.png"

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

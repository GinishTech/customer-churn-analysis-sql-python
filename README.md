## Customer-churn-analysis-sql-python
End-to-end Customer Churn &amp; Retention Analysis using Python and SQLite. Includes ETL data pipelines, support metric tracking, feature engineering (churn risk scoring), and revenue-at-risk analytics.

import os

# Create the images directory if it doesn't exist
os.makedirs('images', exist_ok=True)

# Save your churn by plan plot
# plt.savefig('images/churn_by_plan.png', bbox_inches='tight', dpi=300)

# Save your geographic breakdown plot
# plt.savefig('images/churn_by_state.png', bbox_inches='tight', dpi=300)

## 📈 Key Visualizations

| Monthly vs. Annual Churn | Geographic Distribution |
| :---: | :---: |
| ![Churn by Plan](images/churn_by_plan.png) | ![Geographic Breakdown](images/churn_by_state.png) |
| *Basic Monthly plans showed significantly higher churn (55.6%)* | *Karnataka registered the highest subscriber drop-offs in Sept 2024* |

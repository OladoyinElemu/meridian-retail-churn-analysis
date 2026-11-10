# meridian-retail-churn-analysis
An end-to-end data science project analysing customer churn, sales trends and retention opportunities at Meridian Retail Group
## Project Overview

This project investigates declining sales and customer retention challenges at Meridian Retail Group using data analysis and machine learning.

The goal is to understand customer purchasing behaviour, identify factors associated with churn, analyse sales performance and recommend practical strategies to improve customer retention.

## Business Objectives

- Investigate the decline in sales revenue and order volume.
- Identify customers at risk of churn.
- Examine purchasing behaviour and customer retention patterns.
- Explore relationships between customer characteristics, shopping channels and churn.
- Analyse sales trends over time.
- Develop data-driven recommendations to improve customer retention.

## Tools and Technologies

- Python
- Google Colab
- Pandas
- NumPy
- Matplotlib
- Seaborn
- SQL
- Scikit-learn

## Datasets

The project uses five datasets:

1. Customers
2. Products
3. Orders
4. Order Items
5. Support Tickets

**Data privacy:** Original datasets are not included in this repository because they contain potentially identifiable customer information.

## Key Findings

### 1. Sales Performance

- Sales revenue and completed order volume declined significantly between March and June 2026.
- June revenue was approximately 54.5% lower than March revenue.
- The decline was primarily associated with reduced order volume rather than a major reduction in average order value.
- Sales declined across In-Store, Online and Mobile App channels.

### 2. Customer Churn

Using a provisional 180-day inactivity definition at the July 1, 2026 snapshot:

- Churned customers: 3,625 (59.5%)
- Active customers: 2,015 (33.1%)
- Customers with no recorded purchase: 450 (7.4%)

### 3. Customer Retention

Returning customers contributed approximately 74% of revenue in January 2026, but their contribution fell to approximately 42% by June 2026.

This highlights the importance of strengthening repeat-purchase behaviour.

### 4. Customer Support

Churned customers had slightly lower average support satisfaction and longer average ticket resolution times than active customers. These differences are associations and do not establish that support issues caused churn.

### 5. Churn Prediction

A Random Forest classifier was developed to identify customers at risk of churn.

At the provisional decision threshold of 0.40, the model achieved:

- Accuracy: 77.22%
- Churn precision: 80.57%
- Churn recall: 89.42%
- F1-score: 84.77%

The model identified 651 of 728 actual churners in the test set.

Recency of purchase was the most influential predictive feature.

## Recommendations

1. Develop targeted retention campaigns for customers showing declining purchase activity.
2. Prioritise high-risk customers for appropriate re-engagement offers.
3. Investigate the reasons behind the decline in order volume across all sales channels.
4. Improve customer support resolution processes and monitor customer satisfaction.
5. Strengthen customer feedback and referral-source data collection.
6. Monitor churn and sales performance regularly using clear business metrics.

## Project Limitations

- The 180-day churn definition is provisional and may not represent the company's official churn policy.
- The model uses historical data and requires further validation before operational deployment.
- The random train-test split does not fully simulate future prediction.
- Some customer profile information may not represent its historical state at the feature cutoff.
- Outlet-level analysis was limited by the absence of a confirmed outlet identifier in the available data.

## Conclusion

The investigation indicates that declining order volume and reduced purchasing activity among returning customers are important patterns associated with Meridian Retail Group's sales decline.

The churn prediction model provides a starting point for identifying customers who may need retention attention. Combining predictive insights with targeted customer engagement and continuous monitoring could help the business improve customer retention and sales performance.

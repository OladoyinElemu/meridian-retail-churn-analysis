# Final Project Report: Reducing Customer Churn at Meridian Retail Group

## 1. Executive Summary

This project investigates declining sales performance and customer retention challenges at Meridian Retail Group using data analysis and machine learning.

The investigation examined customer purchasing behaviour, sales trends, customer support interactions, and customer characteristics to understand patterns associated with churn.

The analysis identified a significant decline in completed orders and revenue between March and June 2026. It also revealed a reduction in the contribution of returning customers to overall revenue.

A Random Forest classification model was developed to identify customers at risk of churn. At a provisional decision threshold of 0.40, the model achieved 77.22% accuracy and 89.42% recall for the churn class.

The findings provide a basis for targeted customer retention initiatives and improved business monitoring.

## 2. Introduction

Customer retention is important to the long-term growth and profitability of retail businesses. A decline in repeat purchases can reduce revenue, weaken customer relationships and increase the cost of acquiring replacement customers.

Meridian Retail Group experienced declining sales activity, creating a need to investigate customer behaviour and identify possible retention challenges.

This project applies data science techniques to examine the available business data, identify patterns associated with customer churn and develop a predictive model to support retention decisions.

## 3. Project Objectives

The main objectives were to:

1. Investigate the decline in sales revenue and completed order volume.
2. Identify customers who may have stopped purchasing.
3. Examine customer purchasing behaviour and retention patterns.
4. Investigate the relationship between customer characteristics, support experiences and churn.
5. Analyse sales trends across available periods and shopping channels.
6. Develop a machine learning model for identifying customers at risk of churn.
7. Recommend practical strategies for improving customer retention.

## 4. Data Description

The project used five datasets:

| Dataset | Description |
|---|---|
| Customers | Customer demographic and profile information |
| Products | Product descriptions, categories and pricing |
| Orders | Transaction dates, channels, payment information and order values |
| Order Items | Individual products purchased and quantities |
| Support Tickets | Customer complaints, enquiries, resolution times and satisfaction scores |

The datasets were examined and prepared for analysis using Python and Pandas.

### Data preparation

The preparation process included:

- Checking dataset dimensions and column names.
- Identifying missing values and duplicate records.
- Standardising inconsistent order-status values.
- Converting relevant date and numerical fields into appropriate data types.
- Investigating unusual values, including negative quantities and shipping costs.
- Handling invalid support-ticket resolution times.
- Preparing customer-level features for churn analysis.

Records with missing dates were excluded from date-based analysis where necessary. Unusual transaction values were investigated rather than automatically removed.

Original customer datasets are excluded from this repository to protect personal information.

## 5. Exploratory Data Analysis

### 5.1 Sales Performance

The sales analysis revealed a substantial decline between March and June 2026.

- March 2026 revenue: approximately ₦1.58 million.
- April 2026 revenue: approximately ₦1.49 million.
- May 2026 revenue: approximately ₦1.27 million.
- June 2026 revenue: approximately ₦720,580.

Revenue declined by approximately 54.5% between March and June 2026.

Completed orders also declined from 1,011 in March to 470 in June.

The average order value changed relatively little compared with the reduction in order volume. This suggests that reduced purchasing activity was a major contributor to the observed revenue decline.

July 2026 was excluded from full-month comparisons because the available data covered only the first three days of the month.

### 5.2 Sales Channel Analysis

The business operated across three shopping channels:

- In-Store
- Online
- Mobile App

All three channels experienced substantial declines between March and June 2026.

This indicates that the decline was not limited to one shopping channel. Further investigation into customer demand, marketing effectiveness, stock availability, pricing and operational issues is recommended.

### 5.3 Customer Purchasing Behaviour

Returning customers were an important source of revenue during the first half of 2026.

Their contribution to monthly revenue changed as follows:

- January: approximately 74.2%.
- February: approximately 76.1%.
- March: approximately 70.4%.
- April: approximately 71.0%.
- May: approximately 55.7%.
- June: approximately 42.0%.

This decline highlights a possible weakening in repeat-purchase activity.

The number of customers making purchases also declined considerably, particularly between April and June.

These results suggest that customer re-engagement should be a major business priority.

## 6. Customer Churn Analysis

### 6.1 Churn Definition

For this investigation, a provisional 180-day inactivity rule was used.

The customer status snapshot was set to July 1, 2026.

Customers with a completed purchase within the preceding 180 days were classified as active. Customers whose last completed purchase occurred before the 180-day cutoff were classified as churned.

Customers without a recorded completed purchase before the snapshot were classified as never purchased.

This is a project-specific analytical definition and should be compared with Meridian Retail Group's official churn policy.

### 6.2 Customer Status Distribution

The analysis covered 6,090 customers.

| Customer Status | Number | Percentage |
|---|---:|---:|
| Churned | 3,625 | 59.5% |
| Active | 2,015 | 33.1% |
| Never Purchased | 450 | 7.4% |
| Total | 6,090 | 100% |

The results indicate that approximately six out of every ten customers were classified as churned under the provisional definition.

This represents a significant customer retention concern.

### 6.3 Customer Behaviour and RFM Analysis

Recency, Frequency and Monetary (RFM) analysis was used to compare customer purchasing behaviour.

The results showed:

- Active customers had an average recency of approximately 89 days.
- Churned customers had an average recency of approximately 516 days.
- Active customers had an average historical purchase frequency of 4.80.
- Churned customers had an average historical purchase frequency of 4.25.

These findings show differences in purchasing activity between active and churned customers.

The recency difference is partly expected because inactivity was used to define churn.

## 7. Factors Associated with Customer Churn

Several customer attributes and support-related measures were examined.

### 7.1 Membership Tier

Churn was observed across all membership tiers.

The churn proportions were relatively similar, ranging from approximately 57.4% for Platinum customers to 60.2% for Gold customers.

Membership tier alone did not provide a strong distinction between active and churned customers.

### 7.2 Preferred Shopping Channel

The analysis examined whether customers' preferred shopping channels were associated with their churn status.

A chi-square test produced:

- Chi-square statistic: 3.921.
- Degrees of freedom: 4.
- P-value: 0.4168.
- Cramér's V: 0.0179.

The result did not indicate a statistically significant association between preferred shopping channel and customer status.

### 7.3 Referral Source

Referral sources were also examined.

The chi-square test produced:

- Chi-square statistic: 11.305.
- Degrees of freedom: 14.
- P-value: 0.6619.
- Cramér's V: 0.0305.

The result did not indicate a statistically significant relationship between referral source and customer status.

The number of missing referral-source records also highlights the need for better customer acquisition data collection.

### 7.4 Customer Support Experience

Customer support records were examined to investigate possible differences between active and churned customers.

The analysis found:

- Average satisfaction among active customers: approximately 3.92.
- Average satisfaction among churned customers: approximately 3.86.
- Average resolution time for active customers: approximately 17.33 hours.
- Average resolution time for churned customers: approximately 18.67 hours.

Statistical tests indicated modest differences between the groups.

However, these findings do not establish that support experiences caused customers to stop purchasing. The timing of support interactions relative to customers' last purchases should be investigated further.

## 8. Churn Prediction Model

### 8.1 Modelling Approach

A Random Forest classification model was developed to predict customer churn.

The modelling dataset contained 5,131 customers who had made at least one completed purchase before January 2, 2026.

Historical purchasing information was used as the feature period, while purchasing activity between January 2 and July 1, 2026 was used to establish the prediction outcome.

Customers who did not make a completed purchase during the prediction period were labelled as churned. Those who made at least one completed purchase were labelled as retained.

The dataset contained:

- Churned: 3,639 customers.
- Retained: 1,492 customers.

Customer identifiers were excluded from the predictive features.

### 8.2 Model Development

A Random Forest classifier was trained using a stratified 80/20 train-test split.

Class weighting was applied to help address the imbalance between churned and retained customers.

The model was evaluated using:

- Accuracy
- Precision
- Recall
- F1-score
- ROC-AUC
- Confusion matrix

Recall was particularly important because the business needs to identify as many potentially churned customers as reasonably possible.

### 8.3 Model Performance

At the provisional decision threshold of 0.40, the model achieved:

| Metric | Result |
|---|---:|
| Accuracy | 77.22% |
| Churn Precision | 80.57% |
| Churn Recall | 89.42% |
| F1-score | 84.77% |

The confusion matrix was:

| Actual / Predicted | Retained | Churned |
|---|---:|---:|
| Retained | 142 | 157 |
| Churned | 77 | 651 |

The model correctly identified 651 of the 728 actual churners in the test set.

It missed 77 actual churners and incorrectly flagged 157 retained customers as potential churners.

The results suggest that the model can provide a useful starting point for prioritising customer retention activities.

However, further validation is required before operational deployment.

### 8.4 Feature Importance

The five most influential features in the Random Forest model were:

| Feature | Importance |
|---|---:|
| Recency of purchase | 0.3902 |
| Customer tenure | 0.1630 |
| Historical total spend | 0.1260 |
| Historical order count | 0.0973 |
| Average order value | 0.0868 |

Recency of purchase was the most influential feature.

This indicates that customers' recent purchasing activity played an important role in the model's ability to distinguish between churned and retained customers.

Feature importance measures predictive contribution; it does not establish causation.

## 9. Customer Risk Segmentation

The model's predicted churn probabilities were used to group customers into three provisional risk categories.

| Risk Category | Customers | Observed Churn Rate |
|---|---:|---:|
| Low | 234 | 36.75% |
| Medium | 410 | 74.15% |
| High | 383 | 88.25% |

The high-risk group had the highest observed churn rate.

This segmentation could help the business prioritise customer engagement efforts.

The thresholds used for these categories are provisional and should be adjusted according to available retention resources and the cost of incorrectly identifying customers.

## 10. Business Recommendations

Based on the findings, the following recommendations are proposed.

### 10.1 Introduce Targeted Retention Campaigns

Use customer purchasing history and churn-risk scores to identify customers who may need re-engagement.

Personalised offers and reminders could be tested for customers showing declining purchase activity.

### 10.2 Prioritise High-Risk Customers

Develop retention strategies for customers classified as high risk.

The business should prioritise interventions according to customer value, risk level and the cost of engagement.

### 10.3 Investigate the Decline in Order Volume

Since order volume declined substantially across all three shopping channels, management should investigate:

- Changes in customer demand.
- Product availability and stockouts.
- Competitor pricing.
- Marketing campaign performance.
- Delivery and fulfilment experiences.
- Changes in customer purchasing preferences.

These are areas for further investigation, not established causes from the current analysis.

### 10.4 Improve Customer Support

Monitor support resolution times and satisfaction scores.

Identify recurring complaints and investigate whether unresolved customer issues are followed by reduced purchasing activity.

### 10.5 Strengthen Customer Data Collection

Improve the completeness of customer profiles, particularly referral-source and marketing-consent information.

This will support more reliable customer segmentation and campaign evaluation.

### 10.6 Establish Regular Performance Monitoring

Develop a dashboard to monitor:

- Monthly revenue.
- Completed order volume.
- Active purchasing customers.
- Repeat-purchase rate.
- Customer churn rate.
- Customer support satisfaction.
- Churn-risk distribution.

This will help management identify changes early and evaluate the effectiveness of retention initiatives.

## 11. Project Limitations

The investigation has several limitations:

1. The 180-day inactivity rule is provisional and may differ from the company's official definition of churn.
2. The prediction model was evaluated using a random train-test split rather than a fully time-based validation approach.
3. Some customer profile fields may reflect current rather than historical information.
4. The model's performance does not guarantee similar results when applied to future customers.
5. Support-ticket associations do not establish that support issues caused churn.
6. The available data did not provide a confirmed outlet identifier for reliable outlet-level sales comparisons.
7. The analysis does not independently establish whether competitor pricing, stock availability or marketing changes caused the sales decline.

Further investigation and validation are recommended before business deployment.

## 12. Conclusion

This project investigated customer churn and declining sales performance at Meridian Retail Group through exploratory data analysis, statistical testing and machine learning.

The findings revealed a significant decline in completed orders and revenue between March and June 2026. Returning customers also contributed a smaller share of monthly revenue over this period.

The churn analysis identified a substantial proportion of customers classified as inactive under the provisional 180-day definition.

The Random Forest model demonstrated useful predictive potential, identifying 89.42% of actual churners in the test set at the selected decision threshold.

Overall, the investigation highlights the importance of monitoring purchasing behaviour, improving customer engagement and using data-driven retention strategies.

With further validation and effective implementation, the findings can support better customer retention decisions and improved business performance.

## 13. Tools Used

- Python
- Google Colab
- Pandas
- NumPy
- Matplotlib
- Seaborn
- SQL
- Scikit-learn
- GitHub

## 14. Project Author

**Data Science Capstone Project**

**Project Title:** Reducing Customer Churn at Meridian Retail Group

**Repository:** meridian-retail-churn-analysis

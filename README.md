# Meridian Retail Churn Analysis

**An end-to-end data science project analysing customer churn, sales trends and retention opportunities at Meridian Retail Group.**

## 1. Project Overview

This project investigates declining sales performance and customer retention challenges at Meridian Retail Group using data analysis, SQL and machine learning.

The aim is to understand customer purchasing behaviour, identify patterns associated with customer churn, examine sales performance and develop predictive models that can support better customer-retention decisions.

## 2. Business Objectives

- Investigate changes in sales revenue and completed order volume.
- Measure customer inactivity and examine customer churn patterns.
- Identify customers who may be at risk of churn.
- Examine purchasing behaviour across customer segments and shopping channels.
- Explore customer support experiences and their association with churn.
- Develop and evaluate machine-learning models for churn prediction.
- Recommend practical strategies to improve customer retention and sales performance.

## 3. Tools and Technologies

- Python
- Google Colab
- Pandas
- NumPy
- Matplotlib
- Plotly
- Seaborn
- SQLite and SQL
- Scikit-learn
- FastAPI

## 4. Datasets

The project uses five related datasets:

1. Customers
2. Products
3. Orders
4. Order Items
5. Support Tickets

The original datasets contain 6,090 customer records, 220 product records, 28,297 order records, 73,505 order-item records and 5,200 support-ticket records.

**Data privacy:** Raw customer datasets are not included in this repository because they contain potentially identifiable customer information.

## 5. Project Methodology

The project covers the following stages:

1. Project objectives and business understanding.
2. Initial data inspection.
3. Data cleaning and preparation.
4. Database preparation and SQL analysis.
5. Customer churn analysis and business investigation.
6. Data visualisation.
7. Exploratory Data Analysis (EDA).
8. Visualisation captions and interpretation.
9. Machine-learning modelling and predictive analysis.

## 6. Key Findings

### 6.1 Sales Performance

- Completed-order revenue declined by approximately 54.5% between March and June 2026.
- The decline was accompanied by a reduction in completed order volume.
- The findings suggest that fewer completed transactions contributed substantially to the decline in revenue.
- Sales performance was examined across the available sales channels.

### 6.2 Customer Churn

Using the descriptive customer activity snapshot dated 1 July 2026 and a 180-day inactivity definition:

- Total registered customers: 6,090
- Active customers: 2,018 (33.14%)
- Churned customers: 4,072 (66.86%)

Customers who had never made a completed purchase were included in the descriptive churn category under this definition.

### 6.3 Customer Segmentation

- Gold members recorded the highest churn rate at 67.94%, while Platinum members recorded the lowest at 66.18%.
- In-Store customers recorded the highest channel churn rate at 67.96%, compared with 65.98% for Online customers.
- Friend Referral customers recorded the highest referral-source churn rate at 68.73%, while Influencer referrals recorded the lowest at 63.12%.
- Earlier signup cohorts generally recorded higher churn rates, although recent cohorts had shorter observation periods.

### 6.4 Purchasing Behaviour (RFM Analysis)

Among customers with previous completed purchases:

- Active customers had an average recency of 89.19 days, compared with 515.71 days for churned previous buyers.
- Active customers averaged 4.87 completed orders, compared with 4.31 among churned previous buyers.
- Active customers recorded an average monetary value of ₦7,540.46, compared with ₦6,620.82 among churned previous buyers.

Recency of purchase was particularly useful in distinguishing active customers from churned previous buyers.

### 6.5 Customer Support

- Churned customers averaged 0.87 support tickets per customer, compared with 0.83 among active customers.
- Average satisfaction was 3.89 for both groups.
- Average ticket resolution time was slightly higher among churned customers at 18.83 hours, compared with 17.74 hours for active customers.

These differences are observational and do not establish that support experiences caused customer churn.

## 7. Predictive Modelling

The predictive modelling analysis used a separate dataset of 5,117 eligible customers who had made at least one completed purchase before the historical feature cutoff.

The prediction period covered 2 January to 30 June 2026.

- Churned customers: 3,625
- Retained customers: 1,492
- Modelling churn rate: 70.84%

The modelling process included data preprocessing, a stratified train-test split, a baseline classifier and comparisons of Logistic Regression, Decision Tree, Random Forest and Neural Network models.

### Preferred Model: Neural Network

The final recovered Neural Network model achieved:

| Evaluation Metric | Result |
|---|---:|
| Accuracy | 75.00% |
| Churn Precision | 78.56% |
| Churn Recall | 88.97% |
| Churn F1-score | 83.44% |
| ROC-AUC | 0.7534 |

The confusion matrix was:

| | Predicted Retained | Predicted Churned |
|---|---:|---:|
| Actual Retained | 123 | 176 |
| Actual Churned | 80 | 645 |

The Neural Network was selected as the preferred model because it achieved higher churn recall and F1-score in the final recovered run, making it useful for identifying customers who may require retention attention.

Recency of purchase was also identified as an important predictor in the Random Forest feature-importance analysis.

## 8. Recommendations

1. Develop targeted retention campaigns for customers showing prolonged purchase inactivity.
2. Prioritise customers identified as having a high likelihood of churn.
3. Investigate the decline in completed order volume across sales channels.
4. Strengthen customer engagement through personalised offers and loyalty initiatives.
5. Monitor customer support resolution times and satisfaction.
6. Improve the completeness of customer referral and location information.
7. Monitor sales and churn performance regularly using clear business metrics.

## 9. Model Deployment

A Neural Network model package was saved with its preprocessing pipeline, required feature list and decision threshold.

A FastAPI application was developed with a `/predict` endpoint to accept customer information and return a churn prediction and probability.

The API implementation includes checks for missing features and invalid numerical inputs.

## 10. Project Limitations

- The 180-day inactivity definition is a project-defined measure and may differ from Meridian Retail Group's official churn policy.
- The descriptive churn analysis and predictive modelling use different customer populations and observation definitions.
- Recent signup cohorts have shorter observation periods.
- Missing customer location and referral information limits some segment comparisons.
- The model uses historical data and requires further validation before operational use.
- Predictive associations do not establish the causes of customer churn.

## 11. Repository Contents

- `MERIDIAN_CHURN_PROJECT_FINAL.ipynb` — Jupyter Notebook containing data inspection, cleaning, SQL analysis, visualisations, EDA and machine-learning modelling.
- `Meridian_Retail_Churn_Final_Report.docx` — Written project report containing the business findings, analysis and recommendations.
- `README.md` — Project overview and repository guide.

## 12. Conclusion

The investigation identified substantial customer inactivity and a decline in completed-order revenue during the observed period.

Purchasing recency, frequency and monetary value provided useful insights into differences between active and churned previous buyers. The Neural Network model also demonstrated the potential of machine learning to identify customers who may be at risk of churn.

Combining customer behaviour analysis, predictive insights and targeted retention strategies could help Meridian Retail Group improve customer engagement and strengthen its sales performance.

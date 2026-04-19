## Introduction
Predict whether a customer will churn their subscription within the next 30 days using behavioral and account data available at the current time, so that the company can proactively offer retention incentives such as discounts or personalized support. The primary stakeholders are customer success teams, marketing teams, and customers themselves. Benefits include improved customer retention and more relevant engagement, while potential harms include biased targeting or unfair treatment if certain groups are disproportionately flagged.

## Five-part framing dictionary for your PRD
```
problem_spec = {
    "decision": "offer_discount_or_proactive_support",
    "unit": "customer",
    "event": "churn",
    "horizon_days": 30,
    "prediction_time": "daily_batch",
    "feature_list": [
        "subscription_age",
        "bill_avg",
        "service_failure_count",
        "download_avg",
        "upload_avg",
        "is_tv_subscriber",
        "is_movie_package_subscriber",
    ]
}
```

Features (past data) → Prediction (today) → Outcome (churn in 30 days)

## Model selection
### Baseline Model: Logistic Regression

Logistic Regression is used as the baseline model due to its simplicity and interpretability. It performs well on binary classification tasks and provides a clear benchmark for evaluating more complex models.

### Stretch Model: Random Forest Classifier

Random Forest is selected as the stretch model because it can capture non-linear relationships and interactions between features. It is expected to improve predictive performance, especially in identifying customers at risk of churn.

## Ethics
The dataset does not contain explicit sensitive attributes such as gender, race, or ethnicity. This reduces the risk of direct bias in model predictions, although indirect bias through proxy variables may still need to be monitored.

Regulatory and ethical considerations are addressed in a separate compliance document, where the system is classified as a Limited Risk AI application under the EU AI Act, along with key measures for responsible and fair use.

## Frame the project to the real world (Final summary of Lesson 2) - THIS IS OPTIONAL, IT WAS NOT ASKED TO ADD INTO PRD
Predict whether a customer (unit) will churn their subscription (event) within the next 30 days (horizon) using behavioral and account data available at the current time (prediction time), so that the company can proactively offer retention incentives such as discounts or personalized support (decision). The primary stakeholders are customer success teams, marketing teams, and customers themselves. Benefits include improved customer retention and more relevant engagement, while potential harms include biased targeting or unfair treatment if certain groups are disproportionately flagged.

The primary success metric is recall for churners, as missing a high-risk customer is more costly than incorrectly targeting a low-risk one. However, increasing recall may reduce precision, leading to unnecessary incentives and higher operational costs. The prediction is made daily using features such as recent usage, billing behavior, and support interactions, ensuring all inputs are available before the prediction time to avoid data leakage.

This system falls under a Limited Risk tier according to the EU AI Act. A key ethical concern is indirect bias, where even after removing sensitive attributes like gender, proxy variables may still lead to unfair outcomes across different customer groups.

## Data plan
Multiple datasets were evaluated with respect to licensing and usage constraints. The ISP dataset was selected as it is released under a CC0 (Public Domain) license, allowing unrestricted use without attribution requirements. Other datasets, such as the bank dataset (Apache 2.0) and telecom dataset (unclear ownership), were considered but not selected due to either licensing complexity or lower overall suitability.

## Data selection
The ISP dataset was selected after evaluating multiple datasets based on alignment, scale, data quality, and ethical considerations. It provided the best balance of relevance, accessibility, and overall data quality for the churn prediction task.

## Data overview
The ISP dataset does not exhibit a significant class imbalance.  
The `Churn` column contains 40,050 `True` values and 32,224 `False` values, suggesting that both classes are reasonably well represented.

## Quick Evaluation Summary
| Dataset        | Alignment | Scale  | Labeling Cost | Ethics            |
|----------------|----------|--------|---------------|-------------------|
| Telcom       | High     | Medium | Low           | Unclean (Data files © Original Authors)     |
| Bank Customer Churn  | High   | High   | Low          | Clean (Apache 2.0)     |
| ISP  | High     | High   | Low           | Clean (CC0: Public Domain)  |

























## Ethics
Sensitive data - Potentially sensitive: ['gender']
The feature “gender” was identified as a sensitive attribute due to its potential to introduce bias in model predictions. To mitigate fairness risks and avoid discriminatory outcomes, this variable was removed from the feature set. This ensures that predictions are not directly influenced by protected characteristics. Other features such as tenure were retained, as they are not sensitive and provide important behavioral signals for predicting churn. While more advanced techniques such as fairness constraints could be applied, dropping sensitive attributes is a simple and effective baseline approach aligned with ethical modeling practices.



## Summary
A customer churn prediction model primarily benefits customer success and marketing teams by enabling them to identify at-risk customers and intervene proactively with personalized offers, support, or service improvements. Customers also benefit from more relevant engagement and a better overall experience. Beyond these direct effects, improved churn prediction can lead to broader outcomes such as reduced customer acquisition costs, increased customer lifetime value, and more efficient use of marketing resources. By focusing on retaining existing customers rather than constantly acquiring new ones, companies can operate more sustainably and build stronger long-term relationships. Progress can be measured through key performance indicators such as a 15–25% reduction in churn rate over a few months, improved retention campaign conversion rates, and increased average customer lifetime value. Additionally, a decrease in acquisition spending can signal better efficiency. From a sustainability perspective, this approach aligns with SDG 12 – Responsible Consumption and Production, as it promotes more efficient use of resources by maximizing the value of existing customers and reducing wasteful marketing efforts aimed at constant customer replacement.





## Key dataset characteristics
|Metric| Value|
|----------|-------------|
|Number of samples|     ~72000       |
|Number of classes|           2  |
|Class imbalance|              Moderate|
|Features|              Behavioral, account, and usage data      |
|Target variable|            Churn       |


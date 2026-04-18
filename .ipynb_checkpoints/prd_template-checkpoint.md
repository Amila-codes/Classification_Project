## **Problem Requirement Document (PRD)**

**🧱 PRD Sections at the “Idea Only” Stage**
1. 🧩 Problem Statement (~100 words) Clearly define:
    Predict whether an individual customer will churn (i.e., cancel their subscription or become inactive) within the next 30 days, based on data available at the current time. The prediction informs whether to offer a retention incentive such as a discount, personalized outreach, or service improvement. Each prediction is made at the customer level, with churn as the outcome event. By identifying at-risk customers within this time horizon, the business can take timely action to improve retention and reduce revenue loss.
      
2. 📈 Success Metrics (~50 words + table)
    - Set baseline and aspirational targets
    - Use stakeholder interviews or industry benchmarks
    - Use placeholders now; replace with real numbers in Milestone 3
      
3. 👥 Stakeholders & Impact (~100 words + quadrant visual)
    - Map direct/indirect beneficiaries and harms
    - Qualitative only—no data needed
      
4. 🗃️ Data Overview (~120 words)
    - List anticipated sources (e.g., "TrashNet images from Kaggle")
    - Estimate the 5 V’s: Volume, Variety, Velocity, Veracity, Value
    - Flag uncertainties for validation later
      
5. 🧠 Model Scope (~60 words)
    - Propose one baseline model (e.g., logistic regression)
    - Add a stretch model for higher performance (e.g., ensemble, fine-tuned CNN)
      
6. ⚖️ Ethics & Compliance (~80 words)
    - Identify sensitive attributes (if any)
    - Estimate your AI risk tier (e.g., low under EU-AI Act)
    - No data exploration needed—just domain reasoning
      
7. 🚀 Deployment Context (~60 words)
    - Define runtime setting: real-time or batch
    - Note latency budget and whether predictions will be human-reviewed
    - All based on intended use, not dataset

Template - Predict whether {unit} will {event} within {horizon} using data recorded up to {prediction time} so that we can {impact}
Predict whether a customer will churn (cancel their subscription or become inactive) within the next 30 days using data recorded up to the current day (e.g., daily batch at midnight) so that we can proactively offer retention incentives such as discounts or personalized support to reduce churn and improve customer lifetime value.

## Ethics
Sensitive data - Potentially sensitive: ['gender', 'tenure']
The feature “gender” was identified as a sensitive attribute due to its potential to introduce bias in model predictions. To mitigate fairness risks and avoid discriminatory outcomes, this variable was removed from the feature set. This ensures that predictions are not directly influenced by protected characteristics. Other features such as tenure were retained, as they are not sensitive and provide important behavioral signals for predicting churn. While more advanced techniques such as fairness constraints could be applied, dropping sensitive attributes is a simple and effective baseline approach aligned with ethical modeling practices.



## Frame the project to the real world (Final summary of Lesson 2)
Predict whether a customer (unit) will churn their subscription (event) within the next 30 days (horizon) using behavioral and account data available at the current time (prediction time), so that the company can proactively offer retention incentives such as discounts or personalized support (decision). The primary stakeholders are customer success teams, marketing teams, and customers themselves. Benefits include improved customer retention and more relevant engagement, while potential harms include biased targeting or unfair treatment if certain groups are disproportionately flagged.

The primary success metric is recall for churners, as missing a high-risk customer is more costly than incorrectly targeting a low-risk one. However, increasing recall may reduce precision, leading to unnecessary incentives and higher operational costs. The prediction is made daily using features such as recent usage, billing behavior, and support interactions, ensuring all inputs are available before the prediction time to avoid data leakage.

This system falls under a Limited Risk tier according to the EU AI Act. A key ethical concern is indirect bias, where even after removing sensitive attributes like gender, proxy variables may still lead to unfair outcomes across different customer groups.

## Minority classes
There are no minority classes in the customer churn data set. In the churn column, it has 27% True values and 73% False values after checking the 

| Dataset        | Alignment | Scale  | Labeling Cost | Ethics            |
|----------------|----------|--------|---------------|-------------------|
| Telcom       | High     | Medium | Low           | Clean (CC-BY)     |
| Bank Customer Churn  | Medium   | High   | High          | Clean (CC-BY)     |
| Ocean Cleanup  | High     | High   | Low           | Restricted (NDA)  |
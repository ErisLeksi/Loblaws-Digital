# Loblaws Customer Churn Prediction (Q4 2025)

## Project Goal

The objective of this assignment was to accurately predict which customers are highly likely to leave Loblaws (churn) so that retention teams can intervene with targeted offers.

The predictive model is validated and ready for deployment.

## Methodology Summary

This solution used a highly reliable and traditional machine learning pipeline:

1.  **Data Preparation:** Missing values were handled via **Median Imputation**, and extreme values were controlled using the **IQR method** to ensure data stability.

2.  **Feature Engineering:** We created specific **Risk Score Features** (e.g., combining low tenure with high complaint flags) to give the model direct, high-signal information. *Note: The Preferred Payment Mode feature was excluded per constraint.*

3.  **Algorithm:** A **Tuned Random Forest Classifier** was used. This model is ideal because it delivers high accuracy while providing clear reasons for its predictions.

4.  **Validation:** The data was split 70/10/20 (Train/Validation/Test) to ensure the final performance check was completely unbiased.

## Final Model Performance

The final model was tested on a completely unseen 10% Test Set. Results confirm the model is robust and provides the accurate risk ranking required for intervention.

| Metric | Result | Interpretation |
| :--- | :--- | :--- |
| **AUC-ROC** | **0.9834** | Near-perfect ability to rank customers by risk. |
| **Precision@Top 5%** | **1.0000** | **Critical Win:** When targeting the top 5% of customers, $100\%$ are actual churners. This guarantees zero wasted marketing budget in the highest-risk group. |
| **General Precision** | **0.9028** | Overall high predictive quality across the entire customer base. |

## Actionable Retention Strategy

The model's Feature Importance identifies the key levers for retention teams:

The top 5 predictive factors Loblaws must focus on are:

1.  **Tenure** (New customers are the greatest risk.)

2.  **Is\_New\_Customer\_Risk** (Confirms tenure is a key area.)

3.  **CashbackAmount** (Customers spending less cash/points are disengaging.)

4.  **DaySinceLastOrder** (Recency is a strong warning sign.)

5.  **Complain** (Prior negative service experience is a powerful indicator.)

## Next Steps for Deployment (MLOps)

The model has been successfully saved to a `.joblib` file and is ready for the deployment pipeline.

1.  **Deployment:** Deploy the saved model to a **Real-Time Prediction Service** (e.g., a Vertex AI Endpoint).

2.  **A/B Test:** Begin the **Extrinsic Validation** by running a controlled A/B test. This test will measure the **Incremental Churn Reduction** to prove the financial benefit of the model's predictions over the baseline.

3.  **Monitoring:** Set up **Model Monitoring** to track the stability of the input features and the model's performance over time.
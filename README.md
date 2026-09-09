# AI-Powered Fraud Investigation System

An end-to-end fraud investigation system combining **PySpark, XGBoost, SHAP and Qwen AI**.

The system identifies suspicious credit-card transactions, explains the contributing risk signals and generates guarded investigation reports for human review.

![Fraud Investigation Application](images/application_high_risk.png)

## Project Results

| Metric | Result |
|---|---:|
| Transactions processed | 284,807 |
| Confirmed fraud records preserved | 492 |
| Validation PR-AUC | 0.8451 |
| Validation ROC-AUC | 0.9814 |
| Precision | 91.21% |
| Recall | 83.84% |
| F1-score | 87.37% |
| Selected threshold | 42% |

## System Workflow

1. Process transaction data through PySpark Bronze, Silver and Gold layers.
2. Train a class-weighted XGBoost fraud classifier.
3. Select a decision threshold based on validation performance.
4. Explain predictions using global and individual SHAP values.
55. Generate investigation reports using Qwen.
6. Validate reports using automated guardrails.
7. Display the results through an interactive Gradio application.

## Explainable AI

### Global Fraud Model Feature Importance

![Global SHAP Importance](images/global_shap_importance.png)

### Individual Fraud Alert Explanation

![Individual Fraud Explanation](images/individual_fraud_explanation.png)

## Technology Stack

- Python, Pandas and NumPy
- PySpark
- XGBoost and Scikit-learn
- SHAP
- Qwen and Hugging Face Transformers
- Gradio
- Google Colab

## Repository Structure

```text
ai-fraud-investigation-system/
├── 01_Fraud_Data_Pipeline.ipynb
├── 02_Fraud_Model.ipynb
├── requirements.txt.txt
├── images/
└── README.md
```

## Running the Project

1. Run `01_Fraud_Data_Pipeline.ipynb` in Google Colab.
2. Run `02_Fraud_Model.ipynb` after the pipeline artifacts are created.
3. Select a T4 GPU before loading Qwen.
4. Run the Gradio application cell.
5. Select a transaction and click **Analyze transaction**.

## Important Note

This is an educational portfolio project using anonymized transaction data. Fraud probabilities support investigation prioritization but do not independently prove fraud. Final decisions should include human review.

## Author

**Shilpa Siddharajuennials**  
M.Sc. Data Science  
Berlin, Germany

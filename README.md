# AI-Powered Fraud Investigation System

An end-to-end fraud investigation project combining **PySpark data engineering, XGBoost, SHAP explainability and Qwen generative AI**.

The system processes anonymized credit-card transactions, predicts fraud risk, explains the contributing signals and generates evidence-based investigation reports inside Google Colab.

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
| Validation alerts | 91 |

The decision threshold was selected to balance fraud detection with a manageable number of investigation alerts.

## Fraud Investigation Output

The notebook produces a complete investigation report for a selected transaction, including:

- Fraud probability and risk classification
- Transaction details
- Risk-increasing signals
- Risk-reducing signals
- SHAP feature impacts
- Automated AI guardrail validation
- Recommended action for human review

![Fraud Investigation Notebook Output](images/application_high_risk.png)

## System Workflow

1. Process transaction data through PySpark Bronze, Silver and Gold layers.
2. Validate records and preserve confirmed fraud transactions.
3. Prevent leakage between repeated transaction signatures.
4. Train a class-weighted XGBoost classifier.
5. Select a decision threshold using validation performance.
6. Explain predictions using global and individual SHAP values.
7. Generate investigation reports using Qwen.
8. Validate the reports using automated guardrails.
9. Display the final analysis inside the Colab notebook.

## Explainable AI

### Global Fraud Model Feature Importance

This chart identifies the features with the greatest overall influence on the model’s fraud predictions.

![Global Fraud Model Feature Importance](images/global_shap_importance.png)

### Individual Fraud Alert Explanation

This explanation shows how each feature increased or reduced the fraud prediction for an individual transaction.

Red signals increase the fraud score, while blue signals reduce it.

![Individual Fraud Alert Explanation](images/individual_fraud_explanation.png)

## Technology Stack

- Python
- PySpark
- Pandas and NumPy
- XGBoost
- Scikit-learn
- SHAP
- Qwen
- Hugging Face Transformers
- Google Colab
- Google Drive

## Repository Structure

```text
ai-fraud-investigation-system/
├── 01_Fraud_Data_Pipeline.ipynb
├── 02_Fraud_Model.ipynb
├── requirements.txt
├── images/
└── README.md
```

## Running the Project

1. Open `01_Fraud_Data_Pipeline.ipynb` in Google Colab.
2. Run all cells to create the Bronze, Silver and Gold data layers.
3. Open `02_Fraud_Model.ipynb`.
4. Select a T4 GPU before loading Qwen.
5. Run all cells to train, validate and explain the model.
6. Run the transaction-analysis cell to generate an investigation report.

## Responsible Use

This educational portfolio project uses anonymized transaction data.

The fraud probability supports investigation prioritization but does not independently prove fraud. Final decisions should include human review and appropriate organizational controls.

## Author

**Shilpa Siddharaju**  
M.Sc. Data Science  
Berlin, Germany

# AI-Powered Fraud Investigation System

An end-to-end fraud investigation platform combining **data engineering, machine learning, explainable AI and generative AI**.

The system processes anonymized credit-card transactions through a PySpark pipeline, predicts fraud using XGBoost, explains each decision using SHAP and generates evidence-based investigation reports using Qwen.

## Web Application

The interactive web application allows investigators to select a transaction and analyze its fraud risk.

It displays:

- Fraud probability and risk decision
- Important risk-increasing and risk-reducing signals
- SHAP-based supporting evidence
- AI-generated investigation summary
- Automated guardrail validation
- Recommended action for human review

![AI-Powered Fraud Investigation Web Application](images/application_high_risk.png)

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
| Selected decision threshold | 42% |
| Validation alerts generated | 91 |

The decision threshold was selected to balance fraud recall with a manageable number of investigation alerts.

## System Workflow

1. Ingest and validate anonymized transaction data.
2. Create PySpark Bronze, Silver and Gold data layers.
3. Preserve confirmed fraud records and prevent data leakage.
4. Train a class-weighted XGBoost fraud classifier.
5. Select an operating threshold using validation metrics.
6. Generate global and transaction-level SHAP explanations.
7. Produce grounded investigation reports using Qwen.
8. Validate AI reports through automated guardrails.
9. Display results through an interactive Gradio web application.

## Explainable AI

### Global Fraud Model Feature Importance

The global SHAP chart identifies the features that have the greatest overall influence on the model’s fraud predictions.

![Global Fraud Model Feature Importance](images/global_shap_importance.png)

### Individual Fraud Alert Explanation

The individual SHAP explanation shows how each feature increased or reduced the fraud score for a selected transaction.

Red signals increase the predicted fraud risk, while blue signals reduce it.

![Individual Fraud Alert Explanation](images/individual_fraud_explanation.png)

## Technology Stack

### Data Engineering

- Python
- PySpark
- Pandas
- NumPy
- Bronze–Silver–Gold architecture

### Machine Learning

- XGBoost
- Scikit-learn
- Class-weighted training
- Decision-threshold optimization

### Explainable and Generative AI

- SHAP
- Qwen
- Hugging Face Transformers
- Automated AI guardrails

### Application

- Gradio
- Google Colab
- Google Drive
- GitHub

## Repository Structure

```text
ai-fraud-investigation-system/
├── 01_Fraud_Data_Pipeline.ipynb
├── 02_Fraud_Model.ipynb
├── requirements.txt
├── images/
│   ├── application_high_risk.png
│   ├── global_shap_importance.png
│   └── individual_fraud_explanation.png
└── README.md
```

## Running the Project

1. Open `01_Fraud_Data_Pipeline.ipynb` in Google Colab.
2. Run all cells to create the processed data layers.
3. Open and run `02_Fraud_Model.ipynb`.
4. Select a T4 GPU before loading the Qwen model.
5. Run the Gradio application cell.
6. Select a transaction and click **Analyze transaction**.

## Responsible Use

This educational portfolio project uses anonymized transaction data.

The generated fraud probability supports investigation prioritization but does not independently prove that a transaction is fraudulent. Final decisions should include human review and appropriate organizational controls.

## Author

**Shilpa Siddharaju**  
M.Sc. Data Science  
Berlin, Germany

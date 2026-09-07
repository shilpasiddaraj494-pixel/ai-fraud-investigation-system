# AI-Powered Fraud Investigation System

An end-to-end fraud investigation system combining **data engineering, machine learning, explainable AI, and generative AI**.

The system processes anonymized credit-card transactions through a PySpark pipeline, predicts fraud using XGBoost, explains individual decisions using SHAP, and generates guarded investigation reports using Qwen.

![Application Result](images/application_high_risk.png)

## Project Overview

Fraud datasets are extremely imbalanced, making accuracy an unreliable evaluation metric. This project builds a complete workflow that:

- Processes 284,807 transactions using a Bronze–Silver–Gold architecture
- Preserves all 492 confirmed fraud records
- Prevents leakage between repeated transaction signatures
- Trains a class-weighted XGBoost fraud classifier
- Selects a decision threshold based on fraud-recall requirements
- Explains predictions using global and local SHAP values
- Generates human-readable investigation reports using Qwen
- Validates AI reports with automated guardrails
- Provides an interactive Gradio investigation application

## System Architecture

```text
OpenML Dataset
      ↓
PySpark Bronze Layer
      ↓
Validation and Silver Layer
      ↓
ML-Ready Gold Layer
      ↓
XGBoost Fraud Model
      ↓
SHAP Explanations
      ↓
Qwen Investigation Report
      ↓
Automated Guardrails
      ↓
Gradio Investigation Application

# Cost-Sensitive & Explainable Fraud Detection Framework

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue)](https://www.python.org/)
[![XGBoost](https://img.shields.io/badge/XGBoost-2.0-green)](https://xgboost.readthedocs.io/)
[![SHAP](https://img.shields.io/badge/SHAP-0.46-orange)](https://shap.readthedocs.io/)

**MSc Data Science Thesis Project** - Addresses class imbalance, asymmetric misclassification costs, and explainability in fraud detection.

## 🎯 Problem Statement

Traditional ML models optimize **accuracy** but fail in fraud detection because:
- **99%+ legitimate transactions** (extreme class imbalance)
- **Missing fraud = 100x costlier** than false positives
- **Black-box models** lack regulatory compliance

## 🔬 Core Innovations

1. **Cost-Sensitive Learning** - Bayes Minimum Risk with transaction-specific cost matrix
2. **SHAP Explainability** - Global + local feature importance for every prediction
3. **Imbalance Handling** - SMOTE + class weights
4. **Production Metrics** - Financial savings, not just F1-score

## 🛠 Tech Stack
ML Models: Logistic Regression, SVM-RBF, XGBoost
Explainability: SHAP (KernelExplainer)
Imbalance: SMOTE, class_weight='balanced'
Metrics: Precision-Recall AUC, Cost Matrix Savings
Data: Credit card fraud dataset (284k transactions)

## 📊 Key Results (Expected)

| Model | F1-Score | PR-AUC | Financial Savings |
|-------|----------|--------|------------------|
| Baseline XGBoost | 0.82 | 0.91 | - |
| Cost-Sensitive | **0.89** | **0.95** | **+23%** |
| + SHAP Feedback | **0.92** | **0.97** | **+31%** |

## 🚀 Quick Start

bash
pip install -r requirements.txt
jupyter notebook fraud_detection_pipeline.ipynb

Sample SHAP Visualization
<img width="1185" height="1048" alt="shap_bar" src="https://github.com/user-attachments/assets/fadf34d8-24e6-4c79-8d78-213f87e70d84" />

Most important features:

Transaction amount ratio

Time since last transaction

Merchant risk score

Geographic anomaly

🎓 Research Context
MSc Thesis - Symbiosis Skills University, 2024
Focus: Production-ready fraud detection combining cost-awareness, explainability, and human-in-the-loop learning

📄 Publications
Thesis synopsis & literature review available in repo

Targets: IEEE Access, Expert Systems with Applications

🤝 Contributing
1. Fork the repo
2. Create feature branch (`git checkout -b feature/cost-matrix`)
3. Commit changes (`git commit -m 'Add cost matrix visualization'`)
4. Push to branch (`git push origin feature/cost-matrix`)
5. Open Pull Request


📞 Contact
Garima Yadav - MSc Data Science | Fraud Detection & Explainable AI

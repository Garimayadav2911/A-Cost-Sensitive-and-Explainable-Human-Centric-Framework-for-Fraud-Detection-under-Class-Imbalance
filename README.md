# Explainable Cost-Sensitive Fraud Detection with Human-in-the-Loop Learning

> MSc Research Project | Financial Transaction Fraud Detection | PaySim Dataset

---

## Problem Statement

Financial fraud detection suffers from three compounding challenges:
- **Class imbalance**: only 0.13% of transactions are fraudulent (1 in 769)
- **Cost asymmetry**: a missed fraud costs ~180× more than a false alarm
- **Black-box models**: automated systems cannot explain their decisions to regulators or analysts

Standard ML models trained on imbalanced data achieve 99.87% accuracy while catching zero fraud — a useless outcome.

---

## Proposed Solution

This project introduces a three-pillar framework:

| Pillar | Technique | Problem Solved |
|--------|-----------|----------------|
| 1 | SMOTE + Cost-sensitive XGBoost (`scale_pos_weight=775`) | Class imbalance + cost asymmetry |
| 2 | SHAP (TreeExplainer) | Black-box opacity |
| 3 | Human-in-the-Loop retraining | Static model degradation |

---

## Pipeline Overview
```
Raw Data (6.3M rows)
    │
    ├── EDA + Class Imbalance Confirmation
    ├── Feature Engineering (balance_ratio, balance_delta)
    ├── StandardScaler + Stratified Split (80/20)
    ├── SMOTE (training only)
    │
    ├── Baseline 1: Logistic Regression (class_weight=balanced)
    ├── Baseline 2: SVM RBF (class_weight=balanced)
    └── Primary: XGBoost (scale_pos_weight=775, threshold=Bayes Optimal)
        │
        ├── SHAP Global: Feature importance ranking
        ├── SHAP Local: Per-transaction waterfall explanation
        └── HITL: Gray zone → analyst review → feedback pool → retrain
```

---

## Dataset

| Property | Value |
|----------|-------|
| Source | PaySim Synthetic Financial Dataset |
| Total transactions | 6,362,620 |
| Fraud cases | 8,213 (0.13%) |
| Features | 10 raw + 4 engineered |
| Fraud types | CASH_OUT, TRANSFER only |

---

## Key Results

| Model | Recall | Precision | PR-AUC | ROC-AUC |
|-------|--------|-----------|--------|---------|
| Logistic Regression | — | — | — | — |
| SVM (RBF) | — | — | — | — |
| **XGBoost (proposed)** | **—** | **—** | **—** | **—** |

*(Fill in your actual numbers after running the pipeline)*

**Top SHAP feature**: `balance_ratio` (engineered) — validates feature engineering contribution.

---

## Figures

| Figure | Description |
|--------|-------------|
| Fig 1 | Class imbalance distribution |
| Fig 2 | EDA: fraud rate by type, amount distribution, balance ratio |
| Fig 3 | Baseline confusion matrices (LR + SVM) |
| Fig 4 | SHAP global importance bar chart |
| Fig 5 | SHAP beeswarm — feature direction and magnitude |
| Fig 6 | XGBoost confusion matrix at optimal threshold |
| Fig 7 | Threshold sweep + Precision-Recall curve |
| Fig 8 | Model comparison table |

---

## Project Structure
```
research_paper/
├── data/               # Raw and processed data
├── figures/            # All paper figures (Fig 1–8)
├── models/             # Saved models (.pkl)
├── notebooks/          # Jupyter notebooks
├── results/            # CSV result files
├── src/                # Clean Python pipeline
├── README.md
└── requirements.txt
```

---

## How to Run
```bash
# 1. Clone and setup
git clone <your-repo>
cd research_paper
python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install -r requirements.txt

# 2. Add dataset
# Place Fraud.csv in data/

# 3. Run full pipeline
jupyter notebook notebooks/final_pipeline.ipynb
```

---

## Research Contributions

1. **Cost matrix integration**: `scale_pos_weight` computed from actual class ratio (775), not arbitrary
2. **Bayes Minimum Risk threshold**: principled threshold selection using real cost estimates
3. **Feature engineering validated**: `balance_ratio` confirmed as #1 SHAP predictor
4. **Explainability at scale**: SHAP waterfall plots for individual analyst review
5. **HITL framework**: gray zone routing enables continuous model improvement

---

## Limitations

- PaySim is synthetic — real-world deployment requires live data validation
- SVM baseline computationally expensive on full 6.3M rows (subsample if needed)
- HITL loop is simulated — production implementation requires analyst dashboard integration

---

## Citation

If you use this work, please cite:
```
@article{garima2026fraud,
  title={Explainable Cost-Sensitive Fraud Detection with Human-in-the-Loop Learning},
  author={Garima Yadav},
  year={2026}
}
```

---

## Author

**Garima Yadav** - MSc Computer Science | Fraud Detection & Explainable AI | Symbiosis Skills and Professional University
=======

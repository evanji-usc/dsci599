# dsci599
# 🛡️ DDoS Detection Using Machine Learning

This project explores machine learning approaches for detecting Distributed Denial of Service (DDoS) attacks using NetFlow-based features from real-world network traffic. The focus is on evaluating and comparing different models — including Logistic Regression, Random Forest, LightGBM, and XGBoost — across various feature subsets and configurations.

---

## 📁 What the Project Does

This project performs:

- **Preprocessing & Cleaning** of NetFlow traffic logs
- **Label encoding** for binary classification (Normal = 0, DDoS = 1)
- **Model training and evaluation** using:
  - Logistic Regression
  - Random Forest
  - LightGBM
  - XGBoost
- **Incremental feature analysis**:
  - Training models with increasing numbers of features (1 to n)
- **Feature selection using RFE**:
  - Recursive Feature Elimination with Logistic Regression and Random Forest
- **Benchmarking**:
  - Accuracy, F1 Score, Precision, Recall
  - Confusion matrix (TP, TN, FP, FN)
  - Training and inference time per configuration
- **Visualization**:
  - Accuracy vs. Number of Features
  - Training Time vs. Number of Features
  - Model-to-model comparisons (LogReg vs RF vs XGB vs LGBM)

---

## 📊 Dataset Description

The dataset consists of flow-level records derived from real network traffic, including both **benign traffic** and **labeled DDoS attacks**.

### ✅ Feature Types

- **NetFlow Core Features**:
  - `Flow Duration`, `Tot Fwd Pkts`, `Tot Bwd Pkts`, `TotLen Fwd Pkts`, etc.
  - Directional packet length stats
  - Byte and packet rates

- **NetFlow Extended Features**:
  - Inter-arrival time statistics
  - TCP flag counts (e.g., `FIN`, `SYN`, `ACK`, `URG`)
  - Window sizes, segment sizes, burst behavior
  - Active/idle flow timers

- **Target**: `Label`
  - Categorical: `DDoS` or `BENIGN`
  - Converted to binary: `1` for DDoS, `0` for normal

---

## 🔬 Models and Techniques

| Model              | Use Case                              |
|-------------------|----------------------------------------|
| Logistic Regression | Baseline linear model                |
| Random Forest       | Nonlinear model + built-in feature importance |
| LightGBM            | Gradient boosting, fast, efficient    |
| XGBoost             | Robust boosting, widely used in comps |
| RFE (Recursive Feature Elimination) | Feature selection via model importance |

---

## 📈 Outputs

Each model logs:

- **Num_Features**: Number of features used
- **Sample_Size**: Rows used for training
- **Train / Test Time**
- **Accuracy, Precision, Recall, F1 Score**
- **Confusion Matrix**
- **Selected Features** (for RFE)

All metrics are saved to CSVs for further plotting and comparison.

---

## 📊 Visualizations

- Accuracy vs Number of Features (by model)
- Training Time comparisons
- LightGBM vs XGBoost accuracy differences
- NetFlow vs NetFlow-Extended feature comparison
- Top configuration summary (highest accuracy per model)

---

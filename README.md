# 📉 Customer Churn Prediction using Machine Learning

> Predicting which telecom customers are likely to leave — before they do.

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?style=for-the-badge&logo=numpy&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-11557C?style=for-the-badge&logo=python&logoColor=white)
![Seaborn](https://img.shields.io/badge/Seaborn-4C72B0?style=for-the-badge&logo=python&logoColor=white)

---

## 📌 Project Overview

Customer churn — when a customer stops using a service — is one of the biggest challenges in the telecom industry. Acquiring a new customer costs 5–7x more than retaining an existing one.

This project builds a **Machine Learning model** that predicts which customers are at risk of churning, using the Telco Customer Churn dataset. The goal is to give businesses actionable insights to act **before** a customer leaves.

---

## 📁 Dataset

| Property | Details |
|---|---|
| Source | [Telco Customer Churn — Kaggle](https://www.kaggle.com/datasets/blastchar/telco-customer-churn) |
| Rows | 7,043 customers |
| Columns | 21 features |
| Target | `Churn` (Yes / No) |

**Key features include:** tenure, MonthlyCharges, TotalCharges, Contract type, PaymentMethod, InternetService, and more.

---

## 🛠️ Tech Stack

| Category | Tools |
|---|---|
| Language | Python 3 |
| Data Manipulation | Pandas, NumPy |
| Visualization | Matplotlib, Seaborn |
| Machine Learning | Scikit-learn |
| Models Used | Logistic Regression, Random Forest |
| Environment | Jupyter Notebook |

---

## 🔄 Project Workflow

```
Raw Data
   ↓
Data Cleaning & Type Conversion
   ↓
Exploratory Data Analysis (EDA)
   ↓
Feature Engineering & Encoding
   ↓
Feature Scaling (StandardScaler)
   ↓
Train / Test Split (80/20)
   ↓
Model Training (LR + Random Forest)
   ↓
Model Evaluation
   ↓
Feature Importance Analysis
   ↓
Business Insights
```

---

## 🧹 Data Cleaning

- `TotalCharges` was stored as **text** → converted to numeric using `pd.to_numeric(errors='coerce')`
- **11 null values** created after conversion → filled with **median** (robust to outliers)
- `customerID` dropped — purely an identifier with zero predictive value
- `Churn` column encoded: `Yes → 1`, `No → 0`
- All remaining categorical columns encoded using **LabelEncoder**

---

## 📊 Exploratory Data Analysis (EDA)

Four key visualizations were created to understand churn patterns:

### 1. Churn Distribution
Overall churn rate is ~26% — a moderately imbalanced dataset.

### 2. Tenure vs Churn
Customers with **low tenure (< 12 months)** churn at a significantly higher rate than long-term customers.

### 3. Monthly Charges vs Churn
Churned customers have **higher average monthly charges** — high billing = high churn risk.

### 4. Contract Type vs Churn
**Month-to-month** contract customers churn the most. Two-year contract customers are the most loyal.

---

## ⚙️ Feature Engineering

| Step | Action |
|---|---|
| Fix data types | Convert TotalCharges to float |
| Handle nulls | Fill 11 missing values with median |
| Remove noise | Drop customerID column |
| Encode target | Map Churn Yes/No → 1/0 |
| Encode features | LabelEncode all object columns |
| Scale features | StandardScaler (fit on train only) |
| Split data | 80% train / 20% test with `stratify=y` |

> ⚠️ **Important:** StandardScaler was fit **only on training data** to prevent data leakage. The same scaler was then applied (transform only) to test data.

---

## 🤖 Models Trained

### 1. Logistic Regression
- Simple, interpretable linear model
- Good baseline for binary classification

### 2. Random Forest Classifier
- Ensemble of 100 decision trees
- Captures non-linear patterns
- Provides feature importance scores

---

## 📈 Model Results

| Model | Accuracy | F1-Score |
|---|---|---|
| Logistic Regression | ~80% | ~0.76 |
| **Random Forest** | **~82%** | **~0.78** ✅ |

> Random Forest outperformed Logistic Regression on both Accuracy and F1-score.

**Evaluation metrics used:**
- Accuracy Score
- Precision, Recall, F1-Score
- Confusion Matrix
- Classification Report

---

## 🏆 Feature Importance (Top 5)

| Rank | Feature | Importance |
|---|---|---|
| 1 | tenure | ████████████ Highest |
| 2 | MonthlyCharges | █████████ High |
| 3 | Contract | ███████ Medium |
| 4 | TotalCharges | █████ Medium |
| 5 | InternetService | ███ Lower |

---

## 💡 Key Business Insights

- 🔴 **New customers churn the most** — customers in their first 12 months need more attention and onboarding support
- 🔴 **High monthly charges = high churn risk** — pricing strategy directly impacts retention
- 🔴 **Month-to-month contracts** have the highest churn — incentivizing longer contracts could significantly reduce churn
- 🟢 **Long-tenure customers are loyal** — reward programs for 2+ year customers can further strengthen retention

---

## 📂 Project Structure

```
customer-churn-prediction/
│
├── customer_churn_prediction.py   # Main project code
├── Telco-Customer-Churn.csv       # Dataset (download from Kaggle)
└── README.md                      # Project documentation
```

---

## ▶️ How to Run

**1. Clone the repository**
```bash
git clone https://github.com/ramyakeerthijiguru01-code/customer-churn-prediction.git
cd customer-churn-prediction
```

**2. Install required libraries**
```bash
pip install pandas numpy matplotlib seaborn scikit-learn
```

**3. Download the dataset**

Download `Telco-Customer-Churn.csv` from [Kaggle](https://www.kaggle.com/datasets/blastchar/telco-customer-churn) and place it in the project folder.

**4. Run the script**
```bash
python customer_churn_prediction.py
```

---

## 🔮 Future Improvements

- [ ] Handle class imbalance using SMOTE or class weights
- [ ] Tune hyperparameters using GridSearchCV
- [ ] Try XGBoost / LightGBM for better performance
- [ ] Build an interactive dashboard using Streamlit
- [ ] Deploy the model as a REST API using Flask

---

## 🤝 Connect with Me

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/[your-linkedin-username])
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/ramyakeerthijiguru01-code)

---

<p align="center">⭐ If you found this project helpful, please give it a star! ⭐</p>

# 🛡️ Fraud Detection and Credit Risk Modeling Project

## 📌 Project Overview
This project focuses on identifying fraudulent transactions and assessing credit risk using machine learning and deep learning techniques. It involves:
- Preprocessing and merging multiple datasets.
- Building interpretable classification models.
- Applying explainability techniques (SHAP & LIME).
- Deploying predictive models via an API.

The ultimate goal is to create robust, explainable systems that detect fraud and analyze transaction behavior in both traditional and credit card data.

---

## 📂 Datasets Used

### 1. `Fraud_Data.csv`
Contains detailed transaction info:
- `user_id`, `signup_time`, `purchase_time`, `purchase_value`, `device_id`, `source`, `browser`, `sex`, `age`, `ip_address`, and `class` (fraud indicator).

### 2. `Credit_Card_Transactions.csv`
An anonymized dataset:
- Features: `v1` to `v8`, `Time`, `amount`, and `Class` (fraud indicator).

### 3. `IpAddress_to_Country.csv`
Maps IP addresses to countries:
- `lower_bound_ip_address`, `upper_bound_ip_address`, `country`.

---

## 🧹 Task 1: Data Analysis and Preprocessing

### ✅ Data Cleaning
- Removed duplicates and corrected data types.
- Handled missing values via imputation or removal.

### 📊 Exploratory Data Analysis (EDA)
- Univariate and bivariate analysis to detect trends.
- Visualized class imbalance, temporal fraud patterns, and feature correlations.

### 🌍 Geolocation Mapping
- Converted IP addresses to integers.
- Merged `Fraud_Data.csv` with `IpAddress_to_Country.csv` to analyze country-level fraud patterns.

### 🏗️ Feature Engineering
- **Time-Based**:
  - `hour_of_day`, `day_of_week`, `time_since_signup`
- **Behavioral**:
  - Transaction frequency and velocity

### 🔁 Data Transformation
- Addressed **class imbalance** with SMOTE and Random Undersampling.
- Scaled numerical features using `StandardScaler`.
- Applied One-Hot Encoding to categorical features.

---

## 🤖 Task 2: Model Building and Training

### ⚙️ Data Preparation
- Separated features and labels (`class` / `Class`).
- Applied train-test split strategy with stratification.

### 📌 Models Built
1. **Logistic Regression** (Baseline)
2. **Ensemble Model** (XGBoost / Random Forest)

### 📈 Evaluation Metrics
- **F1 Score**
- **Confusion Matrix**
- **AUC-PR (Precision-Recall)**
  
**Best Model Justification**: Based on F1 Score and PR AUC on imbalanced test sets.

---

## 🧠 Task 3: Model Explainability

### 🔍 SHAP (Shapley Additive exPlanations)
- Used `TreeExplainer` and `KernelExplainer` on traditional and deep models.
- Summary plots reveal global feature importance.
- Force plots used for local, instance-level interpretation.

### 🌈 LIME (Local Interpretable Model-Agnostic Explanations)
- Explained predictions on individual transactions.
- Demonstrated how specific feature values influence fraud classification.

---

## 🔌 Model Deployment

### Flask API + Docker

#### Model API Supports:
- ✅ **Fraud Detection Model** (Decision Tree)
- ✅ **Credit Card Detection Model** (RNN)

### Project Structure:

## Project Structure
```
fraud-detection-project/
│
├── .github/workflows/
│   └── unittests.yml
│
├── .vscode/
│   └── settings.json
│
├── ceaned_data/
│   ├── preprocessed_Fraud_Data.csv
│   ├── merged_data.csv
│   ├── preprocessed_Credit_Card_Transactions.csv
│   └── preprocessed_IpAddress_to_Country.csv
│
├── data/
│   ├── Fraud_Data.csv
│   ├── Credit_Card_Transactions.csv
│   └── IpAddress_to_Country.csv
│
├── DL_saved_models/
│
├── saved_models/
│
├── notebooks/
│   ├── data_preprocessing.ipynb
│   ├── ML_model_creaditcard_data.ipynb
│   ├── ML_model_fraud_data.ipynb
│   ├── model_Building_Training.ipynb   // DL models for both credit and fraud data
│   └── __init__.py
│
├── scripts/
│   └── __init__.py
|
├── src/
│   └── __init__.py
│
├── test/
│   └── __init__.py
│
├── .gitignore
├── requirements.txt
└── README.md
```


---

## 🚀 Getting Started

### Prerequisites
- Python 3.8+
- Libraries listed in `requirements.txt`

### Installation
```
git clone https://github.com/YourUsername/Fraud_Detection_Project.git
cd Fraud_Detection_Project

# Create and activate virtual environment
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

Running Jupyter Notebooks
jupyter notebook

Launching Flask API

cd model_api
python serve_model.py
```
---

##  📊 Results and Insights
- Identified key drivers of fraud:

- Signup-purchase time gap

- Device/browser usage

- Transaction timing (odd hours)

- SHAP revealed model bias toward certain time and value patterns.

- Ensemble models outperformed logistic regression on both datasets.

## 📜 License
- This project is open-source and available under the MIT License

- Let me know if you’d like the `README.md` exported as a file or customized with your GitHub repo link, author profile, or badges!

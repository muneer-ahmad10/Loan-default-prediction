# Loan-default-prediction
This project focuses on predicting whether a customer will  default on a loan using machine learning.
# 💳 Loan Default Prediction using Machine Learning

## 📌 Project Overview
This project focuses on predicting whether a customer will **default on a loan** using machine learning.

Unlike simple classification problems, this project highlights a **real-world challenge**:
👉 **Imbalanced data and cost-sensitive decision making**

The goal is not just accuracy, but to build a model that can **effectively identify high-risk customers**.

---

## 🎯 Objective
To develop a predictive model that:
- Identifies potential defaulters (high-risk customers)
- Minimizes financial risk for lending institutions
- Balances recall and precision for better decision-making

---

## 📂 Dataset Description

- Total Records: **255,347**
- Features: **18**

### Key Features:
- `Age`
- `Income`
- `LoanAmount`
- `CreditScore`
- `DTIRatio` (Debt-to-Income Ratio)
- `EmploymentType`
- `Education`
- `LoanPurpose`
- Target → `Default (0 = No, 1 = Yes)`

---

## ⚠️ Problem: Imbalanced Dataset

| Class | Count | Percentage |
|------|------|-----------|
| Non-default (0) | 225,694 | ~88% |
| Default (1) | 29,653 | ~12% |

👉 A naive model could achieve **88% accuracy** by predicting all customers as non-defaulters.

👉 Therefore, **accuracy is NOT a reliable metric**.

---

## 📊 Exploratory Data Analysis (EDA)

### Key Insights:

- 📉 **Credit Score**: Defaulters tend to have lower scores  
- 💰 **Income**: Lower income → higher default risk  
- 💸 **Loan Amount**: Higher loans → increased risk  
- 📊 **DTI Ratio**: Strongest indicator of default  
- 👨‍💼 **Employment Type**: Unemployed/part-time → higher default rate  
- 🎓 **Education**: Lower education levels show slightly higher risk  

👉 Insight:
**Financial stress indicators (DTI, income, loan size) are more important than demographics**

---

## 🧹 Data Preprocessing

- Dropped identifier column (`LoanID`)
- Applied **One-Hot Encoding** on categorical variables
- Performed **feature scaling** using StandardScaler
- Split data into **train and test sets**

---

## 🤖 Models Implemented

### 1️⃣ Logistic Regression (Baseline)

- Used `class_weight='balanced'` to handle imbalance

#### Results:
- Recall (Default): **0.70** ✅  
- Precision: **0.22** ⚠️  
- Accuracy: **0.68** ❌  

👉 Insight:
- Good at catching defaulters  
- Generates many false positives  

---

### 2️⃣ Random Forest (Without Handling Imbalance)

#### Results:
- Recall: **0.01** ❌  
- Accuracy: **0.89** ❌ (misleading)

👉 Insight:
- Model predicts almost all customers as non-defaulters  
- Completely fails to identify risky customers  

---

## ⚠️ Key Learning

👉 High accuracy ≠ Good model  
👉 Always evaluate using:
- Recall  
- Precision  
- F1-score  

---

## 🔄 Handling Imbalance using SMOTE

Applied **SMOTE (Synthetic Minority Oversampling Technique)**:

- Balances dataset by generating synthetic samples of minority class
- Applied only on training data

---

## ⚙️ Hyperparameter Tuning

Used **GridSearchCV** with:
- Cross-validation = 3
- Scoring = `f1` (to balance precision & recall)

### Parameters Tuned:
- `max_depth`
- `min_samples_split`
- `min_samples_leaf`
- `n_estimators`

---

## 📊 Final Model: Random Forest (SMOTE + Tuning)

### Results:

- Recall (Default): **0.55** ✅  
- Precision: **0.22** ⚠️  
- F1-score: **0.32**  
- Accuracy: **0.73** ❌  

---

## 🧠 Final Insights

- Logistic Regression → better recall (aggressive detection)  
- Random Forest → more stable and balanced  

👉 Trade-off:
- Higher recall → more false positives  
- Higher precision → more missed defaulters  

---

## 💡 Key Takeaways

- Imbalanced datasets require **special handling (SMOTE, class weights)**  
- Accuracy is misleading in real-world classification problems  
- Feature engineering and EDA are more important than model complexity  
- Model selection depends on **business objectives**

---

## 🛠️ Tech Stack

- Python  
- Pandas, NumPy  
- Scikit-learn  
- Imbalanced-learn (SMOTE)  
- Matplotlib, Seaborn  

---

## 🚀 Future Improvements

- Threshold tuning for better precision-recall balance  
- Advanced models (XGBoost, LightGBM)  
- Cost-sensitive learning  
- Feature importance analysis  

---

## 📌 Conclusion

This project demonstrates that:

👉 **In real-world ML problems, understanding the data and evaluation metrics is more important than achieving high accuracy.**

👉 A good model is one that aligns with **business impact, not just numbers**.

---

## 📬 Connect

If you found this project useful or have suggestions, feel free to connect!

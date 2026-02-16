# 🫀 Heart Disease Prediction – End-to-End Machine Learning Project

This project focuses on predicting the presence of heart disease using classical machine learning models. The goal was not just to build a model, but to deeply understand the **data, assumptions, and reasoning behind each step** in the pipeline.

---

## 🚀 Problem Statement
Early detection of heart disease can help in timely treatment and reduce mortality.  
This project aims to build a reliable classification model with **high recall**, prioritizing minimizing false negatives (i.e., not missing patients at risk).

---

## 📊 Dataset
The dataset contains clinical and diagnostic features such as:
- age : Age in years : Continuous
- sex : 1 = male, 0 = female : Binary
- cp : Chest pain type (0–3) : Categorical
- trestbps : Resting blood pressure : Continuous
- chol : Serum cholesterol : Continuous
- fbs : Fasting blood sugar >120 : Binary
- restecg : Resting ECG results : Categorical
- thalach : Max heart rate achieved : Continuous
- exang : Exercise-induced angina : Binary
- oldpeak : ST depression : Continuous
- slope : ST segment slope : Ordinal
- ca : Major vessels colored : Discrete
- thal : Thalassemia : Categorical
- target : Heart disease (1/0) : Binary
---

## 🔍 Data Cleaning

Key observations:
- Found **700+ duplicate samples**, which were removed to prevent model bias and leakage.
- This significantly improved data quality and reliability of results.

---

## 📈 Exploratory Data Analysis (EDA)

EDA was performed to understand the **structure, signal, and separability** of the data.

### ✔ Target imbalance check
- Checked class distribution to understand the baseline.

### ✔ Feature understanding
- Studied clinical meaning of each feature to avoid blind modeling.

### ✔ Univariate analysis
- Continuous and categorical features analyzed separately.

### ✔ Boxplots with target
Key insight:
- Features like **Age, Thalach, and Oldpeak** showed strong interaction and potential separation.

### ✔ KDE plots
- Used to observe distribution and class separation signals.

### ✔ Feature interaction plots
- Interaction between Age, Thalach, and Oldpeak revealed clear patterns.

### ✔ Countplots for categorical features
- Helped identify categories with higher heart disease risk.

### ✔ Multicollinearity check
- Checked correlation between continuous and ordinal features.
- Found minimal collinearity.

### ✔ Discretization experiment
- Continuous features were binned to observe trends with target.
- Most features showed **linear trends**, indicating:
  > Logistic Regression and LDA could perform well due to linear separability.

---

## ⚙️ Preprocessing

- Train-test split (90–10) with validation set held out.
- Focused on preventing **data leakage**.
- Used pipelines to avoid scaling before cross-validation.

⚠️ **Important learning:**  
Scaling data before cross-validation causes leakage and leads to overly optimistic results.

---

## 🎯 Evaluation Metric

The chosen metric was:
> **Recall**

Reason:
- In medical prediction, missing a patient with disease is more dangerous than false positives.

---

## 🤖 Baseline Models

Used cross-validation to understand model behavior:

| Model | Insight |
|------|------|
| Logistic Regression | Strong performance → Data has linear structure |
| LDA | Strong performance → Clear class separation |
| Decision Tree | Overfitting |
| Random Forest | Overfitting |
| KNN | High variance → Sensitive to data |

Key conclusion:
> The dataset has a relatively **simple and linearly separable structure**.

---

## 🔧 Hyperparameter Tuning

Top models selected:
- Logistic Regression
- Linear Discriminant Analysis (LDA)

Used **GridSearchCV** for tuning.

---

## 📊 Final Results

| Model | Recall |
|------|------|
| LDA | **0.89** |
| Logistic Regression | 0.88 |

---

## 📉 Validation

- Evaluated on unseen validation data.
- Confusion matrix used to interpret performance.

---

## 🧠 Final Model

LDA with best parameters trained on the full dataset.

---

## 💡 Key Learnings

- Importance of removing duplicates in medical datasets.
- How EDA guides model selection.
- Understanding linear separability in real-world datasets.
- Preventing data leakage using pipelines.
- Choosing the right metric based on the business problem.
- Model interpretation matters more than chasing accuracy.

---

## ❌ Mistakes Made (and Lessons)

- Initially scaled data before cross-validation → led to leakage.
- Over-trusted tree models before understanding data structure.
- Underestimated importance of feature interaction.

---

## 📌 Future Improvements

- Model explainability (SHAP, LIME).
- Feature engineering using domain knowledge.
- Ensemble models with regularization.
- Calibration of probability scores.
- Deployment using Flask or FastAPI.

---

## 🛠️ Tech Stack

- Python
- Scikit-learn
- Pandas
- NumPy
- Matplotlib
- Seaborn

---

## 📎 How to Run

```bash
git clone <repo-link>
cd heart-disease-prediction
pip install -r requirements.txt
python main.py

# UCI-student-performance-predictor

# 🎓 Student Performance Predictor

This project aims to predict students' final grades (G3) using demographic, academic, and behavioral data. It applies end-to-end machine learning techniques, from data preprocessing and exploratory data analysis (EDA) to model building, evaluation, tuning, and explainability.

## 🔍 Problem Statement

Predict the academic performance of students to:
- Identify at-risk students early
- Understand which factors most influence grades
- Support targeted interventions by schools or educators

Dataset Source: [UCI Student Performance Dataset](https://archive.ics.uci.edu/ml/datasets/Student+Performance)

## 📁 Dataset Overview

I used two datasets:
- `student-mat.csv` (Math course)
- `student-por.csv` (Portuguese course)

Both were merged on 13 common features such as `school`, `sex`, `age`, `famsize`, `Medu`, etc.  
Total after merge: **382 students**, **53 features**

## ⚙️ Tools & Technologies

- **Python** (pandas, numpy, matplotlib, seaborn)
- **Scikit-learn** (LinearRegression, DecisionTree, RandomForest, GridSearchCV)
- **XGBoost**
- **SHAP** (SHapley Additive exPlanations for model interpretability)
- **Jupyter Notebook** for iterative analysis and visualization

## 🔬 ML Workflow

### 1. 📊 Exploratory Data Analysis (EDA)
- Studied relationships between `studytime`, `failures`, `alcohol use`, `parental education`, etc. with final grade `G3`
- Correlation heatmap used to select informative features

### 2. 🧹 Data Preprocessing
- One-hot encoding for categorical features
- No missing values in dataset
- Created two setups:
  - With `G1`, `G2` (prior grades)
  - Without `G1`, `G2` (to simulate prediction before exams)

### 3. 🤖 Model Building( Comparision)
| Model             | G1/G2 Used | MAE  | RMSE |
|------------------|------------|------|------|
| Linear Regression | ✅         | 1.44 | 2.17 |
| Decision Tree     | ✅         | 0.89 | 1.44 |
| Linear Regression | ❌         | 5.09 | 6.68 |
| Decision Tree     | ❌         | 3.86 | 5.16 |
| Random Forest     | ❌         | 3.38 | 4.44 |
| XGBoost           | ❌         | 3.62 | 4.69 |

> Best model: **Random Forest (No G1/G2)**  
> Tuned using **GridSearchCV** for `max_depth`, `n_estimators`, and `min_samples_split`

### 4. 📈 Evaluation Metrics
- **MAE (Mean Absolute Error)**: average prediction error
- **RMSE (Root Mean Squared Error)**: penalizes large errors more

### 5. 🧠 Model Interpretability (SHAP)
Used SHAP to interpret feature importance and individual predictions:
- **Global insights**: `failures`, `romantic relationship`, `Walc` (weekend alcohol), `Medu`, `age` were most influential
- **Force plots**: visualized how each feature pushed a prediction up or down
- **Decision plots**: showed cumulative decision path of model per student

## 📌 Key Learnings

- Predicting student grades without prior performance (G1/G2) is harder but feasible
- Behavioral and demographic factors (like alcohol use and family support) play a strong role
- SHAP provides powerful tools to make black-box models interpretable

## ✅ Next Steps (Optional Ideas)

- Try classification instead of regression (e.g., pass/fail)
- Add external features (e.g., school funding, teacher ratio)
- Build a Streamlit app to allow educators to input student info and get predictions

--------------------

## 💡 Conclusion

This project demonstrates a full ML workflow, from feature engineering to model interpretability. It balances performance and explainability, showing how data science can support decision-making in education.



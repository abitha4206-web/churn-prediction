# Churn-prediction

##  Introduction
Customer retention is crucial for financial institutions and businesses aiming to maximize lifetime customer value and reduce acquisition costs. This project focuses on building a machine learning model to predict customer churn (`Attrition_Flag`) using credit card customer demographics, account behavior, and transaction history. 

By identifying high-risk customers early, businesses can proactively introduce targeted retention strategies to improve customer loyalty.

---

##  Data Overview
The dataset contains transaction records and demographic details for bank credit card holders.

* **Total Records:** 10,127
* **Total Features:** 21 (1 Target Variable + 20 Predictor Features)
* **Data Quality:** Clean dataset with **0 missing values** and **0 duplicate entries**.
* **Target Variable:** `Attrition_Flag`
  * `Existing Customer` – Retained customer
  * `Attrited Customer` – Churned customer

### Feature Categories
* **Categorical Features (10):** `Attrition_Flag`, `Gender`, `Education_Level`, `Marital_Status`, `Income_Category`, `Card_Category`, `Total_Relationship_Count`, `Months_Inactive_12_mon`, `Contacts_Count_12_mon`, `Dependent_count`
* **Numerical Features (10):** `Customer_Age`, `Months_on_book`, `Credit_Limit`, `Total_Revolving_Bal`, `Avg_Open_To_Buy`, `Total_Amt_Chng_Q4_Q1`, `Total_Trans_Amt`, `Total_Trans_Ct`, `Total_Ct_Chng_Q4_Q1`, `Avg_Utilization_Ratio`

##  Data Processing & Exploratory Analysis
The data pipeline and exploratory phases include the following key steps:

1. **Data Inspection & Integrity Check:** 
   * Validated data types, dataset dimensions, missing values, and duplicate records.
2. **Exploratory Data Analysis (EDA):**
   * **Univariate Categorical Analysis:** Analyzed frequency distributions for demographic and behavioral categorical features against the target variable (`Attrition_Flag`).
   * **Univariate Numerical Analysis:** Inspected distributions, skewness, and outliers across numerical metrics like `Credit_Limit` and `Total_Trans_Amt`.
3. **Planned Preprocessing Steps:**
   * Encoding target variables (`Existing Customer` → `0`, `Attrited Customer` → `1`).
   * Applying One-Hot/Label Encoding for predictor categorical variables.
   * Feature scaling numerical inputs using `StandardScaler` prior to model development.
  
##  Model Building & Evaluation

To accurately predict customer churn, multiple classification algorithms are trained and evaluated on preprocessed customer data.

### 1. Algorithms Evaluated
* **Baseline Model:** Logistic Regression
* **Tree-based Models:** Decision Tree Classifier, Random Forest Classifier
* **Boosting Models:** XGBoost / Gradient Boosting Classifier

### 2. Evaluation Metrics
Given that customer churn datasets typically suffer from class imbalance (fewer attrited customers than active ones), performance is evaluated using:
* **Precision & Recall:** To minimize false negatives (failing to identify a churning customer).
* **F1-Score:** To measure the balance between precision and recall.
* **ROC-AUC Score:** To evaluate total classification separation ability across decision thresholds.

##  Conclusion

* **Key Drivers of Churn:** Preliminary findings and feature importance scores highlight that total transaction count (`Total_Trans_Ct`), total transaction amount (`Total_Trans_Amt`), and customer engagement metrics (such as `Months_Inactive_12_mon` and `Contacts_Count_12_mon`) are strong indicators of potential customer churn.
* **Business Impact:** Implementing a proactive identification pipeline allows financial teams to intervene with personalized retention offers before high-value credit card holders cancel their services.

##  Future Enhancements

* [ ] **Hyperparameter Tuning:** Optimize model parameters using `GridSearchCV` or `RandomizedSearchCV` to boost prediction accuracy.
* [ ] **Handling Class Imbalance:** Apply advanced sampling techniques like **SMOTE** (Synthetic Minority Over-sampling Technique) or Random Under-Sampling to improve minority class recall.
* [ ] **Deployment:** Package the final model into a lightweight web API using **Flask** or **FastAPI**, and deploy an interactive dashboard using **Streamlit**.
* [ ] **Pipeline Automation:** Build a seamless `scikit-learn` pipeline for end-to-end data transformation, feature scaling, and inference.

# Employee Attrition Prediction & Analysis

This project aims to predict the likelihood of employee attrition and identify the key drivers behind employee turnover using the **IBM HR Analytics Attrition Dataset**. By applying machine learning techniques, we provide actionable insights for HR departments to improve retention strategies.

## 📊 Project Overview
Employee turnover is a costly problem for any organization. This project explores a dataset of ~1,500 employees to determine which factors (such as overtime, job role, and promotion history) contribute most to an employee deciding to leave the company.

### Final Model Performance
After evaluating multiple architectures, **Logistic Regression** was selected as the final model due to its superior ability to distinguish between classes and its high interpretability.

| Model | Precision | Recall | F1-Score | ROC-AUC | Overall Accuracy |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Logistic Regression** | **0.49** | **0.49** | **0.49** | **0.7956** | **86%** |
| Random Forest | 0.53 | 0.26 | 0.34 | 0.7663 | 87% |
| Gradient Boosting | 0.41 | 0.56 | 0.47 | 0.7539 | 83% |

---

## 🛠️ Data Preprocessing & Methodology
To ensure the models were accurate and unbiased, the following steps were taken:
1.  **Redundant Column Removal:** Dropped columns with zero variance (`EmployeeCount`, `StandardHours`, `Over18`) and unique identifiers (`EmployeeNumber`).
2.  **Categorical Encoding:** Applied **One-Hot Encoding** with `drop_first=True` to avoid the "Dummy Variable Trap" (multicollinearity), which stabilized the Logistic Regression coefficients.
3.  **Feature Scaling:** Used `StandardScaler` to normalize numerical features, ensuring that variables like `MonthlyIncome` didn't mathematically overwhelm smaller variables like `YearsAtCompany`.
4.  **Model Evaluation:** Compared Logistic Regression, Random Forest, and Gradient Boosting using ROC-AUC curves to prioritize the model's ability to rank high-risk employees correctly.

---

## 📈 Key Business Insights
*   **The Overtime Factor:** Working overtime is the #1 predictor of attrition. Employees working extra hours are significantly more likely to resign.
*   **Stagnation:** Employees who haven't been promoted in over 2 years show a sharp increase in turnover risk.
*   **Pay is not everything:** Monthly and Hourly rates had a surprisingly weak correlation with attrition compared to work-life balance factors.
*   **High-Risk Roles:** Sales Representatives and Laboratory Technicians are the most vulnerable roles within the organization.

---

## ⚠️ Limitations & Ethical Considerations
*   **Recall Gap:** The model currently has a recall of ~0.51, meaning it misses roughly half of the actual leavers. It should be used as a **supplementary risk signal**, not a definitive decision-maker.
*   **Historical Bias:** The model reflects historical trends. If specific demographics left more often in the past due to cultural issues, the model will flag them as high-risk today. HR should ensure interventions are applied equitably.
*   **Non-Causality:** The factors identified are correlations. Reducing overtime might not prevent attrition if the underlying cause is a cultural or managerial issue not captured in the data.

---

## 🔗 Dataset Source
The data used in this project is the [IBM HR Analytics Attrition Dataset](https://www.kaggle.com/datasets/pavansubhasht/ibm-hr-analytics-attrition-dataset) available on Kaggle.

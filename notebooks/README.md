
## 🔬 A/B Hypothesis Testing Methodology

In this analysis, we aim to evaluate whether certain features (such as **Province**, **Gender**, or **TrackingDevice**) are associated with **significant differences in risk or profitability**. This is done using A/B hypothesis testing — a widely used statistical method to compare two groups.

---

### ✅ Step-by-Step Process

### **1. Define Key Metrics (KPIs)**

We selected three key metrics to evaluate the performance of insurance plans:

* **Claim Frequency**:
  The proportion of policies with at least one claim.

  Claim Frequency = Policies with Claims / Total Policies

* **Claim Severity**:
  The average claim amount, conditional on a claim occurring.

  Claim Severity = Total Claims / Number of Claims

* **Margin**:
  The profit per policy.

  Margin = Total Premium - Total Claims

---

### **2. Select A and B Groups**

We identify two groups for comparison:

* **Group A (Control)**: Policies **without the feature** or from a baseline category (e.g., `Province = Gauteng`)
* **Group B (Test)**: Policies **with the feature** or from a comparison category (e.g., `Province = Western Cape`)

Example in code:

```python
group_a = df[df['Province'] == 'Gauteng']
group_b = df[df['Province'] == 'Western Cape']
```

---

### **3. Formulate Hypotheses**

For each KPI, we define null and alternative hypotheses:

* **H₀ (Null Hypothesis)**: There is **no significant difference** in the metric between the two groups.
* **H₁ (Alternative Hypothesis)**: There **is a significant difference** between the two groups.

Example:

H₀: Claim Frequency is the same in Gauteng and Western Cape
H₁: Claim Frequency differs between Gauteng and Western Cape

---

### **4. Perform Statistical Tests**

Depending on the metric:

* **Claim Frequency (proportion)**
  ➤ Use **Z-test for proportions** or **Chi-squared test**

* **Claim Severity & Margin (continuous)**
  ➤ Use **T-test** (for normally distributed data)
  ➤ Or **Mann-Whitney U test** (non-parametric)

---

### **5. Interpret Results**

* **If p-value < 0.05** → Reject the null hypothesis (significant difference)
* **If p-value ≥ 0.05** → Fail to reject the null hypothesis (no significant difference)



### **6. Feature Engineering**

Created meaningful features such as vehicle age, client segmentation based on demographics, and interaction terms between vehicle and client attributes.

Encoded categorical variables using one-hot and label encoding for model compatibility.

Engineered aggregate features like fleet size influence on claims.

### **7. Modeling Approach**

Two key predictive modeling goals were addressed:

Claim Severity Prediction (Regression):

1. Target: Predict TotalClaims amount for policies with claims.

Models: Linear Regression, Decision Trees, Random Forests, XGBoost.

Evaluation: Root Mean Squared Error (RMSE), R-squared (R²), Mean Absolute Error (MAE).

2. Premium Optimization (Regression):

Target: Predict CalculatedPremiumPerTerm reflecting fair premium pricing.

Models: Same as above.

Evaluation: RMSE, R², MAE.

Additionally, classification modeling approaches were discussed for segmenting policies into “claim” vs “no claim” groups to assist targeted marketing campaigns.

 ### **8. Model Evaluation **
Focused on regression metrics suited for continuous outcome variables.

Clarified that classification metrics such as accuracy, precision, recall, and F1-score apply only to classification tasks (e.g., predicting claim occurrence).

### **9. Model Interpretation & Explainability**
Model Interpretation & Explainability
Utilized SHAP (SHapley Additive exPlanations) to:

Provide global and local explanations of feature impact on model predictions.

Generate visualizations like summary plots and force plots for interpretability.

Introduced LIME as an alternative for local explanation of individual predictions.

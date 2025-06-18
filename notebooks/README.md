
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

We interpret whether the feature being tested (e.g., province or gender) significantly impacts **risk** or **profit**.

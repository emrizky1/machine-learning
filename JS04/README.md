### Model Performance Comparison

| Metric | Multiple Linear Regression | SVR (RBF Kernel) |
| :--- | :--- | :--- |
| **R² Score** (share of variation explained; closer to 1 is better) | ~0.78 | ~0.85 |
| **MAE** (average error in dollars; lower is better) | ~$4,180 | ~$2,800 |
| **RMSE** (like MAE, but penalizes big mistakes more; lower is better) | ~$5,750 | ~$4,700 |

SVR performs better on all three measures.

---

### Analysis and Discussion

#### 1. Limitations of Multiple Linear Regression

This model adds up the effect of each factor (age, BMI, smoking status) in a straight-line fashion, which causes three problems:

* **Struggles with high costs**: Predictions level off at around $40,000, even though some real claims reach $60,000. Costs rise much more sharply when factors combine, such as being both a smoker and having a high BMI.
* **Predictions form separate bands**: Instead of following the diagonal line (y = x), the points split into three parallel layers, one per risk group. The model makes fixed adjustments per group rather than capturing how much more expensive high-risk groups really are.
* **Negative predictions**: A few young, healthy non-smokers receive negative charges, which is impossible in real insurance billing.

#### 2. Strengths of Support Vector Regression (RBF Kernel)

SVR can capture curved, more complex relationships, not just straight-line ones:

* **Handles complex patterns**: Predictions stay close to the diagonal line (y = x), even for higher expenses.
* **Accurate for common cases**: Most records in `insurance.csv` are non-smokers with expenses under $10,000. SVR predicts this large group accurately without being thrown off by a few very expensive cases, giving lower MAE and RMSE.
* **Feature scaling is essential**: Standardizing the data with `StandardScaler` puts all values on a similar scale. Without it, large dollar amounts would overpower small 0/1 columns and stop the model from learning properly.

#### Conclusion

Multiple Linear Regression is a useful starting point, but its straight-line assumption causes it to underestimate high expenses and produce impossible negative values. SVR with an RBF kernel better captures how factors like smoking and BMI affect insurance charges, making it the stronger model for this dataset.

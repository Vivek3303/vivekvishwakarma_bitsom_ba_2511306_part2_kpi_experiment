# Hypothesis Test Notes

## 1. Test Setup
* **Metric Being Tested:** Paid Conversion Rate (`converted_to_paid`)
* **Reason for Selection:** This is the North Star metric. We must mathematically prove that the new campaign drives actual paying customers, not just vanity engagement (like landing page visits).
* **Null Hypothesis (H0):** There is no significant difference in the Paid Conversion Rate between the Control group and the Treatment group. (P_control = P_treatment)
* **Alternate Hypothesis (H1):** There is a significant difference in the Paid Conversion Rate between the Control group and the Treatment group. (P_control ≠ P_treatment)
* **Test Type:** Two-tailed test (We want to know if it's significantly better OR significantly worse).
* **Significance Level (Alpha):** 0.05 (We require 95% confidence).

## 2. Test Execution & Output
* **Tool Used:** Microsoft Excel (T.TEST function).
* **Inputs:** Array 1 (Control `converted_to_paid` binary values), Array 2 (Treatment `converted_to_paid` binary values).
* **P-Value Result:** 0.000987

## 3. Decision Rule & Business Interpretation
* **Decision Rule:** If P-value < 0.05, reject the Null Hypothesis. If P-value >= 0.05, fail to reject the Null Hypothesis.
* **Interpretation:** The P-Value is 0.000987; Therefore, we reject the Null Hypothesis. The test is statistically significant, proving that the Treatment campaign definitively drove higher conversion rates than the Control experience.

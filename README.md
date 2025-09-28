# CCAR-Aligned NII Forecasting Model with SR 15-18 Benchmarking

## Overview
This project simulates a core quantitative risk task: forecasting quarterly Net Interest Income (NII) under macroeconomic stress, adhering strictly to SR 15-18 Model Risk Management standards (Champion vs. Challenger benchmarking).

---

## 1. Key Findings & Champion Selection

The econometric model (OLS) performed poorly due to low correlation in the real FRED data, confirming the importance of benchmark testing.

| Metric | OLS (Challenger) | MA (Champion) | Winner |
| :--- | :--- | :--- | :--- |
| **RMSE** | 7067.80 | **6343.13** | **MA** |
| **MAPE** | 1.8925 | 2.1341 | OLS |

**Champion:** The **4-quarter Moving Average (MA)** model was selected due to its **lower RMSE**, demonstrating superior stability and less volatile prediction errors in the out-of-sample test period.

---

## 2. Model Diagnostics & Stress Test

### OLS Model Parameters (Used for Stress Test)
| Variable | Coefficient | P-value |
| :--- | :--- | :--- |
| **dGDP** | +2.034 | 0.295 |
| **dUnemp** | +1202.3 | 0.423 |
| **dRate** | +870.9 | 0.157 |

### Stress Test Result
* **Scenario:** Severe Adverse Shock ($\Delta \text{GDP}=-500\text{B}, \Delta \text{Unemp}=+3.0\text{pp}, \Delta \text{Rate}=+1.0\text{pp}$).
* **Predicted $\Delta \text{NII}$:** **$+4302.48$ Million USD** (Counter-intuitive positive change)
* **Model Risk:** The OLS model is statistically invalid ($R^2=0.082$) and produced an economically illogical result under stress.

### Diagnostics
* **Durbin-Watson (2.02):** **OK** (No autocorrelation).
* **Breusch-Pagan (p=0.5623):** **NO** heteroskedasticity.

---

## 3. Project Deliverables

| File | Description |
| :--- | :--- |
| [`ccar_nii_forecast.ipynb`](ccar_nii_forecast.ipynb) | Complete Jupyter notebook with all code, outputs, and model fits. |
| **`CCAR_summary.pdf`** | The final one-page executive summary and Model Note documentation. |
| `actual_vs_forecast.png` | Visual comparison of Actual vs. Forecasted $\Delta \text{NII}$ in the test period. |

---

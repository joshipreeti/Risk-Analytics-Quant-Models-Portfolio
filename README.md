# Risk Analytics & Quantitative Models Portfolio
This repository is a collection of my work in risk analytics, covering market risk, credit risk, and derivative pricing. The focus of these projects is not just on model implementation, but on understanding how quantitative techniques translate into real-world risk management and regulatory frameworks.
## 📂 Projects Overview

### 1. Monte Carlo Option Pricing — Bank of Baroda Case Study
This project implements a stochastic simulation framework to price European options for Bank of Baroda (BOB) using real-world NSE option chain data.Stochastic Modeling using Geometric Brownian Motion (GBM) under the risk-neutral framework to simulate 100,000 potential terminal stock prices. Volatility Calibration implements implied volatility calibration from market option premiums and compares results against exchange-implied volatility.
Validation: Benchmarks Monte Carlo simulation results against the analytical Black-Scholes-Merton pricing framework.

### 2. Credit Risk Modelling — PD, LGD, and EAD
Builds a full credit risk pipeline using LendingClub loan data — the same framework banks use under **Basel II/III** and **IFRS 9**.
- **Credit Scorecard:** Weight of Evidence (WoE) + Information Value (IV) + Logistic Regression → points scale (like CIBIL/FICO)
- **PD Model:** Probability of Default — Logistic Regression · Decision Tree · XGBoost · evaluated using AUC & Gini
- **LGD Model:** Loss Given Default — Linear Regression · Decision Tree · XGBoost · evaluated using RMSE & MAE
- **EAD:** Exposure at Default using outstanding principal and Credit Conversion Factor (CCF)
- **Expected Loss:** $EL = PD \times LGD \times EAD$ → total portfolio EL ~$55.9M (14.7% of EAD)
- **Model Comparison:** XGBoost marginally outperforms — Logistic Regression recommended for production (interpretable + regulator-friendly)
  
### 3. Volatility Modelling — ARCH and GARCH
Volatility modelling using Bank of Baroda (BANKBARODA.NS) stock data — examining why standard regression fails on financial returns and how ARCH/GARCH models address this..
 -**Stylised Facts:** Fat tails, volatility clustering, and heteroskedasticity in daily returns
- **ARCH(5):** Variance as a function of past 5 squared shocks — short memory
- **GARCH(1,1):** Industry standard — adds persistence (β) for long memory
- **GJR-GARCH(1,1):** Asymmetric volatility — tests leverage effect (γ) for equity returns
- **Validation:** GARCH forecast (1.88%/day) compared against actual May 2026 realised volatility and live NSE options chain (ATM IV = 24.10%)
  
##  How to Run
*   **Environment:** All notebooks run on Jupyter or Google Colab.
*   **Dependencies:** Each notebook has a setup cell at the top with necessary installs (e.g., `pip install arch` or `yfinance`).
*   **Data:** Market data is fetched dynamically via APIs or provided within the repository structure.
##  Feedback
 If you have any suggestions or technical questions, please feel free to share them with me!

# Risk Analytics & Quantitative Models Portfolio

This repository is a collection of my work in risk analytics, covering market risk, credit risk, and derivative pricing. The focus of these projects is not just on model implementation, but on understanding how quantitative techniques translate into real-world risk management and regulatory frameworks.

## 📂 Projects Overview

### 1. Monte Carlo Option Pricing — Bank of Baroda Case Study
This project implements a stochastic simulation framework to price European options for Bank of Baroda (BOB) using real-world NSE option chain data. Stochastic Modeling using Geometric Brownian Motion (GBM) under the risk-neutral framework to simulate 100,000 potential terminal stock prices. Volatility Calibration implements implied volatility calibration from market option premiums and compares results against exchange-implied volatility.
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
Volatility modelling using Bank of Baroda (BANKBARODA.NS) stock data — examining why standard regression fails on financial returns and how ARCH/GARCH models address this.
- **Stylised Facts:** Fat tails, volatility clustering, and heteroskedasticity in daily returns
- **ARCH(5):** Variance as a function of past 5 squared shocks — short memory
- **GARCH(1,1):** Industry standard — adds persistence (β) for long memory
- **GJR-GARCH(1,1):** Asymmetric volatility — tests leverage effect (γ) for equity returns
- **Validation:** GARCH forecast (1.88%/day) compared against actual May 2026 realised volatility and live NSE options chain (ATM IV = 24.10%)

### 4. Value at Risk & FRTB — Bank of Baroda Case Study
Implements and compares all three standard VaR methodologies on real NSE data (2022–2025) for a ₹1 Crore BOB equity position, with full Basel III and FRTB regulatory framework application.
- **Historical Simulation VaR:** Non-parametric approach using actual return distribution — VaR 99% = 5.04%, ES 97.5% = 6.05%
- **Parametric VaR:** Variance-Covariance method assuming normality — confirms fat tails (Historical VaR > Parametric VaR)
- **Monte Carlo VaR:** GBM-based simulation with 50,000 paths — VaR 99% = 5.00%, ES 97.5% = 5.01%
- **FRTB Liquidity Horizon Scaling:** ES scaled to 10-day horizon (√10 rule) — FRTB ES capital 20% higher than Basel III VaR capital
- **Backtesting:** Rolling 250-day window — 7 exceptions at 99% → Basel Yellow Zone; confirms fat tails in PSU bank returns
- **Stressed VaR (SVaR):** Worst 252-day rolling window identified (Jan 2022 – Feb 2023) — SVaR 1.45× current VaR
- **Regulatory Capital Comparison:** Simplified Basel III (VaR + SVaR) vs illustrative FRTB ES capital across holding horizons

## ⚙️ How to Run
- **Environment:** All notebooks run on Jupyter or Google Colab
- **Dependencies:** Each notebook has a setup cell at the top with necessary installs (e.g., `pip install arch yfinance`)
- **Data:** Market data is fetched dynamically via APIs or provided within the repository structure

## 💬 Feedback
If you have any suggestions or technical questions, please feel free to share them with me!

# Risk Analytics & Quantitative Models Portfolio
This repository is a collection of my work in risk analytics, covering market risk, credit risk, and derivative pricing. The focus of these projects is not just on model implementation, but on understanding how quantitative techniques translate into real-world risk management and regulatory frameworks.
## 📂 Projects Overview
### 1. Monte Carlo Option Pricing — Bank of Baroda Case Study
This project implements a stochastic simulation to price European options for Bank of Baroda (BOB) using real-world NSE data.
*   **Stochastic Modeling:** Uses Geometric Brownian Motion (GBM) to simulate 50,000 potential price paths.
*   **Volatility Estimation:** Implements the **Parkinson High-Low Estimator**for a more nuanced volatility measure than standard close-to-close returns.
*   **Validation:** Benchmarks simulation results against the analytical **Black-Scholes-Merton**
*   **Risk Metrics:** Calculates Standard Error and $95\%$ Confidence Intervals to ensure simulation convergence.
### 2. Credit Risk Modelling — PD, LGD, and EAD
Builds a full credit risk pipeline using LendingClub loan data—the same framework banks use under **Basel II/III** and **IFRS 9**.
*   **Credit Scorecard:** Developed using Weight of Evidence (WoE) and Information Value (IV).
*   **PD Model:** Probability of Default via logistic regression with AUC evaluation.
*   **LGD & EAD:** Loss Given Default estimation from recovery data and Exposure at Default using Credit Conversion Factors (CCF).
*   **Regulatory Logic:** Calculates **Expected Loss (EL)** $= PD \times LGD \times EAD$.
### 3. Volatility Modelling — ARCH and GARCH
Volatility modelling using Bank of Baroda stock data to address why standard regression fails on financial returns.
*   **Stylized Facts:** Explores why returns are heteroskedastic and why that matters for risk managers.
*   **ARCH Model:** Letting variance depend on past shocks (volatility clusters).
*   **GARCH(1,1):** The industry standard for volatility forecasting, adding persistence to the model.
*   **Market Context:** Forecasting and interpreting results within an active market environment.
## 🛠️ How to Run
*   **Environment:** All notebooks run on Jupyter or Google Colab.
*   **Dependencies:** Each notebook has a setup cell at the top with necessary installs (e.g., `pip install arch` or `yfinance`).
*   **Data:** Market data is fetched dynamically via APIs or provided within the repository structure.
## 🎯 Who this is for
*   **Finance Students & Risk Analysts:** 
## 💬 Feedback
These projects are part of my continuous learning journey in quantitative finance. If you have any suggestions or technical questions, please feel free to share them with me!

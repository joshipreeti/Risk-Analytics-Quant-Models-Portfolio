# Risk Analytics & Quantitative Models Portfolio #

A collection of quantitative finance, risk analytics, and machine learning projects spanning market risk, credit risk, derivative pricing, volatility forecasting, algorithmic trading, and regulatory capital frameworks.

Projects are built using real market and credit datasets with practical applications to Basel II/III, FRTB, IFRS 9, quantitative research, and model risk management.

---

## 📂 Projects Overview

### 1. Monte Carlo Option Pricing — Bank of Baroda Case Study

Stochastic simulation framework to price European options on Bank of Baroda (BOB) using real NSE option chain data.

- **GBM Simulation:** 100,000 paths under risk-neutral framework
- **Volatility Calibration:** Implied volatility from market premiums vs exchange-implied volatility
- **Validation:** Monte Carlo results benchmarked against Black-Scholes-Merton
- **Risk Analysis:** Sensitivity of option values to volatility assumptions and market conditions

---

### 2. Credit Risk Modelling — PD, LGD & EAD (LendingClub)

Full credit risk pipeline using LendingClub loan data, aligned with Basel II/III and IFRS 9 frameworks.

#### Probability of Default (PD)

- Credit Scorecard using WoE + IV + Logistic Regression
- Logistic Regression, Decision Tree, and XGBoost comparison
- Performance evaluated using AUC and Gini

#### Loss Given Default (LGD)

- Linear Regression
- Decision Tree Regressor
- XGBoost Regressor
- Evaluated using RMSE and MAE

#### Exposure at Default (EAD)

- Outstanding Principal
- Credit Conversion Factor (CCF)

#### Expected Loss Framework

**EL = PD × LGD × EAD**

Key Findings:

- Portfolio Expected Loss ≈ $55.9M
- EL represents approximately 14.7% of total EAD
- XGBoost achieved the strongest predictive performance
- Logistic Regression recommended for production deployment due to interpretability and regulatory acceptance

---

### 3. Volatility Modelling — ARCH & GARCH (Bank of Baroda)

Volatility forecasting project on BANKBARODA.NS using classical econometric models.

#### Models Implemented

- ARCH(5)
- GARCH(1,1)
- GJR-GARCH(1,1)

#### Key Findings

- Evidence of volatility clustering
- Fat-tailed return distributions
- Persistent volatility dynamics captured effectively by GARCH
- Leverage effect tested via GJR-GARCH and found statistically insignificant

#### Validation

- Forecast volatility compared against:
  - Realized volatility
  - NSE ATM implied volatility
  - Live market conditions

---

### 4. Market Risk Capital — FRTB IMA & SA | Bank of Baroda Case Study

Comprehensive implementation of the Basel FRTB market risk framework using real NSE market data.

#### Part 1: Internal Models Approach (IMA)

##### Value-at-Risk & Expected Shortfall

- Historical VaR (99%)
- Parametric VaR
- Monte Carlo VaR (50,000 simulations)
- Expected Shortfall (97.5%)

##### FRTB Enhancements

- Liquidity Horizon Scaling
- Stressed VaR
- Regulatory Capital Computation
- Basel Traffic-Light Backtesting

##### Key Findings

- Historical VaR exceeded Parametric VaR, confirming fat tails
- FRTB ES capital approximately 20% higher than Basel III VaR capital
- Backtesting produced 7 exceptions → Basel Yellow Zone

#### Part 2: Standardised Approach (SA)

##### Sensitivity-Based Method (SBM)

- Equity Risk
- FX Risk
- Commodity Risk
- General Interest Rate Risk (GIRR)

##### Additional Components

- Default Risk Charge (DRC)
- Residual Risk Add-On (RRAO)
- Output Floor

##### Portfolio

- Bank of Baroda Equity
- USD/INR FX Position
- Crude Oil Futures
- 10-Year Government Bond

##### Key Finding

Output Floor became binding:

**Final Capital = max(IMA Capital, 72.5% × SA Capital)**

Result:

- IMA Capital = ₹28.7 Lakhs
- SA Capital = ₹87.8 Lakhs
- Final Capital = ₹63.7 Lakhs

---

### 5. Can Machine Learning Beat Buy-and-Hold?
#### A Cost-Aware XGBoost Backtest on Bank of Baroda

A quantitative research project investigating whether machine learning can generate economically meaningful trading profits after accounting for transaction costs and real-world market frictions.

> Can a predictive model outperform a passive buy-and-hold strategy once realistic trading costs are considered?

#### Data

- BANKBARODA.NS
- Daily historical price data
- Yahoo Finance

#### Feature Engineering

32 market features including:

- Momentum Indicators
- RSI
- MACD
- Bollinger Bands
- Moving Average Signals
- Volatility Features
- Volume-Based Indicators

#### Leakage-Free Feature Selection

Feature selection performed exclusively on training data using:

- Variance Threshold Filtering
- Correlation Filtering
- Mutual Information Selection
- Recursive Feature Elimination (RFE)

#### Model

- XGBoost Classifier
- Time-series-aware train/test split
- Hyperparameter tuning
- Probability-based trading signals

#### Validation Framework

- Out-of-Sample Testing
- Walk-Forward Validation
- Cost-Aware Backtesting

#### Trading Framework

- Dead-Zone Threshold
- Transaction Cost Modelling
- Position-Based Returns
- Strategy Equity Curve

#### Key Finding

Although the model demonstrated predictive power above random guessing, the edge was insufficient to overcome:

- Transaction Costs
- Trading Turnover
- Market Noise
- Regime Instability

This project highlights a crucial lesson in quantitative finance:

### Statistical Significance ≠ Economic Significance

A model can be predictive without being profitable.

---

## 🛠️ Tech Stack

`Python` · `NumPy` · `Pandas` · `SciPy` · `Matplotlib` · `scikit-learn` · `XGBoost` · `arch` · `yFinance`

---

## 📚 Regulatory Frameworks Referenced

- Basel II
- Basel III
- FRTB (BCBS d457)
- IFRS 9
- Market Risk Capital Frameworks
- Credit Risk Modelling Standards

---

## 📌 Notes

- Real market and credit datasets used throughout
- No synthetic datasets used for final analyses
- Position sizes are hypothetical and used solely for educational purposes
- Regulatory parameters follow publicly available Basel/FRTB guidance
- Projects are intended for quantitative research, risk analytics, and educational purposes

---

## 🎯 Areas of Interest

- Quantitative Risk Management
- Market Risk
- Credit Risk
- Derivative Pricing
- Regulatory Capital
- Volatility Forecasting
- Machine Learning in Finance
- Quantitative Research
- Financial Engineering

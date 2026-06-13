# Risk Analytics & Quantitative Models Portfolio

A collection of quantitative risk projects covering market risk, credit risk,
and derivative pricing — built on real NSE/LendingClub data with full
regulatory framing (Basel II/III, FRTB, IFRS 9).

---

## 📂 Projects Overview

### 1. Monte Carlo Option Pricing — Bank of Baroda Case Study

Stochastic simulation framework to price European options on Bank of Baroda
(BOB) using real NSE option chain data.

- **GBM Simulation:** 100,000 paths under risk-neutral framework
- **Volatility Calibration:** Implied volatility from market premiums vs
  exchange-implied volatility
- **Validation:** Monte Carlo results benchmarked against Black-Scholes-Merton

---

### 2. Credit Risk Modelling — PD, LGD & EAD (LendingClub)

Full credit risk pipeline using LendingClub loan data — the same framework
used under Basel II/III and IFRS 9.

- **Credit Scorecard:** WoE + IV + Logistic Regression → points scale (CIBIL/FICO style)
- **PD Model:** Logistic Regression · Decision Tree · XGBoost — evaluated on AUC & Gini
- **LGD Model:** Linear Regression · Decision Tree · XGBoost — evaluated on RMSE & MAE
- **EAD:** Outstanding principal + Credit Conversion Factor (CCF)
- **Expected Loss:** EL = PD × LGD × EAD → portfolio EL ~$55.9M (14.7% of EAD)
- **Model Selection:** XGBoost marginally outperforms; Logistic Regression
  recommended for production (interpretable + regulator-friendly)

---

### 3. Volatility Modelling — ARCH & GARCH (Bank of Baroda)

Volatility modelling on BANKBARODA.NS — from stylised facts to asymmetric models.

- **Stylised Facts:** Fat tails, volatility clustering, heteroskedasticity
- **ARCH(5):** Short-memory variance from past 5 squared shocks
- **GARCH(1,1):** Industry standard — adds persistence (β) for long memory
- **GJR-GARCH(1,1):** Tests leverage effect (γ) — found insignificant for BOB
  (documented transparently, not suppressed)
- **Validation:** GARCH forecast (1.88%/day) vs actual May 2026 realised
  volatility and live NSE ATM IV (24.10%)

---

### 4. Market Risk Capital — FRTB IMA & SA | Bank of Baroda Case Study

Two-part series implementing the full FRTB market risk capital framework
on a ₹1 Crore BOB equity position using real NSE data (2022–2025).

#### Part 1: Internal Models Approach (IMA)
*Value-at-Risk, Expected Shortfall & Stressed Capital*

- **Historical VaR:** Non-parametric — VaR 99% = 5.04%, ES 97.5% = 6.05%
- **Parametric VaR:** Variance-Covariance — confirms fat tails
  (Historical > Parametric)
- **Monte Carlo VaR:** GBM, 50,000 paths — VaR 99% = 5.00%
- **FRTB Liquidity Scaling:** ES scaled to 10-day horizon (√10 rule) —
  FRTB ES capital 20% higher than Basel III VaR capital
- **Backtesting:** Rolling 250-day window — 7 exceptions at 99% →
  Basel Yellow Zone
- **Stressed VaR:** Worst 252-day window (Jan 2022–Feb 2023) —
  SVaR = 1.45× current VaR
- **Regulatory Capital:** Basel III (VaR + SVaR) vs FRTB ES across holding horizons

#### Part 2: Standardised Approach (SA)
*Sensitivity-Based Method, DRC, RRAO & Output Floor*

Hypothetical trading book: BOB Equity (₹1Cr) · USD/INR FX (₹50L) ·
Crude Oil Futures (₹25L) · 10Y G-Sec (₹75L)

- **SBM — Equity:** Delta (RW 55%) + Vega (Black-Scholes, 5% vol shock)
- **SBM — FX:** Flat RW 15% on net open position (non-specified pair)
- **SBM — Commodity:** Bucket 2 Crude Oil, RW 35% (BCBS d457, Table 1)
- **SBM — GIRR:** DV01-based, 10Y tenor, RW 1.15%
- **DRC:** Jump-to-default — 15% × 100% LGD × ₹1Cr equity;
  G-Sec exempt (sovereign, domestic currency)
- **RRAO:** 0.1% on hypothetical vanilla call notional (linear positions excluded)
- **Output Floor:** Final Capital = max(IMA ₹28.7L, 72.5% × SA ₹87.8L)
  → **SA Floor binding at ₹63.7L**

---

## 🛠️ Tech Stack

`Python` · `NumPy` · `Pandas` · `yFinance` · `SciPy` · `Matplotlib` ·
`scikit-learn` · `XGBoost` · `arch`

---

## 📌 Notes

- All position sizes are hypothetical — used solely for educational purposes
- Risk weights and regulatory parameters follow BCBS d457 (FRTB SA) and
  Basel II/III frameworks
- Real market data used throughout (NSE/LendingClub) — no synthetic datasets

**Risk Analytics & Quantitative Models Portfolio**
This repository is a collection of my work in risk analytics, covering both market risk and credit risk modelling.
The focus of these projects is not just on model implementation, but on understanding how quantitative techniques translate into real-world risk management and regulatory frameworks.
**Credit Risk Modelling — PD, LGD and EAD**-Builds a full credit risk pipeline using LendingClub loan data — the same framework banks use under Basel II/III and IFRS 9.Credit scorecard using Weight of Evidence (WoE) and Information Value (IV).PD model via logistic regression with AUC evaluation.LGD estimation from recovery data. EAD using Credit Conversion Factor (CCF).Expected Loss = PD × LGD × EAD
**Volatility Modelling — ARCH and GARCH**-Volatility modelling using Bank of Baroda stock data. Starts from why standard regression fails on financial returns and builds up to GARCH(1,1) — the industry standard for volatility forecasting.
Why returns are heteroskedastic and why that matters.ARCH model — letting variance depend on past shocks GARCH(1,1) — adding persistence to volatility Forecasting and interpreting results in a real market context
**How to run-Both notebooks** run on Jupyter or Google Colab. Each has a setup cell at the top with any additional installs needed.
**Who this is for**-Finance students, risk analysts, and anyone building into quant roles. Basic Python and pandas assumed — the finance concepts are explained from scratch.
**Feedback**-If you have any suggestions, please feel free to share with me.

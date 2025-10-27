# Portfolio Risk & Return — JPMorgan vs Morgan Stanley (Copula, GARCH, VaR)

Masters-style analysis of **portfolio risk management** using:
**Coffee Can** stock selection, **copula** modeling (t / Gaussian),
**GARCH(1,1)** volatility forecasting, and **VaR** estimation.  
Compares **equal-weight vs optimized** weights, with NIFTY50 / T-bill benchmarks.

---

## 📦 Contents

- `weight_optimization.ipynb` — Weight optimization workflow
- `Copula_based_Simulation.R` — Copula fitting & simulation
- `A_ret combined (1).csv`, `D_ret combined (1).csv`, `rs_ret_combined (1).csv` — Return datasets
- `calculation of money.xlsx` — Auxiliary calc sheet
- `data.zip` — Input data bundle
- `CAM PORTFOLIO RISK MANAGEMENT.pdf` / `.pptx` — Report & slides
- `README.md` — You’re here

> Base project: a public portfolio-risk study; this version clarifies methods and steps.

---

## 🔬 Methodology

1. **Universe & Selection (Coffee Can)**  
   Select 12 stocks → create **3 portfolios** using technical factors (alpha, beta),
   with **T-bill** & **NIFTY50** as benchmarks.

2. **Dependence Modeling (Copula)**  
   Fit **t** and **Gaussian** copulas on joint returns.  
   Compare **Log-Likelihood** / **AIC** → choose better fit.  
   Simulate joint returns under chosen copula.

3. **Volatility Forecasting (GARCH(1,1))**  
   Estimate and **forecast 50-day** volatility for each series.

4. **Risk Metrics & Backtest**  
   - **Cumulative returns** vs NIFTY50  
   - **Equal-weight** vs **Optimized** weights  
   - **VaR (variance–covariance)** for both portfolios

5. **Conclusion**  
   Decide which portfolio is safer / superior on risk-adjusted basis.  
   *(No stock recommendations.)*

---

## 🛠️ Reproducing

### Python (weights / analysis)
```bash
python -m venv .venv
source .venv/bin/activate   # (Windows) .venv\Scripts\activate
pip install numpy pandas scipy matplotlib statsmodels arch
jupyter notebook
# open weight_optimization.ipynb
R (copulas)
r
Copy code
# In R
install.packages(c("copula", "PerformanceAnalytics", "tseries"))
source("Copula_based_Simulation.R")
Data: Use the provided CSVs (A_ret combined (1).csv, etc.) or replace with your own universe.
Ensure consistent dates / frequency when merging.

📈 Outputs
Copula fit diagnostics (LL / AIC)

50-day GARCH volatility forecasts

Equal-weight vs optimized portfolio performance

VaR comparison

🧠 Notes
Verify stationarity on returns; model GARCH on residuals as needed.

For robust VaR, consider historical / Monte Carlo variants as a cross-check.

Optimization can include constraints (max weight, sector caps).

# portfolio-risk-jpm-ms-copula-garch-var

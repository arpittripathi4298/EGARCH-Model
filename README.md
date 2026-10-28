# EGARCH Model for Infosys (INFY.NS) Stock Volatility Analysis

A comprehensive time-series project analyzing 10 years of historical price action and conditional volatility for Infosys (`INFY.NS`) using an **EGARCH(1,1,1)** model in Python[cite: 1].

---

## 📊 Project Overview
Financial time-series data often exhibit volatility clustering and asymmetry—where negative market shocks cause higher volatility than positive shocks of the same magnitude (the *leverage effect*). This project applies an Exponential Generalized Autoregressive Conditional Heteroskedasticity (EGARCH) model to capture these dynamics over a 10-year period[cite: 1].

* **Dataset:** Daily closing prices and percentage returns for Infosys (`INFY.NS`)[cite: 1]
* **Timeframe:** October 28, 2016 – October 28, 2026 (~2,471 observations)[cite: 1]
* **Key Libraries:** `yfinance`, `arch`, `pandas`, `numpy`, `seaborn`, `matplotlib`[cite: 1]

---

## ⚙️ Model Parameters & Statistical Results

The EGARCH(1,1,1) model was fitted using Maximum Likelihood Estimation via the `arch` library[cite: 1]. Below are the key parameter outputs:

* **$\mu$ (Constant Mean) = 0.0831** ($p = 0.007$)[cite: 1]
* **$\omega$ (Omega / Baseline Volatility) = 0.0552** ($p = 0.019$)[cite: 1]
* **$\alpha$ (Alpha / Shock Magnitude) = 0.1374** ($p = 0.003$): Measures the impact magnitude of recent market shocks on current volatility[cite: 1].
* **$\gamma$ (Gamma / Asymmetry / Leverage Effect) = -0.0583** ($p = 0.008$): Mathematically confirms the leverage effect; downward price drops cause significantly higher volatility than equivalent upward gains[cite: 1].
* **$\beta$ (Beta / Volatility Persistence) = 0.9529** ($p < 0.001$): Indicates extremely high volatility persistence, meaning market turbulence tends to stay elevated for prolonged periods once triggered[cite: 1].

---

## 📈 Visualizations

The project contrasts raw absolute realized volatility against the EGARCH conditional volatility predictions using Seaborn[cite: 1]. 

```python
# Sample snippet from the workflow
import seaborn as sns
import matplotlib.pyplot as plt

sns.lineplot(data=Volatility, dashes=False, palette={'Real Volatility': 'navy', 'EGARCH Volatility': 'crimson'})
plt.title('EGARCH Model for Infosys 10 years Stock Price Volatility', fontsize=10, fontweight='bold')
plt.ylabel('Volatility')
plt.legend(frameon=False)

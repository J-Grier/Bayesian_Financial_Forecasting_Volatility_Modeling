# Bayesian Financial Forecasting & Volatility Modeling

## Quick Links
- [🚀 Recent Experimentation & Enhancements](#project-update-hamiltonian-monte-carlo-bayesian-hmm-implementation-april-2025)
- [Overview](#overview)
- [Methods & Forecasting Approaches](#methods--forecasting-approaches)
- [Model Performance Comparison](#model-performance-comparison-finalized)
- [Key Insights & Findings](#key-insights--findings)
- [Limitations & Future Directions](#limitations--future-directions)
- [References](#references)
---

## Overview
This project investigates statistical methods for forecasting financial market volatility, focusing on comparing classical (frequentist) and Bayesian approaches. Apple Inc. (AAPL) is used as the primary dataset and initial benchmark, with additional evaluation on Microsoft (MSFT) and JPMorgan Chase (JPM). Methods evaluated include ARIMA, Prophet, Bayesian AR(1), and Bayesian Hidden Markov Models (HMMs).

---

## Objectives
- Determine the most accurate short-term volatility forecasting model.
- Assess the effectiveness of Bayesian methods in capturing volatility regimes versus classical models.
- Evaluate the generalizability of Bayesian methods across different stocks.

---

## Methods & Forecasting Approaches

### Classical Methods
- **ARIMA(1,1,1)**: Traditional time series model.
- **Prophet**: Facebook's time series forecasting tool.

### Bayesian Methods
- **Bayesian AR(1)**: Robust Bayesian autoregressive forecasting with uncertainty quantification.
- **Bayesian Hidden Markov Model (HMM)**:
  - Deterministic HMM
  - Gaussian Noise HMM
  - Stochastic Noise HMM
  - Gaussian Rolling HMM
  - **Hamiltonian Monte Carlo (HMC) Bayesian Rolling HMM (New)**: Improved posterior inference and predictive accuracy leveraging advanced MCMC techniques.

---

## Key Findings
### Bayesian AR(1) – Best Short-Term Predictive Accuracy
- **Superior quantitative results** across multiple stocks without retraining:
  - AAPL: MAE = 0.0096, MSE = 0.0003
  - MSFT: MAE = 0.0101, MSE = 0.0003
  - JPM: MAE = 0.0089, MSE = 0.0003

### Bayesian Hidden Markov Model (HMM) – Captures Volatility Regimes
- Identified macro-level market volatility regimes.
- Quantitatively less precise (MAE = 0.1564, MSE = 0.0377) but valuable for qualitative insights into volatility shifts.

### Classical Models – Lagging Accuracy
- ARIMA(1,1,1): MAE = 0.0871, MSE = 0.0108
- Prophet: MAE = 0.1418, MSE = 0.0422

### New HMC-based Bayesian HMM 
-improved predictive accuracy and reduced uncertainty, highlighting promising advancements in computational Bayesian modeling.

---

## Detailed Model Comparison

| Forecast Method                    | MAE    | MSE    |
|------------------------------------|--------|--------|
| ARIMA (1,1,1)                      | 0.0871 | 0.0108 |
| Prophet                            | 0.1418 | 0.0422 |
| **Bayesian AR(1) (AAPL)**          | 0.0096 | 0.0003 |
| **Bayesian AR(1) (MSFT)**          | 0.0101 | 0.0003 |
| **Bayesian AR(1) (JPM)**           | 0.0089 | 0.0003 |
| Deterministic HMM                  | 0.0815 | 0.0103 |
| Gaussian Noise HMM                 | 0.0932 | 0.0130 |
| Stochastic Noise HMM               | 0.0807 | 0.0101 |
| Final Gaussian Rolling HMM         | 0.1564 | 0.0377 |
| **Bayesian Rolling HMM (HMC inference - NEW)** | 0.1546	| 0.0289 |
---

## Visualizations and Insights
- **[Forecast Comparison (ARIMA & Prophet vs Actual)](assets/rolling_ARIMA_prophet_AAPL.png)**: Highlights classical model limitations. 
- **[Bayesian AR(1) Accuracy and Credible Intervals](assets/AR1_credible_intervals.png)**: Illustrates high accuracy with uncertainty quantification.
- **[Bayesian HMM Regime Identification](assets/rolling_HMM_forecast_vs_actual.png)**: Qualitative visualization of volatility regime transitions.

---

## Suitability & Limitations of Bayesian Methods
### Strengths:
- Uncertainty quantification and credible intervals.
- Probabilistic modeling of market volatility and regime shifts.

### Limitations:
- Bayesian HMM has high computational complexity.
- Limited generalizability of HMM across multiple stocks.
- Assumption of linear dynamics in Bayesian AR(1).

---

## Project Update: Hamiltonian Monte Carlo Bayesian HMM Implementation (April 2025)
### Overview
We've introduced an advanced Bayesian Hidden Markov Model leveraging Hamiltonian Monte Carlo (HMC) sampling methods to enhance volatility regime identification and forecasting accuracy. This refined HMM addresses previous computational and predictive challenges, delivering improved insights into volatility transitions and associated trading signals.

### Key Improvements:
Enhanced Accuracy: Significantly improved volatility forecasting precision.

Reliable Regime Detection: Superior clarity in volatility regime transitions.

Actionable Trading Signals: Practical buy/sell signals derived from volatility regimes.

### Visualizations:
**[HMM-based Trading Signals for AAPL](assets/HMM_volatility_trading_signals_AAPL.png)**
Clearly illustrates buy/sell signals generated from the HMC-based Bayesian HMM volatility forecasts.

**[Rolling-window Volatility Forecast (Bayesian HMM vs Actual)](assets/rolling_window_HMM_volatility_AAPL.png)**
Compares the volatility predictions from the improved HMM with actual market volatility, highlighting predictive performance.

**[Average State Transition Probabilities Heatmap](assets/transition_matrix_heatmap_hmc.png)**
Visualizes the stability and clarity of volatility regime predictions, with high probability states clearly indicated (State 0: 70% persistence; State 1: 98% persistence).

### Notice on Code Availability:
Given the advanced and experimental nature of our Bayesian HMM model, the detailed implementation code is currently maintained privately. While the full codebase is not publicly available at this stage, we remain dedicated to openly sharing key insights, methodologies, and visualizations to contribute positively to the broader quantitative finance community.

---

## Limitations & Future Directions
### Current Limitations
- Bayesian HMM remains computationally intensive, despite improvements with HMC.
- Generalizability across diverse market regimes requires further testing.

### Planned Future Work
- Further optimize Hamiltonian Monte Carlo (HMC) sampling efficiency for large-scale deployment.
- Explore integration of advanced probabilistic frameworks (Pyro, NumPyro) for real-time market applications.
- Evaluate hybrid Bayesian modeling approaches for more comprehensive volatility forecasting.

---

## References and Resources

### Datasets and APIs:
- [Yahoo Finance API (`yfinance`)](https://github.com/ranaroussi/yfinance)
- [S&P 500 Tickers (Wikipedia)](https://en.wikipedia.org/wiki/List_of_S%26P_500_companies)

### Methodological & Theoretical Papers:
- Pai, P., & Lin, C. (2005). *A hybrid ARIMA and support vector machines model in stock price forecasting.* Expert Systems with Applications.
- Ticknor, J. (2013). *A Bayesian regularized artificial neural network for stock market forecasting.* Expert Systems with Applications.
- Ghahramani, Z. (2001). *An Introduction to Hidden Markov Models and Bayesian Networks.* International Journal of Pattern Recognition and Artificial Intelligence.
- McElreath, R. (2015). *Statistical Rethinking: A Bayesian Course with Examples in R and Stan.* CRC Press.
- Gelman, A., Carlin, J. B., Stern, H. S., Dunson, D. B., Vehtari, A., & Rubin, D. B. (2013). *Bayesian Data Analysis (3rd ed.).* Chapman and Hall/CRC.
- Kreuzer, A., Hauzenberger, N., Kastner, G., & Lopes, H. F. (2023). [*Efficient Bayesian Inference for Multivariate Factor Stochastic Volatility Models.*](https://arxiv.org/pdf/2310.03775) arXiv preprint arXiv:2310.03775.

### Software & Libraries:
- Python: Pandas, NumPy, Matplotlib, PyMC, Prophet, NumPyro

---

## Author
**John Grier**  
MS Data Science Candidate, Illinois Tech  
[GitHub: J-Grier](https://github.com/J-Grier)

---

## Connect with Me
- [LinkedIn](https://www.linkedin.com/in/john-grier/)
- Email: jgrier@hawk.iit.edu

---

## 🚀 Getting Started
1. Clone this repository:
```bash
git clone [your-repo-link]

# Bayesian Financial Forecasting & Volatility Modeling

## Overview
This project investigates statistical methods for forecasting financial market volatility, focusing on comparing classical (frequentist) and Bayesian approaches. Apple Inc. (AAPL) is used as the primary dataset and initial benchmark, with additional evaluation on Microsoft (MSFT) and JPMorgan Chase (JPM). Methods evaluated include ARIMA, Prophet, Bayesian AR(1), and Bayesian Hidden Markov Models (HMMs).

---

## Objectives
- Determine the most accurate short-term volatility forecasting model.
- Assess the effectiveness of Bayesian methods in capturing volatility regimes versus classical models.
- Evaluate the generalizability of Bayesian methods across different stocks.

---

## Methods and Models Evaluated
- **Classical Models**: ARIMA, Prophet (Facebook)
- **Bayesian Models**: Bayesian AR(1), Bayesian Hidden Markov Models (HMMs)

---

## Key Findings
### Bayesian AR(1) – Best Short-Term Predictive Accuracy
- **Superior quantitative results** across multiple stocks without retraining:
  - AAPL: MAE = 0.0096, MSE = 0.0003
  - MSFT: MAE = 0.0101, MSE = 0.0003
  - JPM: MAE = 0.0089, MSE = 0.0003

### Bayesian Hidden Markov Model (HMM) – Captures Volatility Regimes
- Explicitly identified macro-level market volatility regimes.
- Quantitatively less precise (MAE = 0.1564, MSE = 0.0377) but valuable for qualitative insights into volatility shifts.

### Classical Models – Lagging Accuracy
- ARIMA(1,1,1): MAE = 0.0871, MSE = 0.0108
- Prophet: MAE = 0.1418, MSE = 0.0422

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

---

## Visualizations and Insights
- **[Forecast Comparison (ARIMA & Prophet vs Actual)](assets/rolling_ARIMA_prophet_AAPL.png)**: Highlights classical model limitations. 
- **[Bayesian AR(1) Accuracy and Credible Intervals](assets/AR1_credible_intervals.png)**: Illustrates high accuracy with explicit uncertainty quantification.
- **[Bayesian HMM Regime Identification](assets/rolling_HMM_forecast_vs_actual.png)**: Qualitative visualization of volatility regime transitions.

---

## Suitability & Limitations of Bayesian Methods
### Strengths:
- Explicit uncertainty quantification and credible intervals.
- Probabilistic modeling of market volatility and regime shifts.

### Limitations:
- Bayesian HMM has high computational complexity.
- Limited generalizability of HMM across multiple stocks.
- Assumption of linear dynamics in Bayesian AR(1).

---

## Future Directions
- Computational optimization of Bayesian HMM models (e.g., variational inference, Expectation-Maximization).
- Leverage advanced probabilistic frameworks (Pyro, TensorFlow Probability) for performance enhancements.

---

## References and Resources

### Datasets and APIs:
- [Yahoo Finance API (`yfinance`)](https://github.com/ranaroussi/yfinance)
- [S&P 500 Tickers (Wikipedia)](https://en.wikipedia.org/wiki/List_of_S%26P_500_companies)

### Methodological & Theoretical Papers:
- Pai, P., & Lin, C. (2005). *A hybrid ARIMA and support vector machines model in stock price forecasting.* Expert Systems with Applications.
- Ticknor, J. (2013). *A Bayesian regularized artificial neural network for stock market forecasting.* Expert Systems with Applications.
- Ghahramani, Z. (2001). *An Introduction to Hidden Markov Models and Bayesian Networks.* International Journal of Pattern Recognition and Artificial Intelligence.
- Gelman, A., & Rubin, D. B. (1992). *Inference from Iterative Simulation Using Multiple Sequences.* Statistical Science.
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

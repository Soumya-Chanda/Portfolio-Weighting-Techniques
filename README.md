# Portfolio Weighting Techniques: A Comparative Study of Quantitative Portfolio Optimization Methods

## Overview

Portfolio construction lies at the core of modern quantitative finance. The challenge is to allocate capital across assets in a way that maximizes expected return while controlling risk. This project presents a comprehensive study of classical and modern portfolio optimization techniques applied to the Indian equity market.

The study develops and compares four major portfolio construction frameworks:

* Mean-Variance Optimization (MVO)
* Logistic Regression-Based Portfolio Selection
* Mean Absolute Deviation (MAD) Optimization
* GARCH-Based Dynamic Volatility Forecasting

Using a universe of 50 large-cap NSE stocks, the project evaluates the effectiveness of these approaches through rigorous mathematical derivations, empirical backtesting, and risk-adjusted performance analysis.

---

## Objectives

The primary goals of this project are:

* Develop and implement multiple portfolio weighting methodologies.
* Compare risk-return characteristics of different optimization frameworks.
* Evaluate portfolio performance through out-of-sample backtesting.
* Study the impact of volatility forecasting on portfolio construction.
* Analyze how machine learning techniques can assist in asset selection.
* Benchmark optimized portfolios against the NIFTY 50 Index and Equal-Weight portfolios.

---

## Dataset

### Asset Universe

* 50 Large-Cap NSE Stocks
* Daily Adjusted Closing Prices

### Study Period

| Period          | Duration            |
| --------------- | ------------------- |
| Training Period | Jan 2015 – Dec 2021 |
| Testing Period  | Jan 2022 – Dec 2024 |

### Data Sources

* Yahoo Finance
* National Stock Exchange (NSE)

---

# Methodologies

## 1. Mean-Variance Optimization (MVO)

The classical Markowitz framework constructs portfolios by balancing expected return against portfolio variance.

### Key Concepts

* Expected Returns
* Covariance Matrix
* Efficient Frontier
* Minimum Variance Portfolio
* Maximum Sharpe Ratio Portfolio
* Capital Market Line

Optimization Objective:

```math
\min_w \; w^T \Sigma w
```

Subject to:

```math
w^T\mu = \bar{\mu}
```

and

```math
\sum_i w_i = 1
```

### Key Features

* Efficient frontier construction
* Risk-return optimization
* Quadratic programming implementation
* Long-only portfolio constraints

---

## 2. Logistic Regression Portfolio Selection

Instead of forecasting exact returns, this framework predicts whether a stock is likely to outperform a benchmark in the next period.

### Feature Engineering

The model incorporates:

* 1-Month Return
* 3-Month Return
* 6-Month Return
* 20-Day Volatility
* 60-Day Volatility
* Relative Volume
* RSI (14-Day)
* Market Beta

### Model Pipeline

1. Feature construction
2. Correlation screening
3. VIF-based multicollinearity removal
4. Logistic model estimation
5. Probability scoring
6. Top-K asset selection
7. Portfolio construction

### Advantages

* Avoids direct return estimation
* Interpretable probabilistic framework
* Robust asset ranking methodology

---

## 3. GARCH-Based Portfolio Optimization

Financial markets exhibit volatility clustering and time-varying risk. To address this, GARCH models are used to forecast future volatility and dynamically adjust portfolio allocations.

### Models Used

* ARCH
* GARCH(1,1)

### Diagnostics

* Augmented Dickey-Fuller Test
* ACF/PACF Analysis
* Ljung-Box Test

### Portfolio Construction

Inverse-volatility weighting:

```math
w_i \propto \frac{1}{\sigma_i}
```

where:

```math
\sigma_i
```

is the forecasted asset volatility.

### Benefits

* Dynamic risk management
* Volatility forecasting
* Improved diversification during market stress

---

## 4. Mean Absolute Deviation (MAD) Optimization

MAD optimization replaces variance with absolute deviations as a measure of portfolio risk.

### Motivation

Traditional Mean-Variance Optimization:

* Requires covariance matrix estimation
* Is computationally intensive
* Can produce unstable weights

MAD addresses these limitations by formulating portfolio optimization as a linear programming problem.

### Risk Measure

```math
MAD = E\left[|R - E(R)|\right]
```

### Advantages

* Linear programming formulation
* Computational efficiency
* Scalable to large asset universes
* Sparse and interpretable portfolios

---

# Backtesting Framework

A walk-forward backtesting procedure was implemented to evaluate real-world performance.

### Evaluation Metrics

* Annualized Return
* Annualized Volatility
* Sharpe Ratio
* Sortino Ratio
* Maximum Drawdown (MDD)
* CAGR
* Up Capture Ratio
* Down Capture Ratio

### Benchmarks

* NIFTY 50 Index
* Equal Weight Portfolio

---

# Key Findings

### Mean-Variance Optimization

* Successfully constructs efficient portfolios along the risk-return frontier.
* Sensitive to estimation errors in expected returns.
* Produces strong risk-adjusted performance when covariance estimates are stable.

### Logistic Regression

* Provides a robust framework for stock selection.
* Achieved meaningful predictive power in identifying outperforming assets.
* Converts classification probabilities into portfolio weights.

### GARCH-Based Strategy

* Captures volatility clustering effectively.
* Produced the highest risk-adjusted performance among evaluated strategies.
* Improved portfolio stability during periods of market turbulence.

### MAD Optimization

* Delivered performance comparable to MVO.
* Reduced computational complexity significantly.
* Produced more stable and interpretable allocations.

---

## Technologies Used

### Programming Languages

* Python
* R

### Libraries

```python
numpy
pandas
scipy
statsmodels
sklearn
matplotlib
seaborn
yfinance
arch
cvxpy
PyPortfolioOpt
```

---

## Project Workflow

```text
Market Data Collection
            │
            ▼
Data Cleaning & Preprocessing
            │
            ▼
Return Computation
            │
            ▼
Feature Engineering
            │
            ▼
Portfolio Construction
(MVO / Logistic / MAD / GARCH)
            │
            ▼
Walk-Forward Backtesting
            │
            ▼
Performance Evaluation
            │
            ▼
Comparative Analysis
```

---

## Skills Demonstrated

* Portfolio Optimization
* Quantitative Finance
* Statistical Modeling
* Machine Learning for Finance
* Volatility Forecasting
* Time Series Analysis
* Risk Management
* Financial Econometrics
* Convex Optimization
* Backtesting and Strategy Evaluation

---

## Applications

* Quantitative Asset Management
* Portfolio Construction
* Risk Analytics
* Algorithmic Trading
* Wealth Management
* Financial Research
* Investment Strategy Development

---

## Future Enhancements

Potential extensions include:

* Black-Litterman Portfolio Optimization
* CVaR-Based Optimization
* Multi-Factor Asset Pricing Models
* Deep Learning-Based Asset Selection
* Reinforcement Learning Portfolio Management
* Dynamic Rebalancing Strategies
* Transaction Cost Modeling

---

## Conclusion

This project presents a comprehensive comparison of classical optimization, machine learning, and econometric approaches to portfolio construction. By integrating Mean-Variance Optimization, Logistic Regression, MAD Optimization, and GARCH-based volatility forecasting, the study demonstrates how different quantitative techniques can be leveraged to build portfolios with superior risk-adjusted performance. The results highlight the importance of combining statistical modeling, forecasting, and optimization to develop robust investment strategies in modern financial markets.

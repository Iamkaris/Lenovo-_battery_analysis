# Lenovo _battery_analysis
An end-to-end time series analysis investigating the degradation rate of a laptop battery using Python.

## Project Overview
This repository tracks weekly charge capacity metrics to diagnose the underlying stochastic process of battery depletion. It transitions from basic exploratory data analysis to advanced probabilistic forecasting.

## Tools & Libraries Used
* Python (Pandas, Matplotlib)
* Statsmodels (ACF/PACF Diagnostics, ARIMA Modeling)
* Jupyter Notebook

## Current Progress
* Standardized raw daily diagnostic data into a strict weekly time-series frequency.
* Differenced the non-stationary degradation trend for statistical testing.
* Built a baseline ARIMA(1, 1, 0) forecast model.

## Next Steps
* Implement Bayesian Structural Time Series (BSTS) utilizing Markov Chain Monte Carlo (MCMC) methods to generate probability-driven credible intervals for future capacity loss.

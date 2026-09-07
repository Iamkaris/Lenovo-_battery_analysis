Predicting Hardware Failure with Bayesian Structural Time Series (BSTS)
Overview
This project applies Bayesian state-space modeling to predict laptop battery degradation and forecast future hardware failure. Using weekly charge capacity data from a Lenovo laptop sensor, the model isolates the true physical decay of the battery from highly erratic measurement noise.

The ultimate goal is to predict exactly when the battery capacity will cross a critical failure threshold (30 Wh) to enable proactive, data-driven hardware lifecycle management.

The Problem with Traditional Time Series
An initial baseline model using ARIMA(1, 1, 0) was attempted but proved inadequate. Standard frequentist models struggled with:

Measurement Error: The hardware sensor frequently reported impossible upward spikes in capacity.

Physical Violations: ARIMA cannot natively enforce the laws of thermodynamics (i.e., battery capacity cannot spontaneously regenerate).

Methodology & Bayesian Architecture
To solve this, the project transitions to a probabilistic framework using PyMC.

Signal Extraction: By partitioning variance between the latent state (sigma_state) and the observation noise (sigma_obs), the algorithm successfully learned to ignore false sensor spikes.

Physics-Informed Constraints: The latent state was mathematically constrained to strictly enforce monotonic decay. Using a cumulative sum of HalfNormal step sizes, the model is physically forbidden from predicting capacity regeneration.

Monte Carlo Forecasting: The model samples from the learned posterior distribution to simulate 2,000 potential future realities over a 6-month horizon, generating a mathematically rigorous 94% forecast interval.

Results
The strictly monotonic BSTS model successfully extracted the true degradation curve. The Monte Carlo forecast projects that the battery will degrade from its current state of ~44 Wh to approximately 37 Wh by March 2027.

Most importantly, the 94% credible interval indicates with high confidence that the hardware will safely remain above the critical 30 Wh failure threshold over the next two quarters, saving premature replacement costs.

Technologies Used
Python 3

PyMC (Markov Chain Monte Carlo sampling / NUTS)

ArviZ (Posterior diagnostics and HDI calculation)

Pandas & NumPy (Data manipulation and Monte Carlo simulation)

Matplotlib (Probabilistic visualization)

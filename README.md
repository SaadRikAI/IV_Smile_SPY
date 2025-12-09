📈 SPY Options Implied Volatility Smile — Machine Learning Project

This project analyzes SPY options to compute and visualize the implied volatility (IV) smile, a key concept in options pricing.
It includes:

Loading and cleaning real SPY option chain data

Computing mid-prices and time to maturity

Retrieving the SPY underlying price

Calculating implied volatility using the Black-Scholes model

Visualizing the volatility smile

Exporting results for modeling

This repository provides a full, clean pipeline from raw option chain data to IV computation and visualization.

📂 Repository Structure

IV_Smile_SPY/
│
├── notebooks/
│   ├── 01_load_clean_IV.ipynb     # Load data, clean, compute IV, visualize
│   └── 02_IV_prediction.ipynb     # ML model to predict implied volatility
│
├── src/
│   └── data/
│       └── results/
│           ├── IV_results.csv
│           └── volatility_smile.png
│
├── .gitignore
└── README.md

---------------------------------------------------------------------------------------------------------------------------------------------------------
🧹 Data Preparation & Cleaning

The project performs the following preprocessing steps:

1. Merge call and put chains

2. Compute mid-price


	mid=(2bid+ask​)/2​


3. Remove invalid entries

4. Retrieve spot price from SPY history

5. Compute time to maturity (T)
in years, based on the selected expiration date

6. Keep essential columns for modeling
--------------------------------------------------------------------------------------------------------------------------------------------------------

📐 Implied Volatility Computation

IV is calculated numerically using the Newton–Raphson root-finding method applied to the Black-Scholes pricing formulas.

For each option, the algorithm solves:

𝐵
𝑆
(
𝜎
)
=
market price
BS(σ)=market price

producing a stable IV estimate when possible.

All computed results are stored in:

src/data/results/IV_results.csv
-----------------------------------------------------------------------------------------------------------------------------------------------------------

📊 Volatility Smile Visualization

The project generates a full volatility smile for the selected expiration.

<p align="center"> <img src="src/data/results/volatility_smile.png" width="600"> </p>

This visualization highlights how implied volatility varies with strike price and reveals the convex “smile” structure typical in equity index options.

-------------------------------------------------------------------------------------------------------------------------------------------------------------

🤖 Machine Learning Model for IV Prediction

The second notebook explores predictive modeling using the cleaned dataset.
Models trained include:

Linear Regression

Random Forest Regressor

Gradient Boosting / XGBoost

Model performance is evaluated using RMSE, MAE, and R² metrics.

The goal is to predict implied volatility from standard observable option features:

strike

mid-price

spot price

time to maturity

option type (call/put)

----------------------------------------------------------------------------------------------------------------------------------------------------------------

📁 Generated Outputs
File	Description
IV_results.csv	Clean dataset with computed implied volatilities
volatility_smile.png	Visualization of the IV smile

These files are versioned in the repository for reproducibility.

👤 Author

Saad Rik
Machine Learning & Data Analyst
GitHub: https://github.com/SaadRikAI

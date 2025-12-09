📈 SPY Options — Implied Volatility Smile & Machine Learning Prediction

This project analyzes SPY option chains to compute and visualize the implied volatility (IV) smile, and builds machine learning models to predict IV from observable option features.

It provides a complete pipeline from data retrieval → cleaning → implied volatility computation → visualization → machine learning prediction.

-------------------------------------------------------------------------------------------------------------------------------------------------------------------
📂 Repository Structure

IV_Smile_SPY/
│
├── notebooks/
│   ├── 01_load_clean_IV.ipynb        # Load data, clean, compute IV, visualize
│   └── 02_IV_prediction_model.ipynb  # Machine learning models for IV prediction
│
├── src/
│   └── data/
│       └── results/
│           ├── IV_results.csv
│           ├── model_performance.csv
│           ├── volatility_smile.png
│           └── iv_prediction_fit.png
│
├── .gitignore
└── README.md

-------------------------------------------------------------------------------------------------------------------------------------------------------------------

🧹 Data Preparation & Cleaning

The preprocessing pipeline includes:

1.2Merging call and put option chains

2.Computing mid-price


mid=(2×bid+ask)/3​


3.Removing invalid or missing entries

4.Retrieving SPY spot price using historical data

5.Computing time to maturity (T) in years

6.Keeping essential columns for modeling:

-strike

-mid-price

-spot price

-time to maturity

-option type (call/put)

-------------------------------------------------------------------------------------------------------------------------------------------------------------------
📐 Implied Volatility Computation

Implied volatility is computed using the Newton–Raphson numerical method applied to the Black–Scholes pricing model.

For each option, we solve:


𝐵𝑆(𝜎)=market price


The clean dataset containing computed IV values is stored in:

src/data/results/IV_results.csv

-------------------------------------------------------------------------------------------------------------------------------------------------------------------

🤖 Machine Learning — Implied Volatility Prediction

Using the cleaned dataset, several ML models are trained to predict implied volatility:

Models

Linear Regression

Random Forest Regressor

XGBoost Regressor

Evaluation Metrics

MAE (Mean Absolute Error)

RMSE (Root Mean Squared Error)

R² Score

Features Used

strike

mid-price

spot price

time to maturity

option type

A comparison between predicted and actual IV is shown below:

<p align="center"> <img src="src/data/results/iv_prediction_fit.png" width="600"> </p>

-------------------------------------------------------------------------------------------------------------------------------------------------------------------

📁 Generated Outputs

| File                      | Description                                      |
| ------------------------- | ------------------------------------------------ |
| **IV_results.csv**        | Clean dataset with computed implied volatilities |
| **model_performance.csv** | Performance metrics for all ML models            |
| **volatility_smile.png**  | Visualization of the IV smile                    |
| **iv_prediction_fit.png** | Actual vs predicted IV comparison                |

All files are versioned for reproducibility.


-------------------------------------------------------------------------------------------------------------------------------------------------------------------


👤 Author

Saad Rik
Machine Learning & Data Analyst
GitHub: https://github.com/SaadRikAI

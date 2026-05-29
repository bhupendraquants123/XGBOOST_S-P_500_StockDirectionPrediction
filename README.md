# XGBOOST_S-P_500_StockDirectionPrediction
A machine learning model to predict whether the S&P 500 will go up or go down.

Can a machine learning model predict whether the S&P 500 will go up tomorrow?

📌 The Problem
Predict whether the S&P 500 will rise the next day using 5 years of daily price data (2020–2025). A simple Yes (1) or No (0) — will tomorrow's return exceed 0.25%?

⚙️ What I Built

🔹 Feature Engineering
23 features from daily price and volume data — capturing momentum at different time horizons from 2 weeks to 3 months.

🔹 Feature Selection — The Funnelling Approach
A 3-stage process to reduce noise and keep only the most predictive features:
→ Stage 1 Filter: Removed highly correlated features
→ Stage 2 Wrapper: Recursive elimination using walk-forward cross validation
→ Stage 3 Embedded: XGBoost feature importance scores

Result: 23 features → 4 final features
(Volume + 3 momentum indicators)

🔹 Model — XGBoost Classifier
• Base model overfit badly — 100% train accuracy
• Hyperparameter tuning reduced overfitting — train accuracy dropped to 75.89%
• Test accuracy improved to 57.50% with ROC-AUC of 0.58

🔹 Backtesting
Tested the model's signals as a trading strategy vs simply holding the S&P 500. The strategy underperformed in 2024's strong bull market — which is expected. A conservative model that stays in cash will always lag in strongly rising markets.

💡 Key Takeaways

✅ A ROC-AUC of 0.58 is meaningful — markets are hard to predict and even small edges matter
✅ Never shuffle time series data — it creates data leakage
✅ Always tune hyperparameters — default settings overfit financial data
✅ Accuracy alone is misleading — always use balanced accuracy and ROC-AUC together


# Forecast the next-day GBP/USD exchange rate using an Autoregressive Artificial Neural Network (ARNN)

*Tools Used: Python (Jupiter Notebook)*

## Introduction:
The value of one pound sterling in US dollars is reported as a time series variable. The US/UK exchange rate data is downloaded from the Federal Reserve Economic Data website: https://fred.stlouisfed.org/series/DEXUSUK

## Key Findings:

- The predicted GBP/USD exchange rate for 08 Aug 2020 is expected to experience a slight decrease.

- The changes in the GBP/USD exchange rate show dependence primarily on the most recent rate, but this does not fully capture the complexity of exchange rate movements. Other factors, including economic indicators, market sentiment, and external shocks can be considered to make a more acurrate forecast.

- The ARNN model can accurately predicts the next-day GBP/USD exchange rate when provided with known lag/input values. However, when using predicted values as inputs for longer-term forecasts, the model struggles to accurately capture the exchange rate pattern.

- For reliable long-term predictions, a more advanced approach is required (LSTM, or an Hybrid Model), one that incorporates additional economic indicators beyond historical rates and utilises a more complex model to effectively capture complex market dynamics.

- The source of data is the Board of Governors of the Federal Reserve System (US). The value of one British pound to the US dollar is decreasing after `July 2014` but with some fluctuations. The data set includes the daily exchange rate from `January 4, 2010` until `August 7, 2020`.

## The Detailed Analysis:
Refer to [portfolio_task3.ipynb](./portfolio_task3.ipynb) or [portfolio_task3.html](./portfolio_task3.html)

## Insight Deep-Dive:

### 1. The Original Series of GBP/USD Exchange Rate:

![image](https://github.com/user-attachments/assets/088d7ec9-1af1-4212-8abc-5b280210b1db)

### 2. Predictive Model Summary

A neural network to predict the next day’s `GBP/USD` exchange rate.

- The model takes the previous day’s exchange rate as input (based on statistical analysis).

- It consists of:

  - `1` hidden layer with `5` units using a `sigmoid` activation.

  - `1` output layer predicting the next value directly.

- The data is split into:

  - 80% for training and validation

  - 20% held out for testing

This setup enables the model to learn patterns from past data and make accurate daily forecasts.

### 3. The Model Performance

![image](https://github.com/user-attachments/assets/44efbe1e-8e51-4070-9d3d-294bf602d1c4)

**Errors and Evaluations:**

- **Relative Error** (`0.00425`): This is a very low error, indicating that the model makes predictions with high accuracy relative to the actual values. This suggests that the model is well-fitted to the data and generalises well.
- **Sum of Squared Errors (SSE)** (`0.032`): SSE is the total squared difference between actual and predicted values. A lower SSE means fewer errors overall, which is a positive sign.
- **Mean Squared Errors (MSE):** 5.86e-05

  ![image](https://github.com/user-attachments/assets/c2727e7b-ee51-4c87-880a-6fc3c46da7f9)

**Conclusions:**

- Overall, the ARNN Model is a good model with low errors on holdout set with very few outliers around `+-0.03`, no sign of overfitting and genrealises the data well.
- The Prediction Residuals on holdout set is normally distributed around 0. Predicted values mostly scatter around the perfect prediction line.
- The Importance value of `0.1` suggests that `lag_1_scaled` has a moderate impact on the model's predictions. It is reasonable for the first lag to have moderate to high importance, especially in time series models where past values often influence future predictions.

### 4. Forecasting next-day GBP/USD Exchange Rate:

![image](https://github.com/user-attachments/assets/577fc11e-ec33-481d-b218-fbe813cf7168)

## Future Improvements:

- Use GridSearch to optimise model architecture and training parameters, improving accuracy and robustness through systematic hyperparameter tuning.
- Include external variables such as macroeconomic indicators, commodity prices, or stock indices to enhance predictive power beyond historical exchange rates.
- Enhance feature engineering by creating technical indicators (e.g., moving averages, volatility, momentum) to capture hidden patterns in the exchange rate movements.
- Explore advanced modelling techniques, such as LSTM or Transformer-based models, to better capture long-term dependencies and complex temporal dynamics in the data.








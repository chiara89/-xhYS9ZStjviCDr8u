# Stock trend prediction
## Background:
We are a portfolio investment company and we make investments in the emerging markets around the world. Our company profits by investing in profitable companies, buying, holding and selling company stocks based on value investing principles.

Our goal is to establish a robust intelligent system to aid our value investing efforts using stock market data. We make investment decisions and based on intrinsic value of companies and do not trade on the basis of daily market volatility. Our profit realization strategy typically involves weekly, monthly and quarterly performance of stocks we buy or hold.

## Data Description:
You are given a set of portfolio companies trading data from emerging markets including 2020 Q1-Q2-Q3-Q4 2021 Q1 stock prices. Each company stock is provided in different sheets. Each market's operating days varies based on the country of the company and the market the stocks are exchanged. Use only 2020 data and predict with 2021 Q1 data.

## Goal
Predict stock price valuations on a daily, weekly and monthly basis. Recommend BUY, HOLD, SELL decisions. Maximize capital returns, minimize losses. Ideally a loss should never happen. Minimize HOLD period.

## Methodology
Two model used for time series forecasting prediction were tested: Autoregressive Integrated Moving Average (ARIMA) and Long short-term memory (LSTM). The ARIMA model performs generally well with linear trends and stationary time series detecting also seasonality. It is less efficient with not linear trend making it unsuitable for forecasting complex trends like stock prices. The LSTM model on the other hand is more suitable for non-linear patterns and it can captures long-term dependencies and changing path over time which are common aspect of stock prices. The LSTM model outperformed significantly the ARIMA model, for this reason it was used for the prediction. A trading algorithm was implemented on top of the prediction forecasting in order to recommend BUY, HOLD and SELL decisions. The algorithm is based on the Bollinger Bands and customised parameters which determine decision. The minimum margin parameter can be adjusted according to the different trends: smaller values are better for downward trend while greater values are better for upward trends. The max_hold parameter determine the lenght of the maximum hold period before to sell the stocks. The sell signal is generated when the current price surpasses the upper Bollinger Band or if the maximum holding period has been reached. Additionally, the algorithm checks if the current price is above a minimum margin from the locked price in order to enforce the maximum possible profit. The buy signal is generated when the previous closing price is below the lower Bollinger Band, and the current price is within a specified threshold above the lower Bollinger Band. The minimum loss is achieved with the stop-loss trigger enforcing the sale of the stocks when the current price falls below a certain percentage of the stop-loss price.

## Conclusions
The current solution, consisting in an LSTM model for time series forecasting combined with the Bollinger Bands strategy with triggers and customised parameters, achieves the objective of resulting in no losses and maximum returns while decreasing the hold period. Altough in this specific case the result was achieved, larger and different datasets describing more complex trends could require a more complex LSTM model and/or more fine-tuning. The different parameters can be changed in order to fine tune the algorithm on a different dataset.

---
title: What is a time series model?
source: https://www.ibm.com/think/topics/time-series-model
author:
- '[[Ivan Belcic]]'
- '[[Cole Stryker]]'
published: 2025-06-05
created: 2026-08-31
description: "A time series model is a machine learning model that can analyze sequential time series data and predict future values."
---

## What is a time series model?

A time series model is a [machine learning](https://www.ibm.com/think/topics/machine-learning) model that can analyze sequential time series data and predict future values. Time series [datasets](https://www.ibm.com/think/topics/dataset) consist of data values ordered over time, with time as the independent variable. Time series analysis allows for the [forecasting](https://www.ibm.com/think/topics/forecasting) of future data values based on previous values in the sequence.

### What is time series modeling?

Time series modeling is the use of machine learning algorithms and statistical methods to analyze data points that change over a time period.

Time series datasets differ from other datasets in that they do not consist of independent, unrelated data points. Whereas many datasets are based on individual observations, time series datasets are labeled with timestamps and track variables across time, creating dependencies between data points. Dependencies are relationships between data points in which the value of one affects the value of another.

With univariate time series modeling, time is the only independent variable. All other variables depend on previous values. Multivariate time series modeling introduces more independent variables, such as weather conditions or demographic information.

## Key concepts for time series modeling

Many of the core concepts of time series modeling are temporal features: aspects of the data related to or derived from time. These concepts include:

- Autocorrelation

- Seasonality

- Stationarity

### Autocorrelation

[Autocorrelation](https://www.ibm.com/think/topics/autocorrelation) measures the degree to which current values correspond to the past values of historical data in a time series. High autocorrelation means that the current iteration of a time series maps closely to lagged versions. Autocorrelation identifies whether a time series repeats and can indicate seasonality.

Autocorrelation can be positive or negative. Positive autocorrelation means that high values lead to higher values and low values lead to lower values. Negative autocorrelation is the opposite: high values follow low values and vice versa.

### Seasonality

Seasonality is a characteristic of time series data in which there is a recurrent pattern based on a regular time interval—such as the changing of the seasons. For example, an e-commerce platform might sell more sunglasses in the spring and summer and more scarves in the fall and winter. Households typically use more electricity during the day than at night.

Time-dependent seasonal variations are useful when predicting future values with forecasting models. [Data visualization](https://www.ibm.com/think/topics/data-visualization) tools such as charts and graphs depict seasonality as a repeating fluctuation, often in the form of a sinusoidal wave.

During time series data analysis, the decomposition process reveals any seasonality present in the data, as well as trends and noise. Trends are long-term increases or decreases in data values, while noise refers to random variations that don’t follow predictable patterns. Noise often stems from errors and outliers.

### Stationarity

A stationary time series has static statistical properties, such as the mean and variance. With stationarity, data points can fluctuate with seasonality, but there is no greater trend. A time series of modern yearly average global temperatures would be nonstationary due to the effects of climate change driving temperatures up.

Stationarity is necessary for most time series models to function effectively. The Dickey-Fuller test reveals whether a dataset is stationary. Time series datasets without stationarity can be transformed with techniques such as differencing to remove trends and isolate other patterns, such as seasonality and autocorrelation.

## Time series models

When approaching a [time series forecasting](https://www.ibm.com/think/insights/time-series-forecasting) challenge, data scientists can choose from various [machine learning algorithms](https://www.ibm.com/think/topics/machine-learning-algorithms). Depending on the nature of the dataset, some are more appropriate than others. One-step models predict the next point in a time series, while multistep models yield multiple time series predictions.

Time series model types include:

- Autoregressive integrated moving average (ARIMA)

- Exponential smoothing

- Generalized autoregressive conditional heteroscedasticity (GARCH)

- Long short-term memory (LSTM)

Meta’s [open source](https://www.ibm.com/think/topics/open-source) Prophet and Amazon’s DeepAR are two other [AI models](https://www.ibm.com/think/topics/ai-model) built for time series modeling. It is also possible to adapt [linear regression](https://www.ibm.com/think/topics/linear-regression) models for time series forecasting tasks. Other supervised learning models such as [XGBoost](https://www.ibm.com/think/topics/xgboost) and [random forest](https://www.ibm.com/think/topics/random-forest) can be applied for nonlinear time series data.

### Autoregressive integrated moving average (ARIMA)

The [ARIMA model](https://www.ibm.com/think/topics/arima-model) family consists of numerous modular building-block models that can be run alone or combined in various groupings. ARIMA is a statistical model that predicts future values based on past events and it works best with stationary time series that show seasonality. It excels with univariate datasets and can be adapted for multivariate use cases as well.

ARIMA configurations include:

- **Autoregression (AR):** [Autoregressive models](https://www.ibm.com/think/topics/autoregressive-model), denoted as AR(*p*), predict future values of a variable based on past values in a stochastic term: one that is imperfectly predictable. The parameter *p* indicates the degree of lag or the number of data points used to make a prediction. A *p* value of 1 would reach back to the previous observation in the series.

- **Moving average (MA):** Moving average models, denoted as MA(*q*), predict future values based on past prediction errors. The parameter *q* is the number of errors included in the prediction. An MA(1) model would incorporate one past error.

- **Integration (I):** Integrated models add differencing (*d*) to make a time series stationary. Differencing replaces data values with the difference between current values and past values, creating a new series to represent the change in values. The parameter *d* indicates the number of times the data points are differenced.

- **Autoregressive moving average (ARMA):** ARMA models combine autoregression with moving averages. ARMA models can process stationary time series and are denoted as ARMA(*p*, *q*).

- **Autoregressive integrated moving average (ARIMA):** ARIMA models, denoted as ARIMA(*p, d, q*) add differencing to model nonstationary time series.

- **Seasonal autoregressive integrated moving average (SARIMA):** SARIMA models add seasonality. The parameters for seasonality are represented with capital letters and the parameter *m* indicates the duration of the season. SARIMA models are denoted as SARIMA(*p, d, q*)(*P, D, Q*)*m* and require a large quantity of historical data.

- **SARIMA with exogenous variables (SARIMAX):** More complex time series data includes variables in addition to time. SARIMAX models incorporate external variables to generate more nuanced forecasts.

- **Vector autoregression (VAR):** While ARIMA works best with univariate tasks, vector autoregression (VAR) can handle multivariate datasets. VAR models, including VARMA and VARMAX, can make predictions for multiple time series models at the same time.

### Exponential smoothing

Exponential smoothing models reduce noise by assigning progressively less weight or importance to older observations in the time series. More recent observations are considered to be more relevant in making future predictions. Exponential smoothing models include:

- **Simple exponential smoothing (SES):** The most basic form of exponential smoothing modifies MA to place more weight on recent observations. Compared to a straightforward moving average model, SES reduces noise while preserving more detail.

- **Double exponential smoothing (DES):** Recursively applying exponential smoothing twice can help counter trends. DES uses the parameters *α* as the data smoothing factor and *β* as the trend smoothing factor.

- **Triple exponential smoothing (TES):** For datasets with both trends and seasonality, TES—also known as Holt-Winters exponential smoothing (HWES)—applies smoothing a third time. The parameter *γ* is the seasonal smoothing factor.

- **TBATS:** TBATS (trigonometric, Box-Cox, ARMA, trend and seasonal components) is a specialized exponential smoothing model for time series datasets with complex seasonality.

### Generalized autoregressive conditional heteroscedasticity (GARCH)

GARCH is a specialized model that tracks volatility in the financial sector. For example, in the stock market, volatility is the degree and speed with which stock prices fluctuate. *Heteroscedasticity* means that the errors in a regression model do not share the same variance over time.

In [data science](https://www.ibm.com/think/topics/data-science), variables are considered homoscedastic if their variances are the same and heteroscedastic if they are not.

### Long short-term memory (LSTM)

LSTM brings the power of [deep learning](https://www.ibm.com/think/topics/deep-learning) neural networks to time series modeling. An LSTM model is a [recurrent neural network (RNN)](https://www.ibm.com/think/topics/recurrent-neural-networks) specialized in sequential data—such as a time series. LSTMs excel at capturing long-range dependencies: relationships between distant data points in a sequence.

Because they can retain more context than other types of models, LSTM models work well in complex applications, such as [natural language processing (NLP)](https://www.ibm.com/think/topics/recurrent-neural-networks) and recognizing real-world speech and images. They require large amounts of training data and can be built in Python.

## Time series modeling metrics

Benchmarking metrics, testing and validation help optimize model performance, as they do in many other machine learning applications.

Time series modeling metrics include:

- **Mean squared error (MSE):** The average of the squares of the error at each timestamp.

- **Root mean squared error (RMSE):** The square root of the MSE.

- **Mean absolute error (MAE):** The mean of the error values for each observation.

- **Mean absolute percentage error (MAPE):** Expresses the MAE as a percentage, showing the magnitude of the error. MAPE is also known as mean absolute percentage deviation (MAPD). MAPE is a common [loss function](https://www.ibm.com/think/topics/loss-function) for regression problems.

## Time series modeling use cases

Time series models play a strong role in data analytics, helping data scientists and business leaders alike with:

- **Pattern recognition:** Time series models identify recurrent fluctuations in data over time, such as seasonal changes, longer-term cycles and general trends. For example, in fashion, T-shirt sales seasonally surge every spring and summer. Fashion trends reappear and fade in multidecade cycles—oversized fits are now popular as they were in the 1990s.

- [**Anomaly detection**](https://www.ibm.com/think/topics/anomaly-detection)**:** Anomalies are data points that deviate from the rest of the data points in a dataset. While occasional anomalies can be attributed to noise, larger amounts of anomalous data can indicate unexpected shifts, problems in the data pipeline and opportunities for improvement.

- **Trend forecasting:** Based on historical data, time series models can predict future data points in the series. Organizations can use these predictions to make better [data-driven decisions](https://www.ibm.com/think/topics/data-driven-decision-making).

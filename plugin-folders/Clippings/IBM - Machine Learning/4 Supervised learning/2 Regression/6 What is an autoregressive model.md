---
title: What is an autoregressive model?
source: https://www.ibm.com/think/topics/autoregressive-model
author:
- '[[Joshua Noble]]'
published: 2024-12-05
created: 2026-08-31
description: "Autoregressive modeling uses autocorrelations in sequential data to create a regression for analysis and forecasting."
---

## What is an autoregressive model?

Autoregressive modeling is a [machine learning](https://www.ibm.com/think/topics/machine-learning) technique most commonly used for time series analysis and forecasting that uses one or more values from previous time steps in a time series to create a regression.

It is a simple but powerful technique for time series analysis that provides highly interpretable and effective predictions if your data contains correlations across the time steps. The correlation across time steps is called autocorrelation because it is a measure of how much a value correlates with itself. A purely linear process will autocorrelate perfectly with itself across the time series, making it possible to predict the next value exactly from previous values using an autoregressive process. A completely stochastic process such as white noise will have no autocorrelation since we cannot predict the current or future values by using the past values.

A time series is a sequence of measurements of the same variable or group of variables made over time. The measurements are typically made at evenly spaced times, for instance hourly, monthly or yearly. As an example, we might have values that measure the number of airline passengers in a country, with measurements observed each month. In this case, *y* represents the measured passenger counts and emphasizes the existence of measured values over time. The value of *t* is applied as a subscript rather than the usual *i* to indicate that *y<sub>t</sub>* represents the value of *y* at any time.

An autoregressive model is when we regress a value from a time series on previous values from that same time series. For example, *y<sub>t</sub>* regressed on *y<sub>t-1</sub>* uses the previous value of *y*, called a lagged value, to predict the current value of *y*. In this simple regression model, the dependent variable in the previous time period has become the predictor. The errors represent all the usual assumptions about errors in a simple linear regression model. We often look at the order of an autoregression as the number of preceding values in the series used to predict the value now. So, *y<sub>t</sub>* regressed on *y<sub>t-1</sub>* is a first-order autoregression, which is written as *AR(1)*.

## Definitions of autoregression

In a multiple linear regression, the output of the regression is a linear combination of multiple input variables. In autoregression models, the output is the future data point expressed as a linear combination of the past *p* data points. *p* is the number of lags included in the equation. An AR(1) model is defined mathematically as:

$$ x_{t}= \delta + \phi_1x_{t-1} + \alpha_{t}
 $$

**x<sub>t-1</sub>** is the past series value from one lag back

**ϕ** is the calculated coefficient for that lag

**Alpha<sub>t</sub>** is white noise (such as randomness)

**Delta** is defined as

$$ \delta=( 1 - \sum_{p}^{i=1}\phi_i ) \mu $$

for an autoregressive model of order *p*, where *p* is the total number of covariates calculated for lags and *μ* is the process mean.

When more lags are added to the model, we add more coefficients and lag variables to the equation:

$$ x_{t}=\delta + \phi_1x_{t-1} + \phi_2x_{t-2} + \alpha_{t} $$

The preceding model is a second-order autoregression since it contains two lags.

The general form of an autoregressive equation for an order *p* is

$$ x_{t} = \delta + \phi_1x_{t-1}...\phi_px_{t-p} + \alpha_{t} $$

To use autoregressive models for time-series forecasting we use the current time value and any historical data to predict the next time step. For instance, an AR model with 2 lags might predict a single time step forward like so:

$$ x_{t+1}=\delta + \phi_1x_{t} + \phi_2x_{t-1} + \alpha_{t+1} $$

## Estimating coefficients

The most common approaches to calculating the coefficients for each lag are either maximum likelihood estimation (MLE) or estimation that uses least squares (OLS). The same limitations that these approaches have when fitting a regression of a linear model are present when fitting autoregressive models as well. Depending on whether you're using Python or R and the library, you might be able to use the Yule-Walker or Burg methods in addition to MLE or OLS.

Many libraries allow users to select which criteria to use when selecting models from all the candidate models. For instance, you might want to use the model coefficients to minimize the Akaike Information Criterion or the Bayesian Information Criteria depending on your use case and data.

## Selecting the order of an AR model

Autocorrelation calculates the correlation between a time series and a lagged version of itself. The lag is the number of time units to shift the time series. A lag of 1 compares the series with one previous time step. A lag of 2 compares it with the time step before that one. The degree of autocorrelation at a particular lag shows the temporal dependence of the data. Where the autocorrelation is high, there is a strong relationship between the current value and the value at that lag. Where the autocorrelation is low or close to zero it suggests a weak relationship or no relationship at all.

A common approach to visualize autocorrelation is by calculating the autocorrelation function (ACF) or ACF plot that displays the autocorrelation coefficients at different lags.

The horizontal axis represents the lag, and the vertical axis represents the autocorrelation values. Significant peaks or patterns in the ACF plot can reveal the underlying temporal structure of the data. The selection of the lag order (*p*) in the AR model often relies on the analysis of the ACF plot. In an AR(*p*) model, the current value of the time series is expressed as a linear combination of its past *p* values, with coefficients determined through OLS or MLE. Autocorrelation is also used to assess whether a time series is stationary. For a stationary time series, the autocorrelation should gradually decrease as the lag increases but if the ACF plot doesn't indicate a decrease, the data might contain nonstationarity. You can learn more about autocorrelation [here](https://www.ibm.com/topics/autocorrelation).

## Variants of autoregressive models

There are many different variations of the standard autoregressive time series model that address its challenges and deficiencies.

### Vector autoregressive models

A plain autoregressive statistical model works with univariate datasets, meaning that a dataset must contain one value for each period. Vector autoregressive models (VAR) were developed to allow autoregressions of multivariate time series. They are structured so that each variable is a linear function of past lags of itself and past lags of the other variables. Imagine that you have a time series consisting of two different measurements, the monthly number of plane flights and the monthly number of intercity rail trips. In a VAR model, you might predict the value of using both with a regression for each that includes the other value. Encoding rail trips as *X<sub>r</sub>* and airplane trips as *X<sub>a</sub>* we would have:

$$ x_{t,r} = \alpha_{r} + \phi_{11} x_{t-1,a} + \phi_{12}x_{t-1,r} + \epsilon_{t,r} $$

$$ x_{t,a} = \alpha_{a} + \phi_{11} x_{t-1,a} + \phi_{12}x_{t-1,r} + \epsilon_{t,a} $$

### ARMA and ARIMA

Plain autoregressive models can have difficulties with time series that have a strong trend. Two popular variations of the autoregressive model are the autoregressive moving average (ARMA) and the autoregressive integrated moving average (ARIMA) models. These variations are especially useful when the data has a strong trend. Moving average modeling is another approach to forecasting time series data and ARIMA integrates these two approaches, hence the name. There are also variations on ARIMA models. One of the most common extensions is the vector ARIMA (VARIMA), used when the data is multivariate. Another common extension is seasonal ARIMA (SARIMA) when the data contains a strong seasonality. You can read more about ARIMA models [here](https://www.ibm.com/topics/arima-model).

### Autoregressive conditional heteroscedasticity

Autoregressive models perform much more reliably when the time series data is stationary and the variance across the time series does not vary. Oftentimes the nonstationary data is time differenced to remove changes in variance and then fit an AR model. Sometimes that variance is meaningful and a data scientist wants to leave it in. The autoregressive conditional heteroscedasticity method (ARCH) provides a way to model a change in variance in a time series that is time-dependent, such as increasing or decreasing volatility. An extension of this approach, known as a generalized autoregressive conditional heteroscedasticity (GARCH), allows the method to support changes in the time-dependent volatility. For example, increasing and decreasing volatility in the same series.

When there is a nonstochastic process to changes in time series variances, autoregressive conditional heteroscedasticity or ARCH algorithm can use autoregressive techniques to model and predict changes in dataset volatility. Regular autoregressive models do not model a change in the variance throughout a dataset. Because of this, a data scientist might use a box-cox transform to reduce the variance in the dataset. However, if the change in variance is autocorrelated then an ARCH approach to modeling can provide predictions on when a process might begin to change. This approach is known as volatility forecasting and is commonly used in econometrics and financial analysis. For instance, when working with stock price data, interest might expand beyond modeling potential pricing to forecasting when it begins changing dramatically.

## Other applications of autoregression

Although autoregressive models are commonly associated with time series data, other modeling applications are possible with different types of data.

### Natural language processing

Autoregressive modeling techniques generate the likelihood of sequences of tokens, for instance to suggest a likely next letter or word in predictive text. Autoregressive language models compute the likelihood of each possible token given the previous tokens in the string. Given the chain "the mouse ate the" a model that has seen a reasonable number of English sentences would probably assign a higher probability to "cheese" than "homework". This probability is assigned through an autoregressive process that uses all previous tokens in the chain to assign probabilities to each token in the language model.

### Spatial data

A different application of autoregressive principles is to use the locations of values as a sequence and regress all relevant locations on the location of interest. As an example, we might suspect that the distance from a factory affects air quality readings. An autoregressive model would use the readings from other sites as the lagged values and the distance from the factory as the lags.

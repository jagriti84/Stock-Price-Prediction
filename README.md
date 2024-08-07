# Stock-Price-Prediction
•	A time-series data is a series of data points or observations recorded at different or regular time intervals. In general, a time series is a sequence of data points taken at equally spaced time intervals. The frequency of recorded data points may be hourly, daily, weekly, monthly, quarterly or annually.
•	Time-Series Forecasting is the process of using a statistical model to predict future values of a time-series based on past results.
•	A time series analysis encompasses statistical methods for analyzing time series data. These methods enable us to extract meaningful statistics, patterns and other characteristics of the data. Time series are visualized with the help of line charts. So, time series analysis involves understanding inherent aspects of the time series data so that we can create meaningful and accurate forecasts.
•	Applications of time series are used in statistics, finance or business applications. A very common example of time series data is the daily closing value of the stock index like NASDAQ or Dow Jones. Other common applications of time series are sales and demand forecasting, weather forecasting, econometrics, signal processing, pattern recognition and earthquake prediction.
•	Components of a Time-Series
•	Trend - The trend shows a general direction of the time series data over a long period of time. A trend can be increasing(upward), decreasing(downward), or horizontal(stationary).
•	Seasonality - The seasonality component exhibits a trend that repeats with respect to timing, direction, and magnitude. Some examples include an increase in water consumption in summer due to hot weather conditions.
•	Cyclical Component - These are the trends with no set repetition over a particular period of time. A cycle refers to the period of ups and downs, booms and slums of a time series, mostly observed in business cycles. These cycles do not exhibit a seasonal variation but generally occur over a time period of 3 to 12 years depending on the nature of the time series.
•	Irregular Variation - These are the fluctuations in the time series data which become evident when trend and cyclical variations are removed. These variations are unpredictable, erratic, and may or may not be random.
•	ETS Decomposition - ETS Decomposition is used to separate different components of a time series. The term ETS stands for Error, Trend and Seasonality.
I conduct a time series analysis of stock prices of Apple and also predicted the stock prices.
Types of data in time series
As stated above, the time series analysis is the statistical analysis of the time series data. A time series data means that data is recorded at different time periods or intervals. The time series data may be of three types:-
1 Time series data - The observations of the values of a variable recorded at different points in time is called time series data.
2 Cross sectional data - It is the data of one or more variables recorded at the same point in time.
3 Pooled data- It is the combination of time series data and cross sectional data.

Time series terminologies
There are various terms and concepts in time series that we should know. These are as follows:-
1 Dependence- It refers to the association of two observations of the same variable at prior time periods.
2 Stationarity- It shows the mean value of the series that remains constant over the time period. If past effects accumulate and the values increase towards infinity then stationarity is not met.
3 Differencing- Differencing is used to make the series stationary and to control the auto-correlations. There may be some cases in time series analyses where we do not require differencing and over-differenced series can produce wrong estimates.
4 Specification - It may involve the testing of the linear or non-linear relationships of dependent variables by using time series models such as ARIMA models.
5 Exponential Smoothing - Exponential smoothing in time series analysis predicts the one next period value based on the past and current value. It involves averaging of data such that the non-systematic components of each individual case or observation cancel out each other. The exponential smoothing method is used to predict the short term prediction.
6 Curve fitting - Curve fitting regression in time series analysis is used when data is in a non-linear relationship.
7 ARIMA - ARIMA stands for Auto Regressive Integrated Moving Average.
8 SARIMA – SARIMA stands for Seasonal Autoregressive Integrated Moving Average.



DATA COLLECTION
The data was collected using Tiingo. 
Tiingo is an enterprise-grade API that enables users to download financial data from the Internet. It is possible to access end-of-day stock price data, historical intraday stock price data, and news feeds with curated and tagged content.
Using Pandas data reader the data is converted into a data frame. 
Put the date as the index column. Since the stock market does not perform on weekends and holidays, we do not have data on those days. Hence it is non-continuous data. Applying any time series model to such data is tough since it does not yield good results. Therefore, the data has been converted to the full date range.
When dealing with missing data in a dataset, there are several methods to fill in the gaps. Here are three common methods:
a)	Forward fill involves propagating the last known value forward to replace any missing values that follow it. This technique is useful when the missing data is assumed to be consistent with the most recent previous observation.
b)	Backward fill involves replacing missing values with the next known value in the dataset. This method is useful when it is assumed that the missing data point should take the next observed value.
c)	Linear interpolation estimates missing values by connecting known data points with a straight line. It calculates the value of the missing data point by assuming a linear trend between the two closest known values. This method is useful when the data is expected to change smoothly over time.
Forward fill is often used in stock price data, especially when handling missing values in time series analysis or financial modeling. Therefore, the data has been filled using forward fill.

MOVING AVERAGE
Moving averages are used in technical analysis to identify trends, generate buy and sell signals, and smooth out price data.
A moving average is a statistical technique used to analyze time series data by creating a series of averages of different subsets of the full data set. This method helps smooth out short-term fluctuations and highlight longer-term trends or cycles.
Simple Moving Average (SMA): The simple moving average is calculated by adding up a specified number of the most recent data points and then dividing by that number. It gives equal weight to all data points in the window.
Formula: SMA=P1+P2+⋯+Pnn\text{SMA} = \frac{P_1 + P_2 + \cdots + P_n}{n}SMA=nP1+P2+⋯+Pn Where PiP_iPi represents the data points and nnn is the number of periods.
Exponential Moving Average (EMA): The exponential moving average gives more weight to recent data points, making it more responsive to recent price changes. The weighting decreases exponentially with each older data point.
Formula: EMA=Pt⋅k+EMAt−1⋅(1−k)\text{EMA} = P_t \cdot k + \text{EMA}_{t-1} \cdot (1-k)EMA=Pt⋅k+EMAt−1⋅(1−k) Where:
•	PtP_tPt is the current price.
•	EMAt−1\text{EMA}_{t-1}EMAt−1 is the previous period's EMA.
•	kkk is the smoothing factor, calculated as 2n+1\frac{2}{n+1}n+12, with nnn being the number of periods.
Weighted Moving Average (WMA): The weighted moving average assigns different weights to each data point within the window, often with more recent data points given more weight.
Formula: WMA=∑(wi⋅Pi)∑wi\text{WMA} = \frac{\sum (w_i \cdot P_i)}{\sum w_i}WMA=∑wi∑(wi⋅Pi) Where wiw_iwi represents the weights and PiP_iPi the data points.
SMA is straightforward and is often used to identify long-term trends. It is less sensitive to short-term fluctuations and provides a clear view of the overall direction of the market.
EMA is commonly used in technical analysis to identify trends more quickly than SMA. It reacts more sensitively to recent price changes, making it suitable for capturing short-term trends.
WMA is used when specific weights are required to emphasize certain data points more than others. It can be tailored to give more importance to recent data or any other points deemed significant.
While not traditionally used in stock market analysis, the Savitzky-Golay filter can be applied to stock price data if the goal is to smooth data while preserving features like peaks and troughs. This can be useful in identifying precise moments of change or in the analysis of cyclical patterns.

EMA is generally the most widely used in stock price analysis due to its responsiveness and ability to provide timely signals.

Standardization after applying EMA helps in creating a uniform framework for analyzing, comparing, and interpreting data. It enhances the clarity of signals derived from the EMA, ensures compatibility with further analytical methods, and aids in identifying significant patterns or anomalies in the data.

Exploratory data Analysis

Understanding the trends, seasonality, and cyclic behavior of the data.

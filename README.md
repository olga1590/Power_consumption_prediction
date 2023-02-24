# Power_consumption_prediction
Regression with LSTM


## Objective
Conduct an analysis of multivariate time series of electrical power counsumption and use LSTM to predict future average daily consumption of electricity using the past values, develop and compare different approaches to time-series problems.

## Data
The Household Power Consumption dataset is a multivariate time series dataset that describes the electricity consumption for a single household over four years. The data was collected between December 2006 and November 2010 and observations of power consumption within the household were collected every minute. It is a multivariate series comprised of seven variables (besides the date and time); they are:

- global active power: The total active power consumed by the household (kilowatts).
- global reactive power: The total reactive power consumed by the household (kilowatts).
- voltage: Average voltage (volts).
- global intensity: Average current intensity (amps).
- sub metering 1: Active energy for kitchen (watt-hours of active energy).
- sub metering 2: Active energy for laundry (watt-hours of active energy).
- sub metering 3: Active energy for climate control systems (watt-hours of active energy).

source: http://archive.ics.uci.edu/ml/datasets/Individual+household+electric+power+consumption

## Role
Worked independently for 3 weeks to extract, clean, analyze, visualize household power consumption data and build LSTM models.

In this project I'll test Vanilla LSTM, Stacked LSTM, Bidirectional LSTM and Hybrid LSTM architectures.

## Models and Tools Used
This project was completed with Python's libraries such as Scikit-learn for data analysis, Matplotlib and Seaborn libraries for visualizations, transformers from Feature-engine library and Tensorflow for building LSTM models.

## Results
Power consumption dataset contains 7 features such as global active power, total reactive power, average voltage, active energy for kitchen, laundry and climate control systems consumed by the household. These data were collected every minute, beginning in 2006.

In this project I've dealed with daily predictions, so I've started by sub-sampling the data from 1-minute intervals to 1-day interval.

Resampled dataset had missing values, so I needed to impute NaN values and I checked imputation methods and used for imputation median value as the distribution in variables were skewed a little.

Through time series analysis I found that series are non-stationary, that is average mean and standard deviation are very changeable over time. For this reason I needed some feature engineering with datetime to extract information that could be usefull for model training, such as was that day a weekday or not, labeled quarters and months, day of week and etc. And also made some transformations to reduce the variance: Power Transformation and Wisorizer for capping outliers.

I predicted the electricity consumption for the next day based on the consumption information for the past 7 days and tested four LSTM architectures: Vanilla LSTM, Stacked LSTM, Bidirectional LSTM with Hybrid LSTM.

All four models often failed to predict extremely low or high values. If we see at metric scores we may notice that scores are very similiar but the lowest error valur have Hybrid LSTM:

- The mean absolute error(MAE) in predicting the average consumption of electricity for the next day is 100 watts.
- The mean squared error(MSE) in predicting the average consumption of electricity for the next day is 18 watts.
- The root mean absolute error(RMSE) in predicting the average consumption of electricity for the next day is 135 watts.

** Future research: The prediction of electric power consumption can be improved by trying to discretize the dependent variable and work with the classification problem which I will try to do in the next project.

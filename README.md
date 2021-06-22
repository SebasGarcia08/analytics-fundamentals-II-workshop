# Analytics workshop solution

[Results here](https://wandb.ai/sebastian-garcia-acosta/uncategorized/reports/Grid-search-for-analytics-II-final-workshop--Vmlldzo2NzUyNjg?accessToken=ucn6qexv8fqp5f44gvsdw875hb4yg7xzl4swln3o4qi3sxzrmns6vtffif7891hc)

# Statement

You have been hired by the Texas Commission on Environmental Quality (TCEQ) with the task of building a model that predicts the average temperature of the subsequent days at any given period of the year. You have been provided with a dataset that contains historical records of temperatue, wind speed, etc... from 1998 to 2005. You can access the data and it information via this [link](https://archive.ics.uci.edu/ml/datasets/Ozone+Level+Detection). 

Furhtermore, you would receive a great bonus if your model is also able to predict whether a day will have Ozone peaks or not based on existing features. 

Here is some information about the features:

# Dataset Information:

For a list of attributes, please refer to those two .names files. They use the following naming convention:

All attributes that start with a "T" refer to the temperature measured at different times throughout the day; and those starting with "WS" indicate the wind speed at various times.

- WSR_PK: continuous. Peak wind speed

- WSR_AV: continuous. Average wind speed

- T_PK: continuous. Peak temperature

- T_AV: continuous. Average temperature

- T85: continuous. Temperature at 850 hpa level (or about 1500 m height)

- RH85: continuous. Relative Humidity at 850 hpa

- U85: continuous. U wind - east-west direction wind at 850 hpa

- V85: continuous. V wind - north-sout direction wind at 850 hpa

- HT85: continuous. Geopotential height at 850 hpa

- T70: continuous. T at 700 hpa level (roughly 3100 m height)

- RH70: continuous.

- U70: continuous.

- V70: continuous.

- HT70: continuous.

- T50: continuous. T at 500 hpa level (roughly at 5500 m height)

- RH50: continuous.

- U50: continuous.

- V50: continuous.

- HT50: continuous.

- KI: continuous. K-Index [link](http://www.weather.gov/glossary/index.php?letter=k) 

- TT: continuous. T-Totals [link](http://www.theweatherprediction.com/habyhints/302/)

- SLP: continuous. Sea level pressure

- SLP_: continuous. SLP change from previous day

- Precp: continuous. Precipitation

## Ozone levels known predictors

The following are specifications for several most important attributes that are highly valued by Texas Commission on Environmental Quality (TCEQ). More details can be found in the two relevant papers.

-  O 3 - Local ozone peak prediction

- Upwind - Upwind ozone background level

- EmFactor - Precursor emissions related factor

- Tmax - Maximum temperature in degrees F

- Tb - Base temperature where net ozone production begins (50 F)

- SRd - Solar radiation total for the day

- WSa - Wind speed near sunrise (using 09-12 UTC forecast mode)

- WSp - Wind speed mid-day (using 15-21 UTC forecast mode)

# Part 0. Data (0.5 points)

- Yoy may notice that there are missing values in the data. Use a data imputation technique in order to fill the missing records.

- Try to apply different normalization techniques.

# Part 1. Shallow models (2.5 points)

Apply SHALLOW models (opposed to deep) to develop predictive modelsfor forecasting the temperature of the seventh future day:

- Establish variables from historical data. For instance, you can set data such as the average temperature of the last 3 days, the last 7 days, the last 10 days, etc., the minimum wind speed of the last 3 days, the last 7 days, the last 15 days, etc., the values of the previous day of all the variables, the values of 1 year on the same date, etc...
  
  Create a cross-sectional dataset, estimating the variables to be used every day, or every week, or every month. (0.5 points)

- Apply feature selection techniques such as PCA, LDA and Lasso. (0.5 points) 

- Try SVM, Lasso and Ridge regression models (1 point)

- Try traditional artificial neuronal network models (0.5 points)

Be aware that you must follow a correct evaluation protocol in order to avoid data leakage from the test sets on the normalization and feature selection processes. Mistakes will be punished (-0.5 points)

# Part 2. Convolutional models (2 points + 1 BONUS point)

Consider the data as a multivariate time series and 1-D convolutional neural networks (ConvNets) to predict the temperature of the seventh future day:

Consider the data as time series (do not use forecasting models such as Arima or Holt-Winters, only convolutional networks). 

- You should look for the best data window that allows you the best prediction. The data must then be transformed into a 3D tensor of shape (batch_size, window_size, n_features) (0.5)

- Use 1-D convolutional filters of 1D. Test different architectures in terms of kernel sizes, convolutional and dense layers. For example, for 60-day windows, 32 Kernels of 3, 5, 7 days can be defined in a first layer. (1 point)

- Apply and evaluate the impacts of using dropout layers and lasso/ridge regularizations with different hyper-parameter values. (0.5)

- **(BONUS)** Add another output neuron to the existing ConvNet in order to classify whether the next days will have Ozone peaks or not. You may try the TensorFlow's [functional API](https://towardsdatascience.com/multi-output-model-with-tensorflow-keras-functional-api-875dd89aa7c6) in order to implement a multi-output model. (1 additional point)

As with the shallow models, it is important to establish a well designed evaluation protocol that allows for the comparison of the different architectures.



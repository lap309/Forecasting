# Forecasting Methods
Naive Method:<br>
_All forecasts for the future are equal to the last observed value of the series (good for economic and financial time series) <br>
The  most revent observation is the only importnat one, and all previous observations provide no information for the future_<br>
<br>
Average Method:<br>
_Future forecasts are calculated as the average of the all previous data <br>
Assumes that all previous observations are of equal importance and reeives equal weights<br>
Ex: t_3 = avg(t_1, t_2)	    t_4 = avg( t_1, t_2, t_3)	t_5 = avg(t_1, t_2, t_3, t_4) ………._

Seasonal Naïve Method: <br>
_Each forecast is equal to the last observed value from the same season (ex: the same month of the previous year) <br>
Ex: with monthly data, the forecast for all future February values is equal to the last observed February value
    With quarterly data, the forecast of all future Q2 values is equal to the last observed Q2 value_ <br>
<br>
Drift Method: <br>
_A variant on the naïve method but it allows the forecast to increase or decrease over time. The amount of change over time (drift) is the average change seen in historical data_
![image](https://github.com/lap309/Forecasting/assets/69564111/6f7e3766-1c06-47cb-b248-d6482952ef66)

# Measurement Metrics

__Sum of Squared Errors (SSE)__ [minimize]: <br>
will always select the model with the most variables so not an ideal way to selecting predictors <br>
<br>
__Akaike's Information Criterion (AIC)__ [minimize]: <br>
similar to SSE but penalizes the fit of the model based on the number of parameters that are included. The model with the minimum value of the AIC is often the best model for forecasting <br>
<br>
__Corrected AIC:__ <br>
for small time series datasets, the AIC equation id modified with bias-corection <br>
<br>
__Bayesian Information Criterion (BIC)__ [minimize]: <br>
similar to AIC, but implements a heavier penalization for the use of more parameters. Many statisticians like BIC because it is typically equivalent to AIC or chooses a model with slightly less variables, which is always good.

__Root Mean Squared Error (RMSE)__ [minimize]: <br>
Used to gauge the average distance (error) between the predicted value and the actual value. Typically used in predictive models. KEEP IN MIND, that while we want the RMSE to generally be lower, the data is still subject to uncertainty/randomness/noise, and thus a lower RMSE score does not always gaurantee a better model. For this reason, it is advised to combine RMSE scores with visualizations to explain how the model performs.

Compute the error (the difference between the predicted and actual) for each observation<br>
Square the errors. This is done because the difference will be positive or negative depending on the observation,  and we want to avoid having a zero summation. <br>
Summate the squared errors <br>
Divide by the total number of observations (to compute the mean. This is the Mean Squared Error)
Take the square root to get the RMSE

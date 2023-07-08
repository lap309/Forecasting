# Exponential Smoothing
Forecast using weighted averages of past observations, with the weights decaying exponentially as the observations get older. The weights attached to each observation descreases exponentially as we go back in time. In other words, the more recent the observation the higher the associated weight. 
<br>
<br>
### α { [0,1]
is the smoothing parameter that determines... This must be chosen/specified before running the model. <br>
If alpha is small (close to zero), more weight is given to observations from the more distant past <br>
If alphs ia large (closer to 1), more weight is given to the more recent observations.<br>
<br>
The _α_ parameter is often choosen based off of previous experience or, more reliably and objectively, estimated from the observed data. These can be estimated by minimizing the Sum of Square Errors (SSE), although this involves an optimization tool
<br>
<br>
### Simple exponential smoothing (SES) (non-stationary) <br>
This method is suitable for forecasting data with no clear trend or seasonal pattern. <br>
<br>
__Weighted Average Form__
Each forecast is equal to a weighted average between the most recent observation and the previous forecast. The important thing to note, is the given clause that composes the forecasting equation.<br>
$$y_T+1 = y_T + y_T|T-1$$
<br>
<br>
__Component Form__ <br>
Similar to how time series decomposition is comprised of three different parts (trend, seasonality, residual), the component form for SES has a forecast equation and a smoothing equation. <br>
With some manipulation, the component form will be equivalent to the weighte daverage form, but this model is mostly particularly useful if other components are added. <br>
<br>



Naive Method:<br>
_All forecasts for the future are equal to the last observed value of the series_ <br>
_The  most revent observation is the only importnat one, and all previous observations provide no information for the future_<br>
<br>
Average Method:<br>
_Future forecasts are calculated as the average of the all previous data_ <br>
_Assumes that all previous observations are of equal importance and reeives equal weights_

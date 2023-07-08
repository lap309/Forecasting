# Exponential Smoothing
Forecast using weighted averages of past observations, with the weights decaying exponentially as the observations get older. The weights attached to each observation descreases exponentially as we go back in time. In other words, the more recent the observation the higher the associated weight. 
<br>
### α { [0,1]
is the lvel smoothing parameter that determines... This must be chosen/specified before running the model. <br>
If alpha is small (close to zero), more weight is given to observations from the more distant past <br>
If alphs ia large (closer to 1), more weight is given to the more recent observations
<br>
### β { [0,1]
 is the smoothing parameter for trend/slope. Smaller value of β means a smaller slope and smaller change over time <br>
<br>
 These parameters are often choosen based off of previous experience or, more reliably and objectively, estimated from the observed data. These can be estimated by minimizing the Sum of Square Errors (SSE), although this involves an optimization tool
<br>
<br>
### Simple exponential smoothing (SES) (stationary)
_Parameters:_ α <br>
This method is suitable for forecasting data with no clear trend or seasonal pattern. <br>
<br>
__Weighted Average Form__ <br>
Each forecast is equal to a weighted average between the most recent observation and the previous forecast. The important thing to note, is the given clause that composes the forecasting equation, as it is a one step equation (forecasting one value at a time).
$$y_T+1 = y_T + y_T|T-1$$
__Component Form__ <br>
Similar to how time series decomposition is comprised of three different parts (trend, seasonality, residual), the component form for SES has a forecast equation and a smoothing equation. <br>
With some manipulation, the component form will be equivalent to the weighted average form, but this model is mostly particularly useful if other components are added. <br>
<br>

### Holt's Linear Trend Model (non-stationary-trend) <br>
_Parameters:_ α, β* <br>
An extension of Simple Exponential Smoothing that allows forecasting with a trend in the data <br>
It is comprised of three components:<br>
- Forecast Equation: Last predicted value + h* last identified trend<br>
- Level Equation: Estimate of the values of the series by calculated the weighted average of observation y_t and the one-step-ahead training forecasts for time _t_ <br>
- Trend Equation: Estimate of the trend (slope) of the time series at time t by calculating the weighted average of the estimated trend at time _t_ based on the previous estimate of the trend
<br>
The forecast becomes an h-step ahead forecast equal to the last estimated value, plus _h_ times the last estimated trend value. This is essentially a linear function of _h_ where h specifies the number of steps in each forecast. <br>
However, this model displays a constand trend (increasing or decreasing), which has been proven to over-forecast, specifically for longer forecast horizons. Methods to avoid this are discussed below.

#### Damped Trend Methods (non-stationary-trend)
_Parameters:_ α, β*, and ϕ <br>
The "dampen" parameter (ϕ, [0,1]) dampens the trend to a flat line some time in the future and is a highly successful method<br>
For values 0<ϕ<1, the parameter dampesn the trend so that it approaches a constant at some time in the future. This means that short-run forecasts are trended while long-run forecasts are constant<br>
Very low values of ϕ has a very strong effect for smaller values and will make the slope converge quickly. <br>
One the other side, if ϕ = 1, the method is identifcal to Holt's linear model, for that reason, ϕ is rarely less than 0.8 and rarely greater than 0.98.

#### Holt-Winters Seasonal Method (non-stationary-seasonal)
_Parameters:_ α, β*, m,and γ <br>
_m_ denotes the frequency of the seasonality<br>
The seasonality has two types of seasonal components: <Br>
- additive: prefered when seasonal variations are roughly constant through the time series
- multiplicative: preferred if seasonal variation increases as time moves on. The seasonal variation gets larger overtime (similar to the ideology of heterscedacity and variance)<br>
_note: damping is possible with both additive and multiplicative Holt-Winters methods_
<br>
The forecasting equation is the same as the Holt Trend Model, with the addition of the seasonal component:<br>
- Forecast Equation: l + T + s or (l+t)* s for additive and multiplicative respectively
- Level Equation: Estimate of the values of the series by calculated the weighted average between the seasonally adjusted obervations and the non-seasonal forecast for time t <br>
- Trend Equation: same as Holt's linear method
- seasonal equation: weighted average between the current seasonal index and the seasonal index of the same season m time periods ago

## Choosing a Model
You can use tiem series cross-validation to compare the one-step forecast accuracy of the three methods, and whichever one has the smallest MAE or MSE value can move on to the final forecast.
(![image](https://github.com/lap309/Forecasting/assets/69564111/ecb5710c-b768-4f7b-90d9-a8cc90edd1b3)
)

__Measurements to Consider__ <br>
For all of these measurments, the loewr the better <br>
- Sum Squared Errors<br>
- AIC <br>
- BIC <br>

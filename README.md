# Pricing-Predictions-on-Energy
Predictions on producer energy prices across European Union countries.

# Business Understanding
The highest increase in industrial producer prices in the euro area was recorded in the energy sector in 2022. Producer energy prices are an early indication of trends in consumer prices, which the European Central Bank want to keep at 2.0% in the medium term. 

Energy producer prices affect household energy and non-energy prices. An energy producer increase in the price by 1% over 12 months caused, household energy prices going up by 0.4% and household non-energy prices also going up by 0.04%, on average in the euro área for 2000-2022 (Darvas et al., 2022). Thus, producer energy price is a predictor of what may show up in the economy in the coming months.

After all the aforesaid, the objective of this project is to predict producer energy prices in the EU, to provide some ligth on how the european economy will be in the future.

# Data preparation and understanding
We concentrate the analysis on the data of the energy sector from the **27 European Union (EU) countries** during **the 2000-2022 period**, analyzing monthly information.

We use the following data based on the principles of cause and effect:
* **Producer prices of energy for the 27 EU countries (EU27_2020)** (energy producer prices): producer prices are also known as output prices. We use the domestic output price for the energy sector, which measures the average price development of all goods and related services resulting from that sector and sold on the domestic market. We look for the statistical classification of the energy sector in the European Community (NACE Rev. 2), which is defined by the energy main industrial grouping (MIG_NRG). **Producer prices come from [Eurostat](https://ec.europa.eu/eurostat/databrowser/view/sts_inppd_m/default/table?lang=en)**.
* **Producer prices of energy for each of the 27 EU countries**: data info same as before.  
* **Harmonised index of consumer prices for the 27 EU countries** (consumer price): it is an economic indicator that measures the change over time of the prices of consumer goods and services acquired by households. **Harmonised index of consumer prices come from [Eurostat](https://ec.europa.eu/eurostat/databrowser/view/EI_CPHI_M__custom_4287569/default/table?lang=en)**. 
* **Industrial production index** (industrial production): it shows the output and activity of the industry sector. It measures changes in the volume of output on a monthly basis. **Industrial production index comes from [Eurostat](https://ec.europa.eu/eurostat/databrowser/view/STS_INPR_M__custom_4288019/default/table?lang=en)**.
* **GDP and main components(output, expenditure and income)**: it provides an overall picture of the economic situation and are widely used for economic analysis and forecasting, policy design and policy making. **GDP and main components come from [Eurostat](https://ec.europa.eu/eurostat/databrowser/view/NAMQ_10_GDP__custom_4287774/default/table)**.

Concerning data collection and cleaning, data was loaded from the sources listed above. Outliers were controlled but not deemed to be eliminated. Imputations were only performed on the GDP based on a linear regressions, as it was provided quarterly. The data values were controlled, they were in adequate ranges.

We observe producer prices of energy presents higher volatility compared with the others indicators. It exists correlation among energy producer prices and consumer prices (0.89), and energy producer prices and GDP (0.81). 

Energy producer prices affect consumer prices and GDP. An energy producer increase in the price by 1% promoted, consumer prices going up by 0.27% and GDP also going up by 0.17%, on average in the euro área for 2000-2022. We can observe a lagged effect among the different indicators in the following graph.

<p align="center">
<img src="./images/Indicators.png" alt="drawing" align="center" width="900"/>
</p>

The visualization of the european energy producer prices in the 2000-2022 period reveal the highest prices are reached in 2022.

<p align="center">
<img src="./images/European prices yearly.png" alt="drawing" align="center" width="510"/>
</p>

The visualization of the energy producer prices in each EU country for 2022 reveals the highest prices are reached in Denmark, Belgium, and Romania.

<table><tr>
<td> <img src="./images/Energy producer prices country 2022.png" alt="drawing" align="center" height="637"/> </td>
<td> <img src="./images/European prices 2022.png" alt="drawing" align="center" width="474"/> </td>
</tr></table>

We analyze if time series (TS) are stationary using Augmented Dickey-Fuller (ADF) and Hurst’s exponent test. These tests indicate TS are most likely non-stationary. We detrend energy producer prices by differencing it, but non-stationary continues. 

We check the Autocorrelation Function (ACF) and Partial Autocorrelation Function (PACF) for Energy producer prices TS. We observe the presence of the trend, as the plot of the ACF shows coefficients are high for short lags, and they decrease linearly as the lag increases (an exponential drop). We don not perceive seasonality, as the plot do not display cyclical patterns (an sinusoidal).

<p align="center">
<img src="./images/autocorrelation.png" alt="drawing" align="center" width="350"/>
</p>

We visualize the trend an seasonality evolution for energy producer prices TS using the Box Plot. We observe seasonality remains more or less contant, likely July and September show higher prices, and February and December lower prices. In term of the trend, we observe peaks in 2008, 2012, 2018 and 2022, which correspond with other years of price shocks. The highest energy producer prices volatility was in 2021 and 2022.

<p align="center">
<img src="./images/Trend seasonality box plot.png" alt="drawing" align="center" width="637"/>
</p>

# Modelling
We use the following models to predict producer energy prices across European Union countries.

**TIME SERIES MODELS**
* CASE 1: SARIMA (Seasonal ARIMA) Model – Univariate Modelling
* CASE 2: SARIMAX Adding external variables (X) to the SARIMA model – Multivariate Modelling
**SUPERVISED MACHINE LEARNING MODELS**
* CASE 3: Gradient Boosting with XGBoost
* CASE 4: LightGBM model
* CASE 5: Ensemble with StandardScaler, PCA and XGBRegressor
**ADVANCED MACHINE AND DEEP LEARNING MODELS**
* CASE 6: Combining CNN with Long Short-Term Memory (LSTM)
* CASE 7: Recurrent Neural Networks (RNN): SimpleRNN, GRU, and LSTM
   * CASE 7.1: RNN with one LTSM layer
   * CASE 7.2: RNN with three-layer LSTM
   * CASE 7.3: Gated Recurrent Unit (GRU) with 3 layers
   * CASE 7.4: three layers of SimpleRNN
* CASE 8: Prophet
   * CASE 8.1: Prophet without Transformation
   * CASE 8.2: Prophet with Box-Cox Transformation
* CASE 9: Amazon's DeepAR

SARIMAX provide the best results as the time series part is more present than the external variables part. If the external variables alone could explain a lot and this complemented by a part of autocorrelation or seasonality, supervised models may be the better choice... but this is not our case. 

We use SARIMAX with producer energy prices lag-1..lab-12 as exogenous variables. For this multivariate model, we use the auto_arima function imported from pmdarima.arima. We obtain the following metrics for our test sample: 
 
* MAE  2.1157
* MAPE 0.0151
* R2 Score 0.9836

It is important to say, our best prediction has been traines with the producer energy prices of the 2001..2009 period. We must say, the previous most disruptive oil price shocks before 2022 occurred in 2005-2008 and 2010-2014:
- The first (2005-2008) resulted from increased demand generated by economic growth in China and India. At that time, OPEC was unable to expand production due to long-term lack of investment.
- The second (2010-2014) shock reflected the impacts of Arab Spring pro-democracy protests in the Middle East and North Africa, combined with conflict in Iraq and international sanctions that Western nations placed on Iran to slow its nuclear weapons program. Together, these events pushed oil prices above $100 per barrel for a four-year stretch – the longest such period on record. Relief finally came via a flood of new oil from shale production in the U.S.

Some events ocurring during the 2001..2009 period were:
- 2001-2003: 9/11 and invasion of Iraq raise concerns about Middle East stability: Venezuelan oil workers strike
- 2008: Global Financial Crisis 
- Crude oil reached an all time high of 147.27 in July of 2008.

# Evaluation

# Deployment

# Conclusion

The extent to which EU countries implement a strong and united policy response to the energy crisis will define the continent’s macroeconomic outlook for 2023. Should EU countries slip into energy nationalism, they will get higher energy prices and thus even higher inflation, higher interest rates and lower economic growth. In contrast, good policies in the form of an EU energy grand bargain would contain the direct impact of the energy crisis on households and firms and would stabilise inflation, reducing the need for further interest rate hikes and allowing an earlier recovery. Though avoiding recession is unlikely, making the right policy decisions will give Europe significant control over its short-term economic destiny.

# Bibliography

* *Darvas, Z., Le Mouel, M., Tagliapietra, S., Zettelmeyer, J. 2022. How European Union energy policies could mitigate the coming recession. Bruegel. https://www.bruegel.org/blog-post/how-european-union-energy-policies-could-mitigate-coming-recession-0*

-------------------

* *Baldwin, E., Carley, S., Brass, J. N., & MacLean, L. M. 2016. Global renewable electricity policy: A comparative policy analysis of countries by income status. Journal of Comparative Policy Analysis: Research and Practice, 19(3): 277-298.*
* *Carley, S. 2009. State renewable energy electricity policies: An empirical evaluation of effectiveness. Energy Policy, 37(8): 3071-3081.*
* *Guterres, A. 2019. Remarks to high-level political forum on sustainable development. 24 September 2019, United Nations Secretary General.*
* *Romano, A. A., & Scandurra, G. 2014. Investments in renewable energy sources in OPEC members: A dynamic panel approach. Metodoloski Zvezki, 11(2): 93-106.*
* *Romano, A. A., Scandurra, G., Carfora, A., & Fodor, M. 2017. Renewable investments: The impact of green policies in developing and developed countries. Renewable and Sustainable Energy Reviews, 68: 738-747.*
* *Sachs, J., Schmidt-Traub, G., Kroll, C., Lafortune, G., & Fuller, G. 2020. The sustainable development goals and COVID-19. Sustainable development report 2020. Cambridge: Cambridge University Press.*

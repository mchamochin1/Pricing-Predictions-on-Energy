# Pricing-Predictions-on-Energy
Predictions on producer energy prices across European Union countries.

# Business Understanding
The highest increase in industrial producer prices in the euro area was recorded in the energy sector in 2022. Producer energy prices are an early indication of trends in consumer prices, which the European Central Bank want to keep at 2.0% in the medium term. 

Energy producer prices affect household energy and non-energy prices. An energy producer increase in the price by 1% over 12 months caused, household energy prices going up by 0.4% and household non-energy prices also going up by 0.04%, on average in the euro área for 2000-2022 (Darvas et al., 2022). Thus, producer energy price is a predictor of what may show up in the economy in the coming months.

After all the aforesaid, the objective of this project is to predict producer energy prices in the EU, to provide some ligth on how the european economy will be in the future.

# Data understanding
We concentrate the analysis on the data of the energy sector from the **27 European Union (EU) countries** during **the 2000-2022 period**, analyzing monthly information.

We use the following data based on the principles of cause and effect:
* **Producer prices of energy for the 27 EU countries (EU27_2020)** (energy producer prices): producer prices are also known as output prices. We use the domestic output price for the energy sector, which measures the average price development of all goods and related services resulting from that sector and sold on the domestic market. We look for the statistical classification of the energy sector in the European Community (NACE Rev. 2), which is defined by the energy main industrial grouping (MIG_NRG). **Producer prices come from [Eurostat](https://ec.europa.eu/eurostat/databrowser/view/sts_inppd_m/default/table?lang=en)**.
* **Producer prices of energy for each of the 27 EU countries**: data info same as before.  
* **Harmonised index of consumer prices for the 27 EU countries** (consumer price): it is an economic indicator that measures the change over time of the prices of consumer goods and services acquired by households. **Harmonised index of consumer prices come from [Eurostat](https://ec.europa.eu/eurostat/databrowser/view/EI_CPHI_M__custom_4287569/default/table?lang=en)**. 
* **Industrial production index** (industrial production): it shows the output and activity of the industry sector. It measures changes in the volume of output on a monthly basis. **Industrial production index comes from [Eurostat](https://ec.europa.eu/eurostat/databrowser/view/STS_INPR_M__custom_4288019/default/table?lang=en)**.
* **GDP and main components(output, expenditure and income)**: it provides an overall picture of the economic situation and are widely used for economic analysis and forecasting, policy design and policy making. **GDP and main components come from [Eurostat](https://ec.europa.eu/eurostat/databrowser/view/NAMQ_10_GDP__custom_4287774/default/table)**.

# Data Preparation

Concerning data collection and cleaning, data was loaded from the sources listed above. Outliers were controlled but not deemed to be eliminated. Imputations were only performed on the GDP based on a linear regressions, as it was provided quarterly. The data values were controlled, they were in adequate ranges.

We observe producer prices of energy presents higher volatility compared with the others indicators. It exists correlation among energy producer prices and consumer prices (0.89), and energy producer prices and GDP (0.81). 

Energy producer prices affect consumer prices and GDP. An energy producer increase in the price by 1% promoted, consumer prices going up by 0.27% and GDP also going up by 0.17%, on average in the euro área for 2000-2022. We can observe a lagged effect among the different indicators in the following graph.

<p align="center">
<img src="./images/Indicators.png" alt="drawing" align="center" width="900"/>
</p>

The visualization of the energy producer prices in each EU country for 2022 reveals the highest prices are reached in Denmark, Belgium, and Romania.

<p align="center">
<img src="./images/Energy producer prices country 2022.png" alt="drawing" align="center" height="500"/>
</p>

<p align="center">
<img src="./images/European prices 2022.png" alt="drawing" align="center" width="500" />
</p>

<ul>
    <li><img src="./images/Energy producer prices country 2022.png" alt="drawing" ></li>
    <li><img src="./images/European prices 2022.png" alt="drawing"></li>
</ul>

# Modelling

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

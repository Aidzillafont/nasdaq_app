# Install guide

```python
pip install nasdaq-data
```

# How to
First import and create an instance of your nasdaq data grabber object


```python
from nasdaq_data import nasdaq_grabber as ng
```


```python
my_ng = ng() 
```

## Get Top Stocks by Market Cap
Call nasdaq_stocks and input the number of tickers you want and you will get info on stocks in order of Market Cap


```python
my_ng.nasdaq_stocks(10)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>symbol</th>
      <th>name</th>
      <th>lastsale</th>
      <th>netchange</th>
      <th>pctchange</th>
      <th>marketCap</th>
      <th>url</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>AAPL</td>
      <td>Apple Inc. Common Stock</td>
      <td>$150.43</td>
      <td>-2.31</td>
      <td>-1.512%</td>
      <td>2,608,056,056,200</td>
      <td>/market-activity/stocks/aapl</td>
    </tr>
    <tr>
      <th>1</th>
      <td>MSFT</td>
      <td>Microsoft Corporation Common Stock</td>
      <td>$237.92</td>
      <td>-3.06</td>
      <td>-1.27%</td>
      <td>1,774,381,634,186</td>
      <td>/market-activity/stocks/msft</td>
    </tr>
    <tr>
      <th>2</th>
      <td>GOOG</td>
      <td>Alphabet Inc. Class C Capital Stock</td>
      <td>$99.17</td>
      <td>-1.40</td>
      <td>-1.392%</td>
      <td>1,293,573,480,000</td>
      <td>/market-activity/stocks/goog</td>
    </tr>
    <tr>
      <th>3</th>
      <td>GOOGL</td>
      <td>Alphabet Inc. Class A Common Stock</td>
      <td>$98.74</td>
      <td>-1.40</td>
      <td>-1.398%</td>
      <td>1,287,964,560,000</td>
      <td>/market-activity/stocks/googl</td>
    </tr>
    <tr>
      <th>4</th>
      <td>AMZN</td>
      <td>Amazon.com, Inc. Common Stock</td>
      <td>$113.78</td>
      <td>-3.53</td>
      <td>-3.009%</td>
      <td>1,157,926,339,396</td>
      <td>/market-activity/stocks/amzn</td>
    </tr>
    <tr>
      <th>5</th>
      <td>TSLA</td>
      <td>Tesla, Inc. Common Stock</td>
      <td>$275.33</td>
      <td>-13.26</td>
      <td>-4.595%</td>
      <td>862,738,307,490</td>
      <td>/market-activity/stocks/tsla</td>
    </tr>
    <tr>
      <th>6</th>
      <td>BRK/A</td>
      <td>Berkshire Hathaway Inc.</td>
      <td>$404485.25</td>
      <td>-889.76</td>
      <td>-0.219%</td>
      <td>594,946,837,609</td>
      <td>/market-activity/stocks/brk/a</td>
    </tr>
    <tr>
      <th>7</th>
      <td>BRK/B</td>
      <td>Berkshire Hathaway Inc.</td>
      <td>$267.77</td>
      <td>-0.74</td>
      <td>-0.276%</td>
      <td>590,783,995,813</td>
      <td>/market-activity/stocks/brk/b</td>
    </tr>
    <tr>
      <th>8</th>
      <td>UNH</td>
      <td>UnitedHealth Group Incorporated Common Stock (DE)</td>
      <td>$513.61</td>
      <td>-3.85</td>
      <td>-0.744%</td>
      <td>480,421,913,683</td>
      <td>/market-activity/stocks/unh</td>
    </tr>
    <tr>
      <th>9</th>
      <td>JNJ</td>
      <td>Johnson &amp; Johnson Common Stock</td>
      <td>$166.72</td>
      <td>0.54</td>
      <td>0.325%</td>
      <td>438,336,872,094</td>
      <td>/market-activity/stocks/jnj</td>
    </tr>
  </tbody>
</table>
</div>



## Get Historical Prices
Pass a start date and end date in ISO format along with your ticker to nasdaq_historical_price to get historical prices


```python
from dateutil.relativedelta import relativedelta
import time
import datetime as dt

#today
t = dt.date.today().replace(day=1)
#one year ago
t0 = t - relativedelta(years=1)

#isoformat
iso_t0, iso_t = t0.isoformat(), t.isoformat()

my_ng.nasdaq_historical_price('AAPL', iso_t0, iso_t)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>date</th>
      <th>close</th>
      <th>volume</th>
      <th>open</th>
      <th>high</th>
      <th>low</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>09/01/2022</td>
      <td>$157.96</td>
      <td>74,229,900</td>
      <td>$156.64</td>
      <td>$158.42</td>
      <td>$154.67</td>
    </tr>
    <tr>
      <th>1</th>
      <td>08/31/2022</td>
      <td>$157.22</td>
      <td>87,991,090</td>
      <td>$160.305</td>
      <td>$160.58</td>
      <td>$157.14</td>
    </tr>
    <tr>
      <th>2</th>
      <td>08/30/2022</td>
      <td>$158.91</td>
      <td>77,906,200</td>
      <td>$162.13</td>
      <td>$162.56</td>
      <td>$157.72</td>
    </tr>
    <tr>
      <th>3</th>
      <td>08/29/2022</td>
      <td>$161.38</td>
      <td>73,313,950</td>
      <td>$161.145</td>
      <td>$162.9</td>
      <td>$159.82</td>
    </tr>
    <tr>
      <th>4</th>
      <td>08/26/2022</td>
      <td>$163.62</td>
      <td>78,960,980</td>
      <td>$170.57</td>
      <td>$171.05</td>
      <td>$163.56</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>248</th>
      <td>09/08/2021</td>
      <td>$155.11</td>
      <td>74,420,210</td>
      <td>$156.98</td>
      <td>$157.04</td>
      <td>$153.975</td>
    </tr>
    <tr>
      <th>249</th>
      <td>09/07/2021</td>
      <td>$156.69</td>
      <td>82,278,260</td>
      <td>$154.97</td>
      <td>$157.26</td>
      <td>$154.39</td>
    </tr>
    <tr>
      <th>250</th>
      <td>09/03/2021</td>
      <td>$154.3</td>
      <td>57,866,070</td>
      <td>$153.76</td>
      <td>$154.63</td>
      <td>$153.09</td>
    </tr>
    <tr>
      <th>251</th>
      <td>09/02/2021</td>
      <td>$153.65</td>
      <td>71,171,320</td>
      <td>$153.87</td>
      <td>$154.72</td>
      <td>$152.4</td>
    </tr>
    <tr>
      <th>252</th>
      <td>09/01/2021</td>
      <td>$152.51</td>
      <td>80,313,710</td>
      <td>$152.83</td>
      <td>$154.98</td>
      <td>$152.34</td>
    </tr>
  </tbody>
</table>
<p>253 rows × 6 columns</p>
</div>



## Get Stocks Financal Data
Call nasdaq_financals and pass in a frequency you desire 
1. Annual
2. Semi Annual


```python
my_ng.nasdaq_financals('AAPL', 1)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>symbol</th>
      <th>tabs.incomeStatementTable</th>
      <th>tabs.balanceSheetTable</th>
      <th>tabs.cashFlowTable</th>
      <th>tabs.financialRatiosTable</th>
      <th>incomeStatementTable.headers.value1</th>
      <th>incomeStatementTable.headers.value2</th>
      <th>incomeStatementTable.headers.value3</th>
      <th>incomeStatementTable.headers.value4</th>
      <th>incomeStatementTable.headers.value5</th>
      <th>...</th>
      <th>cashFlowTable.headers.value3</th>
      <th>cashFlowTable.headers.value4</th>
      <th>cashFlowTable.headers.value5</th>
      <th>cashFlowTable.rows</th>
      <th>financialRatiosTable.headers.value1</th>
      <th>financialRatiosTable.headers.value2</th>
      <th>financialRatiosTable.headers.value3</th>
      <th>financialRatiosTable.headers.value4</th>
      <th>financialRatiosTable.headers.value5</th>
      <th>financialRatiosTable.rows</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>AAPL</td>
      <td>Income Statement</td>
      <td>Balance Sheet</td>
      <td>Cash Flow</td>
      <td>Financial Ratios</td>
      <td>Period Ending:</td>
      <td>9/25/2021</td>
      <td>9/26/2020</td>
      <td>9/28/2019</td>
      <td>9/29/2018</td>
      <td>...</td>
      <td>9/26/2020</td>
      <td>9/28/2019</td>
      <td>9/29/2018</td>
      <td>[{'value1': 'Net Income', 'value2': '$94,680,0...</td>
      <td>Period Ending:</td>
      <td>9/25/2021</td>
      <td>9/26/2020</td>
      <td>9/28/2019</td>
      <td>9/29/2018</td>
      <td>[{'value1': 'Liquidity Ratios', 'value2': '', ...</td>
    </tr>
  </tbody>
</table>
<p>1 rows × 29 columns</p>
</div>



## Get Other Data

Calling the nasdaq_data function and supplying type to any of the numbers below will get you 

1. Analyst Target Price and Ratings
2. PEG Ratio
3. Momentum Estimate
4. Earnings Forecast
5. Earnings Surprise
6. EPS


```python
#analysts ratings
my_ng.nasdaq_data('AAPL',1)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>symbol</th>
      <th>historicalConsensus</th>
      <th>consensusOverview.lowPriceTarget</th>
      <th>consensusOverview.highPriceTarget</th>
      <th>consensusOverview.priceTarget</th>
      <th>consensusOverview.buy</th>
      <th>consensusOverview.sell</th>
      <th>consensusOverview.hold</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>aapl</td>
      <td>[{'z': {'buy': 19, 'hold': 5, 'sell': 0, 'date...</td>
      <td>136.0</td>
      <td>220.0</td>
      <td>183.45</td>
      <td>23</td>
      <td>1</td>
      <td>4</td>
    </tr>
  </tbody>
</table>
</div>




```python
#PEG Ratio
my_ng.nasdaq_data('AAPL',2)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>pegr.label</th>
      <th>pegr.text</th>
      <th>pegr.pegValue</th>
      <th>per.peRatioChart</th>
      <th>per.label</th>
      <th>per.text</th>
      <th>per.dataProvider</th>
      <th>gr.peGrowthChart</th>
      <th>gr.title</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Forecast 12 Month Forward PEG Ratio</td>
      <td>Investors are always looking for companies wit...</td>
      <td>1.95</td>
      <td>[{'x': '2021 Actual', 'y': 26.81}, {'x': '2022...</td>
      <td>Price/Earnings Ratio</td>
      <td>Price/Earnings Ratio is a widely used stock ev...</td>
      <td>&lt;b&gt;Data Provider:&lt;/b&gt; Zacks Investment Research</td>
      <td>[{'z': 'Growth', 'x': '2022', 'y': 8.8}, {'z':...</td>
      <td>Forecast P/E Growth Rates</td>
    </tr>
  </tbody>
</table>
</div>

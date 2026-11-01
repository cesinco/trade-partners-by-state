# Primary Import and Export Countries by State

## Background

Following the announcement by the new administration to raise tariffs on Canada, Mexico, and China (and the not entirely unexpected retaliatory measures from those targeted countries), it would be interesting to know which countries are the primary sources and destinations for imports and exports.

This data can be viewed using the US government’s International Trade Administration the page located at [https://www.trade.gov/data-visualization/tradestats-express-state-trade-product](https://www.trade.gov/data-visualization/tradestats-express-state-trade-product) although that page is simply a container for n iframe whose contents are actually located at [https://tsereports.trade.gov/views/StateAnnualDashboardLive_16421978287720/StateTradebyPartners?%3Atoolbar=yes%2Ctop&%3AshowVizHome=no&%3Aembed=true](https://tsereports.trade.gov/views/StateAnnualDashboardLive_16421978287720/StateTradebyPartners?%3Atoolbar=yes%2Ctop&%3AshowVizHome=no&%3Aembed=true) and are themselves created using Tableau.

However, scraping this page is problematic, not least becuase of all the DOM selector work that needs to be done, as well as interacting with the page once it loads (to click on combo box items, etc.), but also because the embedded link contained within the iframe changes constantly (by the time you check again, this link may no longer be valid, even though as of this writing, it is working).

Instead, we can go to the source of this data which is actually hosted on the US government's census.gov site and source the required data using the available API.

After acquiring the data, we also want to display it graphically using a map of the USA to show each state’s dependence on their primary export and import partners. For this, we will employ Choropleth maps.

You can view the resulting notebook file [get_top_export_countries_by_state.ipynb](get_top_export_countries_by_state.ipynb)

## Output

The resulting images that the notebook generates are the following

![export_countries_by_state.png](./images/export_countries_by_state.png)

![import_countries_by_state.png](./images/import_countries_by_state.png)

## Comments

### Original Tariff Anouncment around Feb. 2025

Following the reaction of investors and the destruction of value in the stock markets upon the administration announcing that the tariffs would be imposed, the administration quickly backtracked allegedly for a 30-day reprieve (which, given our understanding of the new president, will likely never be mentioned again) for both Canada and Mexico. Now seeing who the largest trading partners are (~80% of states export primarily to Canada or Mexico, and ~67% of states import primarily from Canada or Mexico), had the tariffs remained in place, the pain on exporters and consumers would have been significant.

### New Tariff Anouncement on Canada in Aug. 2026

Following the announcement that Canada will suffer tariffs of 50% on exports to the USA,
and the reciprocal tariffs enacted by Canada on US exports, based on the stats collected
from the trade.gov website show that the following states all have the percent of goods
and exports to Canada in proportion to the exports to the entire world exceeding
the national average of 25.80%. The reciprocal tariffs are going to bite hard on these states.

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }
    .dataframe tbody tr th {
        vertical-align: top;
    }
    .dataframe thead tr th {
        text-align: left;
    }
    .dataframe tbody td {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: left;">
      <th>STATE</th>
      <th>EXPORT %</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>North Dakota</th>
      <td>80.60%</td>
    </tr>
    <tr>
      <th>Montana</th>
      <td>46.55%</td>
    </tr>
    <tr>
      <th>South Dakota</th>
      <td>45.87%</td>
    </tr>
    <tr>
      <th>West Virginia</th>
      <td>44.10%</td>
    </tr>
    <tr>
      <th>Maine</th>
      <td>41.22%</td>
    </tr>
    <tr>
      <th>Idaho</th>
      <td>38.63%</td>
    </tr>
    <tr>
      <th>Michigan</th>
      <td>38.53%</td>
    </tr>
    <tr>
      <th>Missouri</th>
      <td>34.14%</td>
    </tr>
    <tr>
      <th>Ohio</th>
      <td>32.34%</td>
    </tr>
    <tr>
      <th>Vermont</th>
      <td>30.85%</td>
    </tr>
    <tr>
      <th>Iowa</th>
      <td>30.40%</td>
    </tr>
    <tr>
      <th>Wisconsin</th>
      <td>27.85%</td>
    </tr>
    <tr>
      <th>Pennsylvania</th>
      <td>26.74%</td>
    </tr>
  </tbody>
</table>
</div>


Similarly, the states with the percentage of their imports from Canada in proportion to goods and services
imported from the rest of the world exceeding the average across the USA of 28.39% are:

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }
    .dataframe tbody tr th {
        vertical-align: top;
    }
    .dataframe thead tr th {
        text-align: left;
    }
    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>STATE</th>
      <th>IMPORT %</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Montana</th>
      <td>91.37%</td>
    </tr>
    <tr>
      <th>Vermont</th>
      <td>70.02%</td>
    </tr>
    <tr>
      <th>Maine</th>
      <td>68.69%</td>
    </tr>
    <tr>
      <th>North Dakota</th>
      <td>67.57%</td>
    </tr>
    <tr>
      <th>Wyoming</th>
      <td>48.68%</td>
    </tr>
    <tr>
      <th>Michigan</th>
      <td>47.24%</td>
    </tr>
    <tr>
      <th>Oklahoma</th>
      <td>45.91%</td>
    </tr>
    <tr>
      <th>West Virginia</th>
      <td>37.73%</td>
    </tr>
    <tr>
      <th>South Dakota</th>
      <td>36.01%</td>
    </tr>
    <tr>
      <th>Minnesota</th>
      <td>33.55%</td>
    </tr>
    <tr>
      <th>Idaho</th>
      <td>32.48%</td>
    </tr>
  </tbody>
</table>
</div>
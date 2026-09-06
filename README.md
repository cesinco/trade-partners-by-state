# Primary Import and Export Countries by State

## Background

Following the announcement by the new administration to raise tariffs on Canada, Mexico, and China (and the not entirely unexpected retaliatory measures from those targeted countries), it would be interesting to know which countries are the primary sources and destinations for imports and exports.

This data can be obtained from the US government’s International Trade Administration at trade.gov however, it is not easily obtained since the APIs made available to the public do not have any endpoints to access this type of data. Instead, we will have to resort to scraping the data from where it is available – a web page located at:

[https://www.trade.gov/data-visualization/tradestats-express-state-trade-partners](https://www.trade.gov/data-visualization/tradestats-express-state-trade-partners)

Internally, within an iframe, there is another link to the actual Tableau report we need to scrape at:

~~[https://tsereports.trade.gov/views/StateAnnualDashboardLive_16421978287720/StateTradebyProduct?%3AshowVizHome=no&%3Aembed=true&%3Atoolbar=yes%2Ctop](https://tsereports.trade.gov/views/StateAnnualDashboardLive_16421978287720/StateTradebyProduct?%3AshowVizHome=no&%3Aembed=true&%3Atoolbar=yes%2Ctop)~~

*The above link pointing to the Tableau report contained within an iframe element has been superseded by the link below*

[https://tsereports.trade.gov/views/StateAnnualDashboardLive_16421978287720/StateTradebyPartners?%3Atoolbar=yes%2Ctop&%3AshowVizHome=no&%3Aembed=true](https://tsereports.trade.gov/views/StateAnnualDashboardLive_16421978287720/StateTradebyPartners?%3Atoolbar=yes%2Ctop&%3AshowVizHome=no&%3Aembed=true)

As is often the case with scraping web pages, the data is buried deep within the structure making it unfeasible to use quick and dirty methods like grabbing a table from a webpage using native Pandas functionality. Furthermore, the data on this page is displayed only a single state at a time and requires interacting with the webpage to modify filters. Selenium to the rescue!

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

Following the announcement that Canada will suffer tariffs of 50% on exports to the USA, and the reciprocal tariffs enacted by Canada on US exports, based on the stats collected from the trade.gov website show that the following states all have the percent of goods and exports to Canada in proportion to the exports to the entire world exceeding the national average of 15.3%0. The reciprocal tariffs are going to bite hard on these states.

|State          | Export % |
|---------------|---------:|
|North Dakota   | 80.60%   |
|Montana        | 46.56%   |
|South Dakota   | 45.85%   |
|West Virginia  | 44.10%   |
|Maine          | 41.22%   |
|Idaho          | 38.64%   |
|Michigan       | 38.53%   |
|Missouri       | 34.14%   |
|Ohio           | 32.34%   |
|Vermont        | 30.84%   |
|Iowa           | 30.40%   |
|Wisconsin      | 27.86%   |
|Pennsylvania   | 26.74%   |
|Wyoming        | 24.55%   |
|Minnesota      | 23.90%   |
|Illinois       | 22.56%   |
|Oklahoma       | 22.35%   |
|North Carolina | 19.85%   |
|Nebraska       | 19.80%   |
|Arkansas       | 19.59%   |
|Indiana        | 18.79%   |
|Kentucky       | 18.25%   |
|Alabama        | 18.20%   |
|Tennessee      | 17.31%   |
|New Jersey     | 16.82%   |
|Kansas         | 16.35%   |
|Virginia       | 15.49%   |

Similarly, the states with the percentage of their imports from Canada in proportion to goods and services imported from the rest of the world exceeding the average across the USA of 11.19% are:

|State          | Import % |
|---------------|---------:|
|Montana        | 91.37%   |
|Vermont        | 70.03%   |
|Maine          | 68.69%   |
|North Dakota   | 67.57%   |
|Wyoming        | 48.68%   |
|Oklahoma       | 45.91%   |
|Alaska         | 40.72%   |
|West Virginia  | 37.73%   |
|South Dakota   | 36.04%   |
|Minnesota      | 33.55%   |
|Colorado       | 32.50%   |
|Washington     | 28.58%   |
|Illinois       | 27.65%   |
|Iowa           | 26.56%   |
|Michigan       | 25.96%   |
|Connecticut    | 23.80%   |
|Massachusetts  | 23.26%   |
|Utah           | 20.00%   |
|New Hampshire  | 19.22%   |
|Ohio           | 18.67%   |
|Idaho          | 16.89%   |
|Missouri       | 16.41%   |
|Arkansas       | 15.96%   |
|Wisconsin      | 15.64%   |
|Nebraska       | 14.26%   |
|Kansas         | 14.18%   |
|Rhode Island   | 13.01%   |
|Oregon         | 11.36%   |
# Primary Import and Export Countries by State

## Background

Following the announcement by the new administration to raise tariffs on Canada, Mexico, and China (and the not entirely unexpected retaliatory measures from those targeted countries), it would be interesting to know which countries are the primary sources and destinations for imports and exports.

This data can be obtained from the US government’s International Trade Administration at trade.gov however, it is not easily obtained since the APIs made available to the public do not have any endpoints to access this type of data. Instead, we will have to resort to scraping the data from where it is available – a web page located at:

[https://tsereports.trade.gov/views/StateAnnualDashboardLive_16421978287720/StateTradebyProduct?%3AshowVizHome=no&%3Aembed=true&%3Atoolbar=yes%2Ctop](https://tsereports.trade.gov/views/StateAnnualDashboardLive_16421978287720/StateTradebyProduct?%3AshowVizHome=no&%3Aembed=true&%3Atoolbar=yes%2Ctop)

As is often the case with scraping web pages, the data is buried deep within the structure making it unfeasible to use quick and dirty methods like grabbing a table from a webpage using native Pandas functionality. Furthermore, the data on this page is displayed only a single state at a time and requires interacting with the webpage to modify filters. Selenium to the rescue!

After acquiring the data, we also want to display it graphically using a map of the USA to show each state’s dependence on their primary export and import partners. For this, we will employ Choropleth maps.

You can view the resulting notebook file [get_top_export_countries_by_state.ipynb](get_top_export_countries_by_state.ipynb)

## Output

The resulting images that the notebook generates are the following

![export_countries_by_state.png](./images/export_countries_by_state.png)

![import_countries_by_state.png](./images/import_countries_by_state.png)

## Comments

Following the reaction of investors and the destruction of value in the stock markets upon the administration announcing that the tariffs would be imposed, the administration quickly backtracked allegedly for a 30-day reprieve (which, given our understanding of the new president, will likely never be mentioned again) for both Canada and Mexico. Now seeing who the largest trading partners are (~80% of states export primarily to Canada or Mexico, and ~67% of states import primarily from Canada or Mexico), had the tariffs remained in place, the pain on exporters and consumers would have been significant.
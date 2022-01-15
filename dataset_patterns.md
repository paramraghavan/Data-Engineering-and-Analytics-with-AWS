# Dataset Patterns

Generally, data sets could be of 4 main grades:

- Time series data, a set of observations on the values that a variable takes at different times, used for temporal measurements, forecasting trend
- Spatial data where the observations typically relate to geographical locations
- Cross-sectional data, data of one or more variables, collected at the same point in time, as analyzing data from a population, or a representative subset, at a specific point in time
- Longitudinal or panel data, observations of multiple phenomena over multiple time periods for the same data units; involves repeated observations of the **same variables (e.g., people)** over periods of time; can prove cause and effect, but time-consuming and expensive.

- ref: https://www.quora.com/What-is-the-difference-between-time-series-analysis-and-longitudinal-data-analysis

## Longitudinal data
Longitudinal data is data that is collected sequentially from the same respondents over time. This type of data can be very important in tracking trends and changes over time by asking the same respondents questions in several waves carried out of time.

Longitudinal patient dataset (data that track the same patients over the course of many years) that will guide us to make the best treatment decisions based on actual, real-life experience from patients similar to the individual needing care. For example, longitudinal data helps to answer the question, “I had my aortic valve replaced 15 years ago. Based on the experience of patients with medical histories similar to myself, what course of treatment should I follow when it begins to fail?”

Making data like this accessible in new ways has the potential to significantly impact the way healthcare is delivered. The power of a multivariate dataset, collected from hundreds or thousands of people with similar diseases or conditions over an extended period of time, enables hospitals and health systems to make high quality, cost-effective treatment decisions for their patients. In fact, **the ultimate outcome of longitudinal data is to identify at-risk patients and intervene to preempt the disease from occurring in the first place**

- https://www.rxdatascience.com/blog/getting-most-out-of-longitudinal-patient-data
- https://www.healthdatamanagement.com/articles/why-longitudinal-data-is-crucial-to-making-better-care-decisions

## Timeseries data

Time series data, also referred to as time-stamped data, is a sequence of data points indexed in time order. Time-stamped is data collected at different points in time.These data points typically consist of successive measurements made from the same source over a time interval and are used to track change over time.

Weather records, economic indicators and patient health evolution metrics — all are time series data. Time series data could also be server metrics, application performance monitoring, network data, sensor data, events, clicks and many other types of analytics data.

A time series can be taken on any variable that changes over time. In investing, it is common to use a time series to track the price of a security over time. This can be tracked over the short term, such as the price of a security on the hour over the course of a business day, or the long term, such as the price of a security at close on the last day of every month over the course of five years.

Time series analysis can be useful to see how a given asset, security, or economic variable changes over time. **It can also be used to examine how the changes associated with the chosen data point compare to shifts in other variables over the same time period.**

- https://www.investopedia.com/terms/t/timeseries.asp


## Slowly Changing dimensions
Slowly Changing Dimensions (SCD) - dimensions that change slowly over time, rather than changing on regular schedule, time-base. In Data Warehouse there is a need to track changes in dimension attributes in order to report historical data. In other words, implementing one of the SCD types should enable users assigning proper dimension's attribute value for given date. Example of such dimensions could be: customer, geography, employee. [SCD in detail](https://www.datawarehouse4u.info/SCD-Slowly-Changing-Dimensions.html)

## Facts and Dimensions
In Data Warehouse Modeling, a star schema and a snowflake schema consists of Fact and Dimension tables. Fact and Dimension tables are the main two tables that are used when designing a data warehouse. The fact table contains measures of columns and surrogate keys that link to the dimension tables. Measure columns are the values that you store in order to measure the business fact.

- Fact Table:
It contains all the primary keys of the dimension and associated facts or measures(is a property on which calculations can be made) like quantity sold, amount sold and average sales. A fact table is a primary table in a dimensional model.

- A Fact Table contains
  - Measurements/facts
  - Foreign key to dimension table

- Dimension Tables:
  - A dimension table contains dimensions of a fact.
  - They are joined to fact table via a foreign key.
  - Dimension tables are de-normalized tables.
  - Dimension tables provides descriptive information for all the measurements recorded in fact table.
  - Dimensions are relatively very small in size in  comparison to fact table.
  - Commonly used dimensions are people, products, place and time.
  - 
![image](https://user-images.githubusercontent.com/52529498/149608358-abb01309-c389-4246-91aa-c46010ea9144.png)

- Ref https://stackoverflow.com/questions/20036905/difference-between-fact-table-and-dimension-table/33750545

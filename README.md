### Time Series Analysis with Pandas

A time series is any data set where the values are measured at different points in time.

Dataset of daily time series of Open Power System Data (OPSD) for Germany https://github.com/ankitasuman009/Time_Series/blob/main/opsd_germany_daily.txt

### Time series DataFrame

- We can use the to_datetime() function to create Timestamps from strings in a wide variety of date/time formats.
- we use a DatetimeIndex as the index for our DataFrame.
- The DataFrame has 4383 rows, covering the period from January 1, 2006 through December 31, 2017.

### Time based indexing

- We can select data for a single day using a string such as '2017-08-10'.
- We can also select a slice of days, such as '2014-01-20':'2014-01-22'.
- We can select the entire year 2006 with opsd_daily.loc['2006'], or the entire month of February 2012 with opsd_daily.loc['2012-02'].


### Observation after Visualizing data

- Electricity consumption is highest in winter, and increased lighting usage, and lowest in summer.
- Electricity consumption appears to split into two clusters — one with oscillations centered roughly around 1400 GWh, and another with fewer and more scattered data points, centered roughly around 1150 GWh.
- Solar power production is highest in summer, when sunlight is most abundant, and lowest in winter.
- Wind power production is highest in winter, and lowest in summer.
- There appears to be a strong increasing trend in wind power production over the years.

### Frequencies

- The date_range() function is used to create a sequence of uniformly spaced dates at daily frequency.
- 'freq' with a value of 'D', indicating daily frequency, hourly ('H'), calendar daily ('D'), business daily ('B'), weekly ('W'), monthly ('M'), quarterly ('Q'), annual ('A').
-  DataFrame’s asfreq() method to convert the DataFrame to daily frequency, with a column for unfilled data, and a column for forward filled data.
- In the Consumption - Forward Fill column, the missings have been forward filled.


### Resampling

- The daily OPSD data was downsampled from the original hourly time series.
- Resample the data to a weekly mean time series.
- Weekly time series has 1/7 as many data points as the daily time series.
- mean() sets the output to NaN for any period with all missing data.
- sum() will return output of 0 as the sum of missing data. We use the min_count parameter to change this behavior.
- Resampled data is labelled with the right bin edge for monthly, quarterly, and annual frequencies, and with the left bin edge for all other frequencies.


### Rolling windows

- Similar to downsampling, rolling windows split the data into time windows and the data in each window is aggregated with a function such as mean(), median(), sum(), etc
- Here the transformed time series is at the same frequency as the original time series.
- rolling() method to compute the 7-day rolling mean of our daily data.


### Trends

- Computed the 365-day rolling mean of our OPSD data.
- Plotted the 7-day and 365-day rolling mean electricity consumption, along with the daily time series.
- The 7-day rolling mean reveals that while electricity consumption is typically higher in winter and lower in summer, there is a dramatic decrease for a few weeks every winter at the end of December and beginning of January, during the holidays.
- The 365-day rolling mean time series, we can see that the long-term trend in electricity consumption is pretty flat, with a couple of periods of anomalously low consumption around 2009 and 2012-2013.


### Summary

- We’ve seen how to wrangle, analyze, and visualize our time series data in pandas using techniques such as time-based indexing, resampling, and rolling windows.

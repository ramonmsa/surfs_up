# Surfs Up Analysis
## Overview of Project

To provide analysis on temperature trends for the months of June and December in Oahu to support the investor to determine if the surf and ice cream shop business is sustainable year-round.

The following tasks is needed to presente the analysis:
-   Create a summary of statistics for June
-   Create a  summary of statistics for December


## Results
The analysis of the summaries of temperatures for June and December show that:
- For June: 
	- Minimum of __*64 degrees*__ 
	- Maximum of __*85 degrees*__
	- The median temperature is __*75 degrees*__
	- The average temperature is __*74.94 degrees*__

- For December:
	- Minimum of __*56 degrees*__ 
	- Maximum of __*83 degrees*__
	- The median temperature is __*71 degrees*__
	- The average temperature is __*71.04 degrees*__

![June Temperatures](https://raw.githubusercontent.com/ramonmsa/surfs_up/main/Resources/June_Temps.PNG "June Temperatures" )| ![December Temperatures](https://raw.githubusercontent.com/ramonmsa/surfs_up/main/Resources/December_Temps.PNG "December Temperatures" )
<br/>*June and December Temperatures*




## Summary

As  it is possible to observe in the images, the *average temperatures* are *74.94* an *71.04* in *June* and *December* consecutively which represents a difference of about only 4 degrees from the first month observed to the other. Both presenting similar *maximum temperatures* which are above *80 degrees*.

On the other hand, *December* has cooler days with *minimum temperature observed* as *56 degrees* against *64 degrees* in *June*.

The query below could be also performed in *Jupyter Notebook* for the two months in order to observe the distribution of temperatures in each of the months:
```Python
tobs_df.plot.hist()
```
Another helpful query to observe these major points throughout the twelve months would be the one below which retrieves the maximum, minimum and average temperatures and plot the result in a line chart:

```Python
# retrieve avg, max and min of temperatures for all months
all_months_tobs = session.query(extract("month", Measurement.date),
              func.avg(Measurement.tobs),
              func.max(Measurement.tobs),
              func.min(Measurement.tobs)).group_by(extract("month", Measurement.date)).all()
              
# convert the resulto to data frame and set the column Month as index 
all_months_tobs_df = pd.DataFrame(all_months_tobs, columns=["Month","Average","Max","Min"])
all_months_tobs_df = all_months_tobs_df.set_index("Month")

# plot the data frame
all_months_tobs_df.plot.line()
```


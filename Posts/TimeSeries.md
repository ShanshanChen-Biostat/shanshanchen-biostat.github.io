---
layout: default
---


### Handling Time Series in R

For intensive longitudinal data (e.g. with a sampling rate more than 1/15 Hz), I recommend moving to Matlab for data visualization. 
Still, it's useful to know how to handle time series in R. 

```
library(chron)
library(zoo)
```

- #### Converting string timestamps to proper time format

```
DF<- read.csv("data.csv")
DF$Time <- as.character(DF$Time, format="%H:%M:%S" )
DF$Tvec <- chron(times=DF$Time)
```

- #### Converting timestamps (wihtout date) to time of the day (time elapsed since midnight)

```
DF$ToD_hrs <- hours(DF$Tvec)+minutes(DF$Tvec)/60
DF$ToD_mins <- 60*hours(DF$Tvec)+minutes(DF$Tvec)

```


## Commonly Used R Codes in Exploratory Data Analysis (EDA)

- #### Plot density by group (easier to look at than box plots)

```
library(ggplot2)
DF = read.csv("data.csv")
ggplot(DF, aes(x = x, colour = Group)) + geom_density()
```

- #### Plot longitudinal trajectories by group, with both indidivual and average trajectories

```
library(ggplot2)
DFlong = read.csv("LongData.csv") ## DFlong is the long format of panel data with Time index and ID

Avg = DFlong %>% group_by(Time,Group) %>% summarise(Var = mean(Var)) 

p = ggplot(DFlong, aes(Time, Var,col=Group)) ## input variable names 
     + geom_line(aes(group=ID),alpha = .4)  ## show individual trajectories
     +geom_line(data=Avg,aes(group = Group),size=2) ## show average trajectories
     + facet_wrap(~Group) ## split panel by group indicator 
p
```

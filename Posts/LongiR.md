### Longitudinal Data Cleaning & Structuring
```
library(tidyverse)
library(data.table)
DF = read.csv("data.csv")
```
- #### Pivoting (transform cross-sectional data to the long format)
Assuming the "wide" data have the same type of observation at each time point listed as a set of variables. These variables should have consistent names such as "Time_1", "Time_2",...,"Time-N" or "Month1","Month2",...,"MonthN" etc.
```
DFlong = DF %>% pivot_longer(cols = starts_with("Time_"), 
                           names_to="Time",names_prefix ="Time_",
                           values_to= "ValueName",values_drop_na=FALSE)
```
- #### Filling in repeated entries that were only entered once
```
DF = data.table(DF)
DF[, ID := ID[1], .(cumsum(!is.na(ID)))]
```
- #### Filling in repeated entries per each subject (only entered once for each subject)
```
library(data.table)
library(runner)
DF = data.table(DF)
DF = DF %>% group_by(ID) %>% mutate(Var = runner::fill_run(Var, run_for_first = T))
```
- #### Adding a sequence along each subject, given the total number of observations of that subject
```
DF = DF %>% group_by(ID) %>% mutate(NewSeq = seq_len(n()))
```
- #### Adding a sequence along each subject, by counting the number of observations of a variable (e.g. Date here) of that subject 
```
DF = DF%>% group_by(ID) %>% mutate(Day = dense_rank(Date))
```
- #### Visualzing each subject's longitudinal data sequence
```
library(nlme) ## trellis plot method
GroupedDF <- groupedData(ref~Day|ID, data=DF, inner=~Group)
plot(GroupedDF, aspect=3)
```
or
```
ggplot(DF, aes(x, y, group =ID))+geom_line(col=ID) ## ggplot method
```

- #### Aggregating repeated covariates from long format data
```
XSectional=DFlong%>%distinct(Var1, Var1, Var3, Var4)
```

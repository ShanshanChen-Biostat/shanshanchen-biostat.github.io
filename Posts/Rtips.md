### Longitudinal Data Cleaning & Structuring
```
library(tidyverse)
library(data.table)
DF = read.csv("data.csv")
```
- Pivoting (transform cross-sectional data to the long format)
```
DFlong = DF %>% pivot_longer(cols = starts_with("Time_"), 
                           names_to="Time",names_prefix ="Time_",
                           values_to= "ValueName",values_drop_na=FALSE)
```
- Filling in repeated entries 
```
DF = data.table(DF)
DF[, ID := ID[1], .(cumsum(!is.na(ID)))]
```
- Filling in repeated entries per each subject (only entered once for each subject)
```
library(data.table)
DF = data.table(DF)
DF = DF %>% group_by(ID) %>% mutate(Var = runner::fill_run(Var, run_for_first = T))
```
- Adding a sequence along each subject
```
DF = DF %>% group_by(ID) %>% mutate(NewSeq = seq_len(n()))
```
- Visualzing each subject's longitudinal data sequence
```
library(nlme) ## trellis plot method
GroupedDF <- groupedData(ref~Day|ID, data=DF, inner=~ToD)
plot(GroupedDF, aspect=3)
```

- Aggregating repeated covariates from long format data
```
XSectional=DFlong%>%distinct(Var1, Var1, Var3, Var4)
```

### Longitudinal Data Cleaning & Structuring
```
library(tidyverse)
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
library(data.table)
DF = data.table(DF)
DF[, ID := ID[1], .(cumsum(!is.na(ID)))]
```
- Filling in repeated entries 
```
library(data.table)
DF = data.table(DF)
DF = DF %>% group_by(ID) %>% mutate(Var = runner::fill_run(Var, run_for_first = T))
```
- Adding a sequence along each subject
- Visualzing each subject's longitudinal data sequence

- Aggregating baseline covariates
```
XSectional=DFlong%>%distinct(Var1, Var1, Var3, Var4)
```

### Longitudinal Data Cleaning
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
- Adding a sequence along each subject
- Visualzing each subject's longitudinal data sequence

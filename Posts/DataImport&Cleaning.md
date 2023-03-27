---
layout: default
---
## Data Import and Cleaning

### Data import
- #### import .rda file 
```
data("data.rda")
```

- #### importing .csv file
```
DF = read.csv("data.csv", row.names = FALSE, encoding = "UTF-8")
```

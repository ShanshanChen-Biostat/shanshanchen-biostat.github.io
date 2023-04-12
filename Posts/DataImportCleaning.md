---
layout: default
---
## Data Import and Cleaning

> Before importing a data file compatible with ASCII encoding (e.g. .csv, .xls), I recommend opening the file and check the variable names. Make sure the variable names accurately and succinctly describe the variables. If not, renaming the variables in the script. 
> Avoid following characters are not used in variable names: space, apostrophy, &, *, etc. Prefer underscore "xx_xx" to join words in a variable name.  

Also read my previous post, [R Style](/Posts/RStyle.md), for more detail on naming conventions.

### Data import
- #### import .rda file 
```
data("data.rda")
```

- #### importing .csv file
```
DF = read.csv("data.csv", row.names = FALSE, encoding = "UTF-8")
colnames(DF) = c("ID", "Date", "Time","Var1", ...,"VarN")
```

- #### importing any type of delimited files 
```
DF = read.table("data.csv", sep=",", blank.lines.skip=TRUE, allowEscapes=FALSE, header=TRUE, encoding="UTF-8")
```

- #### importing data saved by SAS
```
library(haven)
DF = read_xpt("data.csv", col_select = NULL, skip = 0, n_max = Inf)
```

### Variable Selection and Deletion 
```
library(tidyverse)
DF = read.csv("data.csv")
## delecting variables with certain patterns in the names
DF = DF %>% select(-contains(c("prefix_","_suffix","_suffix_2","_suffix_3")))
```


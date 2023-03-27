---
layout: default
---
## Data Import and Cleaning

> Before importing a data file compatible with ASCII encoding (e.g. .csv, .xls), I recommend opening the file and check the variable names. Make sure the variable names accurately and succinctly describe the variables. If not, save a copy of the file, and change the variable names to shorter and more accurate descriptions.
>  Avoid following characters are not used in variable names: space, apostrophy, &, *, etc. Prefer underscore "xx_xx" to join words in a variable name.  
> While it is easy to change the variable names in the script, when the number of variables that need renaming is large, a long list of renaming codes can make the script look tedious and lengthy.  

### Data import
- #### import .rda file 
```
data("data.rda")
```

- #### importing .csv file
```
DF = read.csv("data.csv", row.names = FALSE, encoding = "UTF-8")
```

- #### importing any type of delimited files 
```
DF = read.table("data.csv", sep=",", blank.lines.skip=TRUE, allowEscapes=FALSE, header=TRUE, encoding="UTF-8")

```

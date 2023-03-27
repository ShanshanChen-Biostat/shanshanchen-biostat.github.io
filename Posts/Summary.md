---
layout: default
---

- #### Summarizing desriptive statistics 
```
library(table1)
DF <- read.csv("data.csv")
table1(~Var1+Var2+Var3...+Var4|group_of_interest, data=DF)
```

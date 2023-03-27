---
layout: default
---

- #### Summarizing desriptive statistics using the Table1 package
```
library(table1)
DF <- read.csv("data.csv")
table1(~Var1+Var2+as.factor(Var3)+...+Var4|as.factor(group_of_interest), data=DF)
```

- #### Summarizing by tidyverse
```
library(tidyverse)
DF %>%
  group_by(group_of_interest) %>%
  summarize(n=sum(!is.na(Var_of_interest)),
            Mean=mean(Var_of_interest,na.rm=TRUE),
            SD=sd(Var_of_interest,na.rm=TRUE))
```

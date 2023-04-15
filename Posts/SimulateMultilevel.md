---
layout: default
---
## Simulating Multilevel Data 

```
## Simulating Longitudinal Panel Data with Two Groups of Subjects
library(tidyverse)
Time <- c(0:9,21:30)
Group <- c(rep(0,10),rep(1,10))
ID <- seq(1:100)
X <- expand.grid(paste(Time = Time, Group=Group,Outcome = ifelse(Group==0,rnorm(10,36,23),rnorm(10,45,27))),ID=ID)  
T1 = read.table(text=as.character(X$Var1))
X$Time = T1$V1
X$Group = T1$V2
X$Outcome = T1$V3
DF = X%>%select(-c("Var1"))
```

---
layout: default
---

- #### Summarizing desriptive statistics using the Table1 package
```
library(table1)
DF = read.csv("data.csv")
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

- #### Summarizing regression tables with the same set of independent variables but multiple outcomes 
```
library(sjPlot)
DF = read.csv("data.csv") ## DF is a cross-sectional dataset, with group indicator Group and a few covariates
Mod1 = lm(Outcome1 ~ Group + Age + Sex + Race + BMI, data = DF)
Mod2 = lm(Outcome2 ~ Group + Age + Sex + Race + BMI, data = DF)
Mod3 = lm(Outcome3 ~ Group + Age + Sex + Race + BMI, data = DF)
Mod4 = lm(Outcome4 ~ Group + Age + Sex + Race + BMI, data = DF)
Mod5 = lm(Outcome5 ~ Group + Age + Sex + Race + BMI, data = DF)

tab_model(
  Mod1, Mod2, Mod3, Mod4, Mod5,
  collapse.se = TRUE, show.ci=FALSE,
  pred.labels = c("Intercept", "Group", "Age (years)", "Sex (Female)",
                  "Race (AA)", "BMI"),
  dv.labels = c("Outcome1", "Outcome2","Outcome3","Outcome4","Outcome5"),
  string.pred = "Variables",
  string.est = "Estimates (SE)")
```


## Visualzing Marginal Effects after Regression Modeling wiht ggplot
```
library(ggplot2)
library(nlme)
```

 - ### Fit Models (using a nonlinear mixed-effects model as an example)
 ```
model_nlme <- nlme(Outcome ~ nonlinear_func(Var1,Para1, Para2, Para3), data = Data, 
                   fixed = Para1 + Para2 + Para3 ~1, random = Para2+Para3 ~1,
                   groups = ~ID, method = "ML", 
                   start = list(fixed = ...),
                   control = nlmeControl(opt = "nlmnb", msMaxIter = 1e5, 
                   upper = ..., lower = ...))
 fitted <- predict(model_nlme, newdata=PKPD)
 ```
 - #### Plot modeled nonlinear trajectories and raw scatter dots 
 
 ```
 newData <- expand.grid(Var1 = seq(min(Data$Var1),max(Data$Var1),1), ID = unique(Data$ID))
 fittedNew = predict(model_nlme, level=0, newdata = newData)
 ggplot(Data, aes(x=Var1, y=Outcome, colour=ID)) 
        +geom_point(size=3)
        +geom_line(data=Data,aes(y=fitted))
        +geom_line(data=newData, aes(x=Var1, y=fittedNew), size=2, colour="color"))
        +theme_bw(base_size=22) +xlab("Var1 Name ") + ylab("Outcome Name")
 ```

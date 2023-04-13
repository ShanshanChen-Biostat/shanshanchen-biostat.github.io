
## Commonly Used R Codes in Exploratory Data Analysis (EDA)

- #### Plot density by group (easier to look at than box plots)

```
library(ggplot2)
DF = read.csv("data.csv")
ggplot(DF, aes(x = x, colour = Group)) + geom_density()
```

- #### Plot longitudinal trajectories by group, with both indidivual and average trajectories

```
library(ggplot2)
library(tidyverse)
DFlong = read.csv("LongData.csv") ## DFlong is the long format of panel data with Time index and ID

Avg = DFlong %>% group_by(Time,Group) %>% summarise(Var = mean(Var)) 

p = ggplot(DFlong, aes(Time, Var,col=Group)) ## input variable names 
     + geom_line(aes(group=ID),alpha = .4)  ## show individual trajectories
     +geom_line(data=Avg,aes(group = Group),size=2) ## show average trajectories
     + facet_wrap(~Group) ## split panel by group indicator 
p
```

- #### Plot pairwise correlation table 

```
library(corrplot)
library(RColorBrewer)
DF = read.csv("data.csv")
Vars = c("Var1","Var2","Var3","Var4")
VarMat <- DF[Vars]
CorMat<-cor(VarMat,use="pairwise.complete.obs",method ="spearman")

cor.mtest <- function(mat, ...) {
  mat <- as.matrix(mat)
  n <- ncol(mat)
  p.mat<- matrix(NA, n, n)
  diag(p.mat) <- 0
  for (i in 1:(n - 1)) {
    for (j in (i + 1):n) {
      tmp <- cor.test(mat[, i], mat[, j], ...,method ="spearman")
      p.mat[i, j] <- p.mat[j, i] <- tmp$p.value
    }
  }
  colnames(p.mat) <- rownames(p.mat) <- colnames(mat)
  p.mat
}

PMat <- cor.mtest(VarMat)
corrplot(CorMat, method="color",type="upper",addCoef.col = "black", tl.col="blue", number.digits = 3,
         tl.srt=90,p.mat=PMat,sig.level=0.01,insig = "blank",col=brewer.pal(n=10, name="RdYlGn"))
```

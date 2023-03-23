
## Commonly Used R Codes in Exploratory Data Analysis (EDA)

- #### Plot density by group (easier to look at than box plots)

```
library(ggplot2)
DF = read.csv("data.csv")
ggplot(DF, aes(x = x, colour = Group)) + geom_density()
```

### Handling String Sequence Data in R

```
library(stringr)
```

- #### detecting the location of a particular transition in a long sequence
```
DF = read.csv("data.csv")
Str_long = str_flatten(DF$seq) ## reduces a character vector to a single string 
transit_type = "14" ## e.g. detecting the transition location from state 1 to 4
loc = str_locate_all(Str_long, transit_type)
```

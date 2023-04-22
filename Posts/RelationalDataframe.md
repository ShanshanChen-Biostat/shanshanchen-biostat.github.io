## Merging, Bidning, Differtiating Datasets

-### Merging two data frames with different varibles by IDs 
```
library(tidyverse)
COV <- merge(COV1, COV2,by = c("ID","Age","Gender","Ethnicity","HE"), all = TRUE) ## overlapping variables are listed in the "by" argument
```
-### Binding two data frames with same variables 
```
library(tidyverse)
bind_rows(COV1, COV2)
```
-### Checking differences between two similar data frames for same IDs
```
library(diffdf)
diffdf(COV1[COV1$ID %in% COV2$ID,], COV2) ## suppose COV1 is a superset of COV2
```


-### Joining two data frames with same variables, but missing values appear in different rows for different variables
```
library(rqdatatable)
COVall <- natural_join( COV[COV$ID %in% XC$ID,],XC by = "ID",jointype = "FULL")
```

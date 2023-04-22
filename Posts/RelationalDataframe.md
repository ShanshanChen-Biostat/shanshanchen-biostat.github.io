## Merging, Bidning, Differtiating Datasets

-### Merging two data frames with different varibles by IDs 
```
library(tidyverse)
COV <- merge(COV1, COV2,by = c("ID","Age","Gender","Ethnicity","HE"), all = TRUE) ## overlapping variables are listed in the "by" argument
```

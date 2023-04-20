
- ### Calculating driving distance between two zip codes based on Google maps
```
library(ggmaps)
register_google(key = "...", write = TRUE)
GoogleDist = mapdist(from = DF$ZIP_start, to = DF$ZIP_end, mode="driving")
```


- ### Calculating geodistance on a map between two zip codes 
```
library(data.table)
library(geodist)
dt_zips <- as.data.table( zip_code_db[, c("zipcode", "lng", "lat")])
setDT( DF)
DF$ZIP = as.character(DF$ZIP)
DF$ZIP[1]= "01776"

DF[dt_zips, on = .(ZIP = zipcode), `:=`(lng_start = lng, lat_start = lat)]
DF[dt_zips, on = .(ZIPend = zipcode), `:=`(lng_end = lng, lat_end = lat)]
DF[, distance_metres := geodist::geodist_vec( x1 = lng_start, 
                                              y1 = lat_start, x2 = lng_end, 
                                              y2 = lat_end, 
                                              paired = TRUE, 
                                              measure = "haversine")]

DF$Distance_my = DF$distance_metres*0.000621371
```

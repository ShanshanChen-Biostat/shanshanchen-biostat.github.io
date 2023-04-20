
- ### Calculating driving distance between two zip codes based on Google maps
```
library(ggmaps)
DF = read.csv("ZipInfo.csv") ## contains two columns of zip codes, one for origin, the other for destination
register_google(key = "...", write = TRUE)

#### for some reason, vectorization is not great in mapdist, will return duplicated records if the code below is used
#GoogleDist = mapdist(from = DF$ZIP_start, to = DF$ZIP_end, mode="driving")


DF$row.number <- 1:nrow(DF)
for (i in 1:205){
  a <- mapdist(from = DF$ZIP_origin[i], to = DF$ZIP_destination, mode = "driving",output = "simple")
  a$row.number <- i
  DF$miles[match(a$row.number, DF$row.number)] <- a$miles
  DF$hours[match(a$row.number, DF$row.number)] <- a$hours
}


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

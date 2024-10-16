# Autoregressive models vs smoothing splines for spatial analysis

[2024-10-17]

Let's take a look at the differences between using autoregression and smooth spline to fit spatial effects in a mixed linear model context.

```R
library(sommer)
download.file("http://bit.ly/R-spatial-data", "R-spatial-data.zip")
unzip("R-spatial-data.zip", exdir = "data")
unlink("R-spatial-data.zip")
df = read.csv("data/philly_homicides.csv")
df$LOC = paste0(df$SECTOR, "|", df$POINT_X, "|", df$POINT_Y)
vec_loc_freq = table(df$LOC)
vec_id = unlist(lapply(strsplit(names(vec_loc_freq), "\\|"), FUN=function(x){x[1]}))
vec_lon = as.numeric(unlist(lapply(strsplit(names(vec_loc_freq), "\\|"), FUN=function(x){x[2]})))
vec_lat = as.numeric(unlist(lapply(strsplit(names(vec_loc_freq), "\\|"), FUN=function(x){x[3]})))
df = data.frame(id=vec_id, lon=vec_lon, lat=vec_lat, y=as.vector(vec_loc_freq))
### Autoregressive model
model_ar = sommer::mmer(
  fixed = y ~ 1 + id,
  random = ~sommer::AR1(lon):sommer::AR1(lat),
  rcov = ~ units,
  data = df,
  dateWarning = FALSE,
  verbose = TRUE
)
### Smooth spline model
n_lons = length(unique(df$lon))
n_lats = length(unique(df$lat))
model_ar = sommer::mmer(
  fixed = y ~ 1 + id,
  random = ~sommer::spl2Dc(x.coord=lon, y.coord=lat, nsegments=c(n_lons, n_lats), degree=c(3,3)),
  rcov = ~ units,
  data = df,
  dateWarning = FALSE,
  verbose = TRUE
)
```

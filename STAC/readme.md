# stac test


## create geojson polygon

```R
library(terra)
r <- rast("nt_20130114_f17_v01_s.tif")
p <- as.polygons(ext(r))
crs(p) <- crs(r)

eps <- 1e-9
p1 <- vect(rbind(crds(p)[1:4, ], c(eps, ymin(p)), c(0, 0), c(-eps, ymin(p)), crds(p)[5, ]), type = "polygons" ,crs = "EPSG:3031")
#plot(project(densify(p1, 1e5), "OGC:CRS84"))
writeVector(project(densify(p1, 1e5), "OGC:CRS84"), "file.geojson", filetype  = "GeoJSON")
```






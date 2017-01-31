---
layout: post
title: Spatial Data and Maps
subtitle: Using R as a GIS software and creating informative maps
date: 2016-11-25T16:00:00.000Z
author: John
meta: Maps_1
---

<div class="block">
  <center>
  <img src="{{ site.baseurl }}/img/tutheader_maps.jpg" alt="Img">
</center>
</div>

# Tutorial Aims:

# Steps:

## [1\. Why use R to make maps?](#why)

## [2\. Applications of Maps](#uses)

## [3\. Downloading the relevant packages](#download)

## [4\. Getting your head around map data](#map_data)

## [5\. Creating a map using ggmap](#create)

## [6\. Using shapefiles](#shp)

## [7\. Finding map resources and shapefiles](#resources)

--------------------------------------------------------------------------------
All the resources for this tutorial, including some helpful cheatsheets can be downloaded from [this repository](.) Clone and download the repo as a zipfile, then unzip and set the folder as your working directory:

```r
setwd()
```

<a name="why"></a>

## Why use R for spatial data?

- Less clicking 
  - Most conventional GIS software use a Graphical User Interface (GUI) which makes them easier to fumble through when you don't know what you're doing, but point and click interfaces become very laborious when performing analyses for the _n_ th time or when you really know your way around the software. R runs using a Command Line Interface, so while there may be more of a learning curve to begin with, it's pretty sweet once you know what to do.

- Reproducible analyses with new data
  - Imagine you have a data project where you are given new data every week, which you want compare using maps. Using a GUI, you would have to repeat your analyses step by step, every time your data came in, being careful to maintain formatting between maps. Using the command line you only have to plug in the new data to the script and the maps will look the same every time.

- Free
  - While ArcGIS and SuperGIS cost money to use, R packages are free and probably always will be.

- A range of GIS packages for different applications
  - Using the R package system you can find the right GIS application for your project, and if you can adapt and hack the packages already there to create something specific for your project.
  
<a name="download"></a>
  
## Downloading the relevant packages

There are lots of packages used in this tutorial, we will go through them one by one later but for now install the following packages:

```r
install.packages("readr")
install.packages("dplyr")
install.packages("maps")
install.packages("mapdata")
install.packages("rgdal")
install.packages(devtools)
  devtools::install_github("dkahle/ggmap")
```
at the time of writing, `ggmap` needs to be compiled from source to maintain some functionality, hence `  devtools::install_github("dkahle/ggmap")`, but this might change in the future.

<a name="map_data"></a>

## Getting your head around map data

The easiest way to think about map data is to first imagine a graph displaying whatever data you want, but with the x and y axes denoting longitude and latitude:

![Img]({{ site.baseurl }}/img/Trout_Europe_Plot.jpg)

Then it's a simple case of adding a background map to your image to place the data points in the real world. In this case, the map was pulled from google maps.

![Img]({{ site.baseurl }}/img/Trout_Europe_Graph.jpg)

That was a simple example, and maps can incorporate more complex elements like polygons and lines:

![Img]({{ site.baseurl }}/img/Polygon_line_map.jpg)

When constructing maps at larger scales, when combining shapefiles from many different sources, or when extra precision is required, the [map projection system](http://xkcd.com/977/) must be considered. Map projections use different methods to deal with the fact that the earth is roughly spherical but a map is flat.

MORE ABOUT THIS

## Creating a map using ggmap

For this part of the tutorial we are going to create a map showing the spatial extent of 2 species of bird.  Rueppell's Vulture (_Gyps rueppellii_) feeds on large mammalian carrion and the African Penguin (_Spheniscus demersus_) feeds on small marine fish, it's probable that they have distinct spatial patterns, we shall see!

First, import the data we need, `Gyps_rueppellii_GBIF.csv` and `Spheniscus_dermersus_GBIF.csv`:

```r
vulture <- read.csv(Gyps_rueppellii_GBIF.csv)
penguin <- read.csv(Spheniscus_demersus_GBIF.csv)
```

Now to clean up the data using `dplyr`:

```r
library(dplyr)

# Keep only the columns we need
vars <- c("gbifid", "scientificname", "locality", "decimallongitude", "decimallatitude", "coordinateuncertaintyinmeters")

vulture_trim <- vulture %>% select(one_of(vars))
penguin_trim <- penguin %>% select(one_of(vars))

# Combine the dataframes
pc_trim <- bind_rows(vulture_trim, penguin_trim)
names(pc_trim)
str(pc_trim)
# Check that species names are consistent
unique(pc_trim$scientificname)
  # Needs cleaning up

# Clean up "scientificname"
pc_trim$scientificname <- pc_trim$scientificname %>% 
                            recode("Gyps rueppellii (A. E. Brehm, 1852)" = "Gyps rueppellii", 
                              "Gyps rueppellii subsp. erlangeri Salvadori, 1908" = "Gyps rueppellii", 
                              "Gyps rueppelli rueppelli" = "Gyps rueppellii",
                              "Spheniscus demersus (Linnaeus, 1758)" = "Spheniscus demersus"
                              )
# Checking names
unique(pc_trim$scientificname)
  # Done
```

Now we can make a preliminary plot to make sure the data looks right. Like I said before, a map is just a graph with longitude and latitude as the x and y axes:

```r
ggplot(pc_trim, aes(x = decimallongitude, y = decimallatitude, group = scientificname)) +
geom_point(aes(colour = scientificname))
```

It looks like some of the Penguin populations might be from zoos in U.S cities, let's remove those entries:

```r
pc_trim <- pc_trim %>% filter(decimallongitude > -50)
```

Plot it again:

```r
ggplot(pc_trim, aes(x = decimallongitude, y = decimallatitude, group = scientificname)) + geom_point(aes(colour = scientificname))
```

Now to make a map out of our graph using `ggmap`, which pulls map tiles from various online sources, including google maps and open street maps.

First make a bounding box, to tell `ggmap` where to download map tiles from. The bounding box must be in the form of a vector, with decimal latitude and longitude values in this order `lowerleftlon, lowerleftlat, upperrightlon, upperrightlat`, which we can extract from our data frame using the following code:

```r
bbox <- c(min(pc_trim$decimallongitude) - 2,
          min(pc_trim$decimallatitude) - 2,
          max(pc_trim$decimallongitude) + 2,
          max(pc_trim$decimallatitude) + 2
          )
```

the `+2` `-2` values are added to make the edges of the map slightly larger than the limits of the data, purely for aesthetic reasons.

Now to download the map data from `ggmap`:

```r
Map <- get_map(location = bbox, source = "stamen", maptype = "terrain"
```

We can check that the map is correct by plotting the `Map` object:

```r
ggmap(Map)
```

To add the data, use `ggplot2` syntax:

```r
ggmap(Map) +
  geom_point(aes(x = decimallongitude,
                 y = decimallatitude, 
                 colour = scientificname),
             data = pc_trim, 
             alpha = 0.6,
             size = 2) +
  scale_colour_manual(values=c("red", "blue")) + 
  xlab(expression("Decimal Longitude ("*degree*")")) +
  ylab(expression("Decimal Latitude ("*degree*")"))
```

Now you should have a map that looks something like this:

![Img]({{ site.baseurl }}/img/Birds_ggmap.jpg)


## Using shapefiles

## Finding map resources and shapefiles








  

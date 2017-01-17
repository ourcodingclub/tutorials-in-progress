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
All the resources for this tutorial, including some helpful cheatsheets can be downloaded from [this repository](.

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
install.packages("maps")
install.packages("mapdata")
install.packages("rgdal")
install.packages(devtools)
  devtools::install_github("dkahle/ggmap")
```
at the time of writing, `ggmap` needs to be compiled from source to maintain some functionality, hence `  devtools::install_github("dkahle/ggmap")`, but this might change in the future.

<a name="map_data"></a>

## Getting your head around map data

The easiest way to think about map data is to first imagine a graph displaying whatever data you want, but with the x and y axes denoting longitude and latitude, respectively:

![Img]({{ site.baseurl }}/img/Trout_Europe_Plot.jpg)

Then it's a simple case of adding a background map to your image to place the data points in the real world. In this case, the map was pulled from google maps.

![Img]({{ site.baseurl }}/img/Trout_Europe_Graph.jpg)

That was a simple example, and maps can incorporate more complex elements like polygons and lines:

![Img]({{ site.baseurl }}/img/Polygon_line_map.jpg)

When constructing maps at larger scales, when combining shapefiles from many different sources, or when extra precision is required, the [map projection system](http://xkcd.com/977/) must be considered. Map projections use different methods to deal with the fact that the earth is roughly spherical but a map is flat.

MORE ABOUT THIS

## Creating a map using ggmap
For this part of the tutorial we are going to create a map showing the spatial extent of 2 species of bird. The ____ is migratory and the ____ is non migratory, it's probable that they have distinct spatial patterns, we shall see!

First, import the data we need.


## Using shapefiles

## Finding map resources and shapefiles








  

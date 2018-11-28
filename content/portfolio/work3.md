+++
image = "img/portfolio/honeybeepermits.png"
showonlyimage = false
date = "2016-11-05T19:44:32+05:30"
title = "An Introduction to Geographic Data Science in R with Honeybees"
draft = false
weight = 2
+++

This activity is adapted from my talk at R Ladies- Twin Cities on November 7, 2018. Enjoy!

---

In this activity I’ll demonstrate some code that shows the surface of geographic data science in R. We’ll use the packages `sf`, `dplyr`, and `ggplot2` pretty heavily, so make sure those are installed and ready to be loaded! We'll also use `spdep` a bit at the end. 

```{r}
# run this code to install the packages!

install.packages("dplyr")
install.packages("ggplot2")
install.packages("sf")

# and better yet, if you're using dplyr and ggplot2, try running

install.packages("tidyverse") # to install the whole tidyverse
```

```{r}
library(sf)
library(tidyverse)
#library(ggplot2)
#library(dplyr)
```

#### Geographic Data Science (GDS) and Geographic Information Science (GISc)

While very similar, there are some key differences between GDS and GISc. We generally think about geographic operations in R and Python as geographic data science/geocomputation. On the other hand, we think about geogaphic operations in programs like QGIS and ArcMap as GISc (often just written GIS). One of the key distinctions for me is the degree of reproducibility.

<img alt="Table comparing GDS and GISc" src="/img/portfolio/gis-vs-gds.png" width = "100%">

Table taken from Robin Lovelace's post [Can Geographic Data Save the World?](https://www.robinlovelace.net/2017/05/02/can-geographic-data-save-the-world/). 


With geographic operations in R, we can produce a full script of what we ran including any assumptions we made. This isn’t the case with QGIS and ArcMap (I pick on these two only because they are the most popular). An added bonus as an R user is that the `sf` package for geographic data is specifically designed to work within the tidyverse framework. This means spatial data works with things like `dplyr` data verbs and now there’s even a `geom_sf()` function in `ggplot2`!

#### R-Spatial Ecosystem

There are a variety of packages available for spatial data analysis specifically.

* [sp](https://github.com/edzer/sp/): Classes and Methods for Spatial Data
* [sf](https://github.com/r-spatial/sf): Simple Features for R 
* [spdep](https://github.com/r-spatial/spdep): Spatial Dependence: Weighting Schemes, Statistics, and Models
* [lwgeom](https://github.com/r-spatial/lwgeom): Binding to the liblwgeom Library
* ...

The newest, and in my opinion the most helpful to be comfortable with, is `sf`.

A good set of tutorials is available on the (a bit outdated) r-spatial [site](http://rspatial.org/).

Along with data analysis, there is also a great set of packages for data visualization! While sf dataframes work with `plot()`, these packages offer a lot more flexibility for users.

* [ggplot2](https://github.com/tidyverse/ggplot2): An Implementation of the Grammar of Graphics in R (as of version 3, I believe)
* [mapview](https://github.com/r-spatial/mapview): Interactive Viewing of Spatial Data in R
* [leaflet](https://rstudio.github.io/leaflet/): Create Interactive Web Maps with the JavaScript Leaflet Library (great with shiny apps!)
* [tmap](https://github.com/mtennekes/tmap): R Package for Thematic Maps

If you’re interested in keeping up with the latest r-spatial developments, consider following people like Jakub Nowosad, Robin Lovelace, Edzer Pebesma, Jannes Muenchow, Mark Padgham, Angela Li, Michael Sumner, Leah Wasser, Zev Ross, Kyle Walker, Roger Bivand, Jesse Sadler, and many, many more!

#### Structure of sf data

<img alt="Types of Simple Features Data" src="/img/portfolio/sf-data-types.png" width = "75%">

Image taken from [Geocomputation with R](https://geocompr.robinlovelace.net/spatial-class.html)



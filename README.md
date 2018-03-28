# Crime in Essex

Geospatial visualisation of the criminanity in Essex.

## Description

It is based on January 2018 crime data. Knowing it does not chnge much over time, this month alone is quite representative of the criminal hotspots in Essex. Naturally, other months can be ploted and compared.

## Getting Started

### Dependencies

* Windows, MacOS or UNIX platforms

### Installing

* R from http://cran.r-project.org
* RStudio from https://www.rstudio.com

### Executing program

Downloading data:
* The data used here was found here: https://data.police.uk/data/ (January 2018, Essex Police, include crime data, then Generate file)

Importing data to R(Studio):

```
january18 <- read.csv('C:/Users/Alex/Desktop/2018-01/2018-01-essex-street.csv') # Crimes in Essex in January 2018
```
(WORK IN PROGRESS - GGMAP NOT WORKING)

# Crime in Essex

Geospatial visualisation of, and some stats about, the criminanity in Essex.

## Description

It is based on January 2018 crime data (the most recent data). Knowing it does not change much over time, this month alone is quite representative of the criminal hotspots in Essex. Naturally, other months can be plotted and compared.

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

Libraries and packages

```
install.packages("ggplot2") # if needed
install.packages("ggmap") # if needed

library(ggplot2)
library(ggmap)
```

Then,

```
map01 <- ggmap(get_map(location='Essex', zoom=9)) + 
    geom_hex(data = january18, aes(x=Longitude, y=Latitude)) + 
    ggtitle("Crime Density in Essex in January 2018") + 
    theme(plot.title = element_text(hjust = 0.5), axis.title.x = element_blank(), axis.title.y = element_blank())
```
Output

(WORK IN PROGRESS - GGMAP NOT WORKING)

**Data Summmary:**

* Easily and quickly some useful information

```
summary(january18)
```

```
(...)  
    Latitude                                  Location         LSOA.code    
 Min.   :50.73   On or near Parking Area          :  565   E01021649:  267  
 1st Qu.:51.56   On or near Supermarket           :  563   E01022090:  193  
 Median :51.67   On or near Shopping Area         :  413   E01015852:  182  
 Mean   :51.69   On or near Petrol Station        :  371   E01033140:  143  
 3rd Qu.:51.81   On or near Sports/Recreation Area:  307   E01016011:  134  
 Max.   :54.66   On or near Pedestrian Subway     :  161   E01021318:  134  
 NA's   :2       (Other)                          :12406   (Other)  :13733  
                LSOA.name                            Crime.type  
 Colchester 007D     :  267   Violence and sexual offences:3949  
 Uttlesford 006B     :  193   Anti-social behaviour       :3420  
 Southend-on-Sea 015B:  182   Criminal damage and arson   :1311  
 Chelmsford 010F     :  143   Vehicle crime               :1301  
 Basildon 015C       :  134   Burglary                    :1091  
 Thurrock 015B       :  134   Other theft                 :1073  
 (Other)             :13733   (Other)                     :2641  
                                   Last.outcome.category Context       
 Under investigation                          :5031      Mode:logical  
 Investigation complete; no suspect identified:4110      NA's:14786    
                                              :3420                    
 Unable to prosecute suspect                  : 894                    
 Awaiting court outcome                       : 447                    
 Formal action is not in the public interest  : 404                    
 (Other)                                      : 480                
```
* Alternativelly,
```
install.packages("epiDisplay")
library(epiDisplay)

tab1(january18$Crime.type, sort.group = 'decreasing')
```
```
january18$Crime.type : 
                             Frequency Percent Cum. percent
Violence and sexual offences      3949    26.7         26.7
Anti-social behaviour             3420    23.1         49.8
Criminal damage and arson         1311     8.9         58.7
Vehicle crime                     1301     8.8         67.5
Burglary                          1091     7.4         74.9
Other theft                       1073     7.3         82.1
Public order                       776     5.2         87.4
Shoplifting                        731     4.9         92.3
Drugs                              325     2.2         94.5
Other crime                        245     1.7         96.2
Possession of weapons              156     1.1         97.2
Theft from the person              146     1.0         98.2
Bicycle theft                      134     0.9         99.1
Robbery                            128     0.9        100.0
  Total                          14786   100.0        100.0
```
![](https://github.com/alexandrenm/Crime-in-Essex/blob/master/tab1.png)

* Title and colours can be better
* Anyway, an easy and meaningful chart

```
tab1(january18$Crime.type, sort.group = 'decreasing', col='darkred', main = "Crimes in Essex, January 2018")
```

![](https://github.com/alexandrenm/Crime-in-Essex/blob/master/jan18.png)
![](https://github.com/alexandrenm/Crime-in-Essex/blob/master/jan18b.png)
![](https://github.com/alexandrenm/Crime-in-Essex/blob/master/jan18c.png)


(WORK IN PROGRESS)

* Yet, another possibility

```
install.packages("summarytools")
library(summarytools)

Summarytools::freq(january18$Crime.type, order='freq')
```
```
Frequencies   
Crime.type     
Data frame: january18   
Type: Factor (unordered)   

                                      Freq   % Valid   % Valid Cum.   % Total   % Total Cum.
---------------------------------- ------- --------- -------------- --------- --------------
      Violence and sexual offences    3949     26.71          26.71     26.71          26.71
             Anti-social behaviour    3420     23.13          49.84     23.13          49.84
         Criminal damage and arson    1311      8.87          58.70      8.87          58.70
                     Vehicle crime    1301      8.80          67.50      8.80          67.50
                          Burglary    1091      7.38          74.88      7.38          74.88
                       Other theft    1073      7.26          82.14      7.26          82.14
                      Public order     776      5.25          87.39      5.25          87.39
                       Shoplifting     731      4.94          92.33      4.94          92.33
                             Drugs     325      2.20          94.53      2.20          94.53
                       Other crime     245      1.66          96.19      1.66          96.19
             Possession of weapons     156      1.06          97.24      1.06          97.24
             Theft from the person     146      0.99          98.23      0.99          98.23
                     Bicycle theft     134      0.91          99.13      0.91          99.13
                           Robbery     128      0.87         100.00      0.87         100.00
                              <NA>       0                               0.00         100.00
                             Total   14786    100.00         100.00    100.00         100.00
```

(WORK IN PROGRESS)

## Authors

Alexandre Marques

## Acknowledgments

* [Analytics Defined](https://analyticsdefined.com/plotting-maps-in-r-using-ggmap/)


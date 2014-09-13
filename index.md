---
title       : Global Biodiversity 
subtitle    : Mapping the geographic distribution of species using the GBIF API
author      : C. Ribeiro
job         : Data Analyst
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
logo        : GBIF_logo_short_form.gif
knit        : slidify::knit2slides
---

## Global Biodiversity Information Facility (GBIF)

### GBIF's vision

**"A world in which biodiversity information is freely and universally available for science, society and a sustainable future."**

+ GBIF is an international open data infrastructure funded by governments.

+ It provides a single point of access to more than 400 million records related to evidence of more than one million species.

+ It is the biggest biodiversity database on the Internet.

+ `rgbif` is an R package to search and retrieve biodiversity data using the public GBIF API.

---

## Example: Ursus americanus

The American black bear (Ursus americanus) is a medium-sized bear native to North America. It is the continent's smallest and most widely distributed bear species.

`name_backbone()` is used to search against the GBIF backbone taxonomy:


```r
suppressPackageStartupMessages(library(rgbif))
sp <- name_backbone(name='Ursus americanus', rank='species')
cat(paste(sp[c("kingdom","phylum","class","order","family","genus","species")]),sep=",")
```

```
## Animalia,Chordata,Mammalia,Carnivora,Ursidae,Ursus,Ursus americanus
```
Count the number of georeferenced occurrences with `occ_count()`:


```r
(max_occ <- occ_count(taxonKey=sp$speciesKey, georeferenced=TRUE))
```

```
## [1] 2859
```

---

## Example: Ursus americanus

Search for georeferenced occurrences using `occ_search()`:


```r
dat <- occ_search(taxonKey=sp$speciesKey,
        fields=c("name","key","decimalLatitude","decimalLongitude","basisOfRecord"),
        limit=max_occ, return='data',hasCoordinate= TRUE)
head(dat[,3:5])
```

```
##       basisOfRecord decimalLongitude decimalLatitude
## 1 HUMAN_OBSERVATION          -103.29           29.23
## 2 HUMAN_OBSERVATION           -72.53           43.74
## 3 HUMAN_OBSERVATION          -103.29           29.28
## 4 HUMAN_OBSERVATION          -103.32           29.27
## 5 HUMAN_OBSERVATION          -103.30           29.28
## 6 HUMAN_OBSERVATION           -80.07           37.80
```

---

## Example: Ursus americanus

Map occurrences

*** left


```r
gbifmap(dat)
```

![plot of chunk unnamed-chunk-4](assets/fig/unnamed-chunk-4.png) 

*** right

![]("800px-Ursus_americanusDetail.jpg")



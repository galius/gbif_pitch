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

+ International open data infrastructure, funded by governments.

+ It provides a single point of access to more than 400 million records related to evidence of more than one million species.

+ Biggest biodiversity database on the Internet.

+ `rgbif` is an R package to search and retrieve biodiversity data using the public GBIF API.

---

## Example

### Ursus americanus

The American black bear (Ursus americanus) is a medium-sized bear native to North America. It is the continent's smallest and most widely distributed bear species.

`name_backbone()` is used to search against the GBIF backbone taxonomy:


```r
suppressPackageStartupMessages(library(rgbif))

sp <- name_backbone(name='Ursus americanus', rank='species')
# Classification
cat(paste(sp[c("kingdom","phylum","class","order","family","genus","species")]),sep=",")
```

```
## Animalia,Chordata,Mammalia,Carnivora,Ursidae,Ursus,Ursus americanus
```

---

## Example

### Ursus americanus

Search for georeferenced occurrences using `occ_search()`


```r
dat <- occ_search(taxonKey=sp$speciesKey,
        fields=c("name","key","decimalLatitude","decimalLongitude","basisOfRecord"),
        limit=300, return='data',hasCoordinate= TRUE)
head(dat)
```

```
##               name       key     basisOfRecord decimalLongitude
## 1 Ursus americanus 891034709 HUMAN_OBSERVATION          -103.29
## 2 Ursus americanus 891045574 HUMAN_OBSERVATION           -72.53
## 3 Ursus americanus 891041363 HUMAN_OBSERVATION          -103.29
## 4 Ursus americanus 891056344 HUMAN_OBSERVATION          -103.32
## 5 Ursus americanus 911496466 HUMAN_OBSERVATION          -103.30
## 6 Ursus americanus 911495727 HUMAN_OBSERVATION           -80.07
##   decimalLatitude
## 1           29.23
## 2           43.74
## 3           29.28
## 4           29.27
## 5           29.28
## 6           37.80
```


---

## Example

### Ursus americanus




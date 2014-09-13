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

You can also search for subspecies using `name_suggest()`

```r
name_suggest(q='Ursus americanus',limit=6)
```

```
##       key                  canonicalName       rank
## 1 2433407               Ursus americanus    SPECIES
## 2 6163825 Ursus americanus altifrontalis SUBSPECIES
## 3 6163826     Ursus americanus carlottae SUBSPECIES
## 4 6163827      Ursus americanus eremicus SUBSPECIES
## 5 6163828      Ursus americanus kermodei SUBSPECIES
## 6 6163829        Ursus americanus pugnax SUBSPECIES
```

---

## Slide 5

Get taxonomic key
key <- name_backbone(name='Puma concolor')$speciesKey
dat <- occ_search(taxonKey=key, return='data', limit=300)





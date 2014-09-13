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


```r
suppressPackageStartupMessages(library(rgbif))

sp <- name_lookup('Ursus americanus', rank="species", return = 'data', limit=1)
# Classification
sp[5:9]
```

```
##    kingdom   phylum     order  family genus
## 1 Animalia Chordata Carnivora Ursidae Ursus
```

```r
# Authorship
sp$authorship
```

```
## [1] "Pallas, 1780"
```


---

## Slide 4

---

## Slide 5





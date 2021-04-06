---
title: QAnon at Denison (Under development)
author: R package build
date: '2021-04-05'
slug: qanon-at-denison
categories: []
tags: []
subtitle: ''
summary: ''
authors: []
lastmod: '2021-04-05T15:29:27-04:00'
featured: no
image:
  caption: ''
  focal_point: ''
  preview_only: no
projects: []
---







```r
#March Survey Data
#Import Data, if you would like access, email me at Dennen_j1@denison.edu####
library(readr)
March_2021_deidentified_565 <- read_csv("March_2021_deidentified_565 copy.csv")
```

```
## 
## ── Column specification ────────────────────────────────────────────────────────
## cols(
##   .default = col_double(),
##   StartDate = col_character(),
##   EndDate = col_character(),
##   RecordedDate = col_character(),
##   Q8_1 = col_logical(),
##   Q8_2 = col_logical(),
##   Q8_3 = col_logical(),
##   Q9_1 = col_logical(),
##   Q9_2 = col_logical(),
##   Q9_3 = col_logical(),
##   Q47_14_TEXT = col_character(),
##   Q55_6_TEXT = col_character(),
##   Q61_7_TEXT = col_character()
## )
## ℹ Use `spec()` for the full column specifications.
```

```r
m21 <- March_2021_deidentified_565
#Make all variables lowercase
m21 <- m21 %>% rename_all(tolower) 

#Demographics and stuff####
m21 <- m21 %>% mutate(sexo=q55,
                      faminc=q58,
                      ed=q59,
                      pid8=q3)

#Gender stuff
m21 <- m21 %>% mutate(q54_1=car::recode(q54_1, "NA=0"),
                      q54_2=car::recode(q54_2, "NA=0"),
                      q54_3=car::recode(q54_3, "NA=0"),
                      q54_4=car::recode(q54_4, "NA=0"))

m21 <- m21 %>% mutate(gender2= frcode(q54_1==1 ~ "Male",
                                      q54_2==1 ~ "Female"))
#Sexual orientation
m21 <- m21 %>% mutate(sexo4=frcode(q55==1 ~ "Heterosexual",
                                   q55==2 ~ "Homosexual",
                                   q55==3 ~ "Bisexual",
                                   q55==4 | q55==5 | q55==6 ~ "Other"))


#Making QAnon variable
m21 <- m21 %>% mutate(q6r=6-q6)
m21 <- m21 %>% mutate(q6rf=frcode(q6r==1 ~ "Disagree",
                                  q6r==2 ~ "Somewhat Disagree",
                                  q6r==1 ~ "Neither Agree\nNor Disagree",
                                  q6r==2 ~ "Somewhat\nAgree",
                                  q6r==1 ~ "Strongly\nAgree"))

m21 <- m21 %>% mutate(q6rc=car::recode(q6r, "1:3=0; 4:5=1")) 
m21 <- m21 %>% mutate(q6lab=frcode(q6rc==0 ~ "Disagree",
                                   q6rc==1 ~ "Agree"))
```
#This article is in the process of being written


"I definitely believe that there is some sort of sex trafficking ring that the elites are involved in. But I **don't** believe in QAnon." 

While not a direct quote, this is what a good friend of mine told me when I was discussing a previous post I wrote about QAnon (found on my [website]() and [One Twenty Seven]())





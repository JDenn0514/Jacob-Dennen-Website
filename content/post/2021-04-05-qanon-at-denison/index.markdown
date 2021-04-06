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







#This article is in the process of being written

"I  believe that there is some sort of sex trafficking ring that the elites are involved in. Does that mean I believe in QAnon??" This is part of a conversation I had with a close friend of mine when I told him about a previous post of mine that looked at QAnon's relationship with different generations (found on my [website](https://jacob-dennen.netlify.app/post/qanon-millenials-and-gen-z/) and [One Twenty Seven](https://onetwentyseven.blog/2021/03/17/qanon-millennials-and-gen-z/)). 





```r
m21 %>% group_by(gender2) %>% 
  filter(q6rf!="NA") %>% 
  ct(q6rf) %>% 
  ggplot(., aes(x=q6rf, y=pct, fill= gender2)) + 
  geom_col(alpha=.8, color="black", width = .75, position = position_dodge2()) + 
  theme_hc() +
  theme(text=element_text(family="O", size=12),
        legend.position = "bottom",
        panel.grid.major.x = element_blank(),
        panel.grid.major.y = element_line(size=.5, color="gray80"),
        axis.text.x = element_text(size=9),
        plot.title = element_text(hjust = .5)) +
  geom_text(aes(y=(pct+.025), label = round(pct*100, digits=2)), family="O",
            position = position_dodge(width = .75)) +
  scale_y_continuous(labels=percent_format(accuracy=1)) +
  labs(x="", y="", 
       title="Gendered Views of QAnon",
       caption="Source: October 2020 Survey; @JDenn0514") +
  scale_fill_manual(name="Gender", 
                    labels=c("Men", "Women", "NA"), 
                    values = c("#FF6F00FF", "#C71000FF", "White"))
```

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-4-1.png" width="672" />




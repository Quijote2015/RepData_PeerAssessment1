# TEST
Cristian Gutierrez  
26 de marzo de 2018  




```r
library(dplyr)
```

```
## Warning: package 'dplyr' was built under R version 3.4.3
```

```
## 
## Attaching package: 'dplyr'
```

```
## The following objects are masked from 'package:stats':
## 
##     filter, lag
```

```
## The following objects are masked from 'package:base':
## 
##     intersect, setdiff, setequal, union
```

```r
library(ggplot2)
```

```
## Warning: package 'ggplot2' was built under R version 3.4.3
```

```r
library(knitr)
library(lubridate)
```

```
## Warning: package 'lubridate' was built under R version 3.4.3
```

```
## 
## Attaching package: 'lubridate'
```

```
## The following object is masked from 'package:base':
## 
##     date
```

```r
library(scales)
```

```
## Warning: package 'scales' was built under R version 3.4.3
```

```r
activity <- read.csv("activity.csv",header = TRUE, sep = ',')
activity$date <- ymd(activity$date)
steps <- activity %>% 
  filter(!is.na(steps)) %>%
  group_by(date) %>% 
  summarize(steps = sum(steps))
```

```
## Warning: package 'bindrcpp' was built under R version 3.4.3
```
What is mean total number of steps taken per day?

```r
ggplot(steps, aes(x = steps)) +
  geom_histogram(fill = "mistyrose3", col=I("black"), binwidth = 1000) +
  labs(title = "Total Number of Steps Taken Each Day",
       x = "Steps per Day", 
       y = "Occurances")
```

![](TEST_files/figure-html/unnamed-chunk-2-1.png)<!-- -->


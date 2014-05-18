Title
========================================================

This is an R Markdown document. Markdown is a simple formatting syntax for authoring web pages (click the **Help** toolbar button for more details on using R Markdown).

When you click the **Knit HTML** button a web page will be generated that includes both content as well as the output of any embedded R code chunks within the document. You can embed an R code chunk like this:


```r
setwd("D:/Courses/Coursera/RResearch")
activity <- read.csv("activity.csv", header = TRUE)
```



```r
# Calculating total steps per day and creating histogram

hist(totsteps$x, breaks = 12, xlab = "Total steps per day")
```

```
## Error: object 'totsteps' not found
```

```r
# Calculating Mean & Median Steps per day
meansteps <- aggregate(totsteps$x, by = list(totsteps$Group.1), FUN = mean)
```

```
## Error: object 'totsteps' not found
```

```r
mediansteps <- aggregate(totsteps$x, by = list(totsteps$Group.1), FUN = median)
```

```
## Error: object 'totsteps' not found
```



```r
# Creating dataset with average per time period
meansteps1 <- aggregate(activity$steps, by = list(activity$interval), FUN = mean, 
    na.rm = TRUE)
# Plotting data
plot(meansteps1, type = "l")
```

![plot of chunk unnamed-chunk-3](figure/unnamed-chunk-3.png) 

```r
# Interval with maximum steps
maxinterval <- which.max(meansteps1$x)
```



```r
# Calculating number of missing values in dataset
for (Var in names(activity)) {
    missing <- sum(is.na(activity[, Var]))
    if (missing > 0) {
        print(c(Var, missing))
    }
}
```

```
## [1] "steps" "2304"
```




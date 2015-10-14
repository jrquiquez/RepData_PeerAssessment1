# Reproducible Research: Peer Assessment 1
Jr Enriquez  
## Setting up R
We're going to need some libraries in order to make this project easier. In this case we'll use dplyr

```r
library(dplyr)
```


## Loading and preprocessing the data
The data consists of two months of data from an anonymous individual collected during the months of October and November, 2012 and include the number of steps taken in 5 minute intervals each day.  

##### Variables

* steps: Number of steps taking in a 5-minute interval (missing values are coded as NA)

* date: The date on which the measurement was taken in YYYY-MM-DD format

* interval: Identifier for the 5-minute interval in which measurement was taken  

This code loads the csv into a data frame and converts the column classes

```r
dataset <- read.csv(file = "activity.csv",header = TRUE)
dataset$date <- as.Date(dataset$date,"%Y-%m-%d")
```

## What is mean total number of steps taken per day?
First we need to calc the total of steps for each day and put it into a graph for ease of understanding. 


```r
stepsday <- group_by(dataset,date)
stepsday<-summarise(stepsday,stepsday=sum(steps,na.rm = T))
hist(stepsday$stepsday, main = "Steps per Day",xlab = "Steps per day",ylab = "Frequency",col = "orange")
```

![](PA1_template_files/figure-html/unnamed-chunk-3-1.png) 

Once we calc the total steps per day we can use the proccessed data to calc the mean. 

```r
stepsdaymean <- mean(stepsday$stepsday)
stepsdaymedian <- median(stepsday$stepsday)
```

* #### **Mean of steps per day: 9354.23**
* #### **Median of steps per day: 10395**
As you can see above the mean 9354.23 and the median 10395 are pretty close. 

## What is the average daily activity pattern?



## Imputing missing values



## Are there differences in activity patterns between weekdays and weekends?
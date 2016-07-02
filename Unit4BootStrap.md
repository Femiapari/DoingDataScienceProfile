---
title: "Unit4Homework/Bootstrap"
author: "Olufemi Adesanya"
date: "Friday, July 01, 2016"
output: 
   html_document:
    keep_md: true
---

##Normal dist of sample 200 (Bootstrap)
```{r}
y <- rnorm(200, 20, 5)
n <-1000  # Simple normal distribution
tdata <- numeric(n)
for(i in 1:n) {
    samp <- sample(y, 200, replace=TRUE)
    tdata [i] <- mean(samp)
}
summary(tdata)
hist(tdata)
```
##Normal distribution of size 100
```{r}
x <- rnorm(100, 20, 5)
bar <- mean(x)
normdata <- numeric(2000)  ## Find the pivot t-interval
for (i in 1:2000){
    samp <- sample(y,size=70,replace=TRUE)
    bootmean = mean(samp)
    bootsd = sd(samp)
    tpivot = (bootmean - bar)/(bootsd/sqrt(100))
    normdata[i] <- tpivot
}
quantile <- quantile(normdata, c(0.025, 0.975)) # numbers at 2.5% and 97.5% quantile 
quantile
```
##Exponential distribution: sample size 30
```{r}
n <- 30 
exp <- numeric(2000)

for (i in 1:2000){
    x <- exp(n)
    exp[i] <- mean(x)
}
mean(exp)
```
###Exponential distribution: sample size 80
```{r}
n <- 80 
exp <- numeric(2000)
for (i in 1:2000){
    x <- exp(n)
    exp[i] <- mean(x)
}
mean(exp)
```


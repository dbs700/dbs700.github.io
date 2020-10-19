---
title: 'Anomaly detection algorithms. What is it? Which tools works better and how we can add weights and features to boost the accuracy with Extended Isolation Forest
  via R'
authors: 
- Hugo Authors
date: '2020-10-19'
slug: anomaly-detection-algorithms-from-quantiles-to-extended-isolation-forest-with-r
categories: []
tags: []
hero: /images/hero-21.jpg
excerpt: Anomaly detection plays a critical role for any business. For instance, imagine that your streaming service suddenly experiencing some technical problems but the support team have no idea about what's going on, or you're running some on-line mailorder, and transactions or conversion rate dropped without any obvious reason. For these types of events we have to implement some sort of anomaly or changepoint detection systems.
---


Anomaly detection plays a critical role for any business. For instance, imagine that your streaming service suddenly experiencing some technical problems but the support team have no idea about what's going on, or you're running some on-line mailorder, and transactions or conversion rate dropped without any obvious reason. For these types of events we have to implement some sort of anomaly or changepoint detection systems.

Generally speaking, anomaly detection is the process of identifying unexpected items or events, which differ from the normal ones. Instead of this, changepoint detection looks for a probability distribution function. We'll try to cover the main tools that we have in the field, and also find out what works well for a different types of events.

One of the main questions that we need to answer before applying these tools is to get an idea about the data.If we work with timeseries data, then the solution will based on type of time-series. 

Univariate Time Series. The term "univariate time series" refers to a time series that consists of single (scalar) observations recorded sequentially over equal time increments. (www.itl.nist.gov). Multivariate time series, on the other hand, has more than one time-dependent variable. 

Pinterest Engineering team, earlier classified the whole range of tools with 4 main categories:

- State space models: exponential smoothing, Holt-Winters, ARIMA
- Decomposition: classical decomposition, STL
- Deep learning: recurrent neural networks
- Dimensionality reduction: RPCA, SOM, discords, piecewise linear

They're all have pros and cons, and as always, the more deeper preprocessing and feature engineering you do, the better result you get.
In the real world, we face problems like unbalanced data, lots of missing variables, mistypes, etc. So what worked well in my case?

- Labeling not existing hours
- Trend and seasonal decomposition
- Adding rolling mean for time intervals
- Splitting data by day/night
- Creating categorical features
- Using other features like ratios based on weights
- Using Extended Isolation Forest

According to Isolation Forest papers, the score produced by algorithm should be between 0 and 1. The anomaly score of an input sample is computed as the mean anomaly score of the trees in the forest.

![Extended Isolation Forest](/post/2020-10-19-anomaly-detection-algorithms-from-quantiles-to-extended-isolation-forest-with-r_files/anomaly1.jpg)

The measure of normality of an observation given a tree is the depth of the leaf containing this observation, which is equivalent to the number of splittings required to isolate this point. The score is close to 1 could be described as anomalies. If the score is smaller than 0.5, then we could assume that this is normal instance.

So approach like this worked good for my task, there is still a room for improvement. Trying more with STL by decomposing data with seasonal, trend, and remainder components based on different seasonal frequencies. Modeling time-series and working with residuals. Creating a threshold with 3 sigma SD as a ground truth metric for outlier detection. Applying changepoint detection algorithms like PELT.


[Extended Isolation Forest](https://arxiv.org/pdf/1811.02141.pdf)




{{<subscribe email = "your@email.com">}}








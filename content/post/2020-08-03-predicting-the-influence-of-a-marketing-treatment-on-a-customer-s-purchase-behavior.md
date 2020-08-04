---
title: Predicting the influence of a marketing treatment on a customer's purchase behavior
authors: 
- Hugo Authors
date: '2020-08-03'
slug: predicting-the-influence-of-a-marketing-treatment-on-a-customer-s-purchase-behavior
categories: []
tags: []
hero: /images/hero-0555.jpg
excerpt: Usually, the promotion of products occurs through communication with the client via various channels, push, SMS messages, etc. The formation of segments for promotion is solved by using machine learning. Today we will cover some of these approaches that solve the issue.
---


Usually, the promotion of products occurs through communication with the client via various channels: push, SMS messages, etc. The formation of segments for promotion is solved by using machine learning. Today we will cover some of these approaches that solve the issue.

Based on Wikipedia - Uplift modeling, also known as incremental modeling, true lift modeling, or net modeling is a predictive modeling technique that directly models the incremental impact of a treatment (such as a direct marketing action) on an individual's behavior. Uplift modeling has applications in customer relationship management for up-sell, cross-sell, and retention modeling. It has also been applied to the political election and personalized medicine. Unlike the related Differential Prediction concept in psychology, Uplift Modelling assumes an active agent.

##What models do we have?

Look-alike model (Probability based on similarity)
Response model (Probability based on afterward action)
Uplift model (Probability of action with treatment - Probability of action without treatment)


So when its better to use uplift instead of other models? If we want to advertise a well-known and popular product, but at the same time, we do not want to spend the budget on customers who will buy this product even without any advertisement.

There are various research articles on uplift modeling whereas each defends the specific approach, but at the end of the day, we could sum up all with a list of uplift models:

Single model approach. This is the simplest and most intuitive solution: the model is trained simultaneously on two groups, while the binary variable related to ads acts as an additional feature. We rate each object from the test sample twice: with the communication flag equal to 1 and equal to 0. Subtracting the probabilities for each observation, we obtain the required uplift.

Two models approach. It's the most popular and here we separately predict the probability for 2 groups with a communication flag equal to 1 and equal to 0.  Then, we calculate the difference in the probability estimates.

Researchers from Humboldt-University of Berlin made a great research on comparing different algorithms with different types of datasets in 2019. The main finding was that the way how marketing campaign was built is heavily affecting the uplifts. However, we are able to increase model profits with uplift instead of random sampling. Even the simple upliftRF function which comes with uplift R package and implements Random Forests with split criteria designed for binary uplift modeling tasks doing better than random selection.

![UpliftRF](/post/2020-08-03-predicting-the-influence-of-a-marketing-treatment-on-a-customer-s-purchase-behavior_files/upliftRF.png)

The picture above shows the Qini coefficients for Hillström dataset. This dataset contains 64,000 customers who last purchased within twelve months. The customers were involved in an e-mail test. 1/3 were randomly chosen to receive an e-mail campaign featuring Men's merchandise. 1/3 were randomly chosen to receive an e-mail campaign featuring Women's merchandise. 1/3 were randomly chosen to not receive an e-mail campaign. This plot shows a natural generalization of the Gini coefficient to the case of uplift. Qini is defined as the area between the actual incremental gains curve from the fitted model and the area under the diagonal corresponding to random targeting.

Another widespread approach is to use casual trees. The causalTree function (comes with causalTree R package) builds a regression model and returns a rpart object, which is the object derived from rpart package, implementing many ideas in the CART (Classification and Regression Trees), written by Breiman, Friedman, Olshen, and Stone. Like rpart, causalTree builds a binary regression tree model in two stages but focuses on estimating heterogeneous causal effect.

![Causaltree](/post/2020-08-03-predicting-the-influence-of-a-marketing-treatment-on-a-customer-s-purchase-behavior_files/causaltreepruned.png)




Speaking of more complicated models, it was well described in 'Uplift Regression: The R Package tools4uplift' research paper as well:

>Interaction model considers the relationship among three or more variables and describes a situation in which the simultaneous influence of two variables on a third is not additive. Other approaches to uplift modeling try to directly model the difference in conditional success probabilities between the treatment and control groups. Most current active research is in this direction. 

>Such methods are mainly adaptation of three types of machine learning algorithms: 
>a) decision tree learners (Rzepakowski and Jaroszewicz (2010), Radcliffe and Surry (2011), Guelman et al. (2015), So ltys et al. (2015) or Zhao et al. (2017))
b) regression models adapted to the uplift (Radcliffe (2007) or Jaskowski and Jaroszewicz (2012)) 
c) support vector machines for uplift (Zaniewicz and Jaroszewicz (2013), Kuusisto et al. (2014) or Zaniewicz and Jaroszewicz (2017))

At this point, I would like to finish a brief explanation on this topic but we have to keep an eye on uplift as the undoubtful helper for optimization problems in marketing. Uplift modeling is useful for well-established companies that have been on the market for a long time with a developed base of clients. This method allows the business to build better customer interactions and increase profits.

 
[Susan Athey, Guido Imbens. Recursive Partitioning for Heterogeneous Causal Effects.](http://arxiv.org/abs/1504.01132)

[Mouloud Belbahri, Alejandro Murua1, Olivier Gandouet, and Vahid Partovi Nia. Uplift Regression: The R Package tools4uplift](https://dms.umontreal.ca/~murua/research/UpliftRegression.pdf)


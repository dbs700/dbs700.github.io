---
title: How to get insights from Social Media using Machine Learning or why you shouldn't trust everything you see
authors:
- Hugo Authors
date: '2020-05-02'
slug: social-media-using-machine-learning
categories: []
tags: []
hero: /images/hero-16.jpg
excerpt: Wikipedia says influencer marketing is a form of social media marketing involving endorsements and product placement from influencers, people and organizations who have a purported expert level of knowledge or social influence in their field.
---

## Preface

Today I would like to share some insights based on influencer marketing and digital performance. Wikipedia says influencer marketing (a.k.a. influence marketing) is a form of social media marketing involving endorsements and product placement from influencers, people, and organizations who have a purported expert level of knowledge or social influence in their field. Influencer content may be framed as testimonial advertising; influencers play the role of a potential buyer or may be involved as third parties. These third parties can be seen in the supply chain (such as retailers or manufacturers) or as value-added influencers, such as journalists, academics, industry analysts, and professional advisers. 

One of the issues that every social media faces is estimating duplicates and false accounts. If we look at Facebook latest reports, we could find "Limitations of Key Metrics and Other Data" page.

>We regularly evaluate our Facebook metrics to estimate the number of "duplicate" and "false" accounts among our MAUs. A duplicate account is one that a user maintains in addition to his or her principal account. We divide "false" accounts into two categories: (1) user-misclassified accounts, where users have created personal profiles for a business, organization, or non-human entity such as
a pet (such entities are permitted on Facebook using a Page rather than a personal profile under our terms of service); and (2) violating accounts, which represent user profiles that we believe are intended to be used for purposes that violate our terms of service, such as bots and spam. - 1Q 2020 Facebook Quarterly Earnings Report

So even Goliath-sized Facebook agrees that the problem exists and profiles should be reviewed. 

>Duplicate and false accounts are very difficult to measure at our scale, and it is possible that the actual number of duplicate and false accounts may vary significantly from our estimates. In the fourth quarter of 2019, we estimated that duplicate accounts may have represented approximately 11% of our worldwide MAUs. - 1Q 2020 Facebook Quarterly Earnings Report

For our research, I choose the Vkontakte (VK) social network. It's the largest Russian social network owned by Mail.ru Group, and it's finished the year as a strong leader among communication platforms in Russia, with 71.6m MAU (+2.2% YoY), including 65.2m on mobile (+7.9% YoY) as of December 2019. VK is focused on boosting time spent and stickiness: this was up 12.5% in 2019 to 36 minutes per day, including 16% growth on mobile.* 

VK aims to cover all the needs of its users and is actively developing the open Mini Apps platform for third-party developers; this allows users to play games, shop, communicate, order food, look for jobs, and much more all inside the VK ecosystem without having to download third-party apps. According to Mediascope, on average, users visit VK every other day, more than any other Russian social network.

Based on the latest financial report, the strategy for 2020-22 will be focused on the formation of the ecosystem via cross-selling and deeper integration of the Group’s assets. Mail.ru Group is transforming VK into the heart of its ecosystem. A VK account will be the foundation for the Group ID, and VK Pay is being scaled across the Group, VK Mini Apps will turn into a unified Group platform for developers, and the VK Super App Software Development Kit will be the technology uniting all these initiatives.*

So keeping it all in mind, I decided to dive into the biggest and the most popular news page at VK - RIA Novosti. RIA is a state-operated domestic news agency with almost 2.5M followers on Vkontakte. This followers base represents 3,5% of total Monthly Active Users on Vkontakte.

## Uncovering real numbers

Therefore I wanted to quantify the amount of real, active users and get insights based on the sample. Our Switzerland colleagues did similar research with a focus on 115 Swiss Instagram influencers, and the results show that fake followers are indeed a widespread phenomenon, as almost a third of approximately 7 million classified accounts appear to be false. On average, the surveyed influencers have around 30% fake followers.


![RIA Novosti followers on Vkontakte](/post/social-media-using-machine-learning_files/followers.png)

Speaking for RIA Novosti - the most extensive news page at Vkontakte, the results are quite similar. Almost 34% of followers not visited Vkontakte for more than six months, where 14% that still being counted as followers - banned or deleted profiles. In other words, from 2.5M followers, only 1.5M are using Vkontakte daily. For further analysis, we removed banned/deleted profiles.

Let's see if we have any behavioral patterns in terms of time.

![Vkontakte user activity based on 2.1M observations](/post/social-media-using-machine-learning_files/time.png)

The majority of both Female and Male, mostly using the platform at 11:30 (GMT). The geographical breakdown has shown that the majority of users that filled in their location come from Moscow and Saint-Petersburg, where a Female audience prevailed. 


## Who got more followers? Modeling user profile

For this purpose, we used a Bayesian approach with the R brms library. The brms package provides an interface to fit Bayesian generalized (non-)linear multivariate multilevel models using Stan, which is a C++ package for performing full Bayesian inference. The formula syntax is very similar to that of the package lme4 to provide a familiar and straightforward interface for performing regression analyses. 

We fit this model to predict the number of followers since it's one of the primary metrics of success on social media.

![Modeling user profiles on VK](/post/social-media-using-machine-learning_files/Rplot.png)

So to get more followers on VK, we should create Female profile with photo, using mostly iPhone and Windows VK App, we should hide all friends, doesn't accept new ones, as well as messages, we could show any type of education and married status. We could choose Anastasia, Ekaterina, or Yulia, as the names that magnetize more followers. 

As the final word, we should remember that any social media platform has one risk related to their business. If they fail to retain existing users or add new users, and users engagement dropped, then the revenue and business may be significantly harmed, because they generate almost all of the income from advertising. In this case, keeping high numbers (that most of the time should be double checked) is the way to keep business going.














{{<subscribe email = "your@email.com">}}
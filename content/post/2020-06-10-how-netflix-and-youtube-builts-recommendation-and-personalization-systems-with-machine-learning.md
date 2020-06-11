---
title: How Netflix and YouTube built recommendation and personalization systems with
  Machine Learning
authors: 
- Hugo Authors
date: '2020-06-10'
slug: how-netflix-and-youtube-builts-recommendation-and-personalization-systems-with-machine-learning
categories: []
tags: []
hero: /images/hero-610.jpg
excerpt: While analyzing some of YouTube channels, we discovered that suggested videos take 60% of total views, and in this case, it could be useful to know how this type of algorithm works and how we could benefit from it.
---

While analyzing some of YouTube channels, we discovered that suggested videos take 60% of total views, and in this case, it could be useful to know how this type of algorithm works and how we could benefit from it.

So what should we expect in the future?

In the nearest future, we could expect that the share of suggested views may grow up to 80% (as it already turned out for Netflix). Taking both YouTube and Netflix as they compete for the same audience, for the same watch time, we may see that they have the same ecosystem and works on the same problems related to content suggestions and personalizations but on different scales.

For example, YouTube’s recommendation system is comprised of two neural networks: one for candidate generation and one for ranking. The candidate generation network takes events from the user’s YouTube activity history as input and retrieves a small subset (hundreds) of videos from a large corpus. These candidates are intended to be generally relevant to the user with high precision. The candidate generation network only provides broad personalization via collaborative filtering. The similarity between users is expressed in terms of features such as IDs of video watches, search query tokens, and demographics. Demographic characteristics are essential for providing priors so that the recommendations behave reasonably for new users. The user’s geographic region and device are embedded and concatenated. 

## Netflix recommender system

Netflix is well-known for inventing Internet TV. Netflix uses multiple algorithms that rely on statistical and machine learning techniques: supervised (classification, regression) and unsupervised approaches (dimensionality reduction through clustering or compression).

>Consumer research suggests that a typical Netflix member loses interest after perhaps 60 to 90 seconds of choosing, having reviewed 10 to 20 titles (perhaps 3 in detail) on one or two screens. The user either finds something of interest or the risk of the user
abandoning our service increases substantially. The recommender problem is to make sure that on those two screens each member in our diverse pool will find something compelling to view, and will understand why it might be of interest.

Netflix is an amazing place in terms of personalization. Take, for example, a personalized video ranker (PVR) algorithm. As its name suggests, this algorithm orders the entire catalog of videos for each member profile in a customized way. Netflix has also found that shorter-term temporal trends are powerful predictors of videos that the members will watch, especially when combined with the right dose of personalization, which is used in trending ranker algorithm. Netflix also uses the so-called continue watching ranker algorithm that sorts the subset of recently viewed titles based on an estimate of whether the member intends to resume watching or rewatch, or whether the member has abandoned something not as attractive as anticipated.

Then, they also have a Video-Video similarity algorithm that is an unpersonalized algorithm that computes a ranked list of videos the similars for every video in the catalog. And in the end, all these outputs used in the page generation algorithm that constructs every single page of recommendations, taking into account the relevance of each row to the member as well as the diversity of the page.

What are the limitations? The algorithm does a satisfactory job helping users who have some history on the platform, since all the predictions based on historical data. As for new users, it’s still a pretty big room for improvement. That’s why you’re passing some surveys during the sign-up (used by Quora, Netflix, and others).

## How may users improve the performance of the YouTube channel?

Based on multiple research papers from the YouTube developers and Netflix technology team, thumbnail pictures are the only influencer to a user’s decision to watch content. So, if you want to improve your channel performance, you should keep this in mind and focus not only on content and titles itself but also on thumbnails. Recommendation algorithm weights this feature (for example, how a user may watch a given video with high probability generally but is unlikely to click on the specific homepage impression due to the choice of thumbnail image). Experimenting with different layouts and designs will improve the performance of the channel (A/B tests).

We shouldn’t take the YouTube search result page for the specific topic as the model of how videos should look like since search result pages have different algorithms and don’t have straight connections to the recommendation algorithm.

Great stories travel – but regional nuances can be powerful. This was one of the findings from Netflix research. It means that regional differences still exist and are essential for some titles and imagery; what works well in one region, not necessarily means that it would work for other areas or countries.

Another finding was that images that have expressive facial emotion or that convey the tone of the title do particularly well. Images featuring recognizable or polarizing characters from the title tend to do well too, the same for actions - if emotions or characters are not applicable. They’ve also proved in research papers that thumbnail image performs well only when it contained no more than three people.

Also, we shouldn’t try to create clickbait only videos since YouTube works against it. On the other hand, it’s no good to pay too much attention to optimizing view duration only. The best way is to try to find a balance between CTR/average view duration of the video. This could be possible with A/B tests that are still considered as the best tool on the market.

And the last, the most important signals are those that describe a user’s previous interaction with the item itself and other similar items. That means that if you could propose additional content to the audience after or while they watch the video on the channel, this will undoubtfully boost chances to be placed higher in suggested videos scrollbar.


Based on:


[Deep Neural Networks for YouTube Recommendations](https://static.googleusercontent.com/media/research.google.com/en//pubs/archive/45530.pdf)

[The Netflix Recommender System: Algorithms, Business Value, and Innovation](https://dl.acm.org/doi/pdf/10.1145/2843948)

[Recent Trends in Personalization: A Netflix Perspective](https://www.slideshare.net/justinbasilico/recent-trends-in-personalization-a-netflix-perspective)





{{<subscribe email = "your@email.com">}}



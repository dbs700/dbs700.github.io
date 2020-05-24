---
title: Marketing research and spatial planning in retail with R. Glimpse on a MCI/MCI2 packages - market area models for retail and service locations
authors:
- Hugo Authors
date: '2020-05-23'
slug: marketing-research-and-spatial-planning-in-retail-with-r
categories: []
tags: []
hero: /images/hero-27.jpg
excerpt: Market area models can be used in retail location analysis to ﬁnd new locations, to evaluate the existing outlets or to assess the impact of changes in the competitive landscape 
---

Every time when we go to the grocery store or any other shop, we leave some data. On a micro scale this includes any checkout at a retail store. On a macro scale data is collected from groups of retailers. Generally, the point of sale data is collected by a business when some transaction happens.  

This type of data could tell us a lot about consumer preferences and behaviour, but also we could imply market area models. Developed by Thomas Wieland, MCI package provides this type of analysis and the output can be interpreted like any other linear model ﬁtted by lm(), which is easy to understand. Market area models can be used in retail location analysis to ﬁnd new locations, to evaluate the existing outlets or to assess the impact of changes in the competitive landscape. 

Market areas of retail locations result from the consumer spatial shopping behaviour, more precisely, their store choice. Thus, a market area is inﬂuenced by many factors such as the transport costs (e.g. distance, travel time) between customers and locations and, of course, the characteristics of the competitors (e.g. perceived "attraction", pricing, image or the opportunity for multi-purpose and comparison shopping). Mostly, the market areas of competing supply locations overlap, which means that they are in spatial competition (Rodrigue et al., 2006; Wieland, 2015a). 

Traditionally, market area analysis includes the delineation and segmentation of market areas and can be divided into inductive-empirical and deductive-theoretical approaches. The ﬁrst type consists of constructing market areas based on empirical observations such as point-of-sale (POS) surveys (customer spotting), while in the latter approach this work is done by using mathematical market area models (Löfﬂer, 1998). 

Modern market area analyses are mostly a combination of both, especially when using econometric market area models which are ﬁtted by empirical data (Wieland, 2015a). Market area models can be used in retail location analysis to ﬁnd new locations, to evaluate the existing outlets or to assess the impact of changes in the competitive landscape (Berman and Evans, 2013; Huff and McCallum, 2008). The usage of market area models can also be transferred to other service locations, such as health services (Jia et al., 2015). 

So, let's try MCI R package. It comes with prebuilt dataset based on a survey conducted at two supply locations in the east of Karlsruhe, Germany, in May 2016. There are a couple of data including spatial (produced with ggmap), information about the city districts, grocery data, general shopping behaviour.

![](/post/2020-05-23-marketing-research-and-spatial-planning-in-retail-with-r_files/skim1.png)

The first thing that we want to know is how much of the customers and expenditures come from origins with a maximal travel time of 10,20,30 and more than 30 minutes. After some data wrangling, we've got the model with not so good R2, but we could improve it with optimization that is also covered in the research article (Thomas Wieland, The R Journal Vol. 9/1, June 2017 ISSN 2073-4859.)

MCI2 package was made more user friendly, but the overall approach is still the same. Generally, to get distance decay result, we need to reshape our data to interactions matrix first, then create zones of empricial market shares by driving time and after that we could fit distance decay function.

![](/post/2020-05-23-marketing-research-and-spatial-planning-in-retail-with-r_files/km.png)

The second function that is more engaging I think, is predicting the market share. Since we predict the share, we could change variables to see the difference. For example, we could analyze the impact of a change in the competitive environment: what if some store increased it's square by 10% ? How will, purchasing power flows with respect to this supplier and to all other stores change?

We have to create the interaction matrix first, then, we calculate the total customers and expenditures and the overall market shares. We have also add travel times and grocery stores characteristics.

So the main prediction would look like this:

![](/post/2020-05-23-marketing-research-and-spatial-planning-in-retail-with-r_files/first.png)

And if we'll change the sales area of REAL by increasing it, let's say by 10%, the overall market share changes like that:

![](/post/2020-05-23-marketing-research-and-spatial-planning-in-retail-with-r_files/second.png)

As the conclusion, I've wanted to point out that the article written by Dr. Wieland helps a lot with market share prediction, and covers different situations like dealing with the problem of fitting the Huff Model on condition that no empirically observed store choices, market shares and market areas are available and many others things. If you're interested in this topic, please check the following link [here](https://www.researchgate.net/publication/329389548_MCI2_Market_Area_Models_for_Retail_and_Service_Locations_R_package_v100_R_package_documentation_httpsCRANR-projectorgpackageMCI2 ).






{{<subscribe email = "your@email.com">}}




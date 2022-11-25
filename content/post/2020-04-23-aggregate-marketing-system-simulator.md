---
title: Aggregate marketing system simulator for different scenarios and channels
author: ''
date: '2020-04-23'
slug: aggregate-marketing-system-simulator
hero: /images/hero-17.jpg
excerpt: Running a business is like running a race, and in this term every item is
  important, so if you have powerful tools and bright minds, you will definitely get
  in a better position.
---

## Preface

Running a business is like running a race, and in this term every item is important, so if you have powerful tools and bright minds, you will definitely get in a better position. Google are not only well-known for producing high quality products for users, but also for producing tools that helps us gain lot of insights from any type of data.

Today we'll explore one of them for simulating aggregated marketing times series data. The Aggregate Marketing System Simulator is a simulation tool capable of generating channel-level marketing spend, website visits, competitor spend, pricing, sales volume, etc. It is flexible enough to model a wide variety of marketing situations like types of ad targeting, sales seasonality, competitor activity, and much more.

Additionally, AMSS generates ground truth for marketing performance metrics, including return on advertising spend (ROAS) and marginal ROAS (mROAS). The capabilities provided by AMSS create a foundation for evaluating and improving measurement methods, including media mix models (MMMs), campaign optimization, and geo experiments, across complex modeling scenarios.

So what this tool is good for 'what if' analysis such as:

*   Estimate the impact of various media strategies (the media mix) on revenue or some other key performance indicator (KPI).

*   Forecast the impact of future media strategies on the KPI.

*   Recommend media strategies to optimize future KPIs.


We could create multiple years of weekly marketing data including consumer behaviour that could be naturally changed over time. 
Next step would be settig up budget cycle for all media channels as well as each channel behavior. 
For example, TV causes changes in consumer mindset by increasing brand awareness and brand favorability. In our tool, we could specifiy this patterns for traditional media and paid or search channels differently.

The last step would be to set the parameters for Sales module including, but not limited to:

* The price of the advertiser's product at each time point. A constant price can be written as a single number.

* The linear relationship between price and demand for consumers who have reached the 'purchase' activity state. The demand curve differs by brand state (brand favorability, brand loyalty, and brand availability).

* The strength of competitor effects is also specified here. Demand for the competitor's product differs by brand loyalty state.


After that we could see the simulated data and modify scenarios for different budget allocations. 
And now the brilliant thing implemented in this library - Calculating Return on Ad Spent. It's not just calculated KPI but also it compares revenue under two simulation settings (the original, and a counterfactual of what would have happened if the advertiser had set a different budget for the relevant media channel).

Also, we could calculate marginal Return on Ad Spent by setting budget proportion ratio, and see different results like if we had 5% decrease or increase for each marketing channel spend.

So, summing it all up, and keeping in mind that this is unofficial Google product, it still helps us to create a really useful insights from simulated data before we actually spend any money.


{{<subscribe email = "your@email.com">}}
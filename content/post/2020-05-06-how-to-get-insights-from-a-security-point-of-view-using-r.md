---
title: How to get insights from a security point of view using R
authors:
- Hugo Authors
date: '2020-05-06'
slug: how-to-get-insights-from-a-security-point-of-view-using-r
categories: []
tags: []
hero: /images/hero-12.jpg
excerpt: ~
---

Recently I came across some cyber security articles written by Mckinsey but then I suddenly remembered one of the brilliant resource focused on R and cybersecurity research, DFIR, risk analysis, and much more. The person behind this resource is Bob Rudis who wrote a book along with Jay Jacobs - Data, Driven Security: Analysis, Visualization and Dashboards

>Uncover hidden patterns of data and respond with countermeasures Security professionals need all the tools at their disposal to increase their visibility in order to prevent security breaches and attacks. This careful guide explores two of the most powerful ? data analysis and visualization. You'll soon understand how to harness and wield data, from collection and storage to management and analysis as well as visualization and presentation. Using a hands-on approach with real-world examples, this book shows you how to gather feedback, measure the effectiveness of your security methods, and make better decisions. Everything in this book will have practical application for information security professionals. Helps IT and security professionals understand and use data, so they can thwart attacks and understand and visualize vulnerabilities in their networks Includes more than a dozen real-world examples and hands-on exercises that demonstrate how to analyze security data and intelligence

If we want to check some website, we could do a lot of things in R with libraries focused on cyber security analysis. We'll use urlscan.io API by creating the request that will browse the URL like a regular user and record the activity that this page navigation creates. This includes the domains and IPs contacted, the resources (JavaScript, CSS, etc) requested from those domains, as well as additional information about the page itself. urlscan.io will take a screenshot of the page, record the DOM content, JavaScript global variables, cookies created by the page, and a myriad of other observations.

We could also double check all the information with a browser version of urlscan to see all kinds of confirmations.

So basic result for domain:mckinsey.com will look like this:

![Domain check](/post/2020-05-06-how-to-get-insights-from-a-security-point-of-view-using-r_files/mckinsey_result.png)

This is a tiny part of list of findings, but one of the thing that took my attention was similar hits.

So for Mckinsey we have 2 structurally similar hits on different domains, IPs and ASNs. This tool detects websites which have a similar structure but are hosted on different infrastructure, such as Phishing kits. It's still an experimental feature, so it might work or no, but the results worth the look.

* 1stfinanceportal.com
* assets.mckinsey.com/industries/chemicals/contact-us
If the second result could be related for Mckinsey, the first one is strange. We will check it with urlscan script

![Phishing ](/post/2020-05-06-how-to-get-insights-from-a-security-point-of-view-using-r_files/secure request 1st.png)

Ok, we see that the content mostly insecure, but how does it look like?

![Comparison](/post/2020-05-06-how-to-get-insights-from-a-security-point-of-view-using-r_files/comparison.png)

Very nice!






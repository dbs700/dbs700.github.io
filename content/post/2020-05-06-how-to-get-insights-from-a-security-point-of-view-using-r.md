---
title: How to get insights from a security point of view using R
authors:
- Hugo Authors
date: '2020-05-06'
slug: how-to-get-insights-from-a-security-point-of-view-using-r
categories: []
tags: []
hero: /images/hero-12.jpg
excerpt: Recently I came across some cybersecurity articles written by Mckinsey, but then I suddenly remembered one of the brilliant resources focused on R and cybersecurity research
---

Recently I came across some cybersecurity articles written by Mckinsey, but then I suddenly remembered one of the brilliant resources focused on R and cybersecurity research, DFIR, risk analysis, and much more. The person behind this resource is Bob Rudis who wrote a book along with Jay Jacobs - "Data, Driven Security: Analysis, Visualization and Dashboards"

>Uncover hidden patterns of data and respond with countermeasures Security professionals need all the tools at their disposal to increase their visibility in order to prevent security breaches and attacks. This careful guide explores two of the most powerful ? data analysis and visualization. You'll soon understand how to harness and wield data, from collection and storage to management and analysis as well as visualization and presentation. Using a hands-on approach with real-world examples, this book shows you how to gather feedback, measure the effectiveness of your security methods, and make better decisions. Everything in this book will have practical application for information security professionals. 

If we want to check some websites, we could do a lot of things in R with libraries focused on cybersecurity analysis. We'll use urlscan.io API by creating the request that will browse the URL like a regular user and record the activity that this page navigation creates. This includes the domains and IPs contacted, the resources (JavaScript, CSS, etc.) requested from those domains, as well as additional information about the page itself. urlscan.io will take a screenshot of the page, record the DOM content, JavaScript global variables, cookies created by the page, and a myriad of other observations.

We could also double check all the information with a browser version of urlscan to see all kinds of confirmations.

So the primary result for domain:mckinsey.com will look like this:

![Domain check](/post/2020-05-06-how-to-get-insights-from-a-security-point-of-view-using-r_files/mckinsey_result.png)

This is a tiny part of the list of findings, but one of the things that took my attention was similar hits.

So for Mckinsey, we have two structurally similar hits on different domains, IPs and ASNs. This tool detects websites that have the same structure but hosted on different infrastructure, such as Phishing kits. It's still an experimental feature, so it might work or no, but the results worth the look.

* 1stfinanceportal.com
* assets.mckinsey.com/industries/chemicals/contact-us

If the second result could be related to Mckinsey, the first one is strange. We will check it with urlscan script.

![Phishing ](/post/2020-05-06-how-to-get-insights-from-a-security-point-of-view-using-r_files/secure request 1st.png)

Ok, we see that the content mostly insecure, but how does it look like?

![Comparison](/post/2020-05-06-how-to-get-insights-from-a-security-point-of-view-using-r_files/comparison.png)

And now, we could sweep the data available for an IP address related to 1stfinanceportal.com. We use ThreatCrowd search engine API via R.

![](/post/2020-05-06-how-to-get-insights-from-a-security-point-of-view-using-r_files/1fin_domains_ip.png)

So what we have for now.

Current DNS A record: 128.199.247.119 (AS14061 - DIGITALOCEAN-ASN, US)
Domain created: January 30th 2020, 12:39:01 (UTC)
Domain registrar: NameCheap, Inc. 

Suspicious domain with almost insecure content but with Mckinsey corporate website design and logo. Nice try!
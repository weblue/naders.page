---
layout: post
title:  "Data-based Monitoring and BA for Hertz"
date:   2023-03-29 12:18:00 -0400
categories: code development career
---

As a contractor for Hertz, my team and I were responsible for creating an API to allow Uber and Lyft to search and book car rentals. Because of the micro service philosophy at Hertz, this system quickly grew in number of interactions with downstream Hertz systems, both in volume of requests (360k+ daily) and in number of services interacted with. With this amount of data and requests, there was an opportunity for a system that monitored a huge number of services in the Hertz architecture and could query both stability and business analytics.

This system was born out of a requirement set on us by Lyft. Since our system was immature, it had plenty of issues; requests that occasionally stalled or returned 5xx errors. To Lyft, this was unacceptable and needed to be addressed. Working with our client, I formalized a set of SLAs and worked with Hertz Enterprise to get access to resources for us that could create a system to monitor these metrics. This was the jump into creating the stability monitoring part of this application.

## Setting SLA/SLOs

I had two major objectives when drafting our service level agreements, avoid overworking developers and effectively use our time. This was a large project with plenty of areas to improve, but with this large backlog, we need to make sure our precious time was spent effectively. To measure this, we started by measuring our error rate (500 and 400 errors returned by the system) and our response time, followed by qualifying what we considered to be “good” or “bad” responses, or key performance indicators (KPIs). We measured these over a 60 minute window and set broad percentage goals, with the intention of tightening them over time. 

To move the needle as quickly as possible, we used our goal setting time to sort our backlog in terms of impact on our objectives; we dredged for quick, high-impact goals, followed by goals that lead to large improvements, even if they were a bit more work. Over time, we moved to more incremental changes and shifted our SLOs similarly, starting from 50%, to 80%, 95%, 98%, and 99% of good-to-bad requests.

## Creating Monitoring Systems

For our first attempt at monitoring, we naturally gravitated to Cloudwatch for our AWS hosted system. Cloudwatch provided some very basic level tools to allow us to get metrics and visualize them against our goals. At a high level, we could query Cloudwatch logs to get a count of errors, however it came with some quirks. While Cloudwatch can be hugely helpful in understanding an application or architecture, filtering can be difficult and comes with a learning curve. There can also be quirks where the data is coming from; for example, reading the wrong load balancer of a distributed application resulting in under or over reporting or accidentally including health checks (a fast and stable request) making an application seem much healthier than it really is.

As we worked on this, we realized we could also measure the requests our system was making to other Hertz microservices, both inside and outside our AWS architecture. In our process, we could start categorizing which system was being called by “tagging” our logs (just adding information, really) and creating the appropriate Cloudwatch queries.

Eventually, Cloudwatch became too difficult to manage and this data was becoming more and more valuable. We explored some of the possible solutions like Splunk and Solarwinds, but landed on a newer, AI-powered platform, Dynatrace. With AI classification, we were able to categorize more specifically, allowing us to hone in on problematic services or endpoints, although this again came with the responsibility of cleaning up or auditing the data coming in. 

With this setup, not only were we monitoring and reacting to the health and stability of our system, we were quickly able to detect problems in downstream systems as they would develop. As we improved our systems, we were able to detect downstream problems so quickly that we frequently were the notifying party and had considered automating these notifications, although this never became a reality. We also learned that stakeholders do not like their services being put under a microscope.

## Finding Business Value in our Data

Presenting our data in a meaningful way was always the most difficult part of our efforts. However as we improved our methods and gained more understanding around our data, we found ourselves able to answer more questions during business stakeholder meetings.

To try to provide this value more consistently, we worked with business analysts to figure out what questions were most important to them and turning these metrics into queries to run against our data. As we became more consistent, we were able to automate delivery of these reports to business analysts.

As we tracked down problematic endpoints and services, we were more closely able to pinpoint failures that lead to lost business or points of friction where we’d have users quit during a reservation process. With the help of business analysts, we were also able to put a dollar value on process or system failures, helping direct priorities for developer time or stakeholder attention.

## Lessons Learned

Using a proxy-based application to infer information about a larger system was a really cool project at scale. I think a lot of things went right for this particular use case, especially as it evolved from necessity. If I were to do it again, I would definitely want to explore the possibility of using other cloud services, like AWS API Gateway, to generate this data. There’s also opportunities to try using something like AWS Kinesis offerings to store and analyze data of this nature and provide it to other services for processing and analysis. 

Although me and my team got to use Cloudwatch and Dynatrace, there’s many other applications that can infer metrics from this kind of data, like Solar Winds, Splunk, or Datadog. Although I’m certain Dynatrace met our needs and allowed us to innovate, it would be interesting to see what’s possible, in terms of visualization and analysis, with these other offerings.

I look forward to applying this practical knowledge in other applications and architectures, and I also look forward to seeing how this data analysis space (and its current solutions) will evolve over time. I’m certain this field will continue to grow deeper and offer smarter insights.

## Resources

[Google - Site Reliablility Engineering](https://sre.google/sre-book/part-I-introduction/)
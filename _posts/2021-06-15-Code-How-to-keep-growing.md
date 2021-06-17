---
layout: post
title:  "Code: Always growing"
date:   2021-06-15 12:18:00 -0400
categories: code development career
---

Exploring through forums brought me to a question I had heard before; is programming in your 40s a dead end? Over the course of a career, do programmers have to choose between a move to management or becoming outdated resources?

As programmers and software engineers, the only constant in the field is **change**. Good code doesn't necessarily change often, but the tools and times always do and programmers need to take account to stay relevant in the field. Just as doctors constantly look for more effective, safer, or quick procedures to treat illness, engineers must stay at the edge of technology to keep their solutions viable as the field and their careers keep moving.

To me, this means that **being a software engineer is a never-ending pursuit to understand how the field evolves, and figuring out which of those changes are impactful**.

Without this ambition to stay ahead of the curve, engineers may find themselves being pushed in a direction they might not appreciate; however, many find this effort exhausting and might find it more comfortable to dive deeply into research or academia. Even then, not understanding how to keep up with any field is programmer's death sentence.

Naturally, what I wanted to know was <u>"how can we keep growing as developers?"</u>. And this lead me to wonder where anyone would start.

## How can we stay aware of the field?
Staying on the edge requires commitment and passion! Building on that commitment, there's a few resources that are worth checking out habitually:

### News aggregators:
A great way to browse a broad set of headlines and find a wide variety of interesting tech news.

#### [HackerNews](https://news.ycombinator.com)
HackerNews is a technology news aggregator from tech venture capital firm, [ycombinator](https://ycombinator.com). 

#### [Reddit's programming subreddit](https://reddit.com/r/programming)
Reddit's programming subreddit is a community-managed technology news aggregator including articles and interesting topics of discussion frequently involving experienced members of the community.

### Focused Research
#### [ThoughtWorks TechRadar](https://www.thoughtworks.com/radar)
TODO
#### [Microsoft's Channel9](https://channel9.msdn.com)
Microsoft's internal news hub for Microsoft technologies. Recently there's been a strong focus on Azure services, which is to be expected as it's their fastest growing offering.
#### [Github Trending](https://github.com/trending)
Projects and developers getting recent attention on Github.
#### Googling "Best tech to do ____"
Last but not least, frequently searching for new tech will let you stay somewhat updated on what the trends are for different sectors or common functionality.

This list gives a couple of places to start on some broad subjects, but there's always the more focused newsletters on useful products or even discussions/news on the programming subreddit.

With all the awareness in the world, however, there's no replacement for getting hands-on with new tools and technology. Depending on time and interest, that can be as simple as a hello world and as complex as an entire project from scratch. It's happened more than once where learning a new technology at work coincided with a hobby project; to prepare for a work project, putting together a home project in Vue.js is infinitely more helpful than just reading articles about it.

> "The only way to learn a new programming language is by writing programs in it." - Dennis Ritchie

## Recognizing value and separating out fads
With all the new technologies that emerge every day, there's just as many fads and marketing gimmicks as there are useful or practical tools. Many might remember the blockchain craze, and even [companies going up in value for just having "blockchain" in the name](https://www.bloomberg.com/news/articles/2017-12-21/crypto-craze-sees-long-island-iced-tea-rename-as-long-blockchain). 

Even if every project was interesting and useful, it'd be practically impossible to implement more than a handful into a project.

This can make it a challenge to sort out what's going to help your projects vs what's going to waste your time. Anyone can wait for the big companies to pick up new tech and catapult it to the spotlight, but for everyone else, we should start by asking **is this technology doing something better than a competitor, or is it promising something new?**. Also keep in mind, the old adage "if it's too good to be true, it probably is" comes into play.

If the technology is delivers niche or new functionality, it's important to ask **is this solving an important problem?**

If the technology is a new attempt to compete against an existing product
- **How is it better than competing projects?**
- **Does it have any caveats or require any additional services compared to competing projects?**

And if you have a project that could benefit from the improvements:
- **What's the cost of refactoring?** How much has to be redesigned to take advantage?
- **Could a more established tool be better suited for the project's needs?**

[Netflix's Eureka](https://github.com/Netflix/eureka) is an **AWS service registry based load balancer with failover protection**, first of its kind. My company had a project based on modular and hot-swappable plugins where each plugin could be run on a different container and interacts with the base client using REST. The leader of this project saw Eureka as an opportunity to increase backend functionality to these plugins to add features like canary releases (staged rollouts) of plugin updates or hot-swapping new versions or potentially distributing the base platform to clients and using Eureka to deliver a configurable list of plugins to each. All functionality functionality that sounded great on paper, but there were problems to address. **The project itself did not make use of the AWS service registry** and the base application was not designed in a way to exactly accommodate the service registry.

Long story short, Eureka was incredibly cool, and the project leader decided to commit to making it work for the project. Months later, the refactor was completed, took more work than expected, pulled time from other engineers to implement, and introduced a slew of new bugs to the system.

The team promised new features, but ran out of time to deliver. The AWS service registry based design was ditched to avoid the new issues, and the project ended up switching to NGINX to provide the new features that were promised, without the need for further backend design changes.

In this case, <u>it would've simply been better to start off with a simple Google search "load balancer for canary releases"</u>, and a less trendy but more practical solution could've been implemented.

## Signs you or your company might be getting stale



> “The most damaging phrase in the language is... it's always been done this way” - Grace Hopper
https://www.quora.com/Is-software-development-really-a-dead-end-job-after-age-35-40
https://www.reddit.com/r/programming/comments/nytzaz/what_happens_to_a_programmers_career_as_he_gets/h1muoq7/
https://www.reddit.com/r/programming/comments/nytzaz/what_happens_to_a_programmers_career_as_he_gets/h1nbwnl/
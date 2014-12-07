---
layout: post
title:  "Software Testing - five things we got right in 2014"
date:   2014-12-05 16:10:08
categories: testing
---

The end of the year is almost with us and it's always worth looking back at what you set out to accomplish, and what you achieved and what you didn't.
I got together with our Testing team last week for a *2014* retrospective and at the conclusion of the meeting we all agreed that we'd had a tremendously positive year.

Here are some of our key achievements.

####We now have a "proper" testing team
Back in January our testing team totalled two people - we had grown to four a few months previous but were back at two again when those appointments failed to work out.
One of our testers had joined on an apprenticeship the previous year and the other had joined from another team within the organisation.

In some (probably many) companies it's difficult to persuade people that testing is a skilled profession in its own right.
Often I've had people suggest we simply bring in staff from related roles for a few days to help us test.  Once done, they can return to their day jobs leaving developers to continue writing *unimpeded* code.
At the start of the year a sense of this culture, and the limited experience shared by our two remaining testers had left me feeling they lacked the sense of confidence that I wanted to see in a strong testing team.

Move forward 12 months though and we've done an enormous amount to address that, and I'm extremely proud of the team and the faith they now have in their own abilities.
We were lucky to find two tremendous testers to add to the team, but another factor I think played a big part was helping the four individuals become ISEB qualified.
My point does not relate directly to the knowledge gained from the study (having sat the exam myself I can see it has its merits and shortcomings), but rather the change in the outlook it seemed to bring to the team.
The testers seem to have a greater assurance of their value to the development team, and I also see the increased respect they have gained amongst the developers.

It's really gratifying to see a group of testers empowered to make forthright observations where previously they may have relented under pressure from a strong-willed developer.

####Testing Infrastructure
This time last year our testing infrastructure consisted of a single ex-development PC, running a multi-tenanted instance of a particular version of our application suite.  Each tester represented a single tenant, working with their own set of data but forced to cohabit in an environment with limited computing resource.

That's no longer the case however. We now have in the region of 30 separate test environments allowing testers *and developers* to run multiple versions of the software in isolation.
Key to that has been a move from internal hardware to public cloud infrastructure (Microsoft's Azure platform in our case).

We've swapped capital expenditure for operational expenditure.  For the folks in charge of the IT budget, a monthly spend of £100-150 is more palatable than a one-off (hypothetical) cost of £3000 for a new server running Hyper-V.
In fact we've found that managing monthly expenditure encourages us to be increasingly efficient in how we use the cloud.  We ensure boxes are shut down when not in use, and we're learning to treat the chargeable aspects of cloud computing (CPU time for example) as a valuable commodity.

####Automated Provision of Test Environments
At the start of the year our Build and Release Manager was spending a sizable part of his day upgrading our test environments to the latest version.
As we moved from a single physical machine to multiple VMs this began to act as a throttle on our test activities.

Our CI system, by default, runs builds against all our Git branches, therefore needing to upgrade to a new version in order to functionally test a piece of work was a common occurrence.

We invested a lot of effort in addressing this problem and now we have an automated deployment platform, Moonfish, that allows testers (and any other stakeholder for that matter) to provision a new environment on our Azure cloud within 15 minutes.

We can run as many parallel deployments as we need to, and by using cloud infrastructure five simultaneous deployments takes the same time as just one - something we've found really important towards the end of each iteration when developers are committing late changes in order to hit deadlines.

We are quite aggressive in switching off our Azure servers to save money, so test environments only have a lifespan of an hour unless extended by the owner.
While this caused some initial angst, people soon got used to it, helped by one of our devs who wrote a system tray app that pops up to alert you when a site is soon to be switched off.

Although we wrote a fair amount of plumbing and portal code ourselves (using Node.js and AngularJS) we were committed to using existing tooling where possible.
A lot of the heavy lifting was done using Octopus Deploy, which we found to be an ideal component as almost all of its functionality can be accessed through an API.  This meant it was relatively simple to front-end with our own portal.

We're really proud of this system and we're hoping to open-source it in the hope it may be something of value to other organisations.

####Regression Testing
Ah, regression testing. We have to do it because if we don't, then, as the law of sod dictates, we'll end up shipping a critical bug unknowingly introduced into a key system area by an unfortunate developer.
So, just in case that should happen, every time we ship a release we'll spend 2 weeks regression testing all systems areas just in case. CYA and all that.

We'd certainly fallen into that trap at the start of 2014.  Fortunately the light dawned on us that we were spending an inordinate amount of time on this pantomime, and that the ROI was very poor.
Monthly retrospectives proved extremely valuable here - they forced us to stop and consider the uncomfortable truths (why are we still doing this?) instead of simply ploughing on as before.

So over the year we cut the time we spent regression testing by 70%, we adopted a clear risk-focused approach by talking with tech leads at the end of each iteration, and spent more time exploratory testing areas where we knew mistakes were likely to have occurred (and which would have greatest impact).

What's even more encouraging is our testers are determined to take this further and reduce regression testing to a single day each month.
They are convinced that well-focused functional and integration testing while in development will be more effective in finding important defects than repeating the same old regression tests after each iteration ends.

####Automation
The newest kid on the block is our (post CI build) automated testing pipeline.
For a number of years we've had a variety of automated browser tests, written in a number of different languages but this year is the first time we've successfully consolidated our efforts under a single team-wide approach.

But I'll cover that in an upcoming post... :-)

---
layout: post
title: How did InterMine determine its FAIR milestones?
github_comments_issueid: 3
---
![FAIR banner]({{"/images/life-sciences-fair.png"}})

At [InterMine](http://intermine.org), a life sciences data integration platform, we're working on a [BBSRC grant](https://intermineorg.wordpress.com/2017/04/24/the-fair-journey/)
to make data available through InterMine 'FAIR'.  What does this mean?  Well, firstly FAIR is an initiative to make data
Findable, Accessible, Interoperable and Reusable (I've written a lot more about this 
[here](https://software.ac.uk/blog/2018-01-30-life-sciences-data-needs-be-fair)).

Taken on its face this is a bit woolly - isn't InterMine data already FAIR?  You can find data (type some text in its
general search box or perform a structured query), access it (click the web link), interoperate with it 
(run a live query on its API) and reuse it (hey the data's there, download it).  Well, one of the great things about 
FAIR is that it [has specific principles and recommendations on how to make data findable, accessible, interoperable and reusable](https://www.nature.com/articles/sdata201618).
These place a heavy emphasis on uniformity so that software can much more easily use and combine data across the 
countless distinct data sources hosted by different organizations across the planet.

So in applying for the grant, how did we propose to apply these recommendations to InterMine?  Essentially, we 
performed a gap analysis between the 15 guiding principles documented in the [original FAIR paper](https://www.nature.com/articles/sdata201618)
and InterMine's current capabilities, coming up with a plan for how we would bridge this gap.

Let's take the first findability and accessibility FAIR guiding principles as an example

```
F1. (meta)data are assigned a globally unique and 
persistent identifier

A1. (meta)data are retrievable by their identifier 
using a standardized communications protocol
```

One way to fulfil these principles, and something popular in the [semantic web world](https://en.wikipedia.org/wiki/Semantic_Web), 
is to make identifiers be URLs.  So great, InterMine already has URLs that have a 1-to-1 mapping to biological data objects!  Search
for the gene MYH7 in [HumanMine](http://www.humanmine.org/) for instance, and the report page you get back has this
URL (stripping away some non-essential tracking information).

```
http://www.humanmine.org/humanmine/report.do?id=1157771
```
 
Look at another biological object and that ID number will change, since this is the internal ID used to track objects
within an InterMine database.

But there's a problem here.  These ID numbers are not persistent, as required by principle F1.  When the data in an
InterMine installation like HumanMine is updated, this is not done additively, but rather than entire database is 
rebuilt since data sources need to be integrated anew.  And on this rebuild, MYH7 is no longer guaranteed to have the
internal InterMine ID 1157771.  In fact, it's very likely to be completely different.

So part of our proposal was to implement a resolution to this problem.  For InterMine as a data integration platform
rather than a primary data provider it's a very complex topic, particularly as we're generic and model driven (so in
principle you could host something completely different like a company database in InterMine!).  I won't delve into 
the possible solutions too much here, but at the moment it looks
like a tradeoff between trying to make our internal ID persistent (e.g. by maintaining the mapping to biological objects
between database rebuilds) and trying to incorporate external IDs such as MYH7 directly into the InterMine URL as 
specified by the InterMine instance operator, something like 

```
http://www.humanmine.org/humanmine/gene/MYH7
```

We'll be reporting more on this in the future.

This was a fairly straightforward example.  Some of the other principles, such as 

```
I3. (meta)data include qualified references to other 
(meta)data
```

required more interpretation, and in our proposal we related actions broadly to the principles (i.e. whether they 
addressed one or more of findability, accessibility, etc.) rather than specific FAIR clauses.

However, we wrote our proposal some time ago.  Things are moving rapidly and many of the original FAIR paper authors
are working on the [FAIR metrics](http://fairmetrics.org/) initiative, which will measure FAIRness with programattic
and quantitative tests.  I think this is a great step and now something for anybody looking to FAIRify their data
resource to look at closely.  We'll be looking to apply these metrics to our own work as we continue development.
---
layout: post
title: A Buzzbang-tinged report on the EBI Bioschemas Samples hackathon
github_comments_issueid: 2
---
![Buzzbang logo](http://www.buzzbang.science/static/images/logo.png)

First, a little bit of background. As part of our task at the Micklem Lab in Cambridge to help 
[make life sciences data FAIR (Findable, Accessible, Interoperable and Reusable)](https://www.software.ac.uk/blog/2018-01-30-life-sciences-data-needs-be-fair)
, we've been
involved with [ELIXIR](https://www.elixir-europe.org/) [Bioschemas](http://bioschemas.org), an initiative to embed structured markup in life sciences
webpages, so that search engines and other applications can find this data more easily than at present. This is
building on [schema.org](https://schema.org), which already does the same for Products, Recipes, etc., and helps power
the information snippets you often see in the search results from Google and other search engines. Look at [this recipe
for chocolate cake](https://www.google.co.uk/search?q=chocolate%20cake) for instance!

Down the road, we aim to make it easy to embed this kind of markup in [InterMine](http://intermine.org) pages, so that all our
users benefit from better data findability. But to demonstrate the value of doing this, I think that there needs to be a
 consuming application on
the other end. So with a bit of help from a few other folks, I've been hacking on a very prototype Bioschemas crawler and user-facing search frontend called 
[Buzzbang](https://github.com/justinccdev/bsbang-crawler). This will eventually crawl not only the Bioschemas markup 
embedded in InterMine instances, but also all
the other life sciences sites embedding Bioschemas data. Then the user will be able to crawl that search data
in a simple Google-like manner. 

At the moment, this is all very prototype and alpha but you can see a live example at 
[buzzbang.science](http://buzzbang.science). Right now, we're only indexing 
some basic DataCatalog information on a few sites (such as [FAIRsharing](fairsharing.org) 
and [Identifiers.org](https://identifiers.org)) and some prototype JSON-LD data from 
[Synbiomine](http://synbiomine.org), a synthetic biology InterMine data warehouse.  
 
However, I was recently very pleased to learn that Luca Cherubin, Matthew Green and others at the 
[EBI Biosamples database](https://www.ebi.ac.uk/biosamples/) have been using the prototype crawler to demonstrate how their sample entries can
be linked back to information imported and curated in other samples databases, namely the [Marref marine metagenomics
database](https://mmp.sfb.uit.no/databases/marref/#/). So I had the opportunity to go along to a 
[recent hackathon](http://bioschemas.org/meetings/2018-05_SamplesHackathon/) and help others from the around the UK and Europe
to refine the Bioschemas Samples further, so that it can be used by the long tail of 
[Biobanks](https://en.wikipedia.org/wiki/Biobank) to improve the findability of their data.  All in all, it was a great
meeting and it was really nice to meet more people getting involved with Bioschemas.

I also had an opportunity to [present Buzzbang](https://www.slideshare.net/JustinClarkCasey/buzzbang) at the hacktathon,
which I think was received pretty well, and discovered some parallel work by Federico Lopez on scraping Bioschemas data.

As for the future, the immediate challenges are to 

* Make Buzzbang more scalable so that it can crawl large sites like BioSamples.
* Improve the search results returned to users.
* Get access to more hardware or cloud resources to do larger crawls and host the crawled data.
  
In all this, it's going to be important to keep
the crawling backend and search frontend separate, so that other projects at the EBI and elsewhere can keep using
a crawler or common crawl dataset to power different search applications and uses.

As with many of the things we do at the Micklem Lab, this is an open-source project and 
[collaboration is very welcome](https://github.com/justinccdev/bsbang-crawler) :)

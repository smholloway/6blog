---
layout: post
category: technology
tags: [jekyll]
title: Blogging with Jekyll 
---
{% include JB/setup %}

This first pass at this blog was done using Jekyll, a static content generator.

Hosted on Heroku, we keep everything in sync using a GitHub repository.

For the most part, Thomas Stachl's post will tell you everything you need to know.
http://stachl.me/blog/2012/05/26/jekyll-on-heroku.html

Google Analytics wasn't working, but that was not a new issue: https://github.com/plusjade/jekyll-bootstrap/issues/53

This was fixed by adding --safe to the Proc file.

After cloning the Jekyll Bootstrap repository and getting things up and running, we altered the _config.yaml file. We have tweaked the theme and various generators, like atom.xml.

## Pros
Fast
Modern
Cross-platform
Supported by Heroku and GitHub--two dev favorites
Somewhat related to Heroku and GitHub, blogging this way is free
Gaining traction (see ThoughtWorks Tech Radard 2012)
It is not Java (see Java's recent secrurity mishaps)

## Cons
Lack of WYSIWYG editing
Local installation and maintenance
Ruby versioning can be a chore (ruby versions plus gems)
Requires knowledge of several software systems including Git, Ruby, and general web stuff.

## Use cases
If you need (or want) WYSIWYG editing, Jekyll is not for you. The system is fast. I get the impression it is by hackers for hackers.
You might also try Ruhoh, which is Jade Dominguez's new and improved static blogging platform.

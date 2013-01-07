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

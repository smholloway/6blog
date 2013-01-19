---
layout: post
category: technology
tags: [jekyll]
title: Blogging with Jekyll 
---
{% include JB/setup %}

This first incarnation of this blog was created using Jekyll, a static content generator. (We have big plans for future iterations that may not involve Jekyll.) Jekyll was created by GitHub and is still used for their blog pages. It compiles Markdown--the new hotness for straightforward markup--into static HTML pages that can be loaded and served quickly and easily (the static nature of the generated pages allows them to be cached for even faster load times).

We bought the domain name and quickly routed to Heroku. All content is syncronized using a GitHub repository.

For the most part, Thomas Stachl's post will tell you everything you need to know.
http://stachl.me/blog/2012/05/26/jekyll-on-heroku.html

The biggest snag was that Google Analytics wasn't working--a known issue: https://github.com/plusjade/jekyll-bootstrap/issues/53; the fix was easy enough: add --safe to the Proc file leading to this Procfile:

```shell
web: jekyll --safe --server $PORT
```

After cloning the Jekyll Bootstrap repository and getting things up and running, we altered the _config.yaml file. We have tweaked the theme and various generators, like atom.xml.

### Pros
 - Fast
 - Modern
 - Cross-platform
 - Supported by Heroku and GitHub--two dev favorites
 - Somewhat related to Heroku and GitHub, blogging this way is free
 - Gaining traction (see ThoughtWorks Tech Radard 2012)
 - It is not Java (see Java's recent secrurity mishaps)

### Cons
 - Lack of WYSIWYG editing
 - Local installation and maintenance
 - Ruby versioning can be a chore (ruby versions plus gems)
 - Requires knowledge of several software systems including Git, Ruby, and general web stuff.

### Use cases
 - If you need (or want) WYSIWYG editing, Jekyll is not for you. The system is fast. I get the impression it is by hackers for hackers.
 - You might also try Ruhoh, which is Jade Dominguez's new and improved static blogging platform.

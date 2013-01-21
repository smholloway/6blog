---
layout: post
category: technology
tags: [jekyll]
title: Blogging with Jekyll 
---
{% include JB/setup %}

This first incarnation of this blog was created using [Jekyll](http://jekyllrb.com/), a static content generator. (We have big plans for future iterations that may not involve Jekyll.) Jekyll was created by GitHub (specifically, [Tom Preston-Werner](http://tom.preston-werner.com/)) and is still used for their blog pages. It compiles [Markdown](http://daringfireball.net/projects/markdown/)--the new hotness for straightforward markup--into static HTML pages that can be loaded and served quickly and easily (the static nature of the generated pages allows them to be cached for even faster load times).

We bought the domain name and pointed the DNS servers to Heroku. We syncronized using a GitHub repository.

To get going even faster, we used [Jekyll Bootstrap](http://jekyllbootstrap.com/). For the most part, [Thomas Stachl's post](http://stachl.me/blog/2012/05/26/jekyll-on-heroku.html) will get you started. From there, the biggest snag was that Google Analytics wasn't working--a [known issue](https://github.com/plusjade/jekyll-bootstrap/issues/53). The fix was easy enough: add `--safe` to the `Procfile` leading to this:

```shell
web: jekyll --safe --server $PORT
```

After cloning the Jekyll Bootstrap repository and getting things up and running, we altered the `_config.yaml` file. We have tweaked the theme and various generators, like atom.xml.


### Pros
 - Fast
 - Modern
 - Cross-platform
 - Supported by Heroku and GitHub--two of our favorite services
 - Blogging this way is free (thanks to Heroku and GitHub)
 - Gaining traction (see ThoughtWorks Tech Radard 2012)
 - It is not Java (see Java's recent secrurity mishaps)

### Cons
 - Lack of WYSIWYG editing
 - Local installation and maintenance
 - Ruby versioning can be a chore (ruby versions plus gems)
 - Requires knowledge of several software systems including Git, Ruby, and general web stuff.

### Use cases
 - The system is lean and fast (I get the impression it is by hackers for hackers). If you need (or want) WYSIWYG editing, Jekyll is not for you. If you're familiar with GitHub and Ruby (or you want to learn), give Jekyll a try.

### Other notes
 - You might also explore [Ruhoh](http://ruhoh.com/), which is [Jade Dominguez](http://plusjade.com/)'s new and improved static blogging platform.

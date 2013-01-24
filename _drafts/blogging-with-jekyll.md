---
layout: post
category: technology
tags: [jekyll]
title: Blogging with Jekyll 
---
{% include JB/setup %}

Deciding to create a blog is the easy part! Getting it up and running is another story. There's Wordpress, Blogger, Tumblr, static HTML, or even something as heavyweight as a Rails app. We wanted something that was portable, lightweight, efficient, and customizable--all while being simple to bootstrap.

We chose Jekyll for the first incarnation of [6blog](http://6blog.us) because it satisfied our requirements and Jekyll has a growing number of pro peeps using it as a blogging platform. This system also allowed us to learn something new :)

[Jekyll](http://jekyllrb.com/) is a static content generator created by [Tom Preston-Werner](http://tom.preston-werner.com/) at GitHub. Not surprisingly, GitHub uses Jekyll for their [pages](http://pages.github.com/). It compiles [Markdown](http://daringfireball.net/projects/markdown/)--a simple syntax that creates markup--into static HTML pages that can be served quickly and easily.

First off, we bought the domain name and [pointed the DNS servers to Heroku](http://stackoverflow.com/questions/10966407/heroku-and-zerigo-setup-issue). Then we created a GitHub repository to track all blog content. Having everything in GitHub sets up a nice workflow where you can preview, edit, and commit changes Markdown files through a web browser. (I am looking forward to the day when all coding works this way!)

As fans of [Twitter Bootstrap](http://twitter.github.com/bootstrap/), the choice to use [Jekyll Bootstrap](http://jekyllbootstrap.com/) was natural. [Thomas Stachl's post](http://stachl.me/blog/2012/05/26/jekyll-on-heroku.html) covered virtually everything we needed to get going with Jekyll Bootstrap on Heroku. The biggest snag was that Google Analytics wasn't working--a [known issue](https://github.com/plusjade/jekyll-bootstrap/issues/53). The fix was easy enough: add `--safe` to the `Procfile`.

```shell
web: jekyll --safe --server $PORT
```

After cloning the Jekyll Bootstrap repository and getting things up and running, we altered the `_config.yaml` file. We  tweaked the theme and various generators, like atom.xml.

By default, Jekyll publishes Markdown files in the `_posts` directory that start with a timestamp and include title; for example, `2013-01-28-blogging-with-jekyll.md`. This left us with no clear way to create drafts. Initially, we tried removing the timestamp and leaving the file in the posts directory, but this was messy--what happens when we have hundreds of posts and hundreds of drafts? Instead, we opted to create a new directory called `_drafts`. We created a simple template file that we copy to create a new draft. When the post is ready to be published, we move the file from `_drafts` to `_posts` and prepend a timestamp.


### Pros
 - Fast
 - Modern and [gaining traction](http://www.thoughtworks.com/articles/technology-radar-october-2012)
 - Cross-platform
 - Supported by Heroku and GitHub--two of our favorite services
 - Blogging this way is free (thanks to Heroku and GitHub)

### Cons
 - Lack of WYSIWYG editing
 - Local installation and maintenance
 - Ruby versioning can be a chore (ruby versions plus gems)
 - Requires knowledge of several software systems including Git, Ruby, and general web stuff.

### Use cases
 - The system is lean and fast. I get the impression it is by hackers for hackers. If you need WYSIWYG editing, Jekyll is not for you. If you're familiar with GitHub and Ruby (or you want to learn), give Jekyll a try.

### Other notes
 - You might also explore [Ruhoh](http://ruhoh.com/), which is [Jade Dominguez](http://plusjade.com/)'s new and improved static blogging platform.

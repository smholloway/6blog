---
layout: post
category: technology
tags: [jekyll, heroku]
title: Blogging with Jekyll on Heroku
---
{% include JB/setup %}

Deciding to create a blog is the easy part! Getting it up and running is another story. There's Wordpress, Blogger, Tumblr, static HTML, or even something as heavyweight as a Rails app. When deciding what to use for [6blog](http://6blog.us), we wanted something that was portable, lightweight, efficient, and customizable--all while being simple to deploy.

We chose Jekyll for the first incarnation of [6blog](http://6blog.us) because it satisfied our requirements, and Jekyll has a growing number of pro peeps using it as a blogging platform. This system also allowed us to learn something new :)

[Jekyll](http://jekyllrb.com/) is a static content generator created by [Tom Preston-Werner](http://tom.preston-werner.com/) at GitHub. Not surprisingly, GitHub uses Jekyll for their [pages](http://pages.github.com/). It compiles [Markdown](http://daringfireball.net/projects/markdown/)--a simple syntax for creating standards-compliant markup--into static HTML pages that can be served quickly and easily.

To get started we bought the domain name and [pointed the DNS servers to Heroku](http://stackoverflow.com/questions/10966407/heroku-and-zerigo-setup-issue). Then we created a GitHub repository to track all blog content. Having everything in GitHub sets up a nice workflow where you can preview, edit, and commit changes to Markdown files through your web browser. (We are looking forward to the day when all development and editing works this way!)

As fans of [Twitter Bootstrap](http://twitter.github.com/bootstrap/), the choice to use [Jekyll Bootstrap](http://jekyllbootstrap.com/) was natural. [Thomas Stachl's post](http://stachl.me/blog/2012/05/26/jekyll-on-heroku.html) covered virtually everything we needed to get going with Jekyll Bootstrap on Heroku. After cloning the Jekyll Bootstrap repository and getting things up and running, we altered the `_config.yaml` file. We  tweaked the theme and various generators, like `atom.xml`.

The biggest snag was that Google Analytics wasn't working--a [known issue](https://github.com/plusjade/jekyll-bootstrap/issues/53). The fix was easy enough: add `--safe` to the `Procfile`.

```shell
web: jekyll --safe --server $PORT
```

Another thing that was not clear was how to create drafts. By default, Jekyll publishes Markdown files in the `_posts` directory that start with a timestamp and include a title; for example, `2013-01-28-blogging-with-jekyll.md`. Initially, we tried removing the timestamp and leaving the draft in the `_posts` directory, but this was messy--what happens when we have hundreds of posts and hundreds of drafts? Instead, we opted to create a new directory called `_drafts`. We created a simple template file that we copy to create a new post. When the post is ready to be published, we move the file from `_drafts` to `_posts` and prepend a timestamp. The next time the page is loaded, Jekyll publishes the new file.

So far we are pleased with Jekyll, but it won't be for everyone.

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
 - The system is lean and fast. We get the impression it is by hackers for hackers. If you need WYSIWYG editing, Jekyll is not for you. For now, keep your non-techy friends on a more standard solution. If you're familiar with GitHub and Ruby (or you want to learn), give Jekyll a try.

### Other notes
 - If you like Jekyll, check out [Ruhoh](http://ruhoh.com/). Ruhoh is a new static blogging platform created by [Jade Dominguez](http://plusjade.com/), the creator of Jekyll Bootstrap. It promises to be even more powerful and generic than Jekyll.

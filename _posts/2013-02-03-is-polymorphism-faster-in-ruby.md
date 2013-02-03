---
layout: post
category: technology
tags: [polymorphism, ruby]
title: Is Polymorphism Faster in Ruby?
author: Seth
---
{% include JB/setup %}

The [Ruby Rogues podcast about Object Oriented Software](http://rubyrogues.com/object-oriented-programming-in-rails-with-jim-weirich/) with [Jim Weirich](http://onestepback.org/) leads off with admonishments for people who do not embrace [polymorphism](http://en.wikipedia.org/wiki/Polymorphism_in_object-oriented_programming). That made me curious: is polymorphism faster than manually dispatching based on an object (using a case/switch or if statement)?

I wrote a program that makes 1,000,000 calls using both polymorphism and manual dispatch, then I found the average time for 1,000 runs. Here are the results:

    Timing 1000 run(s) -- this may take a while. 
        polymorphic average: 2.0862885460000014 
    not polymorphic average: 2.274771535000001

So, polymorphism is the preferred OO way and it's faster!

This result should make sense because the language is able to call the method directly without doing any sort of conditonal logic. Essentially, the ~10% difference we're seeing is the overhead of a conditional statement.



And the code for anyone who is interested:

<script src="https://gist.github.com/4703351.js"></script>

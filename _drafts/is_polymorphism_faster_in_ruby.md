---
layout: post
category: technology
tags: [polymorphism]
title: Is Polymorphism Faster in Ruby?
---
{% include JB/setup %}

The [Ruby Rogues podcast about Object Oriented Software](http://rubyrogues.com/object-oriented-programming-in-rails-with-jim-weirich/) with [Jim Weirich](http://onestepback.org/) leads off with admonishments for people who do not embrace [polymorphism](http://en.wikipedia.org/wiki/Polymorphism_in_object-oriented_programming). That made me curious: is polymorphism faster than manually dispatching based on an object (using a case/switch or if statement).

I wrote a simple program that makes one million calls; I then ran that program one-thousand times and averaged the times. Here are the results:

```ruby
polymorphic_times = 2.0862885460000014
not_polymorphic_times = 2.274771535000001
```

So, polymorphism is the preferred OO way and it's faster!

This result should make sense because the language is able to call the method directly without doing any sort of conditonal logic. Essentially, the ~10% difference we're seeing is the overhead of a conditional statement.

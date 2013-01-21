---
layout: post
category: technology
tags: []
title: Function Calls And Human Understanding
---
{% include JB/setup %}

{% Key points 
  Ruby's loose syntax makes it more human readable, but leads to ambiguity. 
  It can be frustrating to have two different method calls.
%}

I think there's a link between function calls and understanding. In general, Ruby's parameter-less function invocation leads to a more standard English construction. However, this leads to some ambiguity for the compiler.

```ruby
eight = add_three 5
eight = add_two add_one 5
eight = add 5 2
```

However, this won't work

```ruby
eight = add add 5 2 1
```

You need parentheses

```ruby
add(5, add(5, 2))
```

Humans are adept at parsing language. That being said, if a construction is ambiguous for the compiler, it is also hard to parse for a person.

```ruby
add 5 , 10
add(5, 10)
```

```java
add(5, 10)
```

```lisp
(add 5 10)
```

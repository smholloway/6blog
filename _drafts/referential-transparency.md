---
layout: post
category: technology
tags: []
title: Referential Transparency
---
{% include JB/setup %}

Referential transparency refers to the ability to replace a function with the output.

```ruby
def add(a, b)
  a + b
end
```

Now, add(1, 2) can be replaced with 3 throughout.

Good for the compiler; okay for the human.

You can have a function that is referentially transparent, but poorly named so the programmer has to read and understand the function anyway.

```ruby
def add(a, b)
  a * b
end
```
You might take it at face value, or you were had a simple test

```ruby
if add(2,2) = 4
  "sucess"
end
```
Later, your programming fun grinds to a halt when adding two random, user-input numbers.

# Pros
Referential transparency is always a good idea with functions (that return a value).

# Cons
The real power of referential transparency is increased understanding, so make sure that the function is named properly.

# Use cases
Testing, debugging

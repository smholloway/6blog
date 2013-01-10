---
layout: post
category: technology
tags: [rendering, templates, software]
title: Rendering
---
{% include JB/setup %}

Rendering

When rendering there are two broad options:
- Components that handle their own state
or
- A god controller that handles  all of the state.

Business logic vs rendering logic.
A number of new templating systems make logic-less a feature, but what's so bad about logic in templates?
Logic less to increase separation of concerns. Templates that can use logic allow business logic to leak into the templates.

Reuse
Is reuse always good?
Reuse is bad when you're acting based on context. Don't let the context creep in. Similar to polymorphism vs if.

example similar to our code
if (true) string += "</ol>"
else string += "<br/>"

Reuse and simplicity can be at odds
Reuse or a proliferation of classes/templates/items
With a large number of small components, each component is probably easier to understand than the more general reusable verison; however, the entire system becomes more complex because there are more ideas. 

Can you avoid the total number of concepts? Whether it exists in multiple files or one, it is still there. Two types of users: admin and user. Would people understand two files better than one? Wouldn't they build the same kind of understanding about the two systems?

Can these be solved by tools? Information hiding and automatically showing variable values.


Encapsulations - Component based systems encapsulate 

Part of the problem of things being encapsulated is that when you do need to know the internals, it feels in accessible and often will require a good deal of learning to understand the encapsulated component. 
I think a lot of times the ideas that we are taught for programming in one system end up driving our intuition in another system, not necessarily in a good way. OO programmers bring the ideas of encapsulation to all other systems they create. 

Is encapsulation a universally good idea
- Times where its good:
   - OOP
   - Service oriented 
   - Modular systems
These are basically all synonyms 
- Times where its bad?

# Pros

# Cons

# Use cases

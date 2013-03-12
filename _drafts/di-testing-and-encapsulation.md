---
layout: post
category: technology
tags: [di, test, encapsulation]
title: On Dependency Injection, Testing, and Encapsulation
author: Seth and Nick
---
{% include JB/setup %}

In the past several years, [dependency injection (DI)](http://en.wikipedia.org/wiki/Dependency_injection) has gained significant traction. By removing hard-coded dependencies, DI allows for easier testing--simply replace your production dependencies with mocks and test away. There's a lot of good things about dependency injection. However, DI and encapsulation have an inverse relationship, so as DI grows encapsulation shrinks.

## Example
Suppose there is a Thing interface with a do method.

```java
interface Thing
  do(something)
```

In the implementation the do method needs a datastore to do its thing. In this version it creates it directly.

Version A:

```java
class Thing():
  def do(something)
    DataStore dataStore = new DataStore
    otherThing = dataStore.get(something);
```

The DI pattern says that things should take what they need instead of creating them directly. Don't call us we'll call you (the so-called "Hollywood Principle").

Version B:

```java
class Thing(dataStore):
  def do(something):
     otherThing = dataStore.get(something);
```

One of the many benefits of this pattern is that it makes thing 'testable'. 

In a real app the datastore is likely a database or some networked storage. Since Version A creates the datastore directly, the test will make calls over the network and be subject to failures from the other objects that it integrates with rather than from its own errors. These kinds of test are sometimes called integration tests. Using Version B a fake/mock/stub DataStore can be passed in so that the code of the thing class can be tested without having to connect to the real datastore.

However, the fact that Thing needs a datastore is an implementation detail because not every implementation of Thing will need a datastore, and it isn't defined in the interface. To test the do method on thing, I would have to look at the implementation of the method, figure out how the method uses the datastore and stubb out the fake datastore accordingly. 

It seems like DI and encapsulation have an inverse relationship, so as DI grows encapsulation shrinks. Version A is encapsulated. Whenever i new up a Version A Thing, I don't need to know that it is implemented using a Datastore. In Version B I do know that it is implemented using a datastore.

So this is where DI injectors come in. If you use a DI injector during runtime, then most of the code doesn't know that that Version B of thing takes a datastore, the configuration knows that. But if you don't also do DI injectors for tests then the tests are still testing implementation details. SO....in order to have systems that are unittestable and use the DI pattern and are still encapsulated enough, it seems necessary to use a DI container at App runtime and at Test runtime.

Is this all an artifact of the abstractions and langauges we are using. Would another approach alleviate some of the concerns?

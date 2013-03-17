---
layout: post
category: technology
tags: [di, test, encapsulation]
title: On Dependency Injection, Testing, and Encapsulation
author: Seth and Nick
---
{% include JB/setup %}

In the past several years, [dependency injection (DI)](http://en.wikipedia.org/wiki/Dependency_injection) has gained significant traction. By removing hard-coded dependencies, DI allows for easier testing--simply replace your production dependencies with mocks and test away. There's a lot good about dependency injection. However, DI and encapsulation have an inverse relationship, so as DI grows encapsulation shrinks.

## Example
Suppose there is a `Thing` interface with a `do` method.

```python
interface Thing
  do(something)
```

The interface does not reveal that `do` needs a `datastore` to do its thing. In this version of the implementation we create the `datastore` directly--hiding the `datastore` from outsiders. Standard APIs work like this.

Version A:

```python
class Thing():
  def do(something)
    DataStore dataStore = new DataStore
    otherThing = dataStore.get(something);
```

The DI pattern says that `Thing`s should take what they need instead of creating them directly. "Don't call us, we'll call you" (the so-called _Hollywood Principle_). 

In the second implementation we pass in a `datastore` rather than expecting `do` to know how to get one.

Version B:

```python
class Thing(dataStore):
  def do(something):
    otherThing = dataStore.get(something);
```

One of the many benefits of the DI pattern is that it makes code 'testable.' In a real app the `datastore` is likely a database or some networked storage. Since Version A creates the `datastore` directly, the test will make calls over the network and be subject to failures from the other objects that it interacts with rather than from its own errors. These kinds of test are sometimes called 'integration tests.' Using Version B, a fake/mock/stub DataStore can be passed in so that the code of the `Thing` class can be tested without having to connect to the real `datastore`.

However, the fact that `Thing` needs a `datastore` is an implementation detail because not every implementation of `Thing` will need a `datastore`, and it isn't defined in the interface. To test the `do` method on `Thing`, I would have to look at the implementation of the method, figure out how the method uses the `datastore`, and stub out the test `datastore` accordingly. 

Following this logic, it seems like DI and encapsulation have an inverse relationship: as DI grows encapsulation shrinks. Version A is encapsulated. Whenever I new up a Version A `Thing`, I don't need to know that it is implemented using a `datastore`. In Version B I know that it is implemented using a `datastore`. Note: saying that we know about implementation details sounds scary, but we would generally code to an interface to minimize the damage done--switching from one `datastore` to another is easy.

In practice, DI injectors help. If you use a DI injector during runtime, then most of the code doesn't know that that Version B of `Thing` takes a datastore, the configuration knows that. But if you don't also use DI injectors for tests, then the tests are still testing implementation details. So... in order to have systems that are unit-testable and use the DI pattern and are still encapsulated enough, it seems necessary to use a DI container at `app` runtime and at `test` runtime.

### Open questions
Is this all an artifact of the abstractions and langauges we are using? Would another approach alleviate some of the concerns?

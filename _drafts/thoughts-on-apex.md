---
layout: post
category: technology
tags: [Apex, language, salesforce.com]
title: Thoughts on Apex (Salesforce.com)
author: Seth and Nick
---
{% include JB/setup %}

Apex is Salesforce's programming language for the [Force.com](http://en.wikipedia.org/wiki/Salesforce.com#Force.com_platform) platform. It is basically Java, but specialized a bit.

Inline SQL--technically SOQL--is awesome!

```java
  results = [SELECT Id FROM Users];
```

SOQL is much easier to use than standard JDBC. My biggest complaint was the lack of `SELECT * ...` -- you have to specify every column you want to work with.

Programming in the browser is a bold vision, and one that is worth pursuing. Salesforce hasn't gotten it quite right, yet. The time between saving and receiving an error is just a bit too long.

Intermittent bugs occur infrequently, but still too often. The support is often frustrating and slow.

Salesforce changes things without warning. Their metadata API is a prime example. Several times bugs would arise in parts of the product that we had not touched in months. Perhaps versioning could alleviate frustrations here.

Salesforce is a fairly opinionated framework. 
 - They stress testing and make it very easy to do. Give me Apex's `@Test` annotation over JUnit anyday!
 - Model View Controller (MVC) is baked in and apparent.

Apex is a bit of a bastard because programming is at odds with Salesforce's advertisement of "clicks, not code."

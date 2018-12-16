---
author: "Marcin Biegała"
categories:
  - Code
  - C#
date: "2016-10-26T13:35:31+02:00"
description: ""
title: "Here comes Polly!"
type: "post"
---
{{< img-post path="/img/" file="polly.png" alt="Polly" type="right" >}}


Handling errors is not something new, it was always part of good practices.
But from simple, monolithic applications where in huge number of cases we could think of
scenario that will throw exception, we are now moving to complex architectures, with many independent
components talking with each other over the network.  
That means, we need to cover for a lot more situations related to intermittent issues 
(it could be temporary network failure or just some component being down or upgraded).
Our exception handling becomes more complex, often requiring retry logic.  
Writing this retry logic isn't rocket science for sure. Just a loop and a counter,
simple snippet. You just copy it from place to place, then refactor to helper, extend it
with some edge cases etc. We end up building whole infrastructure that we need to maintain and that 
is not our business logic.

Here comes [Polly](https://github.com/App-vNext/Polly) :)  
A small C# library, that makes those kinds of error handling nice and clean.  
Let's start with an example:

```cs
var policy = Policy
                .Handle<WebException>()
                .Retry(3);

policy.Execute(() => DoSomething());
```

This is very simple snippet, but let's see what happens here.  
First, we define policy which will check if executed code throws `WebException` and retries it up to 3 times if that happens.  
When we have this policy, we can execute our `DoSomething()` method against it.  
Very good thing here is that it's declarative. We can define our handling polices somewhere in shared
part of application and control them from one place. And it doesn't spoil our code with lots of simple for loops that are later hard to read!

That's most simple case we could made. Pollys GitHub page is full of examples so I won't rewrite all of this,
but let's take a look at just a few interesting scenarios.  

Here, we are trying to retry action 3 times, waiting corresponding number of seconds before each retry.
```cs
Policy
  .Handle<HttpException>()
  .WaitAndRetry(new[]
  {
    TimeSpan.FromSeconds(1),
    TimeSpan.FromSeconds(2),
    TimeSpan.FromSeconds(3)
  });
```

You can of course react to every exception, for example by putting something in log file.
```cs
Policy
    .Handle<HttpException>()
    .Retry(3, (exception, retryCount) =>
    {
        // do something 
    });
```

And time for dessert. Circuit breaker pattern is nothing new, but it got second life after [Netflix blog post](http://techblog.netflix.com/2011/12/making-netflix-api-more-resilient.html).
When your app is dependant on some downstream system that could be down or just not responding under heavy load,
in many cases it's not worth trying to connect over and over again (especially if timeout is long).  
This little policy, tells your code to set circuit broken from 1 minute after it fails 2 times with `HttpException`.  
During that minute, every call to this code will immediately fail with an exception, without making http call etc.

```cs
Policy
    .Handle<HttpException>()
    .CircuitBreaker(2, TimeSpan.FromMinutes(1));
```

This library won't world biggest problems, but it should be nice addition to your toolbelt.  
You can find it on GitHub: https://github.com/App-vNext/Polly
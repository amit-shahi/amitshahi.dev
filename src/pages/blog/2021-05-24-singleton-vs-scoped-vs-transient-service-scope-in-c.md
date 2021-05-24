---
templateKey: blog-post
title: 'Singleton vs Scoped vs Transient Service Scope in C#'
date: 2021-05-20T23:54:35.610Z
description: Followings are the specific use-case for different services.
featuredpost: true
featuredimage: /img/service-scope.png
---
**Singleton** 

1. Caching Services 
2. Global Configuration
3. Business Rules 
4. [HttpClients ](https://medium.com/@nuno.caneco/c-httpclient-should-not-be-disposed-or-should-it-45d2a8f568bc)
5. Persisting state that's useful for the runtime of an application

**Scoped**

1. Persisting state throughout application per request - New Instance is created for every request.

**Transient**

1. Database Access
2. File Access
3. Services that should dispose of their state 
4. When you need a fresh instance of an object every single time

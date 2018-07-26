---
name: Express
---

# Express

Example of running an express webserver and serving some routes.

```
title: Express Server
ns: express
name: example

provider https://api.chix.io/v1/nodes/rhalff/{ns}/{name}

Express(express/app), Listen(express/listen)
HomeRoute(express/get), SendHome(express/send)

'8080' -> port Listen
Express app -> app Listen

'/' -> -> path HomeRoute
Express app -> app HomeRoute
HomeRoute res -> res SendHome
'Home' -> ^body HomeRoute

'/about' -> -> path HomeRoute
Express app -> app HomeRoute
HomeRoute res -> res SendHome
'About' -> ^body HomeRoute
```
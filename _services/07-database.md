---
title: Database
class: Data
---

A Database service provides a single network hostname that is used to concurrently save, update and delete application data.

We need a Database service for application persistance and scaling. Multiple containers can interact with a single Database for a consistent set of application data.

A Database depends on a VPC for secure network access from Containers.


```
     https                                        
  ┌────▽──────────────────────────────┐           
┌─┤           Load Balancer           ├──────────┐
│ └───────────────────────────────────┘          │
│┌─────────────────┐┌─────────────────┐          │
││┏━━━━━┓┏━━━━━━━━┓││     ┏━━━━━┓     │┌────────┐│
││┃web 1┃┃worker 1┃││     ┃web 2┃     ││        ││
││┗━━━━━┛┗━━━━━━━━┛││     ┗━━━━━┛     ││Database││
││   Instance 1    ││   Instance 2    ││        ││
│└─────────────────┘└─────────────────┘└────────┘│
│                      VPC                       │
└────────────────────────────────────────────────┘
               ┌──────┐┌────────┐                 
               │Crypto││Registry│                 
               └──────┘└────────┘                 
```
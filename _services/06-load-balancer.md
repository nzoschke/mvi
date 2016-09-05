---
title: Load Balancer
class: Workload
---

A Load Balancer service provides a single, stable hostname that accepts network requests and forwards them to one or more healthy containers.

We need a Load Balancer service for application scaling and High Availability (HA). To scale and to avoid Single Points of Failure (SPOF), we need to run at least two containers on two instances. A Load Balancer needs to coordinate when containers are unhealthy or when new containers are ready to serve traffic.

Load Balancers depend on Containers to return a response for forwarded requests.


```
     https                              
  ┌────▽──────────────────────────────┐ 
┌─┤           Load Balancer           ├┐
│ └───────────────────────────────────┘│
│┌─────────────────┐┌─────────────────┐│
││┏━━━━━┓┏━━━━━━━━┓││     ┏━━━━━┓     ││
││┃web 1┃┃worker 1┃││     ┃web 2┃     ││
││┗━━━━━┛┗━━━━━━━━┛││     ┗━━━━━┛     ││
││   Instance 1    ││   Instance 2    ││
│└─────────────────┘└─────────────────┘│
│                 VPC                  │
└──────────────────────────────────────┘
          ┌──────┐┌────────┐            
          │Crypto││Registry│            
          └──────┘└────────┘            
```
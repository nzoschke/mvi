---
title: Load Balancers
---

A Load Balancer service provides a single, stable hostname that accepts network requests and forwards them to one or more healthy containers.

We need a Load Balancer service to run our app in a High Availability (HA) fashion. To avoid Single Points of Failure (SPOF), we need to run at least two containers on two instances. A Load Balancer needs to coordinate when containers are unhealthy or when new containers or instances are ready to serve traffic.

Load Balancers depend on Containers to return a response for forwarded requests.


```
           http           
  ┌─────────▽──────────┐  
┌─┤   Load Balancer    ├─┐
│ └────────────────────┘ │
│┌──────────┐┌──────────┐│
││ ┏━━━━━┓  ││ ┏━━━━━┓  ││
││ ┃web 1┃  ││ ┃web 2┃  ││
││ ┗━━━━━┛  ││ ┗━━━━━┛  ││
││Instance 1││Instance 2││
│└──────────┘└──────────┘│
│          VPC           │
└────────────────────────┘
```
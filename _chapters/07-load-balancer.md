---
title: Load Balancer
permalink: /load-balancer
---

# Load Balancer

```text
 ┌──────────────────────────────────────────────┐ 
┌┤                Load Balancer                 ├┐
│└──────────────────────────────────────────────┘│
│ ┌─────────────────┐┌─────────────────┐         │
│ │┏━━━━━┓┏━━━━━━━━┓││     ┏━━━━━┓     │┏━━━━━━┓ │
│ │┃web 1┃┃worker 1┃││     ┃web 2┃     │┃ func ┃ │
│ │┗━━━━━┛┗━━━━━━━━┛││     ┗━━━━━┛     │┗━━━━━━┛ │
│ │      VM 1       ││      VM 2       │         │
│ └─────────────────┘└─────────────────┘         │
│                                                │
│                                                │
│                                                │
│                      VPC                       │
└────────────────────────────────────────────────┘
┌──────┐┌────────┐                                
│Crypto││Registry│                                
└──────┘└────────┘                                
```

A Load Balancer service provides a single, stable hostname that accepts network requests and forwards them to one or more healthy containers.

We need a Load Balancer service for application scaling and High Availability (HA). To scale and to avoid Single Points of Failure (SPOF), we need to run at least two containers on two VMs. A Load Balancer needs to coordinate when containers are unhealthy or when new containers are ready to serve traffic.

A Load Balancer depends on a VPC for secure network access, and Containers to return a response for forwarded requests.

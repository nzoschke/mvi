---
title: Metrics
---

A Metrics service provides a place to numerical data from infrastructure services, so operational properties from the entire system can be aggregated, analyzed and graphed for real-time and historical data.

We need Metrics for an operator to get visibility into the availbility, performance and error rate in Containers and the supporting infrastructure.

Metrics is a stand-alone service.

```
     https                                        
  ┌────▽──────────────────────────────┐           
┌─┤           Load Balancer           ├──────────┐
│ └───────────────────────────────────┘          │
│┌─────────────────┐┌─────────────────┐┌────────┐│
││┏━━━━━┓┏━━━━━━━━┓││     ┏━━━━━┓     ││        ││
││┃web 1┃┃worker 1┃││     ┃web 2┃     ││Database││
││┗━━━━━┛┗━━━━━━━━┛││     ┗━━━━━┛     ││        ││
││   Instance 1    ││   Instance 2    ││        ││
│└─────────────────┘└─────────────────┘└────────┘│
│┌────────────────────────────────────┐          │
││         Shared File System         │          │
│└────────────────────────────────────┘          │
│                      VPC                       │
└────────────────────────────────────────────────┘
        ┌──────┐┌────────┐┌────┐┌───────┐         
        │Crypto││Registry││Logs││Metrics│         
        └──────┘└────────┘└────┘└───────┘         
```
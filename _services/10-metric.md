---
title: Metrics
---

A Metrics service provides a place to save numerical data so operational properties of the entire system can be aggregated, analyzed and graphed for real-time and historical data.

```ascii
     https                                        
  ┌────▽──────────────────────────────┐           
┌─┤           Load Balancer           ├──────────┐
│ └───────────────────────────────────┘          │
│┌─────────────────┐┌─────────────────┐          │
││┏━━━━━┓┏━━━━━━━━┓││     ┏━━━━━┓     │          │
││┃web 1┃┃worker 1┃││     ┃web 2┃     │          │
││┗━━━━━┛┗━━━━━━━━┛││     ┗━━━━━┛     │          │
││   Instance 1    ││   Instance 2    │┌────────┐│
│└─────────────────┘└─────────────────┘│        ││
│┌────────────────────────────────────┐│Database││
││         Shared File System         ││        ││
│└────────────────────────────────────┘└────────┘│
│                      VPC                       │
└────────────────────────────────────────────────┘
        ┌──────┐┌────────┐┌────┐┌───────┐         
        │Crypto││Registry││Logs││Metrics│         
        └──────┘└────────┘└────┘└───────┘         
```

We need Metrics for an operator to get visibility into the availbility, performance and error rate in Containers and the supporting infrastructure.

Metrics is a stand-alone service.

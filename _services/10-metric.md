---
title: Metrics
---

A Metrics service provides a place to numerical data from infrastructure services, so operational properties from the entire system can be aggregated, analyzed and graphed for real-time and historical data.

We need Metrics for an operator to get visibility into the availbility, performance and error rate in Containers and the supporting infrastructure.

Metrics is a stand-alone service.

```
           http                                
  ┌─────────▽──────────┐                       
┌─┤   Load Balancer    ├──────────────────────┐
│ └────────────────────┘                      │
│┌──────────┐┌──────────┐                     │
││ ┏━━━━━┓  ││ ┏━━━━━┓  │                     │
││ ┃web 1┃  ││ ┃web 2┃  │                     │
││ ┗━━━━━┛  ││ ┗━━━━━┛  │                     │
││Instance 1││Instance 2│                     │
│└──────────┘└──────────┘                     │
│┌──────────────────────┐                     │
││  Shared File System  │                     │
│└──────────────────────┘                     │
│                     VPC                     │
└─────────────────────────────────────────────┘
┌────────┐┌────────┐┌──────────┐┌────┐┌───────┐
│Registry││KV Store││Blob Store││Logs││Metrics│
└────────┘└────────┘└──────────┘└────┘└───────┘
```
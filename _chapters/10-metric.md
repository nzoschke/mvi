---
title: Metric
permalink: /metric
---

# Metric

```text
 ┌──────────────────────────────────────────────┐ 
┌┤                Load Balancer                 ├┐
│└──────────────────────────────────────────────┘│
│┌─────────────────┐┌─────────────────┐          │
││┏━━━━━┓┏━━━━━━━━┓││      ┏━━━━━┓    │ ┏━━━━━━┓ │
││┃web 1┃┃worker 1┃││      ┃web 2┃    │ ┃ func ┃ │
││┗━━━━━┛┗━━━━━━━━┛││      ┗━━━━━┛    │ ┗━━━━━━┛ │
││      VM 1       ││      VM 2       │┌────────┐│
│└─────────────────┘└─────────────────┘│        ││
│┌────────────────────────────────────┐│Database││
││         Shared File System         ││        ││
│└────────────────────────────────────┘└────────┘│
│                      VPC                       │
└────────────────────────────────────────────────┘
┌──────┐┌────────┐┌───┐┌──────┐                   
│Crypto││Registry││Log││Metric│                   
└──────┘└────────┘└───┘└──────┘                   
```

A Metric service provides a place to save numerical data so operational properties of the entire system can be aggregated, analyzed and graphed for real-time and historical data.

We need Metrics for an operator to get visibility into the availbility, performance and error rate in Containers and the supporting infrastructure.

A Metric service is a stand-alone service.

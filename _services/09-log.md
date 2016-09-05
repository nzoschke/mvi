---
title: Logs
---

A Log service provides a place to send text from an app's stdout and stderr streams, so events from more than one container can be aggregated, tailed in real-time and searched for historical data.

We need Logs for an operator to get visibility into all the events happening in Containers and on Instances.

Logs is a stand-alone service.

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
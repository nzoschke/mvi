---
title: Key-Value Store
---

A Key-Value (KV) Store service provides a way to save small amounts of structured data in a HA fashion while still being easy to query for reporting purposes.

We need a KV Store to save and query metadata like a history of when builds were performed.

A KV Store is a stand-alone service.

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
   ┌──────┐┌────────┐┌────┐┌───────┐┌─────────┐   
   │Crypto││Registry││Logs││Metrics││Key/Value│   
   └──────┘└────────┘└────┘└───────┘└─────────┘   
```
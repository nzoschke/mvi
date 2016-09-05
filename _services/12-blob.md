---
title: Blob Store
---

A Blob Store service provides a way to save arbitrary sized unstructured data in a HA fashion.

We need a Blob Store to put and get data that could be very large like application secrets or build logs.

A Blob Store is a stand-alone service.

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
┌──────┐┌────────┐┌────┐┌───────┐┌─────────┐┌────┐
│Crypto││Registry││Logs││Metrics││Key/Value││Blob│
└──────┘└────────┘└────┘└───────┘└─────────┘└────┘
```
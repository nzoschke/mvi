---
title: Blob Store
---

A Blob Store service provides a way to save arbitrary sized unstructured data in a HA fashion.

We need a Blob Store to put and get data that could be very large like application secrets or build logs.

A Blob Store is a stand-alone service.

```
           http                 
  ┌─────────▽──────────┐        
┌─┤   Load Balancer    ├───────┐
│ └────────────────────┘       │
│┌──────────┐┌──────────┐      │
││ ┏━━━━━┓  ││ ┏━━━━━┓  │      │
││ ┃web 1┃  ││ ┃web 2┃  │      │
││ ┗━━━━━┛  ││ ┗━━━━━┛  │      │
││Instance 1││Instance 2│      │
│└──────────┘└──────────┘      │
│┌──────────────────────┐      │
││  Shared File System  │      │
│└──────────────────────┘      │
│             VPC              │
└──────────────────────────────┘
┌────────┐┌────────┐┌──────────┐
│Registry││KV Store││Blob Store│
└────────┘└────────┘└──────────┘
```
---
title: Blob
---

# Blob

```ascii
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
┌──────┐┌────────┐┌───┐┌──────┐┌──┐┌────┐         
│Crypto││Registry││Log││Metric││KV││Blob│         
└──────┘└────────┘└───┘└──────┘└──┘└────┘         
```

A Blob service provides a way to save arbitrary sized unstructured data in a HA fashion.

We need a Blob service to put and get data that could be very large like application secret data or build logs.

A Blob service is a stand-alone service.

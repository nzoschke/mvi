---
title: Containers
class: Workload
---

A Container service provides a way to run many specialized process types on fewer homogeneous Instances.

```ascii
┌───────────────┐
│┌─────────────┐│
││┏━━━┓┏━━━━━━┓││
││┃web┃┃worker┃││
││┗━━━┛┗━━━━━━┛││
││  Instance   ││
│└─────────────┘│
│      VPC      │
└───────────────┘
    ┌──────┐     
    │Crypto│     
    └──────┘     
```

We need Containers to package our app code and dependencies. We need a Container service to start, stop and monitor app processes.

Containers depend on Instances for a host Operating System and a Registry for application file system data. Containers use Crypto for decrypting application secrets.

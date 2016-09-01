---
title: Instance
---

An Instance service provides a virtual machine with CPU, Memory, Networking and a server Operating System.

We need Instances to run our app code.

An Instance depends on a VPC for network access.

```
┌──────────┐
│┌────────┐│
││Instance││
│└────────┘│
│   VPC    │
└──────────┘
```
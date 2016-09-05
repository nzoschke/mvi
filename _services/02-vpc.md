---
title: VPC
class: Security
---

A Virtual Private Cloud (VPC) service provides private networking.

```ascii
┌──────────┐
│┌────────┐│
││Instance││
│└────────┘│
│   VPC    │
└──────────┘
```

We need a VPC to enable our trusted apps to interact with each other over the network, and to prevent all network access to untrusted apps.

Many services, like Instances and Databases, depend on the VPC for network security.

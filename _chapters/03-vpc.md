---
title: Virtual Private Cloud
---

# Virtual Private Cloud

```ascii
┌────────────────────────────────────────────────┐
│                                                │
│                                                │
│                                                │
│                                                │
│                                                │
│                                                │
│                     ┌────┐                     │
│                     │ VM │                     │
│                     └────┘                     │
│                                                │
│                                                │
│                                                │
│                                                │
│                                                │
│                      VPC                       │
└────────────────────────────────────────────────┘
```

A Virtual Private Cloud (VPC) service provides private networking.

We need a VPC to enable our trusted apps to interact with each other over the network, and to prevent all network access to untrusted apps.

Many services, like VMs and Databases, depend on the VPC for network security.

---
title: Container
permalink: /container
---

# Container

```ascii
┌────────────────────────────────────────────────┐
│                                                │
│                                                │
│              ┌─────────────┐                   │
│              │┏━━━┓┏━━━━━━┓│┏━━━━━━┓           │
│              │┃web┃┃worker┃│┃ func ┃           │
│              │┗━━━┛┗━━━━━━┛│┗━━━━━━┛           │
│              │     VM      │                   │
│              └─────────────┘                   │
│                                                │
│                                                │
│                                                │
│                      VPC                       │
└────────────────────────────────────────────────┘
┌──────┐                                          
│Crypto│                                          
└──────┘                                          
```

A Container service provides a way to run many specialized process types on fewer homogeneous VMs.

We need Containers to package our app code and dependencies. We need a Container service to start, stop and monitor app processes.

Linux Containers depend on VMs for a host Operating System and a Registry for application file system data.

Function Containers remove the dependencies, but add constraints about how to package our app to run on VMs managed by the provider.

Containers use Crypto for decrypting application secrets.

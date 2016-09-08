---
title: Registry
permalink: /registry/
---

# Registry

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
┌──────┐┌────────┐                                
│Crypto││Registry│                                
└──────┘└────────┘                                
```

A Registry service provides a private place to push, store and pull Container Image data.

We need a Registry to efficiently store layers of new file system data for app builds, and to pull the layers of data needed to start a Container.

A Registry is a stand-alone service.

---
title: Registry
class: Workload
---

A Registry service provides a private place to push, store and pull Container Image data.

We need a Registry to efficiently store layers of new file system data for app builds, and to pull the layers of data needed to start a Container.

A Registry is a stand-alone service.

```ascii
┌────────────────┐
│┌──────────────┐│
││┏━━━┓ ┏━━━━━━┓││
││┃web┃ ┃worker┃││
││┗━━━┛ ┗━━━━━━┛││
││   Instance   ││
│└──────────────┘│
│      VPC       │
└────────────────┘
┌──────┐┌────────┐
│Crypto││Registry│
└──────┘└────────┘
```
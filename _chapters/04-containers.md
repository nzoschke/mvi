---
title: Containers
---

A Container service provides a way to run many specialized process types on fewer homogeneous instances.

We need Containers to package our app code and dependencies. We need a Container service to start, stop and monitor app processes.

Containers depends on Instances for a host Operating System.

```
┌──────────┐
│┌────────┐│
││ ┏━━━┓  ││
││ ┃web┃  ││
││ ┗━━━┛  ││
││Instance││
│└────────┘│
│   VPC    │
└──────────┘
```
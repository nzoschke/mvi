---
title: Containers
---

A Container service provides a way to run many specialized process types on fewer homogeneous Instances.

We need Containers to package our app code and dependencies. We need a Container service to start, stop and monitor app processes.

Containers depends on Instances for a host Operating System.

```
┌────────────────┐
│┌──────────────┐│
││┏━━━━━┓┏━━━━━┓││
││┃web 1┃┃web 2┃││
││┗━━━━━┛┗━━━━━┛││
││   Instance   ││
│└──────────────┘│
│      VPC       │
└────────────────┘
```
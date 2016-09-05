---
title: Registry
---

A Registry service provides a private place to push, store and pull Container Image data.

We need a Registry to efficiently store layers of new data for app builds, and to pull the layers of data needed to start a Container.

A Registry is a stand-alone service.

```
           http           
  ┌─────────▽──────────┐  
┌─┤   Load Balancer    ├─┐
│ └────────────────────┘ │
│┌──────────┐┌──────────┐│
││ ┏━━━━━┓  ││ ┏━━━━━┓  ││
││ ┃web 1┃  ││ ┃web 2┃  ││
││ ┗━━━━━┛  ││ ┗━━━━━┛  ││
││Instance 1││Instance 2││
│└──────────┘└──────────┘│
│┌──────────────────────┐│
││  Shared File System  ││
│└──────────────────────┘│
│          VPC           │
└────────────────────────┘
┌────────┐                
│Registry│                
└────────┘                
```
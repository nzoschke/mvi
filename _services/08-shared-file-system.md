---
title: Shared File System
class: Data
---

A Shared File System (FS) service provides a directory of data that is synchronized across two or more containers.

We want a Shared FS service for persistence as Containers move around on Instances.

A Shared File System depends on a VPC for network availability. It is the Instance's responsibility to mount the file system and make it available to Containers

```
     https                                        
  ┌────▽──────────────────────────────┐           
┌─┤           Load Balancer           ├──────────┐
│ └───────────────────────────────────┘          │
│┌─────────────────┐┌─────────────────┐          │
││┏━━━━━┓┏━━━━━━━━┓││     ┏━━━━━┓     │          │
││┃web 1┃┃worker 1┃││     ┃web 2┃     │          │
││┗━━━━━┛┗━━━━━━━━┛││     ┗━━━━━┛     │          │
││   Instance 1    ││   Instance 2    │┌────────┐│
│└─────────────────┘└─────────────────┘│        ││
│┌────────────────────────────────────┐│Database││
││         Shared File System         ││        ││
│└────────────────────────────────────┘└────────┘│
│                      VPC                       │
└────────────────────────────────────────────────┘
               ┌──────┐┌────────┐                 
               │Crypto││Registry│                 
               └──────┘└────────┘                 
```
---
title: Image
permalink: /image
---

# Image

```text
┌──────────────────────────────────────┐
│                                      │
│                                      │
│         ┌─────────────────┐          │
│         │                 │          │
│         │                 │          │
│         │                 │          │
│         │       VM        │          │
│         └─────────────────┘          │
│                                      │
│                                      │
│                 VPC                  │
└──────────────────────────────────────┘
 ┌──────┐┏━━━━━┓                        
 │Crypto│┃Image┃                        
 └──────┘┗━━━━━┛                        
```

An Image service provides a private place to push, store and pull binary application and depdendency data.

We need an Image service to efficiently store layers of new file system data for app builds, and to pull the layers of data needed to start a Container.

An Image service is a stand-alone service.

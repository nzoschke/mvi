---
title: Release a Build
permalink: /release
---

# Release a Build

We can push a custom web server to a Registry, but we need a way to release the new change. For any serious application we will want to isolate the build step and record a build artifact. We also need a way to release or roll back to any build artifact with no downtime.

So we need Key-Value and Blob Service to account for our build metadata.

We also need a Build API to automate the build pipeline:

* Generate a Build ID
* Build new Images
* Tag Images with Build ID
* Push Images to Registry
* Save the Build logs Blob
* Save the Build ID Key, and time and URL to log Values

We need a Release API to:

* Tell the Container Service to start containers from a specific Build ID Images

```ascii
 ┌────────────────┐          
┌┤       LB       ├─────────┐
│└────────────────┘         │
│┌───────┐┌───────┐         │
││┏━━━━━┓││┏━━━━━┓│┏━━━━━━━┓│
││┃web 1┃││┃web 2┃│┃ build ┃│
││┗━━━━━┛││┗━━━━━┛│┃release┃│
││ VM 1  ││ VM 2  │┃  API  ┃│
│└───────┘└───────┘┗━━━━━━━┛│
│            VPC            │
└───────────────────────────┘
┌────────┐┌──┐┌────┐         
│Registry││KV││Blob│         
└────────┘└──┘└────┘             
```

There is one final challenge: rolling out the new images with zero downtime. We need the Container and Load Balancer service to coordinate this:

* Container Service finds spare capacity and starts a new Container
* Container Service registers new Container with Load Balancer
* Load Balancer reports back to Container Service that the new Container is healthy
* Container service stops an old Container

One by one, the Container and Load Balancer orchestrate gracefully releasing our newly built images.
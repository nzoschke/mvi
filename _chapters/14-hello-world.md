---
title: Run Hello World
permalink: /hello-world
---

# Run Hello World

We start with a very simple app: the Apache HTTP Server and its default configuration.

We need:

* A VPC
* A VM
* A web Container
* An Apache Image

Docker Hub offers a pre-built Apache [httpd Image](https://hub.docker.com/_/httpd/). We declare that we want to use this as a web process. To run this in the cloud, we need a VPC, VM and Container Service.

```yaml
web:
  image: httpd
```
{:.left}

```ascii
┌───────┐
│┌─────┐│
││┏━━━┓││
││┃web┃││
││┗━━━┛││
││ VM  ││
│└─────┘│
│  VPC  │
└───────┘
```
{:.right}

However, making a request to this Container poses a challenge.

First, the VPC blocks all network access by default. Next, the VM network address will change if it fails and is replaced. Finally, the Container may not be able to serve the request if it is booting or offline due to a crash or VM failure.

So we need a Load Balancer service, port configuration, and VM and Container redundancy.

```yaml
web:
  image: httpd
  ports:
    - 80:80
```
{:.left}

```ascii
 ┌────────────────┐ 
┌┤       LB       ├┐
│└────────────────┘│
│┌───────┐┌───────┐│
││┏━━━━━┓││┏━━━━━┓││
││┃web 1┃││┃web 2┃││
││┗━━━━━┛││┗━━━━━┛││
││ VM 1  ││ VM 2  ││
│└───────┘└───────┘│
│       VPC        │
└──────────────────┘
```
{:.right}

The Load Balancer will provide a static hostname that is accessable over the Internet and coordinate what internal addresses it should forward a request to.

The Load Balancer will ask for minimal access into the VPC, only the HTTP protocol to a single VM and Container port.

The Container Service will tell the Load Balancer about any changes to Container network addresses as VMs and Containers start and stop due to maintenance or failures.

The Load Balancer will also maintain its own view of what Containers are returning healthy responses. If a Container is repeatedly failing, the Load Balancer can divert traffic from it to a healthy Container.

The manifest and architecture to reliably run "Hello World" is simple.

There are underlying complexities in network security and container orchestration, but the VPC, Instance, Container and Load Balancer service handle this for us.
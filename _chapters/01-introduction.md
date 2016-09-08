---
title: Introduction
permalink: /
---

# Introduction

The goal is simple: take a web app and run it forever in the cloud.

The best practices are understood:

* Declare everything your app needs in code
* Use reliable cloud services
* Automate everything around cloud service setup, changes and failures
* Keep everything as simple as possible

The responsibilities are clear:

1. You provide an application manifest
2. A community of experts designs a cloud service architecture
4. Software automates setting up this architecture
3. Providers operate the underlying cloud services
4. Software automates changes to the architecture that offer security, performance or cost improvements

The "Minimal Infrastructure" methodology is derived from this.

If we understand the simplest set of primative infrastructure services needed to run any application, we can tell a cloud service provider how to set them up to bring our app online.

If a provider runs these infrastructure services with a high Quality-of-Service (QoS) our app will see excellent uptime with minimal operations on our part.

If we can safely modify these infrastructure services below our app, we can maintain availability while adding security, performance and cost improvements over time.

This book enumerates the minimal infrastructure services that are available in the cloud, and guides us through how configure and manage these to support simple to increasingly complex apps.

## Background

This book is inspired by Michael Hartl's [Ruby on Rails Tutorial](https://www.railstutorial.org/) and Adam Wiggins' [The Twelve-Factor App](https://12factor.net/).

The Rails Tutoral teaches you how to develop an application. Twelve-Factor teaches you how to package your application to run as service.

Minimal Infrastructure teaches you how to assemble the underlying cloud services to support a Twelve-Factor Rails app.

## Who is this book for?

The primary purpose is educational. Any technician can read this to better understand what services "the cloud" provides, why we need them, and how to use them.

The secondary purpose is practical. Any developer or ops engineer can use the techniques, tutorials and tools to set up real production-ready infrastructure for apps.

# Cloud Services

```ascii
 ┌──────────────────────────────────────────────┐ 
┌┤                Load Balancer                 ├┐
│└──────────────────────────────────────────────┘│
│┌─────────────────┐┌─────────────────┐          │
││┏━━━━━┓┏━━━━━━━━┓││     ┏━━━━━┓     │ ┏━━━━━━┓ │
││┃web 1┃┃worker 1┃││     ┃web 2┃     │ ┃func 1┃ │
││┗━━━━━┛┗━━━━━━━━┛││     ┗━━━━━┛     │ ┗━━━━━━┛ │
││      VM 1       ││      VM 2       │┌────────┐│
│└─────────────────┘└─────────────────┘│        ││
│┌────────────────────────────────────┐│Database││
││         Shared File System         ││        ││
│└────────────────────────────────────┘└────────┘│
│                      VPC                       │
└────────────────────────────────────────────────┘
┌──────┐┌────────┐┌────┐┌───────┐┌─────────┐┌────┐
│Crypto││Registry││Logs││Metrics││Key/Value││Blob│
└──────┘└────────┘└────┘└───────┘└─────────┘└────┘
```

There are twelve infrastructure services in three service classes that are necessary to run an app.

We first need a secure computing layer. Then we can add our application specific processes and data. Finally we need utility services to help see how our app is running and to manage its lifecycle.

#### Secure Compute

### [1. Virtual Machine](vm)

A Virtual Machine (VM) service provides CPU, Memory, Networking and a server Operating System.

### [2. Virtual Private Cloud](vpc)

A Virtual Private Cloud (VPC) service provides private networking.

### [3. Cryptography](crypto)

A Cryptography (Crypto) service provides a way to create, import and rotate an unguessable key for encrypting data, and provides a way to get and audit access to the key for decrypting data.

#### Application Workload

### [4. Container](container)

A Container service provides a way to run many specialized process types on fewer homogeneous VMs.

### [5. Registry](registry)

A Registry service provides a private place to push, store and pull Container Image data.

### [6. Load Balancer](load-balancer)

A Load Balancer service provides a single, stable hostname that accepts network requests and forwards them to one or more healthy containers.

### [7. Database](database)

A Database service provides a single network hostname that is used to save, update and delete application data records concurrently by one or more containers.

### [8. Shared File System](shared-fs)

A Shared FS service provides a single directory of files that are synchronized across one or more containers.

#### Operations

### [9. Log](log)

A Log service provides a place to send text from an app's stdout and stderr streams, so events from more than one container can be aggregated, tailed in real-time and searched for historical data.

### [10. Metric](metric)

A Metric service provides a place to save numerical data so operational properties of the entire system can be aggregated, analyzed and graphed for real-time and historical data.

### [11. Key/Value (KV)](kv)

A KV service provides a way to save small amounts of structured data in a HA fashion while still being easy to query for reporting purposes.

### [12. Blob](blob)

A Blob service provides a way to save and retrieve arbitrary sized unstructured data in a HA fashion.

# Tutorials

These tutorials demonstrate how we use and configure the cloud services to support the Twelve-Factor methods:

* Hello World (Run)
* Build and Release Custom Images (Dependencies, Build/Release/Run)
* Scaling Workers for Data Science (Processes, Concurrency)
* Scaling and Securing Web for APIs (Port Binding)
* Securing the Environment (Config, Backing Services)
* Rolling Deploys (Disposability)
* Debugging (Logs, Admin Processes)

These tutorials demonstrate how we use everything together for real-world web apps:

* Rails, Nginx, Postgres and Redis
* Wordpress and MySQL

These tutorials demonstrate how we maintain security and deliver architecture improvements over time:

* Automated Infrastructure Updates
---
title: Introduction
permalink: /
---

# Introduction

The goal is simple: take a web app and run it forever in the cloud.

The best practices are understood:

* Declare what an app needs in code
* Automate cloud service setup, change and failure management to support the app
* Keep the systems as simple as possible

The responsibilities are clear:

1. A **community of experts** designs simple cloud service architectures
2. **You** provide an [application manifest](glossary#application-manifest) file that declares what your app needs
3. **Software** automates cloud service setup
4. **Providers** operate the underlying cloud services
5. **Software** monitors the services and automates failures

The "Minimum Infrastructure" methodology is derived from this.

If we, as a community, design a simple cloud service architecture to run any application, we can automate the configuration of cloud services to bring an app online.

If a provider runs the cloud services with a high [Quality-of-Service](glossary#quality-of-service) (QoS) and if automation handles the failures that do happen, an apps will see excellent uptime with minimal operations on our part.

Furthermore, we can apply this methodolgy over the entire lifecycle of an app. When we can safely automate the services supporting our app, we can maintain availability and add further simplicity, security, performance and cost improvements over time.

This book enumerates a simple set of infrastructure services that are availble in the cloud and assembles them into a simple architecture. It then guides us through how manage these services to support simple to increasingly complex apps.

## Background

This book is inspired by Michael Hartl's [Ruby on Rails Tutorial](https://www.railstutorial.org/) and Adam Wiggins' [The Twelve-Factor App](https://12factor.net/).

The Rails Tutoral teaches you how to develop an application. Twelve-Factor teaches you how to package your application to run as service.

Minimum Infrastructure teaches you how to assemble the underlying cloud services to support a Twelve-Factor Rails app.

## Who is this book for?

The primary purpose is educational. Any technician can read this to better understand what services "the cloud" provides, why we need them, and how to use them.

The secondary purpose is practical. Any developer or ops engineer can use the methodologies, tutorials and tools to set up real production-ready infrastructure for apps.

# Cloud Services

```ascii
 ┌──────────────────────────────────────────────┐ 
┌┤                Load Balancer                 ├┐
│└──────────────────────────────────────────────┘│
│┌─────────────────┐┌─────────────────┐          │
││┏━━━━━┓┏━━━━━━━━┓││      ┏━━━━━┓    │ ┏━━━━━━┓ │
││┃web 1┃┃worker 1┃││      ┃web 2┃    │ ┃ func ┃ │
││┗━━━━━┛┗━━━━━━━━┛││      ┗━━━━━┛    │ ┗━━━━━━┛ │
││      VM 1       ││      VM 2       │┌────────┐│
│└─────────────────┘└─────────────────┘│        ││
│┌────────────────────────────────────┐│Database││
││         Shared File System         ││        ││
│└────────────────────────────────────┘└────────┘│
│                      VPC                       │
└────────────────────────────────────────────────┘
┌──────┐┌────────┐┌───┐┌──────┐┌──┐┌────┐         
│Crypto││Registry││Log││Metric││KV││Blob│         
└──────┘└────────┘└───┘└──────┘└──┘└────┘         
```

There are twelve infrastructure services in three service classes that are necessary to run an app.

We first need a secure computing services. Then we add services to support our application specific processes and data. Finally we need utility services to see how our app is running and to manage its lifecycle.

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

A Load Balancer service provides a single, stable hostname that accepts network requests and forwards them to one or more healthy Containers.

### [7. Database](database)

A Database service provides a single network hostname that is used to save, update and delete application data records concurrently by one or more Containers.

### [8. Shared File System](shared-fs)

A Shared File System (FS) service provides a single directory of files that are synchronized across one or more Containers.

#### Operations

### [9. Log](log)

A Log service provides a place to send ordered text from app Containers' stdout and stderr streams, so all the application events can be tailed in real-time and searched later.

### [10. Metric](metric)

A Metric service provides a place to save numerical data from apps and underlying cloud srevices so operational properties of the entire system can be aggregated, analyzed and graphed in real-time and reviewed later.

### [11. Key-Value (KV)](kv)

A Key-Value (KV) service provides a way to save small amounts of structured data in a [highly-available](glossary#highly-available) (HA) fashion while still being easy to query for reporting purposes.

### [12. Blob](blob)

A Blob service provides a way to save and retrieve large amounts unstructured data in a HA fashion.

# Twelve-Factor Tutorials

These tutorials demonstrate how we use and configure the cloud services to support the Twelve-Factor methods:

#### Dependencies / Build, Release, Run

* Run Hello World
* Build Dependencies into a Container Image
* Release a Build

#### Processes / Concurrency / Admin Processes

* Scaling Workers for Data Science
* Scheduled Processes
* Debugging a Running Container
* Running One-Off Containers

#### Port Binding

* Scaling and Securing a Web Server for APIs
* Scaling and Securing a TCP Service

#### Config / Backing Services

* Securing the Environment
* Linking Containers
* Linking to a Database

#### Logs

* Tailing App Logs
* Processing App Logs
* Visualizing App Performance and Availability

# Real-World Tutorials

These tutorials demonstrate everything together for web apps:

* Rails, NGINX, Postgres and Redis
* Wordpress and MySQL

These tutorials demonstrate how we maintain the infrastructure over time:

* Update VMs
* Load Balancer Migrations
* Database Migrations
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

1. **You** provide an application code base and configuration files that declares what the app needs
2. A **community** designs the simplest possible cloud service architecture to satisfy the app needs
3. **Providers** operate the cloud services
4. **Software** automates cloud service setup, monitoring and maintenance

The "Minimum Viable Infrastructure" methodology is derived from this.

If we, as a community, design a simple cloud service architecture to run any application, we can automate the configuration of cloud services to bring an app online.

If a provider runs the cloud services with a high [Quality-of-Service](glossary#quality-of-service) (QoS) and if automation handles the failures that do happen, an apps will see excellent uptime with minimal operations on our part.

Furthermore, we can apply this methodolgy over the entire lifecycle of an app. When we can safely automate the services supporting our app, we can maintain availability and add further simplicity, security, performance and cost improvements over time.

This book enumerates a simple set of infrastructure services that are availble in the cloud and assembles them into a simple architecture. It then guides us through how manage these services to support almost any app, from simple to complex.

## Background

This book is inspired by Michael Hartl's [Ruby on Rails Tutorial](https://www.railstutorial.org/) and Adam Wiggins' [The Twelve-Factor App](https://12factor.net/).

The Rails Tutoral teaches you how to develop an application. Twelve-Factor teaches you how to package an application to run as service.

Minimum Viable Infrastructure teaches you how to assemble cloud services to support an app.

## Who is this book for?

The primary purpose is educational. Any technician can read this to better understand what services "the cloud" provides, why we need them, and how to use them.

The secondary purpose is practical. Any developer or ops engineer can use the methodologies, tutorials and tools to set up real production-ready infrastructure for apps.

# Cloud Services

```text
 ┌────────────────────────────────────┐ 
┌┤           Load Balancer            ├┐
│└────────────────────────────────────┘│
│┌─────────────────┐┌─────────────────┐│
││┌─────┐┌────────┐││     ┌─────┐     ││
│││web 1││worker 1│││     │web 2│     ││
││└─────┘└────────┘││     └─────┘     ││
││      VM 1       ││      VM 2       ││
│└─────────────────┘└─────────────────┘│
│              ┌────────┐              │
│              │Database│              │
│              └────────┘              │
│                 VPC                  │
└──────────────────────────────────────┘
 ┌──────┐┌─────┐┌───┐┌──────┐┌──┐┌────┐ 
 │Crypto││Image││Log││Metric││KV││Blob│ 
 └──────┘└─────┘└───┘└──────┘└──┘└────┘ 
```

There are eleven infrastructure services in three service classes that are necessary to run an app.

First, we need a base secure computing service layer. Next, we need services to support our application specific processes and data. Last, we need utility services that provide visibility into how the app is running over its lifecycle.

#### Secure Compute

### [1. Virtual Machine](vm)

A Virtual Machine (VM) service provides CPU, Memory, Networking and a server Operating System.

### [2. Virtual Private Cloud](vpc)

A Virtual Private Cloud (VPC) service provides private networking.

### [3. Cryptography](crypto)

A Cryptography (Crypto) service provides a way to create, import and rotate an unguessable key for encrypting data, and provides a way to get and audit access to the key for decrypting data.

#### Application Workload

### [4. Image](image)

An Image service provides a private place to push, store and pull binary application and dependency data.

### [5. Container](container)

A Container service provides a way to run many specialized process types on fewer homogeneous VMs.

### [6. Load Balancer](load-balancer)

A Load Balancer service provides a single, stable hostname that accepts network requests and forwards them to one or more healthy Containers.

### [7. Database](database)

A Database service provides a single network hostname that is used to save, update and delete application data records concurrently by one or more Containers.

#### Visibility

### [8. Log](log)

A Log service provides a place to send ordered text from app Containers' stdout and stderr streams, so all the application events can be tailed in real-time and searched later.

### [9. Metric](metric)

A Metric service provides a place to save numerical data from apps and underlying cloud services so operational properties of the entire system can be aggregated, analyzed and graphed in real-time and reviewed later.

### [10. Key-Value (KV)](kv)

A Key-Value (KV) service provides a way to save small amounts of structured data in a [highly-available](glossary#highly-available) (HA) fashion while still being easy to query for reporting purposes.

### [11. Blob](blob)

A Blob service provides a way to save and retrieve large amounts unstructured data in a HA fashion.

# Tutorials

These tutorials demonstrate how we use and configure the cloud services to run simple apps:

#### Intro to Images, Containers, and Load Balancers

* [Run Hello World](hello-world)
* [Build a Custom Image](build)
* Expose the Web Server
* Configure a Secret

#### Containers

* Add a Second Container Type
* Scale Containers
* Schedule Tasks
* Debug a Running Container
* Run a One-Off Containers

#### Load Balancers

* Secure an HTTP API
* Secure a TCP Service
* Health Checks
* Rolling Deploys

#### Config

* Architecture for Secret Management

#### Backing Services

* Link to a Database
* Link Containers

#### Visibility

* Tail App Logs
* Process App Logs
* See App Performance and Availability

# Real-World Systens

These tutorials demonstrate how to tie these concepts together to run complex apps:

#### Build, Release, Run

* Architecture for a Build Service
* Architecture for a Release Service

#### Apps

* Rails, NGINX, Postgres and Redis
* Wordpress and MySQL

# Operations

These tutorials demonstrate how we maintain the infrastructure over time:

* Update VMs
* Load Balancer Migrations
* Database Migrations

---
title: FAQ
permalink: /faq
---

## Why don't stand-alone services like a Registry use the VPC? Is this a security concern?

Stand-alone services, like all cloud services, use HTTPS for secure communication.

On AWS, some of the stand-alone services like S3 do offer a "VPC endpoint" where traffic stays within the private networking layer. It's likely that more of the stand-alone services will offer this over time.

## Why do we need three data services (Database, KV and Blob)?

A general purpose database like Postgres is capable of anything from storing and retreiving small structured data, large binary data, and synchronizing data between many containers. But a Postgres server has some undesirable SPOF and failover properties.

Specialized data services impose constraints around how data is stored and received to provide better consistency, availability or partitioning. See the [CAP Theorem](https://en.wikipedia.org/wiki/CAP_theorem) for more details.

## What about a Shared File System?

It's tantilizing to share files between containers and persist files while containers are rescheduled.

There is widely used network and distributed file system software that offers this. Some platforms offer this as a network file system service.

However, these are very sophisticated systems and certainly add new complexity and operational challenges.

For simplicity, treat file systems as ephemeral and use a Database Service for shared state and a Blob Service for durable storage.

## What about "serverless"? Should there be a "Function" service type?

Application code + Lambda + API Gateway is effectively a Container and Load Balancer service. It no longer requires us to think about the underlying VM, but it doesn't change the application architecture.

A custom function + Lambda + triggered service events like S3 uploads or CloudWatch Logs data is a very powerful pattern that does fit into how we build a simple and robust system. This is a way to customize the behavior of the platform services.

## What about Twelve-Factor?

Higher level abstractions around "Containers" are replacing a lot of computing concepts, including some of the twelve factors.

Images encapsulate Codebase and Dependencies.

Containers encapsulate Processes, Concurrency, Disposability, Dev/prod parity and Admin Processes.

Load Balancers encapsulate Port binding and Concurrency

We now have a mere seven factors:
* Images
* Containers
* Load Balancers
* Config
* Backing Services
* Build, release, run
* Logs

## What about Service Discovery? Overlay networks? Ambassador containers?

These add a lot of complexity for very little gain. For simplicity, set environment variables with URLs to managed services.

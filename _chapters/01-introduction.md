---
title: Introduction
---

The goals is simple: take a web app and run it forever in the cloud.

The best practices are understood:

* Declare everything your app needs in code
* Use reliable cloud services
* Automate everything around setup, deploy and failures
* Keep everything as simple as possible

The responsibilities are clear:

1. You provide an application manifest
2. Experts design a cloud service architecture
4. Software automates setting up this architecture
3. Providers operate the underlying cloud services
4. Software automates changes to the architecture that offer security, performance or cost improvements

A "Minimum Viable Infrastructure" (MVI) methodology is derived from this.

If we understand the simplest set of primative cloud services needed to run any application, we can easily tell any cloud service provider to set them up. If the provider runs these at a high Quality-of-Service (QoS) and at a low cost, our apps will see good availability, security, performance and cost.

This book guides us through simple to complex types of applications and explains the cloud services we can use to satisfy our requirements.

## Background

This methodology is inspired by Adam Wiggins' [The Twelve-Factor App](https://12factor.net/). What Twelve-Factor does for understanding how to build apps, MVI guide does for understanding how to build cloud systems to support apps.

## Who is this book for?

The primary purpose is educational. Any technician can read this to better understand what services "the cloud" provides, why we need them, and how to use them.

The secondary purpose is practical. Any developer or ops engineer can use the tutorials and tools to set up real, production-ready services.

The final purpose is strategic. Anyone responsible for picking cloud providers can use this as a map to navigate the always evolving landscape.

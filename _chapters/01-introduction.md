---
title: Introduction
---

The goal is simple: take a web app and run it forever in the cloud.

The best practices are understood:

* Declare everything your app needs in code
* Use reliable cloud services
* Automate everything around cloud service setup, changes and failures
* Keep everything as simple as possible

The responsibilities are clear:

1. You provide an application manifest
2. A Community of Experts designs a cloud service architecture
4. Software automates setting up this architecture
3. Providers operate the underlying cloud services
4. Software automates changes to the architecture that offer security, performance or cost improvements

The "Minimum Viable Infrastructure" (MVI) methodology is derived from this.

If we understand the simplest set of primative infrastructure services needed to run any application, we can tell a cloud service provider how to set them up to bring our app online.

If a provider runs these infrastructure services with a high Quality-of-Service (QoS) our app will see excellent uptime with minimal operations on our part.

If we can safely modify these infrastructure services our app, we can maintain availability while adding security, performance and cost improvements over time.

This book enumerates the minimal infrastructure services that are available in the cloud, and guides us through how these are used to support simple to increasingly complex apps.

## Background

This book is inspired by Michael Hartl's [Ruby on Rails Tutorial](https://www.railstutorial.org/) and Adam Wiggins' [The Twelve-Factor App](https://12factor.net/).

The Rails Tutoral teaches you how to develop an application. Twelve-Factor teaches you how to run your application as service. MVI teaches you how to assemble the underlying cloud services to support a Twelve-Factor Rails app.

## Who is this book for?

The primary purpose is educational. Any technician can read this to better understand what services "the cloud" provides, why we need them, and how to use them.

The secondary purpose is practical. Any developer or ops engineer can use the tutorials and tools to set up real production-ready infrastructure.

The final purpose is strategic. Any decison maker can use this as a map to navigate the always evolving landscape of cloud services and cloud providers.

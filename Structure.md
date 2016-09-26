1. Introduction
2. VM
3. VPC
4. Crypto
5. Container
6. Registry
7. Load Balancer
8. Database

Service Chapters
  What is it?
    One sentence definition
    Supporting paragraphs if necessary

  Why do we need it?

  What does it depend on?
    Architecture diagram

  How does it work?
    Illustration

  What are the "knobs" and "guages"?

--

Theses
  1. To support an application we need:
    Secure Compute
      CPU
      Memory
      Network
      Crypto

    App Workload
      Package
      Config
      Data
      Proxy

    Visibility
      Logs
      Metrics
      Events

  2. A single computer can provide this but has challenges
    SPOF
    Fragile interfaces
    Constant pricing
    Coarse scaling

  3. A Service Oriented Architecture (SOA) can provide this and has benefits
    Service Level Agreement
    API
    Automation
    Utility pricing
    Independent scaling

  4. An SOA is derived from:
    Secure Compute
      CPU/Memory    Virtual Machine
      Network       Virtual Private Cloud
      Crypto        HSM  

    App Workload
      Package       Container, Image
      Config        Crypto, Blob
      Data          Database
      Proxy         Load Balancer

    Visibility
      Logs          Logs
      Metrics       Metrics
      Events        Key-Value, Blob

  5. Therefore, we can build an SOA with 11 services to support any application.

  6. There are additional best practices to manage an application:
    Build / Release / Run




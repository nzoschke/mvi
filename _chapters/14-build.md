---
title: Build a Custom Image
permalink: /build
---

# Build a Custom Image

Now that we can run [Hello World](hello-world), we need to customize the web server response.

This customization poses a challenge.

First, we need a way to specify in code our new layer of customization. Next, we need place to push any new custom data. Finally we need a way to pull the custom data to run it as a Container.

So we need build configuration and a Registry Service.

We can specify our build configuration by adding a `Dockerfile` that adds a [Layer](glossary#layer) on top of the pre-built Apache [httpd Image](https://hub.docker.com/_/httpd/).

```Dockerfile
FROM httpd
COPY ./public-html/ /usr/local/apache2/htdocs/
```

```yaml
web:
  build: .
  ports:
    - 80:80
```
{:.left}

```text
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
┌────────┐          
│Registry│          
└────────┘          
```
{:.right}

The Registry will provide an API and persistance for pushing and pulling custom layers of data like our new `public-html` directory.

A Build System will push layers to the Registry and the Container Service will pull layers when starting new Cotnainers.
---
title: Infrastructure Services
---

The following twelve infrastructure services offer everything we need to run, operate and manage the lifecycle of an application.

```ascii
     https                                        
  ┌────▽──────────────────────────────┐           
┌─┤           Load Balancer           ├──────────┐
│ └───────────────────────────────────┘          │
│┌─────────────────┐┌─────────────────┐          │
││┏━━━━━┓┏━━━━━━━━┓││     ┏━━━━━┓     │          │
││┃web 1┃┃worker 1┃││     ┃web 2┃     │          │
││┗━━━━━┛┗━━━━━━━━┛││     ┗━━━━━┛     │          │
││   Instance 1    ││   Instance 2    │┌────────┐│
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

- Computing
    - Instances
- Security
    - VPC
    - Crypto
- Application Workload
    - Containers
    - Registry
    - Load Balancer
- Application Data
    - Database
    - Shared File System
- Operational
    - Logs
    - Metrics
- Accounting
    - Key/Value Store
    - Blob Store

<br style="clear: both;" />

{% for s in site.services %}
<h2><a href="{{ s.url }}">{{ forloop.index }}. {{ s.title }}</a></h2>
<h3>{{ s.excerpt }}</h3>
{% endfor %}

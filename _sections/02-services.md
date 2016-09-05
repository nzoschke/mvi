---
title: Infrastructure Services
---

The following twelve services offer everything we need to run and operate an application.

We will take a base computing serving, then add security services, application workload and data services, and finally operational services.

{% for s in site.services %}
<h2>{{ forloop.index }}. {{ s.title }}</h2>
<h3>{{ s.excerpt }}</h3>
{% endfor %}

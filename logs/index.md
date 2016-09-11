---
layout: default
title: Logs
---

Logs!

{% for log in site.logs %}
  <h2>{{ log.title }}</h2>
{% endfor %}
---
layout: default
title: Logs
---

Logs!

{% for log in site.logs %}
   <li><a href="{{ log.url }}">{{ log.title }}</a></li>
{% endfor %}
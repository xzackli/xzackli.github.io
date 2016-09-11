---
layout: default
title: Logs
---

Logs!

{% for log in site.logs %}
   <a href="{{ log.url }}">{{ log.title }}</a> 
{% endfor %}
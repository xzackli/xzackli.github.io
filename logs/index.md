---
layout: default
title: Logs
---

Logs!

{% for log in site.logs %}
   <li><a href="{{ page.url }}">{{ page.title }}</a></li>
{% endfor %}
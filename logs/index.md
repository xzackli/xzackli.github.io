---
layout: default
title: Logs
---

Logs!

{% for album in site.logs %}
  <h2>{{ album.title }}</h2>
{% endfor %}
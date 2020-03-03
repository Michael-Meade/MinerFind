
---
layout: default
title: Blog
---
{% for Projects in site.Projects %}
  <li><a href="{{ page.url }}">{{ page.title }}</a></li>
{% endfor %}

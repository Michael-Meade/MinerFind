
---
layout: default
title: Blog
---
{% for Projects in site.Projects %}
  <h3><a title="{{ page.title }}" href="{{ page.url | prepend: site.baseurl }}">{{ page.title }}</a></h3>
{% endfor %}

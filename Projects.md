
---
layout: default
title: Blog
---
{% for Projects in site.Projects %}
  <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
  </li>
{% endfor %}

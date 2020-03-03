## Projects
---
layout: default
title: Blog
---
<h1>Latest Posts</h1>

  {% for projects in site.posts %}
    <li>
      <h2><a href="{{ projects.url }}">{{ projects.title }}</a></h2>
      <p>{{ projects.excerpt }}</p>
    </li>
  {% endfor %}
</ul>

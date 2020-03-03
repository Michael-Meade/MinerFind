## Posts

<ul>
  {% for post in site._Projects%}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>

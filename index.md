
## Posts

<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a><br>
      {{ post.date | date_to_string }} - {{post.author }}
    </li>
  {% endfor %}
</ul>

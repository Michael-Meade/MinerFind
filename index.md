
## Posts

<ul>
  {% for post in site.posts %}

      <h1>{{ post.title }}</h1>
      <li>
        <a href="{{ post.url }}">{{ post.title }}</a><br>
         {{ post.date | date_to_string }}
      </li>

  {% endfor %}
</ul>

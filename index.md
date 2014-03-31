---
layout: page
tagline: Supporting tagline
---
{% include JB/setup %}

<ul class="posts">
  {% for post in site.posts %}
    <h3><a href="{{ BASE_PATH }}{{ post.url }}">{{ post.date | date_to_string }} &raquo; {{ post.title }}</a></h3>
    <p>{{ post.excerpt }} <a href="{{ BASE_PATH }}{{ post.url }}">[Read More...]</a></p>
  {% endfor %}
</ul>


---
layout: default
title: List of all posts in the blog
---

# List of all posts in the project

<ul>
{% for post in site.posts %}
 <li><a href="{{ post.url }}">{{ post.title }}</a></li>
{% endfor %}
</ul>

{% if page.author %}
  {% include author/{{page.author}}.html %}
{% endif %}

[back](./)


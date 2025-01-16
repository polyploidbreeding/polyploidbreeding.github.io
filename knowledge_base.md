---
layout: default
title: List knowledge-base posts
---

# Knowledge base

Here we list the posts that fall in the category "knowledge base", where we write something which is related to 
the scientific disciplines covered by the project.

<ul>
{% for category in site.categories %}
  <li><a name="{{ category | first }}">{{ category | first }}</a>
    <ul>
    {% for post in category.last %}
      <li><a href="{{ post.url }}">{{ post.title }}</a></li>
    {% endfor %}
    </ul>
  </li>
{% endfor %}
</ul>

[back](./)


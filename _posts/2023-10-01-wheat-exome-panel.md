---
layout: post
title: "Wheat exome sequencing panels"
author: "Filippo Biscarini"
date: "2023-11-02"
categories: KNOWLEDGE BASE
tags: "polyploid genome" sequencing wheat exome
---

From: IWGSC (International Wheat Genome Sequencing Consortium) webinar series


### Sources
[Comprehensive Cost Effective Exome Sequencing with Arbor Biosciences Wheat Exome Panel](https://www.youtube.com/watch?v=8ExNVak8UTU)

{% for tag in post.tags %}
  {% assign tag_slug = tag | slugify: "raw" %}
  <a class="tag-link"
    href={{ site.baseurl | append: "/tags/" | append: tag_slug | append: "/" }}
    rel="category tag">
    #{{ tag }}
  </a>
{% endfor %}


{% if page.author %}
  {% include author/{{page.author}}.html %}
{% endif %}


---
layout: page
title: Progress
---

{% for post in site.posts %}
  {% if post.categories contains 'progress' %}
  * {{ post.date | date_to_string }} &raquo; [ {{ post.title }} ]({{ post.url }})
  {% endif %}
{% endfor %}
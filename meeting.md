---
layout: page
title: Meeting Note
---

{% for post in site.posts %}
  {% if post.categories contains 'meeting' %}
  * {{ post.date | date_to_string }} &raquo; [ {{ post.title }} ]({{ post.url }})
  {% endif %}
{% endfor %}
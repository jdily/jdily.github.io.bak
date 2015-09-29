---
layout: page
title: Drafts
---

{% for post in site.posts %}
  {% if post.categories contains 'draft' %}
  * {{ post.date | date_to_string }} &raquo; [ {{ post.title }} ]({{ post.url }})
  {% endif %}
{% endfor %}
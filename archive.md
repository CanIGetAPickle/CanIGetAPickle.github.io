---
layout: page
title: Archive
---

## Posts of Past and Present

{% for post in site.posts %}
  * {{ post.date | date_to_string }} &rarr; [ {{ post.title }} ]({{ post.url }})
{% endfor %}
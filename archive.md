---
layout: page
title: Archive
---

## Posts of Past and Present

{% for post in site.posts %}
  * {{ post.date | date: "%m-%d-%Y" }} &rarr; [ {{ post.title }} ]({{ post.url }})
{% endfor %}
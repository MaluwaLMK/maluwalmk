---
layout: archive
permalink: /pages/articles
title: "Posts by Year"
author_profile: true
---

{% include base_path %}
{% capture written_year %}'2017'{% endcapture %}
{% for post in site.posts %}
  {% capture year %}{{ post.date | date: '%Y' }}{% endcapture %}
  {% include archive-single.html %}
{% endfor %}

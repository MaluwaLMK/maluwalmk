---
layout: archive
permalink: /pages/articles
title: "Articles"
author_profile: true
excerpt: "_Stay Hungry, Stay Foolish.<br> A learning route of computer vision and machine learning._"
header:
  overlay_image: /assets/images/home-head.jpg
---

{% include base_path %}
{% capture written_year %}'2017'{% endcapture %}
{% for post in site.posts %}
  {% capture year %}{{ post.date | date: '%Y' }}{% endcapture %}
  {% include archive-single.html %}
{% endfor %}

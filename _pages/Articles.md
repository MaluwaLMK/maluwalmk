---
layout: archive
permalink: /pages/articles
title: "Articles"
author_profile: true
excerpt: "_Analytics, Statistics, Statistical Programming, Economics and Fun._"
header:
  overlay_image: /assets/images/network-viz.jpg
---

{% include base_path %}
{% capture written_year %}'2017'{% endcapture %}
{% for post in site.posts %}
  {% capture year %}{{ post.date | date: '%Y' }}{% endcapture %}
  {% include archive-single.html %}
{% endfor %}

---
layout: archive
permalink: /
header:
  overlay_color: "#5e616c"
  overlay_image: mm-home-page-feature.jpg
title: "Latest Posts"
author_profile: true
modified: 2016-04-18T16:39:37-04:00
---

{% include base_path %}

<div class="grid__wrapper">
  {% for post in site.categories.articles limit:5 %}
    {% include archive-single.html %}
  {% endfor %}
</div>

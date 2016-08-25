---
layout: splash
permalink: /
excerpt: "Minimal Mistakes is a flexible two-column Jekyll theme."
layouts_gallery:
  - url: mm-layout-splash.png
    image_path: mm-layout-splash.png
    alt: "splash layout example"
  - url: mm-layout-single-meta.png
    image_path: mm-layout-single-meta.png
    alt: "single layout with comments and related posts"
  - url: mm-layout-archive.png
    image_path: mm-layout-archive.png
    alt: "archive layout example"
author_profile: true
modified: 2016-04-18T16:39:37-04:00
---

<!--header:-->
<!--  overlay_color: "#5e616c"-->
<!--  overlay_image: mm-home-page-feature.jpg-->
<!--  cta_label: "<i class='fa fa-download'></i> Install Now"-->
<!--  cta_url: "/docs/quick-start-guide/"-->
<!--  caption:-->
<!------->

{% include base_path %}
{% include group-by-array collection=site.posts field="categories" %}

{% for category in group_names %}
  {% assign posts = group_items[forloop.index0] %}
  <h2 id="{{ category | slugify }}" class="archive__subtitle">{{ category }}</h2>
  {% for post in posts %}
    {% include archive-single.html %}
  {% endfor %}
{% endfor %}

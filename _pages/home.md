---
layout: archive
permalink: /
header:
  image: https://unsplash.it/g/1000/700?random
  caption: "Photo credit: [**Unsplash**](https://unsplash.com)"
author_profile: true
modified: 2016-08-26T16:39:37-04:00
---

{% include base_path %}

<div class="grid__wrapper">
  <h2>Recent Posts</h2>
  {% for post in site.posts %}
    {% include archive-single.html %}
  {% endfor %}
</div>

<!--{% include base_path %}-->

<!--<div class="grid__wrapper">-->
<!--  <h2>Recent Posts</h2>-->
<!--  {% for post in site.categories.articles %} <!--limit: 5 %}-->-->
<!--    {% include archive-single.html %}-->
<!--  {% endfor %}-->
<!--</div>-->

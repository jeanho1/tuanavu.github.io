---
layout: archive
permalink: /
author_profile: true
modified: 2016-04-18T16:39:37-04:00
---

<!--{% include base_path %}-->

<!--<div class="grid__wrapper">-->
<!--  <h2>Recent Posts</h2>-->
<!--  {% for post in site.categories.articles limit:5 %}-->
<!--    {% include archive-single.html %}-->
<!--  {% endfor %}-->
<!--</div>-->

{% include base_path %}

<h3 class="archive__subtitle">Recent Posts</h3>

{% for post in paginator.posts %}
  {% include archive-single.html %}
{% endfor %}

{% include paginator.html %}

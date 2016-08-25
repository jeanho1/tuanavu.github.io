---
layout: archive
permalink: /
author_profile: true
modified: 2016-04-18T16:39:37-04:00
---


{% include base_path %}

<div class="grid__wrapper">
  {% for post in site.posts %}
    {% include archive-single.html type="grid" %}
  {% endfor %}
</div>
<!--{% capture written_year %}'None'{% endcapture %}-->
<!--{% for post in site.posts %}-->
<!--  {% capture year %}{{ post.date | date: '%Y' }}{% endcapture %}-->
<!--  {% if year != written_year %}-->
<!--    <h2 id="{{ year | slugify }}" class="archive__subtitle">{{ year }}</h2>-->
<!--    {% capture written_year %}{{ year }}{% endcapture %}-->
<!--  {% endif %}-->
<!--  {% include archive-single.html %}-->
<!--{% endfor %}-->

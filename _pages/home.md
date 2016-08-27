---
layout: archive
permalink: /
author_profile: true
modified: 2016-04-18T16:39:37-04:00
---


{% include base_path %}

<!--{% if page.image.feature %}<div class="image-wrap">-->
<!--  <img src="{{ site.url }}/images/{{ page.image.feature }}" alt="{{ page.title }} feature image" itemprop="primaryImageOfPage">-->
<!--  {% if page.image.credit %}<span class="image-credit">Photo Credit: <a href="{{ page.image.creditlink }}">{{ page.image.credit }}</a></span>{% endif %}-->
<!--</div><!-- /.image-wrap -->-->
<!--{% endif %}-->

<!--{% include _browser-upgrade.html %}-->

<!--{% include _navigation.html %}-->

{% if page.image.feature %}
  <div class="image-wrap">
  <img src=
    {% if page.image.feature contains 'http' %}
      "{{ page.image.feature }}"
    {% else %}
      "{{ site.url }}/images/{{ page.image.feature }}"
    {% endif %}
  alt="{{ page.title }} feature image">
  {% if page.image.credit %}
    <span class="image-credit">Photo Credit: <a href="{{ page.image.creditlink }}">{{ page.image.credit }}</a></span>
  {% endif %}
  </div><!-- /.image-wrap -->
{% endif %}



<div class="grid__wrapper">
  <h3><a href="{{ site.url}}/categories/">Articles</a></h3>
  {% for post in site.posts limit:5 %}
    {% include archive-single.html %}
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

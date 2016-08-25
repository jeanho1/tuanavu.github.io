---
layout: splash
permalink: /
header:
  overlay_color: "#5e616c"
  overlay_image: mm-home-page-feature.jpg
  cta_label: "<i class='fa fa-download'></i> Install Now"
  cta_url: "/docs/quick-start-guide/"
  caption:
---

<div id="index">
  <h3><a href="{{ site.url}}/articles/">Recent Articles</a></h3>
  {% for post in site.posts limit:5 %}    
  <article>
    {% if post.link %}
      <h2 class="link-post"><a href="{{ site.url }}{{ post.url }}" title="{{ post.title }}">{{ post.title }}</a> <a href="{{ post.link }}" target="_blank" title="{{ post.title }}"><i class="fa fa-link"></i></h2>
    {% else %}
      <h2><a href="{{ site.url }}{{ post.url }}" title="{{ post.title }}">{{ post.title }}</a></h2>
      <p>{% if post.description %}{{ post.description }}{% else %}{{ post.content | strip_html | strip_newlines | truncate: 120 }}{% endif %}</p>
    {% endif %}
  </article>
  {% endfor %}
</div>

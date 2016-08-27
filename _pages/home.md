---
layout: page
permalink: /
title: Latest Posts
excerpt: "An archive of articles sorted by date."
author_profile: true
modified: 2016-04-18T16:39:37-04:00

---

<ul class="post-list">
{% for post in site.categories.articles %} 
  <li><article><a href="{{ site.url }}{{ post.url }}">{{ post.title }} <span class="entry-date"><time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%B %d, %Y" }}</time></span></a></article></li>
{% endfor %}
</ul>

---
layout: splash
permalink: /
header:
  overlay_color: "#5e616c"
  overlay_image: mm-home-page-feature.jpg
  cta_label: "<i class='fa fa-download'></i> Install Now"
  cta_url: "/docs/quick-start-guide/"
  caption:
excerpt: 'A flexible two-column Jekyll theme. Perfect for personal sites, blogs, and portfolios hosted on GitHub or your own server.<br /> <small><a href="https://github.com/mmistakes/minimal-mistakes/releases/tag/3.4.3">Latest release v3.4.3</a></small><br /><br /> {::nomarkdown}<iframe style="display: inline-block;" src="https://ghbtns.com/github-btn.html?user=mmistakes&repo=minimal-mistakes&type=star&count=true&size=large" frameborder="0" scrolling="0" width="160px" height="30px"></iframe> <iframe style="display: inline-block;" src="https://ghbtns.com/github-btn.html?user=mmistakes&repo=minimal-mistakes&type=fork&count=true&size=large" frameborder="0" scrolling="0" width="158px" height="30px"></iframe>{:/nomarkdown}'
---

<div id="index">
  <h3><a href="{{ site.url}}/posts/">Recent Projects</a></h3>
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

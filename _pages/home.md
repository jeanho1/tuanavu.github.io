---
layout: splash
permalink: /
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
{% capture written_year %}'None'{% endcapture %}
{% for post in site.posts %}
  {% capture year %}{{ post.date | date: '%Y' }}{% endcapture %}
  {% if year != written_year %}
    <h2 id="{{ year | slugify }}" class="archive__subtitle">{{ year }}</h2>
    {% capture written_year %}{{ year }}{% endcapture %}
  {% endif %}
  {% include archive-single.html %}
{% endfor %}

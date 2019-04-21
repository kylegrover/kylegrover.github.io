---
layout: page
title: Blog
date: 2019-04-20 18:45:44 +0000

---
Things I've written about stuff and stuff I've written about things:

{% for category in site.categories %}
## <a href="/blog/{{ category | first | slugify }}" name="{{ category | first }}">{{ category | first }}</a>
<ul>
{%- for post in category.last -%}
  <li><a href="{{ post.url }}">{{ post.title }}</a></li>
{%- endfor -%}
</ul>
{% endfor %}
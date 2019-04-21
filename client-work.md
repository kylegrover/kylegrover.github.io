---
layout: client-work-index
title: Client Work

---
#### a handful of projects I've enjoyed working on recently

{% for client in site.client-work %}
 [{{ client.title }}]({{ client.url }})<br>
 {{ client.content | strip_html | truncatewords:16 }}
{% endfor %}

{% comment %}

grid of logos, left and right arrows to slide to overviews of each project, clicking logos goes directly to that project page. 
title goes from 

"Client Work"
 
to (ie)

"[Client Work]() > Cruz Culture"

{% endcomment %}
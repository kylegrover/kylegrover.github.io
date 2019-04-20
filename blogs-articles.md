---
layout: page
title: Blogs
permalink: "/blogs"
date: 2019-04-20 18:45:44 +0000

---
Things I've written about stuff and stuff I've written about things:

### [Web Dev](https://kylegrover.com/blog/web-dev)

### [Code Art](https://kylegrover.com/blog/code-art)

### [Music](https://kylegrover.com/blog/music)


<ul>
{% for category in site.categories %}
  <li><a name="{{ category | first }}">{{ category | first }}</a>
    <ul>
    {% for post in category.last %}
      <li><a href="{{ post.url }}">{{ post.title }}</a></li>
    {% endfor %}
    </ul>
  </li>
{% endfor %}
</ul>

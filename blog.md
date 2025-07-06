---
layout: page
title: vforch's blog
permalink: /blog/
---
<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.date | date: "%b %-d, %Y" }} – {{ post.title }}</a>
      {% if post.tags %} • <small>{{ post.tags | join: ", " }}</small>{% endif %}
    </li>
  {% endfor %}
</ul>

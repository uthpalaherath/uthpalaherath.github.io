---
layout: archive
permalink: /articles/
title: "Articles"
author_profile: true
header: 
    image: "/assets/images/beach.jpg"
---

<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}{{post.date}}</a>
    </li>
  {% endfor %}
</ul>
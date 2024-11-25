---
layout: home
title: Posts
permalink: /posts/
author_profile: true
---

<head> {% include katex.html %} </head>
<h2>Latest Posts</h2>

<ul>
  {% for post in site.posts %}
    <li>
	<h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
      {{ post.excerpt }}
    </li>
  {% endfor %}
</ul>
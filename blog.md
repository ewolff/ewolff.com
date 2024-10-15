---
title: Eberhard Wolff's Blog
---

<ul>
{% for post in site.posts %}
   <li>
	<a href="{{ post.url }}">{{ post.title }}</a><br>{{ post.date | date:	" %Y-%m-%d" }}
	<p>
	{{ post.description }}
	</p>
   </li>
{% endfor %}
</ul>

[Feed](/feed.xml)

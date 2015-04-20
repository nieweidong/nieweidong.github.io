---
layout: page
title: 各种杂记
excerpt: "聂微东,前端,前端面试,前端攻略,前端博客,JavaScript,JS,React,Gulp,Nodejs,darren"
search_omit: true
---

<ul class="post-list">
{% for post in site.categories.note %}
  <li><article><a href="{{ site.url }}{{ post.url }}">{{ post.title }} <span class="entry-date"><time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%B %d, %Y" }}</time></span>{% if post.excerpt %} <span class="excerpt">{{ post.excerpt }}</span>{% endif %}</a></article></li>
{% endfor %}
</ul>

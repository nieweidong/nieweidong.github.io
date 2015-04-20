---
layout: page
title: "Search"
date:
modified:
excerpt: "聂微东,前端,前端面试,前端攻略,前端博客,JavaScript,JS,React,Gulp,Nodejs,darren"
image:
  feature:
search_omit: true
sitemap: false
---

<!-- Search form -->
<form method="get" action="{{ site.url }}/search/" data-search-form class="simple-search">
  <label for="q">Search {{ site.title }} for:</label>
  <input type="search" name="q" id="q" placeholder="What are you looking for?" data-search-input id="goog-wm-qt" autofocus />
  <input type="submit" value="Search" id="goog-wm-sb" />
</form>

<!-- Search results placeholder -->
<h6 data-search-found>
  <span data-search-found-count></span> result(s) found for &ldquo;<span data-search-found-term></span>&rdquo;.
</h6>
<ul class="post-list" data-search-results></ul>

<!-- Search result template -->
<script type="text/x-template" id="search-result">
  <li><article>
    <a href="##Url##">##Title## <span class="excerpt">##Excerpt##</span></a>
  </article></li>
</script>

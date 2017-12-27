---
layout: default
title: Blog Posts
---
{% include header.html %}

<body>
  
<article>
    <p>Hi, I am <b>Sid Rao</b>. Welcome to my <a href="/about/">blog</a>!</p>
    <p>Primary purpose of this blog is to reflect the observation and opinions of my academic journey. However, I try to rant about the things that matter to me, such as Internet freedom and digital rights. </p>
    <p>This blog is <a target="_blank" href="https://github.com/sidtechnical/sidtechnical.github.io">open source</a>. Factual errors or spelling/grammar corrections are always welcome (and much appreciated) via pull requests.</p>

<div id="home">
	<h1 class="title">
    <i class="fa fa-bookmark"></i> Blog Posts
  </h1>
  <!-- <h2><i class="fa fa-bookmark"></i> Blog Posts</h2> -->
  <ul id="blog-posts" class="posts">
    {% for post in site.posts %}
      <li><span>{{ post.date | date_to_string }} &raquo;</span> <a href="{{ post.url }}">{{ post.title }}</a> </li>
    {% endfor %}
  </ul>
</div>

</article>

<hr/>

{% include fine-print.html %}

</body>



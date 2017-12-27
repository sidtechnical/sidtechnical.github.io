---
layout: post
title: Archives
skip_related: true
---

{% assign totalwords = 0 %}
{% for post in site.posts %}
  {% assign wordcount = post.content | number_of_words %}
  {% assign totalwords = totalwords | plus: wordcount %}
{% endfor %}

Even though I intend to blog regularly, somehow I get busy with other important things in life, for example, cooking, traveling, and sleeping. I dream to be a frequent blogger someday. I believe that blogging about any topic not only helps me understand that topic better, but also helps me communicate better with general public.

Since {{ site.posts.last.date | date: "%B %d, %Y" }}, I've written {{ totalwords }}. I hope you've enjoyed reading at least some of those words. My favorite posts are **bolded** below.

An archive of these blog posts, categorizied based on their tags is also available [HERE][categories].

[categories]: /categories/

<div id="archive">
{% for post in site.posts %}
  {% assign currentdate = post.date | date: "%Y" %}
  {% if currentdate != date %}
    {% unless forloop.first %}</ul>{% endunless %}
<h2>{{ currentdate }}</h2>
<ul>
    {% assign date = currentdate %}
  {% endif %}
  <li {% if post.favorite and post.layout != "writeup" %}class="favorite"{% endif %}>
    <a href="{{ post.url }}">{{ post.title }}{% if post.layout == "writeup" %} (Book Writeup){% endif %}</a>
  </li>
  {% if forloop.last %}</ul>{% endif %}
{% endfor %}
</div>



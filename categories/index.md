---
layout: default
title: Categorizing the blog based on their tags
---

{% include header.html %}

<article>
    <p>This is the categorizing the blog posts based on their tags. Please note that the post might have been tagged with multiple tags, which is why you see some repetitions.
    <br><br>An archive of these blog posts categorizied based on their year is also available <a href="/archive/"><b>here</b></a>.</p>
    <hr />
</article>

<div id="series">
  {% for series in site.data.series %}
    <h3 id="{{ series.tag_name }}">{{ series.name }}</h3>
    <p>{{ series.desc }}</p>

    <ul>
      {% for post in site.tags[series.tag_name] %}
        <li {% if post.favorite %}class="favorite"{% endif %}>
          <a href="{{ post.url }}">{{ post.title }}</a>
        </li>
      {% endfor %}
    </ul>
  {% endfor %}
</div>
---

{% include fine-print.html %}
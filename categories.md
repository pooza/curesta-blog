---
layout: default
title: カテゴリ一覧
permalink: /categories/
---

# カテゴリ一覧

<ul class="category-list">
  {% for category in site.categories %}
    {% assign name = category[0] %}
    {% assign posts = category[1] %}
    <li><a href="#{{ name | slugify }}">{{ name }}</a> ({{ posts | size }})</li>
  {% endfor %}
</ul>

{% for category in site.categories %}
  {% assign name = category[0] %}
  {% assign posts = category[1] %}
  <h2 id="{{ name | slugify }}">{{ name }}</h2>
  <ul class="post-list">
    {% for post in posts %}
      <li>
        <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
        <small>({{ post.date | date: "%Y-%m-%d" }})</small>
      </li>
    {% endfor %}
  </ul>
{% endfor %}
